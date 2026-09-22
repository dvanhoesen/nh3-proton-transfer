# Temperature-Dependent Ammonia–Ammonium Interconversion in Atmospheric Water

## Working title

**Raman vibrational signatures of temperature-dependent ammonia/ammonium interchange in atmospheric water from Ab initio molecular dynamics**

---

## Central question

How do natural above freezing temperature fluctuations alter the microscopic equilibrium between aqueous NH₃ and NH₄⁺, and can the associated restructuring of the water network be identified spectroscopically?

The study is intended to connect molecular-scale proton-transfer thermodynamics with atmospheric aqueous chemistry. Rather than treating temperature as a secondary sensitivity test, temperature is the main independent variable.

The central physical picture is:

```text
Temperature
    ↓
water-network structure and local electric fields
    ↓
NH₃ ⇌ NH₄⁺ protonation equilibrium
    ↓
Raman-active vibrational response
    ↓
implications for aqueous/gas-phase ammonia partitioning
```

The atmospheric system of interest is liquid water above freezing, especially cloud droplets, fog water, wet aerosol, and other dilute aqueous atmospheric environments subject to natural temperature cycles.

---

# Scientific motivation

Ammonia is highly water soluble and undergoes reversible protonation in aqueous solution. In the atmosphere, its distribution is governed by at least three coupled processes:

1. gas-to-water partitioning of neutral NH₃,
2. aqueous NH₃/NH₄⁺ acid–base equilibrium,
3. microscopic solvent reorganization that stabilizes or destabilizes protonated configurations.

The relevant atmospheric sequence is therefore better represented as

```math
\mathrm{NH_3(g) \rightleftharpoons NH_3(aq) \rightleftharpoons NH_4^+(aq)}.
```

For molecular proton-transfer simulations, the minimal water-only reaction remains useful:

```math
\mathrm{NH_3 + H_2O \rightleftharpoons NH_4^+ + OH^-},
```

but the atmospheric interpretation should be framed more generally through

```math
\mathrm{NH_4^+ + H_2O \rightleftharpoons NH_3 + H_3O^+},
```

or equivalently

```math
\mathrm{NH_4^+ \rightleftharpoons NH_3 + H^+}.
```

This distinction is important because real atmospheric water contains acids, bases, sulfate, nitrate, carbonate, organics, and other solutes that control pH. The AIMD study is therefore a molecular model of the intrinsic aqueous protonation process, not a complete cloud-chemistry model.

---

# Core hypothesis

**Natural temperature variations in liquid atmospheric water alter the hydrogen-bond configurations and local electric fields that stabilize aqueous ammonia and ammonium. Cooling should favor hydration structures associated with protonated NH₄⁺, while warming should increase the relative population of molecular NH₃ and ultimately favor NH₃ volatilization. These reversible changes should produce temperature-dependent vibrational signatures that connect the microscopic proton-transfer free-energy landscape to macroscopic atmospheric NH₃/NH₄⁺ partitioning.**

A key mechanistic question is whether temperature changes:

1. the **identity and structure of the reactive solvent motif**, or
2. mainly the **population of an otherwise similar reactive motif**.

These two cases imply different physical mechanisms.

### Scenario A: same mechanism, different population

```text
same proton-transfer precursor at all T
            ↓
P(precursor) changes strongly with T
            ↓
NH₃/NH₄⁺ equilibrium changes
```

### Scenario B: temperature-dependent mechanism

```text
T changes the transition-state solvent structure itself
            ↓
reactive topology and spectral signature evolve with T
```

Scenario B would be a stronger and more surprising result, but Scenario A would still be scientifically important because it would directly link thermal fluctuations to reactive water-network statistics.

---

# Why this is a useful atmospheric problem

Temperature affects ammonia chemistry through several distinct mechanisms that should be separated conceptually.

## 1. Aqueous acid–base equilibrium

The equilibrium

```math
\mathrm{NH_4^+ \rightleftharpoons NH_3 + H^+}
```

