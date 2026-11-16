# Virtual Screening and Molecular Filtering Using RDKit

## 1. Project Overview

This project demonstrates the application of cheminformatics techniques to molecular filtering, structural analysis and similarity-based virtual screening using Python and RDKit.

A random subset of 100,000 compounds was selected from a ChEMBL-derived molecular dataset. The compounds were investigated using physicochemical descriptors, drug-likeness metrics, synthetic accessibility estimates, structural alerts and molecular similarity.

The aim was to explore how computational methods can support preliminary compound assessment and prioritisation for further drug discovery investigations.

## 2. Screening Approaches and Criteria

The notebook explores five major screening approaches:

| Screening criterion | Description | Applied threshold or approach |
|---|---|---|
| Lipinski's Rule of Five | Evaluates selected physicochemical properties associated with oral drug-likeness | MW ≤ 500 Da, LogP ≤ 5, HBD ≤ 5, HBA ≤ 10 |
| QED | Estimates overall quantitative drug-likeness | QED ≥ 0.67 |
| Synthetic Accessibility (SA) | Estimates the relative synthetic accessibility of molecules | SA score ≤ 3.0 |
| PAINS | Identifies potentially problematic substructures using structural alerts | SMARTS-based substructure screening |
| Tanimoto similarity | Measures structural similarity to a reference molecule | Initial filtering at ≥ 0.1, with additional examination at ≥ 0.3 |

These approaches are explored as individual computational assessments. Their thresholds should be interpreted in the context of the corresponding notebook operations.

## 3. Computational Workflow

The notebook covers the following operations:

1. Importing molecular data from a ChEMBL-derived SMILES dataset.
2. Random sampling of 100,000 compounds using a fixed random seed.
3. Conversion of SMILES strings into RDKit molecular objects.
4. Calculation of molecular weight, LogP, hydrogen-bond donors and hydrogen-bond acceptors.
5. Calculation and visualisation of QED scores.
6. Calculation and visualisation of synthetic accessibility scores.
7. Identification and visualisation of PAINS-associated substructures.
8. Generation of Morgan fingerprints.
9. Calculation of Tanimoto similarity against a reference molecule.
10. Visualisation of the reference molecule and selected structurally similar compounds.

## 4. Tools and Libraries

- Python
- Jupyter Notebook
- RDKit
- Pandas
- Matplotlib
- tqdm

## 5. Molecular Similarity Analysis

The similarity analysis uses the following reference SMILES:

```text
C1=CC2=C(C=CC(=C2))N=C1
```

Morgan fingerprints were generated using a radius of 2 and a fingerprint size of 1,024 bits. Tanimoto similarity was subsequently calculated to assess structural resemblance between the reference molecule and screened compounds.

## 6. Scope and Limitations

This project demonstrates the use of molecular descriptors, drug-likeness estimates, structural alerts and molecular fingerprints for preliminary compound assessment.

These computational filters are prioritisation tools and do not independently establish biological activity, oral bioavailability, safety or experimental synthetic feasibility.

PAINS alerts require careful interpretation, as structural alerts do not automatically indicate that a compound is unsuitable. Similarly, molecular similarity does not establish equivalent biological activity.

The results should therefore be considered exploratory and require further computational and experimental investigation.

## 7. Project Structure

```text
Virtual-Screening-with-RDKit/
├── README.md
└── notebooks/
    ├── virtualscreening_github.ipynb
    └── .gitkeep
```

The notebook contains the Python code, explanations and molecular analyses. You can view it here: [Open the RDKit Virtual Screening Notebook](notebooks/virtualscreening_github.ipynb).. The original molecular dataset is not redistributed with this repository and must be obtained separately to reproduce the workflow.

## 8. Reproducibility

To reproduce the analysis:

1. Install Python and the required libraries.
2. Install RDKit in a compatible Python environment.
3. Obtain the ChEMBL-derived SMILES dataset used by the notebook.
4. Update the dataset file path in the notebook to match its location.
5. Execute the notebook cells in sequence.

*This project documents practical experience in RDKit, molecular descriptor calculation, structural filtering and similarity-based virtual screening.*
