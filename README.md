# Symbiosis-Industry-2
# Prioritizing Industrial Symbiosis Strategies for Supply-Chain Decarbonization

**Paper:** Bridging Expert Priorities and Firm-Level Adoption
**Journal:** Journal of Cleaner Production (JCP)
**Revision:** Response to Reviewers 1, 2, and 4

---

## Folder structure
Revisi JCP/
├── 01_Data/ Input data files
├── 02_Code/ Python notebooks
├── 03_Outputs/ Generated CSV results
├── 04_Figures/ Generated PNG figures
├── 05_Manuscript/ Manuscript and response letters
├── 06_Supplementary/ Recovered supplementary materials
└── README.md

text

---

## Data

| File | Description |
|---|---|
| `01_Data/IS_Strategy_Prioritization_Data.xlsx` | Master data: BWM_Data, MARCOS_Data, ABM_Data, Metadata sheets |
| `01_Data/ABM_firm_population.xlsx` | 400 firms × 23 attributes (sector, expert, size, budget, emissions, theta, coefficients, f(K_S1–S5)) |

---

## Code

| Notebook | Purpose | Output |
|---|---|---|
| `01_load_and_check.ipynb` | Data integrity check | Console output |
| `ABM_baseline_v6_FINAL.ipynb` | Baseline ABM (Table 9) | `ABM_results_baseline_FINAL.csv` |
| `ABM_carbon_tax_FINAL.ipynb` | Carbon tax τ = 80 | `ABM_results_tax_FINAL.csv` |
| `ABM_tax_subsidy.ipynb` | Tax + subsidy (Table 13) | `R2_4_*.csv` (4 files) |
| `R2_2_panel_composition.ipynb` | Panel sensitivity (Table 8b) | `R2_2_*.csv` |
| `R2_5_alpha_sweep.ipynb` | α-sweep (Table 12) | `R2_5_alpha_sweep.csv` |
| `R2_6_table4b_sector_summary.ipynb` | Firm attributes by sector (Table 4b) | `R2_6_*.csv` |
| `R2_7_gap_metrics.ipynb` | Gap metric (Table 11) | `R2_7_*_metrics.csv` |
| `R2_7_sector_adoption.ipynb` | Sector adoption (Table 9b) | `R2_7_sector_adoption.csv` |
| `R2_9_S3_counterfactual.ipynb` | E8 counterfactual | `R2_9_*.csv` |
| `Figure_9_recreation.ipynb` | Figure 9 with labels | `Figure_9_priority_adoption_gap.png` |

---

## Key results

| Table | Value | Source |
|---|---|---|
| Table 4b | Firm attributes by sector | `R2_6_table4b_sector_summary.csv` |
| Table 8b | Panel composition | `R2_2_panel_composition.csv` |
| Table 9 | Baseline: S4=300, S5=300, S3=99, S2=33, S1=0 | `ABM_results_baseline_FINAL.csv` |
| Table 9b | Sector-stratified adoption | `R2_7_sector_adoption.csv` |
| Table 11 | Gap index = 5 (baseline and tax) | `R2_7_*_metrics.csv` |
| Table 12 | α-sweep | `R2_5_alpha_sweep.csv` |
| Table 13 | Tax + subsidy (no effect) | `R2_4_*.csv` |

---

## ABM parameters

| Parameter | Value |
|---|---|
| α (priority) | 1.00 |
| β (network) | 0.30 |
| γ (carbon tax) | 0.20 |
| δ (adoption cost) | 0.30 |
| θ | 0.636 (SME) / 0.539 (large) |
| Network | Watts-Strogatz (n=400, k=6, p=0.10) |
| Seed | 42 |
| Horizon | 240 months |

**Budget thresholds** (calibrated to reproduce Table 9):
- S1: $3,394,160 (1 firm)
- S2: $2,436,134 (35 firms)
- S3: $1,564,280 (103 firms)
- S4: $705,313 (300 firms)
- S5: $705,313 (300 firms)

---

## Reproduce

1. Run `01_load_and_check.ipynb` — verifies 400 firms, θ values, coefficients
2. Run `ABM_baseline_v6_FINAL.ipynb` — expects S4=300, S5=300, S3=99, S2=33, S1=0
3. Run remaining notebooks in any order — each is independent

All analyses use `numpy.random.default_rng(42)` and `networkx.watts_strogatz_graph(seed=42)` for deterministic reproducibility.

---
mbiosis Industry 2