is temperature dependent. At fixed pH,

```math
\frac{[\mathrm{NH_3}]}{[\mathrm{NH_4^+}]} = 10^{\mathrm{pH}-pK_a(T)}.
```

Therefore ordinary atmospheric temperature changes can alter the molecular-ammonia fraction even without changing bulk composition.

## 2. Gas–aqueous partitioning

Neutral NH₃ is less strongly retained in warmer water. Warming can therefore drive

```math
\mathrm{NH_4^+(aq) \rightarrow NH_3(aq) \rightarrow NH_3(g)},
```

while cooling drives the reverse tendency:

```math
\mathrm{NH_3(g) \rightarrow NH_3(aq) \rightarrow NH_4^+(aq)}.
```

## 3. Solvent-network restructuring

The AIMD contribution is the molecular-scale link

```text
T
↓
hydrogen-bond topology
↓
local electric fields / solvent coordination
↓
proton-transfer free energy
↓
NH₃/NH₄⁺ populations
```

This provides a microscopic interpretation of the bulk temperature dependence.

---

# Atmospheric temperature window

The main study should focus on above-freezing liquid water under naturally plausible atmospheric conditions.

A practical baseline temperature series is:

```text
278 K   288 K   298 K   308 K
 5 °C    15 °C    25 °C    35 °C
```

This range is broad enough to expose thermodynamic trends while avoiding complications specific to deeply supercooled water.

An alternative series is:

```text
273/275 K   288 K   298 K   313 K
```

which provides a larger span and stronger overlap with some experimental temperature-dependent water/ammonia datasets.

Near-freezing simulations should be treated carefully because liquid-water structure becomes more temperature sensitive and finite-size/electronic-structure artifacts may become more pronounced.

---

# Relationship to previous work

Several pieces of the problem are already established independently.

## Acid–base free-energy coordinates

Grifoni, Piccini, and Parrinello developed collective variables capable of describing aqueous acid–base reactions without assigning a proton permanently to a specific water molecule. Their ammonia calculation used SCAN AIMD and well-tempered metadynamics for one NH₃ plus 31 H₂O molecules at 300 K.

Relevant concept:

```math
F(s_p,s_d) = -k_B T \ln P(s_p,s_d),
```

where

- `s_p` describes protonation state,
- `s_d` describes acid/base defect separation.

This provides the natural starting point for the present work.

## Solvent preorganization and local electric fields

Cassone et al. showed that proton transfer in aqueous ammonia is associated with a cooperative local water structure involving approximately five neighboring molecules and enhanced local electric fields.

This means the novelty should **not** be stated as discovery of solvent preorganization itself.

The new question is instead:

> How does the probability and spectroscopy of that preorganized solvent environment change with temperature?

## NH₃ and NH₄⁺ hydration

Existing spectroscopy and AIMD show that:

- NH₃ is a strong hydrogen-bond acceptor at the nitrogen lone pair,
- NH₄⁺ is a strong hydrogen-bond donor,
- NH₄⁺ can exhibit unusually high coordination and bifurcated hydrogen bonds,
- these hydration motifs affect rotational and vibrational dynamics.

## Temperature-sensitive ammonia–water structure

Experimental and simulation studies indicate that ammonia hydration and the surrounding water network change with temperature. Raman measurements of aqueous ammonia show temperature-dependent intensities, and neutron-diffraction measurements have shown stronger/more ordered hydration-network motifs at lower temperature in concentrated ammonia–water mixtures.

These provide experimental motivation and possible validation targets for the AIMD study.

## Structure-to-spectrum mapping

Recent spectroscopy work on aqueous NH₃ has shown that hydration-shell asymmetry can be mapped onto spectroscopic observables such as nitrogen K-edge X-ray absorption. The present study would extend the same general idea to a **reactive vibrational coordinate** and to **temperature-dependent protonation**.

---

# Proposed novelty

A narrow, defensible statement is:

