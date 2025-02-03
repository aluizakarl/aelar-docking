# Protein Tyrosine Phosphatase LAR in *Aedes aegypti* (AeLAR): Data Repository

This repository contains the data used in the manuscript **"Protein Tyrosine Phosphatase LAR in *Aedes aegypti* (AeLAR) links nutritional reserves and mosquito behavior"**. The repository provides all the necessary files for replicating the experiments of protein-protein docking between the *Insulin Receptor* (IR) and *AeLAR*.

---

## Repository Contents

### 1. **FASTA Sequences**
- Contains the original FASTA sequences used for modeling the proteins involved in the docking experiments.
- **Location:** `./sequences/`
- **Files:**
  - `IR_catalyticDomain.fasta`
  - `IR_complete.fasta`
  - `ptp-lar_d1&d2domains.fasta`

### 2. **Modeled Structures**
- Protein 3D models generated using homology modeling tool SwissModel.
- **Location:** `./models/`
- **Files:**
  - `ir_catalyticDomain.pdb`
  - `ptp-lar_d1&d2domains.pdb`

### 3. **Prepared and Optimized Models**
-  Structures were prepared and optimized for docking using the SwissSidechain tool (Pymol plugin) and the PrepWizard tool (Maestro suite).
- **Location:** `./prepared_structures/`
- **Files:**
  - `ir_pt2tyr_prepared.pdb`
  - `ir_pt3tyr_prepared.pdb`
  - `ptp-lar_d1&d2domains_prep.pdb`

### 4. **Docking Results**
- Results from protein-protein docking experiments using HADDOCK.
- **Location:** `./dockingResults/`
- Files: Selected docking poses in PDB format, a summary of the scoring results, and a ZIP file with the best-ranked structures.
