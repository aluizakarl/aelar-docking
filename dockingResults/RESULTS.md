## Docking Results Comparison

|              Metric              |     3PTR (174, 178 and 179)     |       2PTR (178 and 179)        |
|----------------------------------|---------------------------------|---------------------------------|
| **HADDOCK Score**                | -95.6 ±   6.6                   | -99.6 ± 8.5                     |
| **Cluster Size**                 | 39                              |  6                              |
| **RMSD (Overall Lowest-Energy)** | 0.8 ± 0.5                       | 21.1 ± 0.2                      |
| **Van der Waals Energy**         | -47.5 ± 6.8                     | -46.5 ± 4.5                     |
| **Electrostatic Energy**         | -323.8 ± 27.7                   | -320.4 ± 38.5                   |
| **Desolvation Energy**           | 2.7 ± 5.9                       | 3.7 ± 3.3                       |
| **Restraints Violation Energy**  | 138.6 ± 1.8                     | 73.0 ± 2.4                      |
| **Buried Surface Area**          | 1962 ± 53.3                     | 1937.1 ± 149.3                  |
| **Z-Score**                      | -1.9                            | -2.1                            |

### Summary

- Although the **2PTR** system exhibits a slightly more favorable HADDOCK score (-99.6 vs -95.6) and Z-score, this result is associated with a **small cluster size (n = 6)** and **poor structural convergence (RMSD ~21 Å)**, indicating a less reliable and poorly defined solution.

- In contrast, the **3PTR** system shows a **substantially larger cluster (n = 39)** and good convergence (RMSD = 0.8 Å), supporting a **well-defined and reproducible binding mode**.

- The energetic contributions (van der Waals, electrostatic, and desolvation energies) are comparable between both systems, as well as the buried surface area (BSA), suggesting that both interaction modes are energetically feasible.

- However, the **high structural consistency observed in 3PTR**, compared to the conformational dispersion in 2PTR, indicates that the additional phosphorylation (Tyr174) plays a key role in **stabilizing and guiding molecular recognition**.

- These findings suggest that while the 2PTR system allows **multiple competing binding modes**, the **3PTR system favors a dominant and more structurally defined interaction**, which is likely more biologically relevant.

- **Both systems will be further evaluated using molecular dynamics (MD) simulations** to assess stability and refine the structural and functional interpretation of the complexes.
