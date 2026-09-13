# Master parameter reference

Two columns of values:

- **Kon & Labadin (2019)**: *Simulating Dengue: Comparison
  of Observed and Predicted Cases from Generic Reaction-Diffusion Model...*,
  MATEMATIKA 35(3):309–330. Table 1 (temporal fit, Kuching column) and Table 2.
  Time unit = **week**. These are used verbatim in notebook 02.
- **Biological / Malaysia**:literature ranges and Malaysia-specific demography,
  time unit = **day**. Used in notebooks 01, 03, 04, 05.

## Vector–host transmission

| Symbol | Meaning | Kon & Labadin 2019 | Biological / Malaysia | Source |
|--------|---------|--------------------|-----------------------|--------|
| `g` | mosquito searching rate (encounters per unit human density per time) | 2.8 week⁻¹ | — (folded into `b` below) | Chitnis 2005 PhD [22] |
| `λ` (lam) | handling time — time to complete one blood meal per bite | 3.5 week (Table 1); 3.3 (Table 2) | — | Wang & Zhao 2011 [15] |
| `g·N/(1+gλN)` | Holling type-II per-capita biting rate (saturates at `1/λ`) | — | — | Castillo-Chavez 1994 [28] |
| `b_bite` | biting rate (bites per mosquito per day), mass-action limit of Holling II | ≈ `1/λ` ≈ 0.29 week⁻¹ | 0.3 – 1.0 day⁻¹ (use 0.5) | Andraud 2012; Chitnis 2006 |
| `c` = `β_HV` | transmission probability, infectious **mosquito → human**, per bite | 0.75 | 0.3 – 0.75 (use 0.5) | Derouich & Boutayeb 2006 [23] |
| `b` = `β_VH` | transmission probability, infectious **human → mosquito**, per bite | 0.75 | 0.3 – 0.75 (use 0.5) | Derouich & Boutayeb 2006 [23] |
| `m` = `N_V/N_H` | mosquitoes per human | implied ~0.05–0.4 (fitted `S_M`) | 1 – 10 (use 2) | Chitnis 2006; Ferguson 1999 |

## Progression and recovery

| Symbol | Meaning | Kon & Labadin 2019 | Biological / Malaysia | Source |
|--------|---------|--------------------|-----------------------|--------|
| `τ_H` / `1/ν_H` | intrinsic incubation period (human latent) | 1 week | 5 – 7 days (use 5.5) | Gubler 1998 [24]; Chan & Johansson 2012 |
| `τ_M` / `1/ν_V` | extrinsic incubation period (mosquito latent, EIP) | 1.4 week | 8 – 12 days (use 10) | Gubler 1981 [20]; Chan & Johansson 2012 |
| `r` / `γ_H` | human recovery rate (→ 1/`r` infectious period) | 0.824 week⁻¹ (≈ 8.5 d); Bintulu 0.34 week⁻¹ (≈ 4 wk) | 1/7 – 1/4 day⁻¹ (use 1/6) | Andraud 2012 [18]; range 3–14 d |

## Vital dynamics

| Symbol | Meaning | Kon & Labadin 2019 | Biological / Malaysia | Source |
|--------|---------|--------------------|-----------------------|--------|
| `γ` (Gamma) | human recruitment (births + immigration), **absolute** | 201 individuals week⁻¹ | — (use per-capita `μ_H·N_H`) | DOSM Yearbook [21] |
| `d_H` / `μ_H` | human natural mortality | 8.27×10⁻⁵ week⁻¹ | 1 / 76.8 yr = 3.57×10⁻⁵ day⁻¹ | World Bank WDI 2024 |
| `Λ` (Lambda) | mosquito recruitment, **absolute** | 1000 individuals week⁻¹ | — (use `μ_V·N_V`) | fitted |
| `d_M` / `μ_V` | mosquito mortality (→ 1/`d_M` lifespan) | 8.0×10⁻³ week⁻¹ (Table 1); 0.2 week⁻¹ (Table 2) | 1/14 – 1/10 day⁻¹ (use 1/12) | Andraud 2012; Chitnis 2006 |
| CBR | Malaysia crude birth rate | — | 12.36 per 1000 yr⁻¹ | World Bank WDI 2024 |
| CDR | Malaysia crude death rate | — | 5.27 per 1000 yr⁻¹ | World Bank WDI 2024 |
| `N_H` | Malaysia population | 6.2×10⁵ (Kuching) | 3.556×10⁷ (2024) | World Bank WDI 2024 |

