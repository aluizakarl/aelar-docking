## Atom Name Modification

To address the errors related to missing atom types in the provided PDB file (`top9_aelar-2py_ligand-withoutH.pdb`), several atom names were adjusted to ensure compatibility with the parameters defined in the **ff19SB** force field. Below are the details of the modifications:

### Modifications Made

- **Residue:** PTR (Phosphotyrosine)
- **Updated Atom Names:**
  - `PT` was renamed to **P** (corresponding to the central phosphorus atom).
  - `OI1`, `OI2`, `OI3` were renamed to **O1P**, **O2P**, **O3P** (oxygen atoms connected to the phosphorus atom, following the naming conventions of the Amber force field).
  - `OP1` and `OP2` were reviewed and adjusted to match the atom types defined in the force field parameters.

These modifications ensure compatibility with the **ff19SB** force field and its associated phosphorylated residue libraries (e.g., `phosaa19SB.lib` or `phosaa14SB.lib`). They resolve the fatal errors encountered in **tleap**, specifically related to undefined atom types for the PTR residue.

### Justification for Changes

1. **Amber Naming Standards**: The Amber force field requires specific naming conventions for atom types in residues. For phosphorylated residues like PTR, the phosphorus atom must be named **P**, and the oxygen atoms connected to it must be named **O1P**, **O2P**, and **O3P**.

2. **Consistency with the Force Field Files**:
   - The **MASS** block in `frcmod.phosaa19SB` or `frcmod.phosaa14SB` defines types and interactions for atoms.
   - The `phosaa19SB.lib` or `phosaa14SB.lib` libraries provide the expected atom names and residue definitions.
   - Renaming atoms to match these files is crucial for proper parameterization.

3. **Simulation Stability**:
   - By ensuring proper atom naming, the residue is fully recognized during topology and coordinate file generation, preventing simulation errors or inconsistencies.

4. **Testing in tleap**:
   - The updated atom names were validated using **tleap**, and no fatal errors were encountered after the corrections were applied.

---

### Complementary Notes

- **OP1 and OP2 Corrections**: While `OP1` and `OP2` initially caused errors, they were either renamed or redefined to ensure compatibility with the expected atom types. This adjustment resolved the `FATAL: Atom .R<PTR>.A<...> does not have a type` error.

- **Automated Corrections**: A Python script was used to automate these renaming operations for consistency and efficiency, reducing the possibility of manual errors.

- **Validation**: The corrected structure was processed through **tleap**, solvation, and neutralization protocols, demonstrating the effectiveness of the modifications without introducing new issues.

These changes ensure that the atom names align with the **MASS** block in the `frcmod.phosaa19SB` file and the PTR residue definitions in the `phosaa19SB.lib` file. 

The updates resolved the fatal errors reported in **tleap**, allowing proper system processing.

## System Preparation with H++

The system was preprocessed using the **H++ server** to ensure accurate addition of hydrogen atoms and protonation states under physiological pH conditions. 

### Why H++ was Used:
- **Physics-Based Approach:** Unlike semi-empirical methods such as PropKa, H++ relies on the **Poisson-Boltzmann (PB)** or **Generalized Born (GB)** models, which calculate protonation states by solving the full electrostatic environment of the system.
- **Robustness for Modified Residues:** H++ is more suitable for handling non-standard residues, such as phosphotyrosine (PTR), and accounts for the specific electrostatic interactions of phosphorylated groups.
- **Protonation Accuracy:** The tool ensures proper hydrogen placement, even in residues with unique environments or altered chemistry.

This preprocessing step addressed issues where other tools, such as PropKa, failed to add hydrogens correctly due to the residue's non-standard nature.

## tleap Protocol

The protocol outlined below was used to prepare the system using the **ff19SB** force field and the **OPC3** water model with an ionic strength of 0.15 M NaCl.

### Steps Executed in tleap

```bash
# 1. Load the ff19SB force field
source leaprc.protein.ff19SB

# 2. Load the OPC3 water model
source leaprc.water.opc3

# 3. Load the force field for phosphorylated residues
source leaprc.phosaa19SB
loadoff phosaa19SB.lib

addPdbAtomMap {
    {"OP1" "O1P"}
    {"OP2" "O2P"}
}

# 4. Load the system's PDB file
mol = loadpdb top9_aelar-2py_complex.pdb

# 5. Check the system for errors or issues
check mol
charge mol

addIons mol Cl- 14
addIons mol Na+ 14

# 6. Solvate the system with the OPC3 water model
solvatebox mol OPC3BOX 10.0

# 7. Adjust ionic strength to 0.15 M NaCl
addionsrand mol Na+ 0.15
addionsrand mol Cl- 0.15

# 8. Save the necessary files for AMBER simulations
saveamberparm mol 2py_ff19SB_OPC3_0.15M.top 2py_ff19SB_OPC3_0.15M.crd

# 9. Save the solvated system as a PDB file for verification
savepdb mol 2py_complex_ff19SB_OPC3_0.15M_solvated.pdb

# 10. Exit tleap
quit
```

### Protocol Justification

1. **ff19SB Force Field**:
   - Selected for its high accuracy in protein simulations and compatibility with phosphorylated residues through the `leaprc.phosaa19SB` file.

2. **OPC3 Water Model**:
   - The OPC3 model provides more accurate thermodynamic properties and is optimized for use with ff19SB.

3. **H++ Preprocessing**:
   - Ensured accurate protonation states and hydrogen placement for non-standard residues like PTR.

4. **Atom Name Correction**:
   - Ensured compatibility with the parameters defined in the force field files (`frcmod.phosaa19SB` and `phosaa19SB.lib`).

5. **Neutralization and Ionic Strength Adjustment**:
   - Neutralization with Na+ and Cl- adjusted the system's total charge to achieve an ionic strength of 0.15 M, mimicking physiological conditions.

6. **Solvation**:
   - Solvation with a 10 Å buffer ensured appropriate periodic boundary conditions for simulations.

7. **Output Files**:
   - `.top` and `.crd` files are required for running simulations in AMBER.
   - The solvated PDB file is valuable for visual inspection and structural verification.

### Results

After preprocessing with H++ and executing the tleap protocol:
- Atom names and protonation states were corrected.
- The system was solvated and neutralized correctly with 0.15 M ionic strength.
- The system is now ready for molecular dynamics simulations using AMBER with the ff19SB force field and OPC3 water model.
