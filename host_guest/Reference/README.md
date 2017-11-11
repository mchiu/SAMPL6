# Main SAMPL challenge reference calculation files

These input files will be used to run the reference calculations for the main SAMPL challenge. More details about the exact methods will be provided later. Files are available in Amber (`prmtop`/`rst7`), Gromacs (`top`/`gro`), OpenMM (`XML`) and PDB formats. Solvated system files are available both for the host-guest complex (e.g. `complex`) and the guest alone (e.g. `solvent`).

## Preparation
All the host-guest system files in this directory were prepared using the following protocol:
- Protonation states and initial starting configurations were taken as given by the original `mol2` files in the `../OctaAcidsAndGuests/` and `../CB8AndGuests/` directories.
- Hosts and guests were both parametrized with GAFF v1.8 and antechamber. AM1-BCC charges were generated using OpenEye's QUACPAC toolkit through `openmoltools 0.8.1`.
- The systems were solvated in a 12A buffer of TIP4P-Ew water molecules using tleap.
- The systems' net charge was neutralized with Na+ and Cl- ions. More Na+ and Cl- ions were added to reach the ionic strength of 60mM for OA/TEMOA systems and 150mM for CB8 to simulate the effect of the 10mM and 25mM sodium phosphate buffer used in their respective experiments.
- `prmtop`, `inpcrd` and `pdb` files for each system were generated by tleap. The `prmtop`/`inpcrd` files were converted to GROMACS (`top`/`gro`) files using ParmEd `2.7.3`.
- The serialized OpenMM system (`XML`) was generated by OpenMM `7.1.1`. It includes a `MonteCarloBarostat` set at 298.15K and 1atm, and it is configured to use PME, a nonbonded cutoff of 11A, a switching distance of 10A, and constraints on all hydrogen bonds lengths.