> **To our knowledge, no study has resolved the Raman response of aqueous ammonia continuously along its proton-transfer free-energy coordinate while simultaneously connecting the spectral changes to solvent preorganization, ion-pair separation, and above-freezing temperature dependence relevant to atmospheric water.**

A stronger atmospheric formulation is:

> **The study aims to provide a molecular description of how natural temperature variations control reversible NH₃/NH₄⁺ interconversion in liquid atmospheric water, linking temperature-dependent proton-transfer free energies and solvent organization to Raman observables and established atmospheric gas–aqueous partitioning thermodynamics.**

The paper should avoid claiming that typical atmospheric droplets universally switch between mostly NH₃ and mostly NH₄⁺. In acidic droplets, NH₄⁺ will remain dominant across much of the relevant temperature range. The important result is that temperature can still strongly alter the neutral fraction, microscopic proton-transfer propensity, and gas–aqueous exchange.

---

# Specific scientific questions

The project should be organized around four questions.

## Q1. How does temperature alter the proton-transfer free-energy landscape?

Compute

```math
F(s_p,s_d;T)
```

for several temperatures.

Extract:

```math
\Delta G_{\rm prot}(T),
```

```math
\Delta G^{\ddagger}(T),
```

and basin populations corresponding to:

- neutral NH₃,
- proton-sharing configurations,
- contact NH₄⁺/OH⁻ configurations,
- more separated ionic defects where accessible.

The temperature dependence can be analyzed through

```math
\Delta G(T) = \Delta H - T\Delta S.
```

A major goal is to determine whether the thermal response is primarily energetic or entropic.

---

## Q2. What does the solvent do as temperature changes?

For configurations resolved by both protonation coordinate and temperature, calculate:

```math
P(n_{\rm HB}\mid s_p,T),
```

```math
P(E_N\mid s_p,T),
```

```math
P(r_{N\cdots O}\mid s_p,T),
```

and related descriptors.

Recommended structural observables:

- N···O distances,
- N···H distances,
- hydrogen-bond angles,
- ammonia hydration number,
- NH₄⁺ coordination number,
- bifurcated hydrogen-bond count,
- local tetrahedral order,
- water-ring and water-wire topology,
- local electric field projected along the transferring bond,
- number of waters donating to NH₃,
- number of waters accepting from NH₄⁺,
- lifetime of reactive hydration motifs.

A central diagnostic is:

```math
P(\text{reactive precursor}\mid T).
```

This should test whether cooling simply increases the population of the same reactive structure or changes the structure itself.

---

## Q3. How does the Raman response evolve with protonation and temperature?

Compute both equilibrium and reaction-coordinate-conditioned spectra:

```math
I(\omega\mid T)
```

and

```math
I(\omega\mid s_p,T).
```

Candidate modes include:

- NH₃ symmetric and asymmetric N–H stretches,
- NH₃ umbrella mode,
- nascent fourth N–H stretch during protonation,
- NH₄⁺ N–H stretches and bends,
- transferring-water O–H stretch,
- low-frequency N···H–O motion,
- collective water hydrogen-bond modes,
- broad water O–H envelope.

The main spectroscopic map could be

```math
I(\omega,s_p;T).
```

For example:

```text
I(ω,sp;278 K)
I(ω,sp;288 K)
I(ω,sp;298 K)
I(ω,sp;308 K)
```

This allows direct comparison of how the spectral pathway changes with temperature.

---

## Q4. Is there a spectroscopic precursor to proton transfer?

This should remain one of the most important mechanistic tests.

The analysis should be restricted to configurations that are still chemically NH₃-like and ask whether a spectral observable predicts future proton transfer.

Conceptually:

```math
P(\mathrm{PT\ within\ }\tau\mid\mathrm{spectrum},s_p\approx0)
```

versus

```math
P(\mathrm{PT\ within\ }\tau\mid\mathrm{geometry},s_p\approx0).
```

A strong result would be a Raman-active feature that appears before formal proton transfer and correlates with committor probability or near-future protonation.

The precursor may be associated with:

- donor-water O–H softening,
- NH₃ umbrella distortion,
- local electric-field-induced frequency shifts,
- formation of a specific water-chain topology,
- increased low-frequency collective motion,
- growth of NH₄⁺-like N–H character prior to complete proton transfer.

---

# Simulation strategy

## Stage 1 — Reproduce the 300 K reference free-energy surface

Start with the known Grifoni-style setup:

```text
1 NH₃ + 31 H₂O
T ≈ 300 K
SCAN
Born–Oppenheimer AIMD
PLUMED
well-tempered metadynamics
```

The purpose is methodological validation, not the final production system.

Reproduce the qualitative topology of

```math
F(s_p,s_d).
```

Do not begin the full temperature series until this baseline is stable.

---

## Stage 2 — Expand to a temperature-dependent free-energy series

Run matched enhanced-sampling simulations at approximately:

```text
278 K
288 K
298 K
308 K
```

For each temperature:

- use the same cell composition and comparable sampling criteria,
- monitor metadynamics convergence,
- calculate uncertainty in basin free energies,
- compare transition-region sampling,
- quantify finite-size sensitivity where feasible.

The principal product is:

```math
F(s_p,s_d;T).
```

---

## Stage 3 — Transition-state and committor analysis

The maximum of a projected free-energy curve is not by itself a rigorous transition-state ensemble.

Select independent configurations near the apparent barrier and launch short unbiased trajectories.

Estimate:

```math
p_B(x) = P(\text{trajectory reaches NH}_4^+\text{ before NH}_3\mid x).
```

Configurations with

```math
p_B \approx 0.5
```

represent the transition-state ensemble more meaningfully.

Perform this analysis at multiple temperatures to determine whether the transition-state solvent structure changes with temperature.

---

## Stage 4 — Validate equilibrium NH₃ and NH₄⁺ spectroscopy

Before computing reactive spectra, calculate equilibrium Raman spectra of:

```math
S_{\rm NH_3}(\omega,T)
```

and

```math
S_{\rm NH_4^+}(\omega,T).
```

Compare calculated peak positions and temperature trends with available aqueous spectroscopy.

The Raman observable should be based on polarizability correlation functions.

For the isotropic contribution:

```math
I_{\rm iso}(\omega) \propto
\int e^{-i\omega t}
\langle \delta\alpha(0)\delta\alpha(t)\rangle\,dt.
```

Where feasible, also calculate anisotropic Raman because intermolecular coupling can be represented differently in isotropic and anisotropic spectra.

---

## Stage 5 — Construct reaction-coordinate-conditioned spectra

Avoid directly Fourier transforming biased metadynamics trajectories.

Use enhanced sampling for thermodynamics and configuration discovery, then generate physical spectroscopy from unbiased dynamics.

Preferred conceptual estimator:

```math
C_{\alpha}(t\mid s)
=
\left\langle
\delta\alpha(0)\delta\alpha(t)
\middle|
s_p(0)=s
\right\rangle.
```

The time origin is classified according to reaction progress, but subsequent dynamics remain unbiased.

Possible practical strategies:

1. launch many unbiased short trajectories from configurations selected by `s_p`,
2. use weak restraints only for preparing ensembles, then release the restraint for spectroscopy,
3. use transition-path or committor-selected configurations for the barrier region.

Low-frequency water-network Raman features will require longer correlation times than high-frequency N–H/O–H modes and may become the dominant computational cost.

---

# Temperature-cycle analysis

A secondary but useful demonstration is a reversible thermal cycle:

```text
278 K → 298 K → 308 K → 298 K → 278 K
```

Track:

```math
s_p(t),
```

```math
n_{\rm HB}(t),
```

```math
E_N(t),
```

and one or more local spectroscopic descriptors.

The purpose is not to reproduce the literal timescale of atmospheric temperature changes. Atmospheric heating/cooling occurs far more slowly than individual hydrogen-bond rearrangements and proton-transfer events.

The expected physical interpretation is therefore close to quasi-equilibrium reversible response:

```text
warming
→ fewer NH₄⁺-stabilizing hydration motifs
→ more NH₃-like configurations

cooling
→ more NH₄⁺-stabilizing hydration motifs
→ larger protonated fraction
```

Do not claim hysteresis unless statistically significant hysteresis is actually observed.

---

# Atmospheric interpretation layer

The AIMD system should remain chemically simple, while atmospheric interpretation is added using established thermodynamic relationships.

The molecular simulations provide:

```math
\Delta G_{\rm protonation}(T),
```

```math
\Delta G^{\ddagger}(T),
```

hydration structure, local fields, and Raman signatures.

The atmospheric layer uses literature thermodynamics to connect these to:

```math
\mathrm{NH_3(g) \rightleftharpoons NH_3(aq) \rightleftharpoons NH_4^+(aq)}.
```

Useful derived quantities include:

```math
f_{\rm NH_3}(T,\mathrm{pH})
=
\frac{[\mathrm{NH_3}]}{[\mathrm{NH_3}]+[\mathrm{NH_4^+}]},
```

and potentially a gas/aqueous partition metric using a temperature-dependent Henry coefficient.

The final paper could include a map of

```text
NH₃ fraction vs temperature and pH
```

with atmospheric regimes indicated qualitatively.

Candidate regimes:

- acidic cloud/fog water,
- moderately neutralized cloud water,
- ammonia-rich agricultural fog,
- marine aqueous particles,
- weakly acidic or near-neutral wet aerosol.

The regime with the clearest NH₃/NH₄⁺ back-and-forth response is likely weakly acidic to near-neutral water rather than strongly acidic sulfate aerosol.

---

# Recommended atmospheric focus

The most informative regime for visible speciation changes may be approximately:

```text
pH 6–8
T = 278–308 K
```

This should not be interpreted as representative of every cloud or aerosol particle.

The reason to focus there is that:

- strongly acidic droplets remain overwhelmingly NH₄⁺,
- near-neutral aqueous environments show larger changes in neutral NH₃ fraction,
- gas–aqueous exchange becomes more sensitive to warming and cooling,
- Raman signatures of mixed NH₃/NH₄⁺ populations become easier to interpret.

---

# Finite-size and concentration considerations

A cell containing one NH₃ per 31 H₂O is not truly dilute.

A rough concentration estimate is:

```text
55.5 / 31 ≈ 1.8 M NH₃-equivalent
```

and one NH₃ per 64 H₂O corresponds to roughly:

```text
55.5 / 64 ≈ 0.87 M.
```

The 31-water system is therefore best treated as a benchmark for reproducing earlier work, not as a literal model of dilute atmospheric cloud water.

Recommended approach:

1. reproduce the established 31-water result,
2. repeat key temperatures or key free-energy slices in at least one larger box,
3. explicitly test whether precursor structure and free-energy differences survive finite-size changes,
4. avoid overinterpreting long-range ion separation in a ~1 nm periodic box.

Finite-size effects may be especially important for `s_d` because solvent-separated NH₄⁺/OH⁻ defects interact with their periodic images.

---

# Electronic-structure strategy

SCAN is a defensible baseline because it has already been used for ammonia protonation and NH₄⁺ hydration.

However, the paper should not rely entirely on a single functional.

Recommended validation:

- reactant-like ensemble,
- precursor ensemble,
- proton-sharing ensemble,
- transition-state ensemble,
- contact ion pair,
- equilibrium NH₄⁺ hydration structures.

Selected configurations should be recalculated using a hybrid functional and, where feasible, higher-level cluster calculations.

A stronger test would use statistical reweighting, free-energy perturbation, or Δ-learning rather than comparing only a few optimized snapshots.

This matters particularly for a temperature study because the functional must describe both proton-transfer energetics and temperature-dependent liquid-water structure.

---

# Nuclear quantum effects and isotope tests

Classical H/D substitution is useful for vibrational assignment, but it does **not** reproduce equilibrium isotope effects on a fixed Born–Oppenheimer potential.

