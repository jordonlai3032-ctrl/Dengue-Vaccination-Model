# Dengue transmission modelling — Malaysia

A teaching-oriented, notebook-by-notebook build of a dengue spread model, from a
deterministic vector–host SEIR core up to a stochastic multi-serotype model with
vaccination. Every notebook explains **what each code chunk does**, lists **every
parameter with its value, unit, meaning and source**, and **flags every equation**.

Malaysia is the setting throughout: Malaysia has licensed Takeda's dengue vaccine
Qdenga / TAK-003 (Drug Control Authority approval Feb 2024, conditional approval
renewed Feb 2026; currently private-market only, not yet in the National
Immunisation Programme), which makes the vaccination and ADE parts (3 and 4)
directly relevant to current Malaysian policy questions.

## Notebooks

| # | File | Content |
|---|------|---------|
| 0 | `notebooks/00_epidemiology_and_data.ipynb` | Dengue epidemiology primer; Malaysia case data (OpenDengue 1963–2024) and demography; derivation of the parameter values used everywhere else. |
| 1 | `notebooks/01_base_vector_host_seir.ipynb` | **Part 1** — base epidemic model: coupled human SEIR + mosquito SEI, mass-action force of infection, next-generation R₀, numerical solution, sensitivity. |
| 2 | `notebooks/02_baseline_transmission_taufiq.ipynb` | **Part 2** — baseline transmission dynamics exactly as given in Kon & Labadin (2019) ("the Taufiq document"): Holling type-II biting, delayed force-of-infection equations, the paper's explicit R₀ (reproduces R₀ = 0.5985), equilibria and their stability. |
| 3 | `notebooks/03_vaccination.ipynb` | **Part 3** — dengue vaccination: population stratification by serostatus, vaccination rate (continuous, campaign, routine-age), leaky vs all-or-nothing efficacy, coverage/efficacy sweeps. |
| 4 | `notebooks/04_advanced_ade_waning_multiserotype.ipynb` | **Part 4** — two-serotype vector–host model: antibody-dependent enhancement (ADE), waning cross-protection, serotype cycling and replacement, vaccine-as-silent-infection in seronegatives. |
| 5 | `notebooks/05_stochastic_gillespie_sde.ipynb` | **Part 5** — stochastic version: state vector, event/stoichiometry matrix and hazards; Method 1 Gillespie SSA (exact); Method 2 Euler–Maruyama on the chemical Langevin / diffusion approximation; extinction probability and peak-size distributions vs the ODE. |

Read them in order — each builds on the previous one's model and parameters.

## Data (`data/`)

| File | Source | Notes |
|------|--------|-------|
| `raw/National_extract_V1_3.csv` | [OpenDengue](https://github.com/OpenDengue/master-repo) V1.3 national extract | All countries, annual; Malaysia filtered in notebook 0. |
| `malaysia_opendengue_national_V1_3.csv` | derived | Malaysia rows only, 1963–2024 annual dengue case totals. |
| `malaysia_demography.json` | [World Bank WDI](https://data.worldbank.org/country/malaysia) | Population, birth/death rate, life expectancy (2024). |

Other sources referenced in notebook 0 (fetch as needed):
iDengue (https://idengue.mysa.gov.my), data.gov.my (https://data.gov.my),
DOSM (https://www.dosm.gov.my), MOH-Malaysia (https://github.com/MoH-Malaysia),
Open-Meteo (https://open-meteo.com), Copernicus CDS (https://cds.climate.copernicus.eu),
OpenDengue Australia mirror DOI 10.26188/24314689.

## Parameters

`PARAMETERS.md` is the master table — every symbol, the Kon & Labadin (2019)
value, a plausible biological/Malaysia value, and where it comes from. Each
notebook also re-states, inline, the parameters it actually uses.

## Setup

```bash
pip install -r requirements.txt
jupyter lab   # or: jupyter notebook
```
