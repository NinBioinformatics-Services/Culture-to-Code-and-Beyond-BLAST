# 🧬 Module 2: Structural Bioinformatics & Protein Modeling

[![Course Level](https://img.shields.io/badge/Level-FY_UG_to_Professor-blueviolet?style=for-the-badge)](#)
[![Focus](https://img.shields.io/badge/Focus-Structural_Bioinformatics_%26_3D_Modeling-emerald?style=for-the-badge)](#)
[![Vibe](https://img.shields.io/badge/Vibe-Gen_Z_Approved-ff69b4?style=for-the-badge)](#)

---

## 📌 Section 1: Protein Structural Levels, Domains, and File Architectures

Proteins execute catalysis, structural integrity, signal transduction, and molecular transport across all cellular life. Understanding three-dimensional macromolecular architectures requires analyzing structural hierarchies alongside standardized computational file specifications.

```
Primary Sequence  -->  Secondary Structures  -->  Tertiary Domains  -->  Quaternary Complex
 (Amino Acids)         (Helices / Sheets)         (3D Folding)         (Multi-Subunits)
```

### 🧪 Structural Hierarchies and Ramachandran Geometry
Protein architecture organizes into four distinct structural tiers:
* **Primary Structure**: Linear sequence of amino acid residues linked covalently by peptide bonds.
* **Secondary Structure**: Local spatial folding stabilized by hydrogen bonds between backbone carbonyl oxygens ($C=O$) and amide hydrogens ($N-H$). Primary geometries comprise right-handed $lpha$-helices and $eta$-pleated sheets (parallel or antiparallel orientation). Backbone conformational flexibility remains restricted by sterically allowed backbone dihedral angles: $\phi$ (phi, rotation about the $N-C_lpha$ bond) and $\psi$ (psi, rotation about the $C_lpha-C$ bond). Ramachandran steric maps plot $\phi$ versus $\psi$ angle distributions, highlighting allowed non-disrupted steric regions for helices (left-upper quadrant for right-handed $lpha$-helices) and sheets.
* **Tertiary Structure**: Three-dimensional spatial conformation of a single polypeptide chain driven by hydrophobic collapse, disulfide bridges (`SSBOND`), salt bridges, and van der Waals forces.
* **Quaternary Structure**: Spatial arrangement and non-covalent or covalent interaction of multiple polypeptide subunits forming functional multimeric complexes.

### 🧬 Domains, Motifs, and CATH Structural Classification
Protein domains represent modular, independently folding structural units that recur across distinct evolutionary lineages. Motifs (or supersecondary structures) consist of conserved combinations of secondary structure elements, such as helix-turn-helix motifs in transcription factors or Rossmann folds in nucleotide-binding enzymes.

The **CATH Protein Structure Classification Database** classifies experimental biological macromolecular structures from the Protein Data Bank into a rigorous four-tier hierarchy:
1. **Class (C)**: Determined by overall secondary structure composition (e.g., Mainly Alpha, Mainly Beta, Alpha-Beta, or Few Secondary Structures).
2. **Architecture (A)**: Describes the overall 3D shape and orientation of secondary structures independent of connectivity (e.g., barrel, sandwich, roll).
3. **Topology (T)**: Refers to the fold family, accounting for structural connectivity and strand ordering.
4. **Homologous Superfamily (H)**: Groups domains sharing structural core conservation and evolutionary divergence from a common ancestor.

Complementing structural hierarchies, CATH sub-classifies superfamilies into **Functional Families (FunFams)**. FunFams group domains sharing identical enzymatic functions, leveraging Scorecons conservation algorithms to highlight functional catalytic residues mapped directly onto 3D structures.

```
CATH Hierarchy:
  [C] Class  (Mainly Alpha, Mainly Beta, Alpha-Beta)
    └── [A] Architecture  (Sandwich, Barrel, Roll)
          └── [T] Topology  (Fold Family, Connectivity)
                └── [H] Homologous Superfamily  (Evolutionary Relatives)
                      └── [FunFam] Functional Families  (Conserved Catalytic Residues)
```

### 💾 The Protein Data Bank (PDB) Flat-File Architecture
The **Protein Data Bank (PDB)** archives atomic coordinates determined via X-ray crystallography, NMR spectroscopy, and cryo-electron microscopy. The legacy PDB format enforces an 80-column fixed-width ASCII record format:

```
1--------10--------20--------30--------40--------50--------60--------70--------80
HEADER    HYDROLASE                               13-JUL-11   1B73              
TITLE     CRYSTAL STRUCTURE OF GLUTAMATE RACEMASE                               
SEQRES   1 A  266  MET GLU ASN LYS ILE GLY ILE VAL GLY GLY MET GLY GLY ILE      
HELIX    1   1 GLU A   12  ALA A   24  1                                        
SHEET    1   A 5 VAL A    7  VAL A   10  0                                        
ATOM      1  N   MET A   1       2.573  -1.034  -1.721  1.00 15.20           N  
ATOM      2  CA  MET A   1       2.493  -1.949  -1.992  1.00 14.80           C  
HETATM 2100  FE  HEM A 300      12.160  -0.537  -2.427  1.00 18.50          FE  
CONECT 2100 2050 2051                                                          
END                                                                             
```

Key PDB record types include:
* `HEADER`: Deposited PDB identification code, deposition date, and functional classification.
* `SEQRES`: Primary amino acid sequence of all polymer chains present in the experiment.
* `HELIX` / `SHEET`: Secondary structure annotations defining starting and ending residue positions.
* `ATOM`: Orthogonal atomic coordinates ($x, y, z$ in Ångströms), occupancy ($q$), and temperature B-factor ($B$) for standard polymeric residues.
* `HETATM`: Coordinates for non-standard groups, cofactors, ligands, and water molecules.
* `SSBOND` / `CONECT`: Covalent disulfide linkage assignments and inter-atomic bond connectivity definitions.
* `CRYST1`: Crystallographic unit cell dimensions ($a, b, c, lpha, eta, \gamma$) and space group symmetry.

---

## 📌 Section 2: 3D Structure Visualization and Command-Line Manipulation

Molecular visualization transforms abstract atomic coordinates into interpretable structural insights. Interactive visualization tools facilitate active site analysis, surface electrostatic potential mapping, and structural superposition.

### 💻 PyMOL Command Language and Rendering
PyMOL utilizes a robust command-line interface for molecular manipulation, selection algebra, and ray-tracing graphics generation:

```python
# PyMOL Scripting Commands for Structural Analysis
load 1b73.pdb, glutamate_racemase              # Load structural coordinate entry
hide everything, all                           # Clear default representations
show cartoon, polymer                          # Display protein backbone ribbon
show sticks, organic                           # Highlight bound ligands/inhibitors

# Atom Selection Algebra
select active_site, resi 73+184                # Select catalytic cysteine residues
color ruby, active_site                        # Apply color to active site selection
show sticks, active_site                       # Render active site side chains

# Distance Measurement and Display
distance H_bond, /glutamate_racemase//A/73/SG, /glutamate_racemase//A/184/SG
set dash_color, yellow                         # Color measurement dashes
```

Key visualization operations and algorithms in PyMOL include:
* **Secondary Structure Assignment (`dss`)**: Reassigns helices and strands based on backbone geometry and hydrogen-bonding networks.
* **Solvent Accessible Surface Area (`get_sasa_relative` / `get_area`)**: Computes solvent-exposed versus buried residue surface area using rolling sphere probes.
* **Structural Alignment (`align` vs `cealign`)**: `align` performs sequence-dependent pairwise fitting followed by outlier rejection cycles. `cealign` executes sequence-independent alignment via Combinatorial Extension, ideal for distant evolutionary homologs with sequence identity under 30%.

### 🔬 Polyacrylamide Gel Electrophoresis (SDS-PAGE) Visualization
In experimental biochemistry, structural composition and purity are verified prior to crystallization using Sodium Dodecyl Sulfate Polyacrylamide Gel Electrophoresis (SDS-PAGE). Denaturing detergent SDS unfolds proteins and coats polypeptides with uniform negative charge, enabling size-based migration separation within polyacrylamide matrices visualized via Coomassie stain.

---

## 📌 Section 3: Homology Modeling and AI-Driven Structure Prediction

Experimental structure determination via X-ray crystallography or cryo-EM can be resource-intensive. Computational structure prediction bridges the gap between abundant genomic sequences and limited 3D coordinate archives.

```
Target Sequence  -->  Template Search  -->  Target-Template  -->  Backbone & Loop  -->  Side-Chain  -->  Model Validation
 (UniprotKB)          (BLAST / HHblits)     Alignment             Construction         Packing         (QMEAN / pLDDT)
```

### 🧬 Homology (Comparative) Modeling Protocols
Homology modeling rests on the evolutionary principle that protein structural tertiary folds remain far more conserved than primary sequences [85]. When sequence identity exceeds 30%, homologous proteins adopt highly similar backbone conformations.

The automated homology modeling pipeline (e.g., SWISS-MODEL) follows a strict workflow:
1. **Template Identification**: Search the PDB for known structural homologs using BLAST or profile-HMM algorithms (HHblits).
2. **Target-Template Alignment**: Generate dynamic programming alignments to align target sequence residues with template atomic coordinates.
3. **Backbone Generation & Loop Modeling**: Transfer conserved core backbone coordinates ($N, C_lpha, C, O$) from the template. Reconstruct insertion/deletion loops using fragment libraries or energy minimization algorithms.
4. **Side-Chain Packing & Refinement**: Model rotamer conformations for divergent side chains, optimizing steric contacts and hydrogen-bonding networks.
5. **Quality Assessment**: Evaluate stereochemical accuracy via Ramachandran outlier detection, packing density, and QMEAN scoring parameters.

### 🤖 Deep Learning Structural Prediction: AlphaFold
AlphaFold transforms structural biology by predicting atomic coordinates directly from primary amino acid sequences with experimental accuracy.

```
Multiple Sequence Alignment  ──┐
                               ├──>  Evoformer Blocks  ──>  Structure Module  ──>  3D Atomic Coordinates
Pairwise Residue Matrix      ──┘    (Attention Mechanism)    (Invariant Point)      (pLDDT Confidence)
```

Key technological innovations within AlphaFold include:
* **Evoformer Network**: Processes target Multiple Sequence Alignments (MSAs) and spatial pair representations simultaneously, exchanging evolutionary and geometric spatial information via neural attention mechanisms.
* **Structure Module**: Constructs explicit 3D backbone rotations and translations without template constraints using Invariant Point Attention (IPA).
* **Predicted Local Distance Difference Test (pLDDT)**: Provides per-residue local confidence scores ranging from 0 to 100:
  * $pLDDT > 90$: High confidence; ideal for active site characterization.
  * $70 < pLDDT \le 90$: Confident backbone prediction.
  * $pLDDT < 50$: Flexible, disordered, or unstructured regions.
* **Predicted Aligned Error (PAE)**: Quantifies inter-domain alignment position uncertainties, facilitating domain boundary definition.

---

## 📌 Section 4: Structural Enzymology and Active Site Mechanics

Enzymes function as biological catalysts, accelerating chemical reaction rates by lowering activation energy barriers ($\Delta G^\ddagger$) without altering overall reaction equilibria.

### ⚡ Catalytic Residues and Active Site Architecture
Active sites represent specialized structural pockets lined with catalytic residues that stabilize transition states through precise spatial geometry:
* **Catalytic Triad Mechanics**: Classical serine proteases (e.g., trypsin, chymotrypsin) employ a His-Asp-Ser catalytic triad. Aspartate polarizes Histidine, enabling Histidine to act as a general base that deprotonates Serine, forming a potent nucleophilic alkoxide ion ($O^-$) attacking substrate carbonyl carbons.
* **Oxyanion Hole Stabilization**: Hydrogen bonding networks within active site pockets stabilize transient negatively charged oxygen atoms in tetrahedral reaction intermediates.
* **Induced-Fit Conformational Shifts**: Ligand binding triggers structural adjustments, orienting catalytic residues optimal for orbital overlap and substrate conversion.

### 📚 Mechanism and Catalytic Site Atlas (M-CSA)
The **Mechanism and Catalytic Site Atlas (M-CSA)** provides hand-curated annotations of enzyme active sites, catalytic residues, cofactors, and step-by-step chemical reaction schemes featuring curly electron flow arrows.

```
Enzyme Entry  -->  Catalytic Residues  -->  Curated Reaction Schemes  -->  EnzyMM Motif Search
 (EC Number)        (PDB/UniProt IDs)       (Step-by-step Electron Flow)   (3D Active Site Geometry)
```

M-CSA integration features include:
* Detailed chemical reaction steps mapped to Enzyme Commission (EC) numbers, UniProtKB identifiers, and PDB coordinate structures.
* Mapping of catalytic domains to CATH homologous superfamilies.
* **Enzyme Motif Miner (EnzyMM)**: Enables 3D active site geometric searches across user-submitted PDB or AlphaFold coordinates to identify catalytic motifs independent of overall sequence identity.

### 🔬 Case Study: Bacterial Glutamate Racemase
Glutamate racemase (EC 5.1.1.3, M-CSA Entry 1) catalyzes the interconversion of L-glutamate to D-glutamate in bacteria, producing an essential building block for peptidoglycan cell wall biosynthesis. Peptidoglycan structures contain D-amino acids that protect bacterial cell walls against proteolytic degradation by host proteases.

The catalytic mechanism utilizes a two-cysteine active site architecture (*Aquifex pyrophilus*, PDB ID: 1b73, CATH domain 3.40.50.1860):
* Cysteine 73 acts as a general base, deprotonating the $C_lpha$ position of L-glutamate to yield a planar carbanion intermediate.
* Cysteine 184 acts as a general acid, protonating the opposite face of the intermediate to complete inversion to D-glutamate.

```
L-Glutamate  +  Cys73 (Base)  ──>  Planar Carbanion Intermediate  +  Cys184 (Acid)  ──>  D-Glutamate
```

Because human cells lack glutamate racemase and peptidoglycan cell wall machinery, bacterial glutamate racemase represents an ideal therapeutic target for novel antimicrobial drug design.

Similarly, structural enzymology revealed that the 50S large ribosomal subunit from *Haloarcula marismortui* utilizes peptidyl transferase RNA catalytic centers to form peptide bonds during translation, proving that ribosomal RNA functions as a ribozyme catalyst.

---

## 📚 References

1. OpenStax. 10.3 Structure and Function of RNA. *Microbiology*, OpenStax, 2016.
2. Nissen P, Hansen J, Ban N, Moore PB, Steitz TA. The structural basis of ribosome activity in peptide bond synthesis. *Science*, 289(5481):920-930, 2000.
3. OpenStax. 12.2 Visualizing and Characterizing DNA, RNA, and Protein. *Microbiology*, OpenStax, 2016.
4. OpenStax. Polyacrylamide Gel Electrophoresis (PAGE) and SDS-PAGE. *Microbiology*, OpenStax, 2016.
5. Needleman SB, Wunsch CD. A general method applicable to the search for similarities in the amino acid sequence of two proteins. *J Mol Biol*, 48(3):443-453, 1970.
6. Ramachandran GN, Sasisekharan V. Conformation of polypeptides and proteins. *Adv Protein Chem*, 23:283-438, 1968.
7. Madden T. The BLAST Sequence Analysis Tool. *NCBI Handbook*, 2013.
8. Altschul SF, Gish W, Miller W, Myers EW, Lipman DJ. Basic local alignment search tool. *J Mol Biol*, 215(3):403-410, 1990.
9. Callahan BJ, McMurdie PJ, Rosen MJ, Han AW, Johnson AJ, Holmes SP. DADA2: High-resolution sample inference from Illumina amplicon data. *Nat Methods*, 13(7):581-583, 2016.
10. Wright ES. Using DECIPHER v2.0 to analyze big biological sequence data in R. *The R Journal*, 8(1):352-359, 2016.
11. Sillitoe I, Dawson N, Lewis T, Lee D, Lees J, Orengo C. CATH: Protein Structure Classification Database at UCL. *Nucleic Acids Res*, 43(D1):D219-D226, 2015.
12. CATH-Gene3D Team. Protein Structure Sequence Search and Domain Mapping. UCL, 2024.
13. Orengo C, et al. CATH Homologous Superfamily Diversity and Structural Cores. UCL, 2024.
14. Orengo C, et al. Functional Families (FunFams) in CATH. UCL, 2024.
15. Sillitoe I, et al. CATH Functional Family Annotations and CAFA Assessment. UCL, 2024.
16. Scorecons Server. Conservation Mapping in CATH Functional Families. UCL, 2024.
17. Waman VP, Bordin N, Lau A, Kandathil S, Wells J, Miller D, Velankar S, Jones DT, Sillitoe I, Orengo C. CATH v4.4: major expansion of CATH by experimental and predicted structural data. *Nucleic Acids Res*, 53(D1):gkae1087, 2025.
18. Sillitoe I, et al. CATH Release Statistics and Gene3D Predictions. UCL, 2024.
19. Ribeiro AJM, et al. Mechanism and Catalytic Site Atlas (M-CSA): a database of enzyme reaction mechanisms and active sites. *Nucleic Acids Res*, 46(D1):D618-D623, 2018.
20. M-CSA Entry 1. Glutamate racemase mechanism in Aquifex pyrophilus (PDB 1b73). *EMBL-EBI*, 2026.
21. M-CSA Team. EnzyMM: The Enzyme Motif Miner for Catalytic Motif Search in PDB and AlphaFoldDB. *EMBL-EBI*, 2025.
22. Zardecki C, Dutta S, Goodsell DS, Lowe R, Voigt M, Burley SK. PDB-101: Educational resources supporting molecular explorations through biology and medicine. *Protein Sci*, 31(1):129-140, 2022.
23. PyMOL Development Team. PyMOL Command Reference. *Schrödinger, LLC*, 2026.
24. PyMOL Development Team. Align Command Documentation. *Schrödinger, LLC*, 2026.
25. PyMOL Development Team. Selection Algebra and Representations. *Schrödinger, LLC*, 2026.
26. Shindyalov IN, Bourne PE. Protein structure alignment by incremental combinatorial extension (CE) of the optimal path. *Protein Eng*, 11(9):739-747, 1998.
27. PyMOL Development Team. Molecular Clean and Energy Minimization MMFF94. *Schrödinger, LLC*, 2026.
28. PyMOL Development Team. Color and Selection Utilities. *Schrödinger, LLC*, 2026.
29. PyMOL Development Team. DSS Secondary Structure Assignment. *Schrödinger, LLC*, 2026.
30. PyMOL Development Team. Fab Peptide Builder Documentation. *Schrödinger, LLC*, 2026.
31. PyMOL Development Team. Fragment Library Documentation. *Schrödinger, LLC*, 2026.
32. PyMOL Development Team. Area and Solvent Surface Area Calculation. *Schrödinger, LLC*, 2026.
33. PyMOL Development Team. Dihedral and Phi-Psi Querying Commands. *Schrödinger, LLC*, 2026.
34. PyMOL Development Team. Relative SASA and B-factor Mapping. *Schrödinger, LLC*, 2026.
35. PyMOL Development Team. Phi_Psi Querying Documentation. *Schrödinger, LLC*, 2026.
36. PyMOL Development Team. Ray Tracing and High Resolution Rendering. *Schrödinger, LLC*, 2026.
37. PyMOL Development Team. Super Command Documentation. *Schrödinger, LLC*, 2026.
38. UniProt Consortium. UniProtKB manual: User manual for the UniProtKB flat file format. *UniProt Help*, 2026.
39. wwPDB Consortium. wwPDB Format Version 3.3: Introduction and Record Architecture. *wwPDB*, 2011.
40. wwPDB Consortium. Record Format and Fixed Column Specifications. *wwPDB*, 2011.
41. wwPDB Consortium. Title Section Records (HEADER, CRYST1, TITLE). *wwPDB*, 2011.
42. wwPDB Consortium. Continuation Records and Multi-line Data. *wwPDB*, 2011.
43. wwPDB Consortium. Coordinate Section Records (ATOM, HETATM, HELIX, SHEET, SSBOND). *wwPDB*, 2011.
44. wwPDB Consortium. SEQRES and Primary Structure Records. *wwPDB*, 2011.
45. wwPDB Consortium. MODEL, ENDMDL, and TER Grouping Records. *wwPDB*, 2011.
46. wwPDB Consortium. Order of Records and Mandatory Record Tables. *wwPDB*, 2011.
47. wwPDB Consortium. Sections of a PDB Entry and Record Types. *wwPDB*, 2011.