Classical isotope simulations can help identify which spectral modes involve the transferring proton:

```text
NH₃/H₂O
ND₃/D₂O
NH₃/D₂O
```

but quantitative isotope effects on

```math
F(s_p,s_d)
```

require nuclear quantum treatment.

A stronger extension would use path-integral molecular dynamics or another approximate quantum-dynamics method at selected temperatures.

Because proton sharing is central to the problem, nuclear quantum effects should be discussed explicitly as a limitation if not included.

---

# Statistical analysis of precursor behavior

A strong paper should go beyond visual correlations.

Potential analyses:

```math
P(\mathrm{PT\ within\ }\tau\mid X),
```

where `X` could be:

- local electric field,
- donor O–H frequency,
- NH₃ umbrella frequency,
- hydrogen-bond count,
- water-wire topology,
- bifurcated-bond count,
- low-frequency Raman intensity,
- combinations of structural and spectral variables.

Compare predictive ability against simple geometric coordinates.

Possible statistical tools:

- logistic regression,
- mutual information,
- receiver-operating characteristic analysis,
- committor correlation,
- low-dimensional machine-learning classifier,
- information-balance or feature-selection approaches.

The goal is not to maximize machine-learning performance, but to identify a physically interpretable descriptor that connects spectroscopy to future proton-transfer probability.

---

# Expected key figures

## Figure 1 — Atmospheric molecular framework

```text
NH₃(g) ⇌ NH₃(aq) ⇌ NH₄⁺(aq)
```

with temperature acting on both gas–water partitioning and aqueous protonation.

---

## Figure 2 — Temperature-dependent free-energy surfaces

Four panels:

```text
F(sp,sd;278 K)
F(sp,sd;288 K)
F(sp,sd;298 K)
F(sp,sd;308 K)
```

with NH₃, proton-sharing, contact-ion, and separated-ion regions identified.

---

## Figure 3 — Solvent preorganization vs temperature

Examples:

```math
P(n_{\rm HB}\mid s_p,T)
```

```math
P(E_N\mid s_p,T)
```

```math
P(\text{precursor motif}\mid T)
```

plus representative structures.

---

## Figure 4 — Reaction-coordinate-resolved Raman maps

```text
I(ω,sp;278 K)
I(ω,sp;288 K)
I(ω,sp;298 K)
I(ω,sp;308 K)
```

The goal is to show how vibrational features emerge, shift, split, or disappear as NH₃ protonates at different temperatures.

---

## Figure 5 — Spectroscopic precursor analysis

A spectral feature plotted against:

```math
p_B
```

or future proton-transfer probability.

Potential comparison:

```text
spectral descriptor
vs
local electric field
vs
simple N···H distance
```

for predicting proton transfer.

---

## Figure 6 — Atmospheric interpretation

Map of:

```math
f_{\rm NH_3}(T,\mathrm{pH})
```

with arrows showing the conceptual thermal cycle:

```text
cooling:
NH₃(g) → NH₃(aq) → NH₄⁺(aq)

warming:
NH₄⁺(aq) → NH₃(aq) → NH₃(g)
```

---

# Primary mechanistic figure concept

The paper can be built around one central schematic:

```text
       warming →
278 K → 288 K → 298 K → 308 K
  ↕       ↕       ↕       ↕
water-network structure
  ↕
local electric fields
  ↕
NH₃ ⇌ NH₄⁺
  ↕
Raman spectrum

278 K ← 288 K ← 298 K ← 308 K
       ← cooling
```

The atmospheric extension is:

```text
NH₄⁺(aq)
   ⇅  proton transfer
NH₃(aq)
   ⇅  gas–liquid partitioning
NH₃(g)
```

with temperature shifting both equilibria.

---

# What would make the paper scientifically significant

The paper should not be sold as simply another computed Raman spectrum of ammonia or another calculation of ammonium pKa.

Its scientific value would come from establishing a molecular connection between:

