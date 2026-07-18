# Dynamic Modelling and Sensitivity Analysis of the Homologous Recombination DNA Repair Network

This repository contains a computational systems-biology project focused on the homologous recombination (HR) DNA repair pathway. The workflow combines graph-based network analysis, ordinary differential equation (ODE) modelling, and sensitivity analysis to identify the molecular mechanisms that most strongly regulate repair progression.

## Project objectives

- Reconstruct and analyse a protein-interaction network for homologous recombination.
- Identify structurally important proteins using graph centrality metrics.
- Represent the main HR repair stages with a mechanistic ODE model.
- Refine the RPA-to-RAD51 exchange and RAD51 filament-formation steps.
- Evaluate parameter influence using local sensitivity analysis, Morris screening, and LHS-PRCC analysis.
- Compare the baseline and expanded HR models.

## Biological scope

The model represents the progression from a DNA double-strand break to repaired DNA through the following states:

1. Double-strand break recognition
2. DNA end resection
3. RPA-coated single-stranded DNA
4. RAD51 loading
5. RAD51 filament formation
6. Strand invasion and D-loop formation
7. Late repair progression
8. Repaired DNA

The expanded model includes regulators such as CtIP, EXO1, DNA2, DSS1, RAD54, and FANCM.

## Main findings

- The simulated trajectories reproduce a biologically coherent progression from DNA damage to repaired DNA.
- RPA-coated ssDNA and the RPA-to-RAD51 exchange step emerge as major regulatory control points.
- BRCA2-DSS1-mediated RAD51 loading and RAD51 filament assembly show strong sensitivity.
- Refining the RAD51 module increases the apparent influence of RAD51-related mechanisms.
- FANCM-related parameters influence D-loop stabilization and downstream repair progression.
- Because most kinetic constants are not experimentally calibrated, the model is exploratory and hypothesis-generating rather than quantitatively predictive.

## Repository structure

```text
homologous-recombination-dynamic-model/
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
├── data/
│   ├── README.md
│   └── homologous_recombination_interactions.tsv
├── notebooks/
│   └── homologous_recombination_model.ipynb
├── src/
│   ├── network_analysis.py
│   ├── ode_model.py
│   └── sensitivity_analysis.py
├── figures/
│   └── README.md
├── results/
│   └── README.md
└── report/
    └── dynamic_modelling_hr_network.pdf
```

## Installation

Create and activate a virtual environment, then install the required packages:

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

macOS/Linux:

```bash
source .venv/bin/activate
pip install -r requirements.txt
```

## Usage

### Network analysis

```bash
python src/network_analysis.py
```

This script reads the interaction table, builds a directed graph, calculates centrality metrics, and saves the results in `results/network_centrality.csv`.

### ODE simulation

```bash
python src/ode_model.py
```

This script simulates the main mechanistic HR repair states and saves the trajectories and figure.

### Sensitivity analysis

```bash
python src/sensitivity_analysis.py
```

This script performs a simple local sensitivity analysis on the ODE model and saves a ranked parameter table and heatmap.

### Jupyter notebook

```bash
jupyter notebook notebooks/homologous_recombination_model.ipynb
```

## Input data

The interaction dataset contains three tab-separated columns:

- `NODE`: source protein
- `INTERACTION`: interaction type
- `NODE`: target protein

Interaction types include `interacts with`, `controls state change of`, `controls expression of`, and `in catalysis with`.

## Limitations

The numerical values used in the demonstration ODE model are illustrative. They should not be interpreted as experimentally calibrated in-vivo kinetic constants or concentrations.

## Author

Ania Rotondi

## Citation and references

The accompanying report contains the complete bibliography and biological discussion. The project draws on work concerning homologous recombination mechanisms, BRCA2-DSS1-dependent RAD51 loading, dynamic DNA-repair modelling, and Pathway Commons interaction data.
