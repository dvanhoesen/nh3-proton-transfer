# NH3 Proton-Transfer AIMD Environment

## Science Objective

See README_science_objective.md

---

## Local Development Environment

The local development system is an Apple Silicon Mac running Docker through Colima.


### Colima

Current Colima configuration:

```text
ARCH:    aarch64
CPUS:    8
MEMORY:  20 GiB
DISK:    100 GiB
RUNTIME: docker
```

Docker is native ARM64 end-to-end:

```text
Docker client: darwin/arm64
Docker server: linux/arm64
```

The Colima VM uses QEMU but runs an ARM64 Linux guest, so the CP2K image is built natively for `linux/arm64` rather than using x86 emulation.

---

## CP2K + PLUMED Container

The working simulation image is:

```text
nh3-cp2k-plumed:2026.2-arm64
```

Confirmed software versions:

```text
CP2K version:       2026.2
CP2K source commit: 67b5da8
PLUMED version:     2.10
Compiler:           GCC 13.3.0
MPI:                MPICH 5.0.1
```

CP2K reports the following compiled features:

```text
omp libint fftw3 libxc parallel scalapack plumed2
```

This confirms that CP2K is linked against PLUMED and has MPI/OpenMP support.


### Build Notes

- `python3-venv` is required by the CP2K 2026.2 `make_cp2k.sh` build workflow. Without it, the build failed while creating a Python virtual environment.
- The CP2K 2026.2 helper text inconsistently refers to `libint`, but the accepted feature name for the build script is `libint2`.
- The final image requires these runtime library locations:

```text
/opt/cp2k/install/lib
/opt/cp2k/spack/spack/opt/spack/view/lib
```

These paths are already included in `LD_LIBRARY_PATH` in the Dockerfile.

---

## Packmol Preparation Container

A separate lightweight image is used for initial structure generation:

```text
nh3-prep:arm64
```

Dockerfile:

```dockerfile
FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    packmol \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /work
```

Packmol version:

```text
20.14.3
```

Note: `packmol --version` does not behave as a conventional version query in this package; the version is displayed in the startup banner.

---

## Basic CP2K Validation

A single isolated water molecule was used to validate the CP2K runtime.

Input:

```text
inputs/test/h2o_energy.inp
```

Calculation details:

```text
RUN_TYPE ENERGY
PBE
DZVP-MOLOPT-GTH
GTH-PBE
15 Å cubic cell
```

Single-process result:

```text
ENERGY| Total FORCE_EVAL ( QS ) energy [hartree] -17.2209629
```

The run completed with zero warnings.

The same calculation was then run under MPI with two ranks and two OpenMP threads. The resulting energy was:

```text
-17.2209629 Hartree
```

The agreement confirms that:

- CP2K runtime works.
- MPI works.
- OpenMP-enabled `cp2k.psmp` works.
- Basis and pseudopotential files are accessible.
- macOS-to-container volume mounting works.

---

## PLUMED Integration Validation

A simple PLUMED input was created:

```text
inputs/test/plumed.dat
```

```text
d: DISTANCE ATOMS=2,3
PRINT ARG=d FILE=runs/test/COLVAR STRIDE=1
```

A five-step water MD test was run using:

```text
inputs/test/h2o_plumed_md.inp
```

with:

```text
RUN_TYPE MD
ENSEMBLE NVE
STEPS 5
TIMESTEP 0.5
```

The CP2K input included:

```text
&MOTION
  &MD
    ENSEMBLE NVE
    STEPS 5
    TIMESTEP 0.5
  &END MD

  &FREE_ENERGY
    METHOD METADYN

    &METADYN
      USE_PLUMED .TRUE.
      PLUMED_INPUT_FILE inputs/test/plumed.dat
    &END METADYN
  &END FREE_ENERGY
&END MOTION
```

PLUMED successfully wrote:

```text
runs/test/COLVAR
```

Example output:

```text
#! FIELDS time d
0.000500 0.152984
0.001000 0.154795
0.001500 0.156734
0.002000 0.158677
0.002500 0.160492
```

This confirms that CP2K can successfully call PLUMED during an MD calculation.

---

## NH3 + Water Starting System

Template structures were created as:

```text
systems/templates/water.xyz
systems/templates/ammonia.xyz
```

### Water Template

```text
3
water
O   0.000000   0.000000   0.000000
H   0.957200   0.000000   0.000000
H  -0.239987   0.927297   0.000000
```

### Ammonia Template

```text
4
ammonia
N   0.000000   0.000000   0.116489
H   0.000000   0.939731  -0.271809
H   0.813831  -0.469865  -0.271809
H  -0.813831  -0.469865  -0.271809
```

Packmol was used to generate a periodic starting configuration containing:

```text
1 NH3 + 31 H2O
```

inside a nominal:

```text
9.8 × 9.8 × 9.8 Å
```

box.

Packmol input:

```text
systems/nh3_31h2o/packmol.inp
```

```text
tolerance 1.8
filetype xyz
output systems/nh3_31h2o/nh3_31h2o.xyz
seed 1234567

structure systems/templates/ammonia.xyz
  number 1
  inside box 0.5 0.5 0.5 9.3 9.3 9.3
end structure

structure systems/templates/water.xyz
  number 31
  inside box 0.5 0.5 0.5 9.3 9.3 9.3
end structure
```

Generated structure:

```text
systems/nh3_31h2o/nh3_31h2o.xyz
```

Total atom count:

```text
97
```

which is consistent with:

```text
4 atoms from NH3 + 31 × 3 atoms from H2O = 97 atoms
```

---

## First 97-Atom DFT Calculation

Current input:

```text
inputs/nh3_31h2o/pbe_energy.inp
```

Main settings:

```text
RUN_TYPE ENERGY
PBE
DZVP-MOLOPT-GTH
GTH-PBE
CUTOFF 400 Ry
REL_CUTOFF 50 Ry
EPS_SCF 1.0E-6
MAX_SCF 100
OT / DIIS
FULL_SINGLE_INVERSE preconditioner
9.8 Å cubic periodic cell
```

Coordinates are read from:

```text
systems/nh3_31h2o/nh3_31h2o.xyz
```

The calculation was run using:

```text
OMP_NUM_THREADS=2
mpirun -np 4 cp2k.psmp
```

Result:

```text
*** SCF run converged in    89 steps ***
ENERGY| Total FORCE_EVAL ( QS ) energy [hartree] -544.907235904524782
```

The 97-atom periodic NH3/H2O system therefore converges successfully at the PBE/DZVP level.

The relatively high 89-step SCF convergence should be investigated before launching long AIMD trajectories.

---

## Standard CP2K Container Invocation

The current working pattern is:

```bash
docker run --rm \
  -e OMP_NUM_THREADS=2 \
  -v "$PWD:/work" \
  -w /work \
  nh3-cp2k-plumed:2026.2-arm64 \
  mpirun -np 4 cp2k.psmp \
  -i <input> \
  -o <output>
```

The host project directory is mounted into the container at `/work`, while CP2K, PLUMED, MPI, and all runtime libraries remain inside the container.

---

## Current Status

The following components have been validated:

```text
native ARM64 Docker/Colima
        ↓
CP2K 2026.2 compilation
        ↓
MPI/OpenMP execution
        ↓
PLUMED 2.10 integration
        ↓
Packmol structure generation
        ↓
97-atom NH3 + 31 H2O periodic system
        ↓
successful PBE single-point DFT
```

The environment does not need to be rebuilt unless a software or configuration change is desired.

