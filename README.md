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
  - `ir_pt2tyr.pdb`
  - `ir_pt3tyr.pdb`
  - `ptp-lar_d1&d2domains.pdb`

### 3. **Prepared and Optimized Models**
- Structures prepared and optimized for docking using tools: Vienna (http://vienna-ptm.univie.ac.at/) and Maestro (PrepWizard).
- **Location:** `./prepared_structures/`
- **Files:**
  - `ir_pt2tyr_prepared.pdb`
  - `ir_pt3tyr_prepared.pdb`

### 4. **Docking Results**
- Results from protein-protein docking experiments using HDOCK.
- **Location:** `./dockingResults/`
- Files: PDB files from selected docking poses.
- Supporting log files and scoring summaries.
- Important files are in the 'dynamicFiles' directory.

