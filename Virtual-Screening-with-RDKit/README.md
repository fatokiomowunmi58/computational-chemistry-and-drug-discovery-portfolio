# Virtual Screening and Molecular Filtering Using RDKit

## 1. Project Overview

This project demonstrates the application of cheminformatics techniques to virtual screening and compound prioritisation using Python and RDKit.

A subset of 100,000 compounds was randomly selected from a ChEMBL-derived dataset and evaluated using physicochemical properties, drug-likeness metrics, synthetic accessibility, structural alerts and molecular similarity.

The objective was to explore how computational filters can help prioritise compounds for further drug discovery investigations.

## 2. Screening Criteria

The notebook explores five major screening approaches:

| Screening criterion | Description | Applied threshold or approach |
|---|---|---|
| Lipinski's Rule of Five | Evaluates selected physicochemical properties | MW ≤ 500 Da, LogP ≤ 5, HBD ≤ 5, HBA ≤ 10 |
| QED | Estimates overall drug-likeness | QED ≥ 0.67 |
| Synthetic Accessibility (SA) | Estimates synthetic difficulty | SA score ≤ 3.0 |
| PAINS | Identifies potentially problematic structural substructures | SMARTS-based substructure screening |
| Tanimoto similarity | Measures structural similarity to a reference molecule | Initial filtering at ≥ 0.1, with additional examination at ≥ 0.3 |

## 3. Computational Workflow

The notebook covers the following operations:

1. Importing molecular data from a ChEMBL-derived SMILES dataset.
2. Random sampling of 100,000 compounds.
3. Conversion of SMILES strings into RDKit molecular objects.
4. Calculation of molecular weight, LogP, hydrogen-bond donors and acceptors.
5. Calculation and visualisation of QED scores.
6. Calculation and visualisation of synthetic accessibility scores.
7. Identification and visualisation of PAINS-associated substructures.
8. Generation of Morgan fingerprints.
9. Calculation of Tanimoto similarity against a reference molecule.
10. Visualisation of the reference molecule and top-ranking similar compounds.

## 4. Tools and Libraries

- Python
- Jupyter Notebook
- RDKit
- Pandas
- Matplotlib
- tqdm

## 5. Reference Molecule

The similarity analysis uses the following reference SMILES:

```text
C1=CC2=C(C=CC(=C2))N=C1
```

Morgan fingerprints were generated using radius 2 and 1,024 bits.

## 6. Scope and Limitations

This project demonstrates the use of computational molecular descriptors and structural filters for preliminary compound prioritisation.

The screening criteria are prioritisation tools rather than definitive evidence of biological activity, oral bioavailability or synthetic feasibility. PAINS alerts also require appropriate interpretation and experimental follow-up.

The screening operations documented in the notebook should be interpreted according to their individual implementations and thresholds.

## 7. Project Files

- `notebooks/virtualscreening.ipynb` — Jupyter Notebook containing the Python code, explanations and molecular analyses.

*This project documents practical experience in RDKit, molecular descriptor calculation, structural filtering and similarity-based virtual screening.*
