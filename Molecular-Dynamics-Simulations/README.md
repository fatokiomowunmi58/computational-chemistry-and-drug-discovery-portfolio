# Molecular Dynamics Simulation of Protein–Ligand Complexes

## 1. Project Overview

This project documents the use of molecular dynamics (MD) simulations to investigate the structural stability and dynamic behaviour of a protein structure (PDB ID: 2W8Y) in its apo form and in complex with three ligands: the co-crystallized ligand (co-ligand), Compound 184, and Compound 384.

The simulations were performed to examine the stability of the protein–ligand complexes and compare their structural and dynamic properties over a 100 ns simulation period.

## 2. Research Objectives

The study aimed to:

- Evaluate the structural stability of the apo protein and protein–ligand complexes.
- Investigate residue-level flexibility during the simulations.
- Assess changes in protein compactness and solvent exposure.
- Examine hydrogen-bond interactions between the protein and the selected ligands.
- Compare the dynamic behaviour of the three ligand-bound systems.

## 3. Computational Methodology

Molecular dynamics simulations were performed using **GROMACS 2024** on an Ubuntu operating system with GPU-enabled computational resources.

The protein structure was prepared using UCSF Chimera, while ligand parameters were generated using SwissParam. The CHARMM36 force field was used for protein topology generation.

The simulation workflow involved:

1. Protein and ligand preparation.
2. Topology generation and system assembly.
3. Solvation and charge neutralisation.
4. Energy minimisation.
5. NVT and NPT equilibration.
6. 100 ns production molecular dynamics simulations.
7. Trajectory processing and structural analysis.

## 4. Molecular Dynamics Analysis

The following parameters were evaluated:

| Analysis | Purpose |
|---|---|
| RMSD | Evaluates structural deviation throughout the simulation |
| RMSF | Examines residue-level flexibility |
| Radius of Gyration (Rg) | Assesses protein compactness |
| Solvent Accessible Surface Area (SASA) | Evaluates protein solvent exposure |
| Hydrogen Bonds | Examines hydrogen-bond interactions during the simulations |

## 5. Key Findings

Comparative analysis of the four simulated systems revealed differences in their structural and dynamic behaviour.

Compound 184 generally exhibited comparatively favourable profiles across the evaluated parameters, including:

- Relatively stable RMSD behaviour.
- Lower residue fluctuations in the RMSF analysis.
- Comparatively consistent protein compactness.
- More persistent hydrogen-bond interactions during the simulation.

The co-ligand also maintained relatively stable structural behaviour, while Compound 384 exhibited greater variations in some of the evaluated parameters.

Overall, Compound 184 demonstrated comparatively favourable dynamic behaviour among the three evaluated ligands under the simulation conditions.

These computational observations provide a basis for further investigation but do not independently establish binding affinity or biological activity.

## 6. Project Files

- [Project Methodology](methodology/md-methodology.md)
- [Results and Analysis](results/md-analysis.md)
- [Simulation Figures](figures/)
- [References](references/references.md)

## 7. Software and Computational Tools

- GROMACS 2024
- UCSF Chimera
- SwissParam
- CHARMM36 force field
- XMGrace
- Ubuntu Linux

## 8. Scope and Limitations

This project focuses on the comparative structural and dynamic evaluation of the apo protein and three protein–ligand systems using molecular dynamics simulations.

The findings are computational and require complementary approaches, such as binding free-energy calculations and experimental validation, for further assessment of the compounds.

---

*This project documents practical experience in molecular dynamics simulation, protein–ligand interaction analysis, and computational drug discovery.*
