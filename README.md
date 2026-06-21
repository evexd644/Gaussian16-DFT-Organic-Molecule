# Computational Quantum Chemistry: DFT Calculations on Small Organic Molecules

**Course:** CHEM 326: Computational Quantum Chemistry, UC Santa Barbara  
**Method:** Density Functional Theory, B3LYP/6-31+G(d,p)  
**Software:** Gaussian 16, Molden, Linux/Unix HPC cluster at UCSB CCL

## Overview

This repository contains Gaussian z-matrix input files and selected results from density functional theory (DFT) calculations on several small organic molecules. The calculations were performed on the UCSB Chemistry Computing Lab (CCL) cluster using Gaussian 16.

The project focuses on geometry optimization, vibrational frequency analysis, thermochemical properties, resonance effects, and tautomer stability in both gas phase and aqueous solution.

## Repository Contents

```text
.
├── README.md
├── formaldehyde.zmt
├── formamide.zmt
├── methylamine.zmt
├── 2-pyridone.zmt
├── 2-hydroxypyridine.zmt
└── results/
```

The `.zmt` files contain Gaussian input structures written in z-matrix format. The `results/` directory may include optimized geometries, frequency outputs, thermochemical summaries, or visualization files.

## Computational Details

- **Level of theory:** B3LYP/6-31+G(d,p)
- **Program:** Gaussian 16
- **Visualization:** Molden
- **Cluster environment:** UCSB Chemistry Computing Lab Linux/Unix HPC cluster
- **Frequency check:** All optimized structures reported here have zero imaginary frequencies
- **Solvation model:** SMD implicit solvation model for aqueous calculations

## Molecules Studied

### 1. Formaldehyde, CH2O

**Symmetry:** C2v  
**Imaginary frequencies:** 0

| Property | Value |
|---|---:|
| Electronic energy | -114.5115252 a.u. |
| Zero-point energy, ZPE | 16.061 kcal/mol |
| C=O bond length | 1.2096 Å |
| H-C-H bond angle | 116.2° |
| O-C-H bond angle | 121.9° |

### 2. Formamide, HCONH2

**Symmetry:** Cs  
**Imaginary frequencies:** 0

| Property | Value |
|---|---:|
| Electronic energy | -169.9108185 a.u. |
| Zero-point energy, ZPE | 27.382 kcal/mol |
| C=O bond length | 1.2195 Å |
| C-N bond length | 1.3617 Å |
| O-C-N bond angle | 124.7° |
| H-N-H bond angle | 119.1° |

**Key observations**

- The C=O bond in formamide, 1.2195 Å, is longer than the C=O bond in formaldehyde, 1.2096 Å. This suggests reduced double-bond character due to resonance.
- The C-N bond in formamide, 1.3617 Å, is shorter than the C-N bond in methylamine, 1.4662 Å. This indicates partial double-bond character.
- The nitrogen bond angles are close to 120°, consistent with sp2 hybridization and resonance delocalization into the C-N bond.

### 3. Methylamine, CH3NH2

**Symmetry:** Cs  
**Imaginary frequencies:** 0

| Property | Value |
|---|---:|
| Electronic energy | -95.8718477 a.u. |
| Zero-point energy, ZPE | 38.579 kcal/mol |
| C-N bond length | 1.4662 Å |
| C-N-H bond angle | 111.2° |

**Key observation**

- The nitrogen bond angles are close to 111°, consistent with sp3 hybridization, a single C-N bond, and no major resonance delocalization.

### 4. 2-Pyridone and 2-Hydroxypyridine Tautomerism

**Symmetry:** Cs for both tautomers  
**Imaginary frequencies:** 0 for both tautomers

#### Gas Phase Results

| Molecule | Electronic Energy (a.u.) | Enthalpy (a.u.) | Free Energy (a.u.) |
|---|---:|---:|---:|
| 2-Pyridone | -323.5444393 | -323.448197 | -323.483655 |
| 2-Hydroxypyridine | -323.5347618 | -323.438978 | -323.474481 |

For the reaction:

```text
2-Hydroxypyridine -> 2-Pyridone
```

| Thermodynamic Quantity | Calculated | Experimental |
|---|---:|---:|
| ΔE, electronic | -6.07 kcal/mol | N/A |
| ΔH, gas phase | -5.78 kcal/mol | -0.3 kcal/mol |
| ΔG, gas phase | -5.75 kcal/mol | +0.8 kcal/mol |

#### Aqueous Solution Results, SMD Solvation Model

| Molecule | Gas Phase Energy (a.u.) | Aqueous Energy (a.u.) | ΔG_solv (kcal/mol) |
|---|---:|---:|---:|
| 2-Pyridone | -323.5444393 | -323.563308 | -11.84 |
| 2-Hydroxypyridine | -323.5347618 | -323.553989 | -12.07 |

**Predicted ΔG in water:** -5.52 kcal/mol  
**Experimental ΔG in water:** -4.0 kcal/mol

**Discussion**

- Both tautomers are stabilized by aqueous solvation.
- 2-Hydroxypyridine is slightly more stabilized by the SMD water model, with ΔG_solv = -12.07 kcal/mol compared with -11.84 kcal/mol for 2-pyridone. This is likely due to stronger hydrogen bonding from the free OH group.
- The SMD model correctly predicts that 2-pyridone is more stable in water, consistent with experiment.
- The B3LYP/6-31+G(d,p) calculations overestimate the gas-phase stability of 2-pyridone relative to experimental thermochemical values.

## Skills Demonstrated

- Constructing z-matrix input files for molecules with Cs, C2v, and C1 symmetry
- Running DFT geometry optimizations in Gaussian 16
- Performing vibrational frequency calculations and confirming optimized minima
- Extracting zero-point energies, enthalpies, and Gibbs free energies
- Comparing calculated bond lengths and angles to chemical bonding models
- Evaluating resonance effects in amide bonding
- Modeling solvent effects with the SMD implicit solvation model
- Using a Linux/Unix HPC cluster through SSH
- Visualizing optimized molecular structures with Molden

## How to Reproduce

1. Upload or copy the `.zmt` Gaussian input files to the computing cluster.
2. Submit each Gaussian job using the appropriate cluster submission script.
3. Confirm that each optimized structure has zero imaginary frequencies.
4. Extract electronic energies, zero-point energies, enthalpies, free energies, bond lengths, and bond angles from the Gaussian output files.
5. Visualize optimized structures using Molden or another molecular visualization program.

Example Gaussian route section:

```text
# B3LYP/6-31+G(d,p) Opt Freq
```

For aqueous SMD calculations:

```text
# B3LYP/6-31+G(d,p) SCRF=(SMD,Solvent=Water)
```

## Reference

Aue, D. H.; Webb, H. M.; Bowers, M. T.; Liotta, C. L.; Alexander, C. J.; Hopkins, H. P. *Journal of the American Chemical Society* **1979**, *101*, 1361.

## Notes

All energies and structural parameters reported in this README are taken from the corresponding Gaussian calculations for this course project. Experimental values are included only for comparison with the calculated tautomerization thermodynamics.
