# Molecular Dynamics Simulation Methodology

## 1. Software and Computational Environment

Molecular dynamics (MD) simulations were performed using GROMACS 2024 on an Ubuntu operating system running on a GPU-enabled computational system. The simulations were conducted to evaluate the structural stability and dynamic behaviour of the protein–ligand complexes over a 100 ns production period (Abraham et al., 2015).

## 2. Protein and Ligand Preparation

The protein structure (PDB ID: 2W8Y) was prepared using the DockPrep tool in UCSF Chimera (Pettersen et al., 2004). Hydrogen atoms were added to the protein structure before generating its topology.

The three ligand systems investigated were the co-crystallized ligand (co-ligand), Compound 184, and Compound 384. Hydrogen atoms were added to the ligand structures using UCSF Chimera.

## 3. Topology Generation and System Assembly

The protein topology was generated using the `pdb2gmx` utility in GROMACS with the CHARMM27 force field (Huang and MacKerell, 2013). Ligand topologies and parameters were generated using SwissParam (Zoete et al., 2011).

The protein and ligand coordinate files were subsequently combined to obtain the corresponding protein–ligand complex coordinate files for simulation.

## 4. Solvation and Neutralisation

Each protein–ligand complex was placed in a simulation box with periodic boundary conditions. The systems were solvated using the TIP3P water model. Counterions were added where necessary to neutralise the system.

## 5. Energy Minimisation and Equilibration

Energy minimisation was performed using the steepest-descent algorithm for up to 50,000 steps to remove unfavourable steric contacts and optimise the initial system geometry.

The minimised systems were subsequently equilibrated in two stages:

- **NVT equilibration:** Performed at 300 K for 100 ps using the velocity-rescaling (V-rescale) thermostat.
- **NPT equilibration:** Performed at 1 bar for 100 ps using the Parrinello–Rahman barostat.

Position restraints were maintained on the protein during the equilibration stages.

## 6. Production Molecular Dynamics Simulation

Following equilibration, production MD simulations were performed for 100 ns for each protein–ligand system using GROMACS. The simulations were executed on a high-performance computing (HPC) system.

## 7. Trajectory Analysis

The resulting trajectories were processed using the GROMACS `trjconv` utility. Structural and dynamic properties were evaluated using the following analyses:

| Parameter | GROMACS utility | Purpose |
|---|---|---|
| Root Mean Square Deviation (RMSD) | `gmx rms` | Evaluates structural deviation over the simulation period |
| Root Mean Square Fluctuation (RMSF) | `gmx rmsf` | Examines residue-level flexibility |
| Radius of Gyration (Rg) | `gmx gyrate` | Assesses protein compactness |
| Solvent Accessible Surface Area (SASA) | `gmx sasa` | Evaluates changes in solvent exposure |
| Hydrogen Bond Analysis | `gmx hbond` | Examines hydrogen-bond interactions during the simulation |

The resulting data were plotted and visualised using XMGrace to compare the dynamic behaviour of the apo protein and protein–ligand complexes.