```text
natural temperature fluctuations
        ↕
solvent hydrogen-bond structure
        ↕
proton-transfer free energy
        ↕
NH₃/NH₄⁺ speciation
        ↕
Raman observable
        ↕
atmospheric gas–aqueous partitioning
```

The strongest possible result would be:

> A specific solvent-network or vibrational feature appears while the solute is still NH₃-like, becomes more or less probable with temperature, and quantitatively predicts subsequent proton transfer.

That would establish a true **temperature-dependent spectroscopic precursor** to aqueous ammonia protonation.

---

# Minimum viable paper

If computational cost becomes limiting, the minimum publishable version could be:

1. reproduce the 300 K Grifoni-style free-energy surface,
2. calculate matched free-energy surfaces at three temperatures,
3. determine the temperature dependence of the reactive solvent motif,
4. validate equilibrium NH₃ and NH₄⁺ Raman spectra,
5. compute conditional Raman spectra for reactant, precursor, transition, and product ensembles,
6. connect the resulting temperature dependence to atmospheric NH₃/NH₄⁺ equilibrium thermodynamics.

A three-temperature design such as

```text
278 K
298 K
308 or 313 K
```

would already be sufficient to establish whether the effect is systematic.

---

# Higher-impact extensions

Possible extensions, in order of value:

1. **Committor-resolved precursor spectroscopy**
2. **Larger simulation cell / finite-size validation**
3. **Path-integral treatment of selected temperatures**
4. **Hybrid-functional free-energy correction**
5. **Explicit pH-control strategy or hydronium-containing systems**
6. **A second atmospheric solute such as sulfate or nitrate**
7. **Droplet/interfacial geometry rather than bulk periodic water**

The last two should probably be reserved for a follow-up paper unless they become necessary to explain the bulk results.

---

# Key risks

## Risk 1 — NH₃/NH₄⁺ equilibrium is overwhelmingly shifted at some conditions

At strongly acidic pH, NH₄⁺ will dominate at all relevant temperatures.

**Mitigation:** frame the AIMD study as microscopic equilibrium and proton-transfer physics, then use pH-dependent atmospheric thermodynamics to identify where temperature-driven shifts become experimentally significant.

## Risk 2 — Direct Raman changes are dominated by ordinary thermal broadening

Temperature affects all liquid-water spectra.

**Mitigation:** use reaction-coordinate conditioning, structural correlations, isotropic/anisotropic decomposition, and difference spectra rather than comparing raw spectra alone.

## Risk 3 — Biased dynamics contaminate spectroscopy

Metadynamics trajectories do not have physical time correlation functions.

**Mitigation:** use metadynamics for sampling and free energies, then launch unbiased trajectories for Raman calculations.

## Risk 4 — Functional dependence

The proton-transfer barrier and water structure may be sensitive to the density functional.

**Mitigation:** benchmark statistically meaningful ensembles using a hybrid functional or higher-level corrections.

## Risk 5 — Nuclear quantum effects

Classical nuclei may misrepresent proton sharing and barrier heights.

**Mitigation:** quantify this limitation and perform selected path-integral calculations if feasible.

## Risk 6 — Finite-size artifacts

Small periodic cells may distort ion-pair separation and concentration.

**Mitigation:** treat the small cell as a methodological benchmark and repeat central results in a larger box.

---

# Proposed paper narrative

## Introduction

1. Atmospheric ammonia partitions among gas-phase NH₃, dissolved NH₃, and NH₄⁺.
2. Temperature affects both gas–aqueous partitioning and protonation equilibrium.
3. Existing atmospheric models treat these effects thermodynamically but do not describe the molecular water-network mechanism.
4. AIMD studies have independently established aqueous ammonia proton-transfer coordinates, NH₃/NH₄⁺ hydration structure, and solvent preorganization.
5. Raman spectroscopy can provide a molecular observable of hydrogen-bond and proton-transfer structure.
6. The missing connection is a temperature-dependent reaction-coordinate-resolved structure–spectrum map.

## Results