## Diffusion (notebook 02 only, spatio-temporal extension)

| Symbol | Meaning | Kon & Labadin 2019 | Source |
|--------|---------|--------------------|--------|
| `D_H` | human diffusion coefficient | 2 km² week⁻¹ (Table 2) | fitted |
| `D_M` | mosquito diffusion coefficient | 2 km² week⁻¹ (Table 2) | fitted |

## Vaccination — Qdenga / TAK-003 (notebook 03)

| Symbol | Meaning | Value | Source |
|--------|---------|-------|--------|
| `ψ` (psi) | per-capita vaccination rate | scenario (0 – 0.5 yr⁻¹) | — |
| `C` | target coverage | scenario (0 – 0.8) | — |
| `ε_inf` | efficacy vs infection, 3-year | 0.62 overall | TIDES trial; Takeda; WHO SAGE 2023 |
| `ε_hosp` | efficacy vs hospitalisation, 3-year | 0.83 overall | TIDES trial |
| `ε_sym` | efficacy vs symptomatic dengue | 0.61 (0.80 first year) | TIDES trial |
| `ε_pos` | efficacy in **seropositive** recipients | ~0.65 – 0.85 | TIDES subgroup |
| `ε_neg` | efficacy in **seronegative** recipients | ~0.53 overall but **serotype-dependent**; poor / uncertain vs DENV3–4 | TIDES subgroup; WHO SAGE |
| `ω_v` | vaccine protection waning rate | 1/(4–6 yr) | TIDES 4.5-yr follow-up |

Dengvaxia / CYD-TDV (the ADE cautionary tale, Philippines 2016–17): efficacy
**negative** in seronegatives (enhanced hospitalisation), used in notebook 04 as
the `ε_neg < 0` case.

## Multi-serotype / ADE (notebook 04)

| Symbol | Meaning | Value | Source |
|--------|---------|-------|--------|
| `n` | number of serotypes modelled | 2 (of 4: DENV-1..4) | Kon & Labadin §2 |
| `σ` (`sigma_sus`, `sigma_inf`) | ADE factor on secondary infection (susceptibility and infectiousness ×`σ`) | 1 (none) – 3 | Ferguson 1999; Cummings 2005 |
| `ω` (`omega`) | waning rate of temporary cross-immunity (→ 1/`ω` cross-protected) | 1/(0.5 – 2 yr) | Reich 2013 [12]; Wearing & Rohani 2006 |
| `ω_long` (`omega_long`) | `R_b → S`: proxy for infection by the 2 serotypes not modelled (DENV-3/4); keeps the 2-serotype model endemic | 1/(8 yr) | modelling choice |
| `β2_scale` | serotype-2 transmission multiplier (fitness asymmetry knob) | 1.0 – 1.15 | — |
| `seas` | seasonal amplitude of the biting rate (notebook 01 Eq. 1.12) | 0 – 0.4 | — |
| `χ` (chi) | cross-immunity strength while cross-protected (0 = full) — documented, not used | 0 | Reich 2013 [12] |

## Stochastic (notebook 05)

State vector `X = (S_H, E_H, I_H, R_H, S_V, E_V, I_V)`; 6 event types with
hazards built from the rates above. No new epidemiological parameters. Numerical
choices, stated in the notebook: **`N_H = 3 000`** (a district — Gillespie cost
scales with population size), `m = 3`, `β_HV = β_VH = 0.45` (→ R₀ ≈ 2.7); `Δt`
(Euler–Maruyama step) and the number of realisations.
