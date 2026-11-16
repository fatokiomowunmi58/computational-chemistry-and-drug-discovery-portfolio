# DFT-Based Quantum Chemical Analysis of Hexahydroquinoline Derivatives

## 1. Project Overview

This project documents a practical application of Density Functional Theory (DFT) to four selected hexahydroquinoline (HHQ) derivatives identified as promising hits through virtual screening against Plasmodium falciparum calcium-dependent protein kinase 4 (PfCDPK4).

The practical exercise involved performing geometry optimisation and quantum mechanical calculations to investigate the electronic properties of the selected compounds.

## 2. Objectives

The objectives of this practical exercise were to:

- Perform geometry optimisation of four selected hexahydroquinoline derivatives.
- Apply DFT to investigate the electronic properties of the selected compounds.
- Examine the Highest Occupied Molecular Orbital (HOMO) and Lowest Unoccupied Molecular Orbital (LUMO).
- Calculate and investigate important quantum chemical descriptors.
- Explore the relationship between molecular electronic properties and chemical reactivity.

## 3. Software and Computational Methods

The computational work involved:

- **Quantum chemistry software**: Gaussian 09
- **Molecular structure preparation and visualisation**: GaussView 6.0.16
- **Density functional**: Becke, three-parameter, Lee–Yang–Parr (B3LYP)
- **Basis set**: 6-311G(d,p)

### Geometry Optimisation

The molecular structures of the four selected HHQ derivatives were prepared using GaussView 6.0.16. Geometry optimisation was performed using the DFT/B3LYP method with the 6-311G(d,p) basis set in Gaussian 09.

Geometry optimisation was used to obtain favourable molecular geometries for subsequent electronic-property analysis.

### Frontier Molecular Orbital Analysis

Frontier Molecular Orbital (FMO) analysis was used to investigate the Highest Occupied Molecular Orbital (HOMO) and Lowest Unoccupied Molecular Orbital (LUMO) of the selected compounds.

The HOMO and LUMO energy levels were examined to determine the HOMO–LUMO energy gap and explore the electronic characteristics of the molecules. Molecular orbital distributions were also visualised using GaussView.

## 4. Quantum Chemical Descriptors

The calculated HOMO and LUMO energies were used to estimate chemical reactivity descriptors, including:

- HOMO–LUMO energy gap (ΔE)
- Ionisation potential (I)
- Electron affinity (A)
- Chemical hardness (η)
- Chemical softness (S)
- Electronegativity (χ)
- Chemical potential (μ)
- Electrophilicity index (ω)

Under the frontier molecular orbital approximation, the descriptors were estimated using the following relationships:

**Ionisation potential:**

I=-E_HOMO

**Electron affinity:**

A=-E_LUMO

**HOMO–LUMO energy gap:**

ΔE=E_LUMO-E_HOMO

**Chemical hardness:**

η=(I-A)/2

**Chemical softness:**

S=1/(2η)

**Electronegativity:**

χ=(I+A)/2

**Chemical potential:**

μ=-χ

**Electrophilicity index:**

ω=μ^2/2η

## 5. Learning Outcomes

This practical exercise provided hands-on experience in:

- Performing quantum mechanical calculations using Gaussian 09.
- Carrying out geometry optimisation using Density Functional Theory.
- Preparing and visualising molecular structures using GaussView.
- Visualising and interpreting frontier molecular orbitals.
- Examining HOMO and LUMO energy levels.
- Calculating and interpreting quantum chemical descriptors.

## 6. Scope and Reproducibility

This repository documents the computational workflow, methodology and results of DFT calculations performed on four selected hexahydroquinoline derivatives.

The original Gaussian input and output files for the calculations are retained privately and are not included in this public repository. This is an intentional decision to keep the original computational files separate from the publicly accessible research portfolio.

The repository therefore focuses on documenting the computational methods, electronic properties, molecular orbital visualisations and derived quantum chemical descriptors. Numerical results presented are based on my computational work, with published sources appropriately acknowledged where applicable.

## Research Areas

Computational Chemistry | Quantum Chemistry | Density Functional Theory | Molecular Modelling | Drug Discovery | Medicinal Chemistry