### 1. Temperature-dependent protonation free-energy landscape

```math
F(s_p,s_d;T)
```

### 2. Thermal reorganization of the reactive water network

Hydrogen bonding, local fields, coordination, and precursor statistics.

### 3. Temperature-dependent NH₃ and NH₄⁺ Raman spectra

Validation against available spectroscopy.

### 4. Reaction-coordinate-resolved Raman response

```math
I(\omega,s_p;T)
```

### 5. Spectroscopic precursor to proton transfer

Committor or future-event analysis.

### 6. Atmospheric implication

Connect molecular results to

```math
\mathrm{NH_3(g) \rightleftharpoons NH_3(aq) \rightleftharpoons NH_4^+(aq)}.
```

## Discussion

Focus on whether temperature changes:

- solvent structure,
- precursor probability,
- transition-state structure,
- proton-transfer thermodynamics,
- Raman response,
- atmospheric speciation.

---

# One-sentence paper objective

> **Determine how natural above-freezing temperature fluctuations reorganize liquid water around ammonia, shift reversible NH₃/NH₄⁺ protonation, and generate Raman signatures that connect microscopic proton-transfer physics to atmospheric ammonia partitioning.**

---

# Short abstract concept

Atmospheric ammonia cycles among gaseous NH₃, dissolved molecular NH₃, and protonated NH₄⁺, with temperature strongly affecting both aqueous protonation and gas–liquid partitioning. Here we propose enhanced-sampling ab initio molecular dynamics simulations to resolve the aqueous NH₃ ⇌ NH₄⁺ free-energy landscape over an above-freezing atmospheric temperature range. By combining temperature-dependent protonation free energies with analysis of hydrogen-bond topology, local electric fields, and Raman polarizability fluctuations, the study will determine whether natural temperature changes alter the microscopic solvent configurations that enable proton transfer. Reaction-coordinate-conditioned Raman spectra will be used to search for vibrational signatures of solvent preorganization before proton transfer occurs. The resulting structure–reaction–spectrum relationship will provide a molecular interpretation of temperature-dependent ammonia/ammonium speciation and its role in atmospheric aqueous chemistry.

---

# Key references to retain in the working bibliography

- Grifoni, Piccini, Parrinello — microscopic descriptors and metadynamics for acid–base equilibria in water, including ammonia.
- Ekimova et al. — aqueous solvation and spectroscopy of NH₃ and NH₄⁺.
- Guo et al. — NH₄⁺ hydration, bifurcated hydrogen bonds, and temperature-dependent rotational dynamics.
- Cassone et al. — cooperative water clusters and local electric fields controlling ammonia proton transfer.
- Nagaoka et al. — transition-state characterization of aqueous ammonia ionization.
- Koyano et al. — free-energy reaction-path tracing for ammonia ionization in water.
- Bankura and Chandra — AIMD of proton and hydroxide migration in water–ammonia mixtures.
- Wan et al. — first-principles Raman spectra of liquid water.
- Partovi-Azar and Kühne — efficient Wannier-polarizability Raman methodology.
- Simonelli and Shultz — temperature-dependent Raman behavior of aqueous ammonia.
- Odelius et al. — spectroscopic mapping of hydration-shell asymmetry around aqueous NH₃.
- Nasralla et al. — temperature-dependent structure of aqueous ammonia from neutron diffraction.
- Recent Raman/IR work on vibrational coupling in liquid water — important for interpreting isotropic and anisotropic Raman signals.

---

# Current preferred scope

The recommended first paper is **bulk aqueous atmospheric water above freezing**, not an explicit air–water interface model.

The core deliverable is:

```math
\boxed{
T
\longleftrightarrow
\text{water-network structure}
\longleftrightarrow
\mathrm{NH_3/NH_4^+}
\longleftrightarrow
\text{Raman response}
}
```

with atmospheric gas–aqueous partitioning added as the interpretation layer.

An explicit droplet/interface study would be a natural follow-up once the bulk temperature-dependent mechanism is established.
