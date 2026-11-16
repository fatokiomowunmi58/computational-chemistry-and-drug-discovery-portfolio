# GROMACS Command-Line Workflow for Molecular Dynamics Simulations

## 1. Overview

This document records the command-line workflow used to perform protein–ligand molecular dynamics simulations with GROMACS on Ubuntu Linux. It covers system preparation, topology generation, solvation, energy minimisation, equilibration, production MD, and trajectory analysis.

The workflow was applied to the protein structure (PDB ID: 2W8Y) and its ligand-bound systems.

## 2. Protein and Ligand Preparation

### Ligand preparation

The ligand structure was prepared using UCSF Chimera by adding hydrogen atoms and saving the structure in MOL2 format.

The MOL2 file was organised before topology generation:

```bash
perl sort_mol2_bonds.pl LIG.mol2 LIG.mol2
```

The prepared ligand was subsequently submitted to SwissParam to generate ligand topology and parameter files.

### Protein preparation

The receptor structure was prepared using UCSF Chimera. The bound ligand, where present, was removed before DockPrep was performed. The prepared protein was saved as:

```text
REC.pdb
```

## 3. Topology Generation and System Assembly

Protein topology and coordinate files were generated using:

```bash
gmx pdb2gmx -f REC.pdb -ignh
```

The CHARMM27 all-atom force field was selected during the interactive setup.

The ligand coordinates were converted into GROMACS format:

```bash
gmx editconf -f LIG.pdb -o LIG.gro
```

The protein and ligand coordinate information was then combined to generate the initial complex coordinate file.

The ligand topology was incorporated into `topol.top` using an appropriate include statement, and the ligand molecule name was made consistent across the topology files.

## 4. Box Definition, Solvation and Ion Addition

A simulation box was defined around the protein–ligand system:

```bash
gmx editconf -f conf.gro -d 1.0 -bt triclinic -o box.gro
```

The system was solvated:

```bash
gmx solvate -cp box.gro -cs spc216.gro -p topol.top -o box_sol.gro
```

The input file for ion addition was generated:

```bash
gmx grompp -f ions.mdp -c box_sol.gro -p topol.top -o ION.tpr
```

Counterions were added to neutralise the system and establish the specified salt concentration:

```bash
gmx genion -s ION.tpr -p topol.top -conc 0.1 -neutral -o box_sol_ion.gro
```

The solvent group was selected when prompted by GROMACS.

## 5. Energy Minimisation

The energy-minimisation input file was generated:

```bash
gmx grompp -f EM.mdp -c box_sol_ion.gro -p topol.top -o EM.tpr
```

Energy minimisation was performed using:

```bash
gmx mdrun -v -deffnm EM
```

## 6. Equilibration

### NVT equilibration

The ligand index and position-restraint files were generated using:

```bash
gmx make_ndx -f LIG.gro -o index_LIG.ndx
```

```bash
gmx genrestr -f LIG.gro -n index_LIG.ndx -o posre_LIG.itp -fc 1000 1000 1000
```

The system index file was generated:

```bash
gmx make_ndx -f EM.gro -o index.ndx
```

The NVT input file was prepared and processed:

```bash
gmx grompp -f NVT.mdp -c EM.gro -r EM.gro -p topol.top -n index.ndx -o NVT.tpr
```

The NVT equilibration was run:

```bash
gmx mdrun -deffnm NVT
```

### NPT equilibration

The NPT input file was generated:

```bash
gmx grompp -f NPT.mdp -c NVT.gro -r NVT.gro -p topol.top -n index.ndx -o NPT.tpr
```

The NPT equilibration was performed:

```bash
gmx mdrun -deffnm NPT
```

## 7. Production Molecular Dynamics

The production MD input file was generated using:

```bash
gmx grompp -f MD.mdp -c NPT.gro -t NPT.cpt -p topol.top -n index.ndx -o MD.tpr
```

The production simulation was performed using:

```bash
gmx mdrun -deffnm MD
```

The production simulation was run for the specified simulation duration.

## 8. Trajectory Processing

The trajectory was processed to centre the protein and correct periodic boundary artefacts:

```bash
gmx trjconv -s MD.tpr -f MD.xtc -o MD_center.xtc -center -pbc mol -ur compact
```

The protein group was selected for centring, and the system group was selected for output.

## 9. Molecular Dynamics Trajectory Analysis

The following GROMACS commands were used to investigate the structural and dynamic properties of the simulated systems.

### Root Mean Square Deviation (RMSD)

```bash
gmx rms -s MD.tpr -f MD_center.xtc -o rmsdprot.xvg -tu ns
```

The protein group was used for least-squares fitting, while the backbone group was selected for RMSD calculation.

Conversion from nanometres to ångströms:

```bash
awk '!/^[@#]/ { $2=$2*10 } {print}' rmsdprot.xvg > MD_rmsd_prot_Angstrom.xvg
```

### Root Mean Square Fluctuation (RMSF)

```bash
gmx rmsf -s MD.tpr -f MD_center.xtc -o rmsf.xvg -res
```

The output was converted from nanometres to ångströms:

```bash
awk '!/^[@#]/ { $2=$2*10 } {print}' rmsf.xvg > MD_rmsf_Angstrom.xvg
```

### Hydrogen-Bond Analysis

```bash
gmx hbond -s MD.tpr -f MD_center.xtc -num hb.xvg -tu ns
```

Protein and ligand groups were selected for the analysis.

### Radius of Gyration (Rg)

Protein radius of gyration:

```bash
gmx gyrate -s MD.tpr -f MD_center.xtc -o gyrateprot.xvg -tu ns
```

Complex radius of gyration:

```bash
gmx gyrate -s MD.tpr -f MD_center.xtc -o gyratecom.xvg -tu ns
```

### Solvent Accessible Surface Area (SASA)

```bash
gmx sasa -s MD.tpr -f MD_center.xtc -o sasa.xvg -tu ns
```

### Energy Analysis

```bash
gmx energy -f MD.edr -o energy1.xvg
```

The required energy terms were selected interactively.

## 10. Plotting and Visualisation

The generated `.xvg` files were visualised using XMGrace:

```bash
xmgrace rmsdprot.xvg
xmgrace rmsf.xvg
xmgrace hb.xvg
xmgrace gyrateprot.xvg
xmgrace sasa.xvg
```

These plots were used to examine structural deviation, residue flexibility, hydrogen-bond interactions, protein compactness and solvent exposure.

## 11. Software and Tools

- GROMACS
- Ubuntu Linux
- UCSF Chimera
- SwissParam
- XMGrace
