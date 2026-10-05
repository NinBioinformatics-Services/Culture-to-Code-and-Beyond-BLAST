<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/370d4c81-47e5-468e-9747-4175d035d027" />


# Module 2: Structural Bioinformatics & Protein Modeling
---

### Structural Bioinformatics & Protein Modeling

**Focus:**

Understanding how protein sequences form three-dimensional structures and how computational tools can be used to visualize, model, and study proteins.

### Major Topics

* Basics of proteins and protein structure
* Levels of protein structure
* Protein domains
* Protein motifs
* Secondary structure
* Structure visualization
* PyMOL
* UCSF Chimera
* Homology modeling
* SWISS-MODEL
* AlphaFold
* Protein structure prediction
* Active sites
* Catalytic residues
* Structure-based functional interpretation

---

<img width="1920" height="1080" alt="2" src="https://github.com/user-attachments/assets/d55925a8-b41f-4c33-a6c8-ed22759a433b" />


# PART A: BASICS OF PROTEINS
---

## What is a Protein?

A **protein** is a biological molecule made up of amino acids.

Proteins perform many important functions inside cells.

### Examples

* Enzymes
* Transport proteins
* Structural proteins
* Receptors
* Antibodies
* Signaling proteins

### Simple Example

Hemoglobin is a protein that helps transport oxygen.

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/0bcdeb1b-e795-4097-9430-fb9eb0bb36ed" />


Insulin is a protein hormone involved in regulating blood glucose.

### Key Idea

**Protein sequence → Protein structure → Protein function**

---

## What is an Amino Acid?

Amino acids are the basic building blocks of proteins.

Proteins are mainly made from **20 standard amino acids**.

Each amino acid contains characteristic chemical groups.

### Simple Representation

```text
Amino Acid
     ↓
Many amino acids
     ↓
Polypeptide chain
     ↓
Protein
```

The order of amino acids in a protein is called its **amino acid sequence**.

---

## Protein Sequence

A protein sequence represents the order of amino acids in a protein.

Amino acids are commonly represented using one-letter codes.

### Example

```text
MKTLLILAV...
```

Each letter represents an amino acid.

### Why is Protein Sequence Important?

The sequence provides information about:

* Protein composition
* Conserved regions
* Possible domains
* Possible functional sites
* Structural characteristics

### Important Concept

The amino acid sequence contains information that influences how a protein folds into its three-dimensional structure.

---

## From Protein Sequence to Structure

A protein can be studied at different levels.

```text
Amino Acid Sequence
        ↓
Protein Folding
        ↓
3D Structure
        ↓
Biological Function
```

The sequence determines the physical and chemical properties of the protein.

These properties influence how the protein folds.

The resulting three-dimensional structure is closely related to its function.

### Example

An enzyme must have an appropriate three-dimensional arrangement to bind its substrate.

---

<img width="1920" height="1080" alt="3" src="https://github.com/user-attachments/assets/812bfa01-8ade-4257-aeb6-74c532c861e2" />


---
# PART B: LEVELS OF PROTEIN STRUCTURE

## Four Levels of Protein Structure

Protein structure is commonly described at four levels:

1. Primary structure
2. Secondary structure
3. Tertiary structure
4. Quaternary structure

### Simple Flow

```text
Primary
   ↓
Secondary
   ↓
Tertiary
   ↓
Quaternary
```

Each level provides different information about protein organization.

---

## Primary Structure

The **primary structure** is the linear sequence of amino acids in a protein.

### Example

```text
M K T L A V G C ...
```

The exact order of amino acids is important.

Changing even one amino acid can sometimes affect protein structure or function.

### Example

```text
Sequence A: MKTAL...
Sequence B: MKTSL...
```

One amino acid is different.

### Key Point

**Primary structure = amino acid sequence**

---

## Secondary Structure

Secondary structure describes local folding patterns of a protein backbone.

The two major secondary structures are:

* **Alpha helix**
* **Beta sheet**

Other regions can form loops and turns.

### Simple Representation

```text
Alpha Helix → Spiral-like structure

Beta Sheet → Extended sheet-like structure
```

### Why is Secondary Structure Important?

It helps explain how a protein chain begins to fold into a three-dimensional structure.

---

## Alpha Helix

An **alpha helix** is a common secondary structure.

It has a spiral-like shape.

### Characteristics

* Regular helical arrangement
* Stabilized mainly by hydrogen bonding
* Common in many proteins

### Simple Example

```text
~~~~~~~
 Alpha
 Helix
~~~~~~~
```

The alpha helix is a structural element, not an entire protein.

---

## Beta Sheet

A **beta sheet** is another major secondary structure.

It consists of extended regions of the protein backbone arranged next to each other.

### Simple Representation

```text
→→→→
←←←←
→→→→
```

Beta sheets can contain strands running in:

* Parallel orientation
* Antiparallel orientation

### Key Point

Alpha helices and beta sheets together form important components of protein structure.

---

## Loops and Turns

Not every part of a protein forms an alpha helix or beta sheet.

Proteins also contain:

* Loops
* Turns
* Flexible regions

These regions can connect different secondary structures.

### Biological Importance

Loops may contribute to:

* Binding
* Catalysis
* Molecular recognition
* Protein-protein interactions

### Key Idea

A protein's structure is a combination of regular and flexible regions.

---

## Tertiary Structure

**Tertiary structure** refers to the overall three-dimensional arrangement of a single polypeptide chain.

It results from interactions between different parts of the protein.

### Tertiary Structure Includes

* Alpha helices
* Beta sheets
* Loops
* Turns
* Side-chain interactions

### Simple Concept

```text
Primary Sequence
       ↓
Secondary Structures
       ↓
Overall 3D Folding
       ↓
Tertiary Structure
```

---

## Quaternary Structure

Some proteins contain more than one polypeptide chain.

The arrangement of these chains is called **quaternary structure**.

### Example

A protein may contain:

```text
Subunit A + Subunit B
       ↓
Functional Protein Complex
```

### Example

Hemoglobin contains multiple protein subunits.

### Important Point

Not every protein has quaternary structure.

Only proteins containing multiple associated subunits have this level of organization.
---

<img width="350" height="571" alt="image" src="https://github.com/user-attachments/assets/88a11442-083a-4c70-ad16-7fade7d7955c" />

---

<img width="1920" height="1080" alt="5" src="https://github.com/user-attachments/assets/d6a73753-d389-4ab4-a3d1-c943746723ea" />

---
# PART C: DOMAINS AND MOTIFS

## What is a Protein Domain?

A **protein domain** is a distinct region of a protein that can often fold into a stable structural or functional unit.

A protein can contain:

* One domain
* Multiple domains

### Example

```text
Protein
|------Domain 1------|---Domain 2---|
```

Different domains can perform different functions.

### Simple Example

One domain may bind DNA while another domain interacts with another protein.

---

## Why are Protein Domains Important?

Domains help researchers understand protein organization and function.

### Domains can be associated with:

* Enzymatic activity
* DNA binding
* Protein binding
* Membrane interaction
* Signal recognition

### Importance in Bioinformatics

Domain analysis can help predict possible protein function from sequence information.

---

## What is a Protein Motif?

A **motif** is a short, characteristic sequence or structural pattern that can be associated with a particular function.

### Example

A protein may contain a short sequence pattern that is commonly found in a particular family of proteins.

### Simple Concept

```text
Protein Sequence
-----------------------------
------MOTIF------------------
-----------------------------
```

### Domain vs Motif

**Domain:** Larger functional or structural region.

**Motif:** Usually a shorter characteristic pattern.

---

## Domain vs Motif

| Feature   | Domain                                  | Motif                                        |
| --------- | --------------------------------------- | -------------------------------------------- |
| Size      | Usually larger                          | Usually shorter                              |
| Structure | Can form an independent structural unit | Often a short sequence/structural pattern    |
| Function  | May perform a specific function         | May indicate a functional or binding feature |
| Detection | Sequence/structure databases            | Sequence/structure patterns                  |

### Key Message

Domains and motifs provide useful clues about protein function.

---

<img width="1920" height="1080" alt="6" src="https://github.com/user-attachments/assets/ad90ec70-1128-4d69-9dbe-e4b631def5de" />

---
# PART D: SECONDARY STRUCTURE PREDICTION

## What is Secondary Structure Prediction?

Secondary structure prediction attempts to predict whether regions of a protein sequence are likely to form:

* Alpha helices
* Beta sheets
* Loops or other non-regular regions

### Input

Usually:

**Protein amino acid sequence**

### Output

A predicted pattern of secondary structures.

```text
Protein Sequence
       ↓
Prediction Method
       ↓
Helix / Sheet / Loop
```

---

## Why Predict Secondary Structure?

Secondary structure prediction can provide an early understanding of protein organization.

It can help with:

* Structural analysis
* Protein modeling
* Functional interpretation
* Comparing related proteins
* Identifying structured and flexible regions

### Important Point

Prediction is computational.

It should not automatically be treated as equivalent to experimentally determined structure.

---

<img width="1920" height="1080" alt="7" src="https://github.com/user-attachments/assets/da8d6ff4-bbc1-43e2-b791-d84ff7951d82" />

---
# PART E: STRUCTURAL BIOINFORMATICS

## What is Structural Bioinformatics?

**Structural bioinformatics** is the application of computational methods to study the structures of biological molecules.

For proteins, it can involve:

* Protein structure visualization
* Structure comparison
* Structure prediction
* Homology modeling
* Domain analysis
* Active-site analysis
* Protein-ligand interactions

### Basic Concept

```text
Protein Sequence
       ↓
Structural Information
       ↓
Computational Analysis
       ↓
Biological Interpretation
```

---

## Why Study Protein Structure?

Protein structure can provide clues about protein function.

For example:

* A binding pocket may indicate ligand interaction.
* A catalytic arrangement may suggest enzymatic activity.
* A membrane-spanning region may suggest membrane association.
* Similar structures may suggest related functions.

### Simple Example

Two proteins may have different sequences but similar three-dimensional folds.

This can provide evidence of structural or functional relationships.

---
<img width="1920" height="1080" alt="8" src="https://github.com/user-attachments/assets/4467f53a-e2dd-49f6-b6a9-e380af746903" />

---
# PART F: PROTEIN STRUCTURE VISUALIZATION

## What is Protein Structure Visualization?

Protein structure visualization means displaying a protein's three-dimensional structure using computer software.

Instead of viewing a protein only as a sequence:

```text
MKTLL...
```

the structure can be viewed as:

```text
3D Protein
    ↓
Helices
Sheets
Loops
Chains
Ligands
```

### Why Visualize Proteins?

Visualization helps understand:

* Overall shape
* Domains
* Binding sites
* Secondary structures
* Residue positions
* Protein interactions

---

## Common Protein Visualization Tools

Two commonly used molecular visualization tools are:

### PyMOL

A molecular visualization system widely used to display and analyze biological structures.

### UCSF Chimera

A molecular visualization and analysis system that provides multiple ways to inspect molecular structures.

### Both can help visualize:

* Protein structures
* Ligands
* Molecular surfaces
* Secondary structures
* Specific residues
* Protein interactions

---

## PyMOL — Basic Introduction

**PyMOL** is a molecular visualization system.

It can be used to display protein structures in different representations.

### Common Representations

* Cartoon
* Sticks
* Spheres
* Surface
* Lines

### Example

A protein can be displayed as:

```text
Cartoon → Overall fold

Sticks → Selected residues or ligand

Surface → Molecular surface
```

### Main Learning Goal

Use visualization to understand the relationship between protein structure and function.

---

## UCSF Chimera — Basic Introduction

**UCSF Chimera** is a molecular visualization and analysis tool.

It can be used to:

* Display protein structures
* Examine residues
* Measure distances
* Compare structures
* Visualize molecular surfaces
* Examine interactions

### Simple Example

A ligand-binding region can be displayed and individual amino acids around the ligand can be examined.

---

# PART G: PRACTICAL STRUCTURE VISUALIZATION

## Practical Demonstration — Viewing a Protein Structure

### Objective

Visualize a protein and identify its major structural features.

### Step 1

Obtain a protein structure file.

Common structural formats include:

* PDB
* mmCIF

### Step 2

Open the structure using PyMOL or UCSF Chimera.

### Step 3

Display the protein using a cartoon representation.

### Step 4

Identify:

* Alpha helices
* Beta sheets
* Loops
* Chains

### Step 5

Select a specific residue.

### Step 6

Change the representation to sticks.

### Step 7

Examine the selected residue in the surrounding structure.

---

## Slide 27: Reading a 3D Protein Structure

When viewing a protein, ask:

### 1. How many chains are present?

### 2. What secondary structures are visible?

### 3. Are there multiple domains?

### 4. Is a ligand present?

### 5. Which residues are close to the ligand?

### 6. Are there pockets or cavities?

### 7. Are some regions flexible or poorly defined?

### Important Message

A 3D viewer is not just for making attractive images.

It is a tool for asking biological questions about structure and function.

---
<img width="1920" height="1080" alt="9" src="https://github.com/user-attachments/assets/793724a9-f888-4b34-b0fb-fc7762b227e8" />

---
# PART H: HOMOLOGY MODELING

## What is Homology Modeling?

**Homology modeling** is a computational method for predicting the three-dimensional structure of a protein using the experimentally determined structure of a related protein as a template.

### Basic Principle

Related proteins can have similar structures.

Therefore:

```text
Target Protein Sequence
        ↓
Find Related Protein Structure
        ↓
Use as Template
        ↓
Build Model
        ↓
Evaluate Model
```

### Key Concept

A suitable template is important for producing a useful model.

---

## Why is Homology Modeling Useful?

Experimental determination of protein structures can be difficult, expensive, or time-consuming.

Homology modeling can provide a structural model when a suitable related structure is available.

### Possible Uses

* Studying protein structure
* Identifying possible active sites
* Comparing related proteins
* Understanding mutations
* Supporting drug discovery
* Generating hypotheses for experiments

### Important Point

A computational model is a prediction and should be evaluated before biological conclusions are made.

---

## Basic Steps of Homology Modeling

A typical homology modeling workflow includes:

```text
Target Sequence
       ↓
Template Identification
       ↓
Target–Template Alignment
       ↓
Model Building
       ↓
Model Quality Evaluation
       ↓
Structural Interpretation
```

### Four Major Components

1. Template selection
2. Sequence alignment
3. Model construction
4. Model evaluation

SWISS-MODEL integrates these stages into a web-based homology-modeling workflow.

---

<img width="1920" height="1080" alt="10" src="https://github.com/user-attachments/assets/d8d07a5f-7052-4ee5-a1d0-a6b88bada192" />

---
# PART I: SWISS-MODEL

## What is SWISS-MODEL?

**SWISS-MODEL** is a web-based service for protein structure homology modeling.

It can be used to generate a three-dimensional model from a protein sequence when suitable structural templates are available.

### Basic Input

```text
Protein Sequence
```

### General Output

```text
Predicted 3D Protein Model
```

### Main Workflow

```text
Sequence
   ↓
Template Search
   ↓
Template Selection
   ↓
Alignment
   ↓
Model Building
   ↓
Quality Evaluation
```

---

## Template Selection in SWISS-MODEL

A **template** is an experimentally determined protein structure used as a structural reference for modeling.

A good template generally has useful sequence and structural similarity to the target.

### Important Factors

* Sequence similarity
* Coverage
* Structural quality
* Biological relevance
* Alignment quality

### Simple Concept

```text
Target Protein
       ↓
Search known structures
       ↓
Find suitable template
       ↓
Build model
```

---

## Target–Template Alignment

Before model construction, the target protein sequence must be aligned with the template sequence.

### Why is this important?

The alignment determines which residues in the target correspond to residues in the template.

Incorrect alignment can lead to an incorrect model.

### Simple Example

```text
Target:   A B C D E F G
Template: A B C D - F G
```

The alignment determines how the target sequence is mapped onto the known structure.

---

## Model Quality Evaluation

A generated model should not be accepted simply because a 3D structure has been produced.

The model must be evaluated.

### Questions to Ask

* Is the template appropriate?
* Is sequence coverage sufficient?
* Is the target-template alignment reliable?
* Are modeled regions structurally reasonable?
* Are there poorly modeled regions?
* Are important functional residues positioned reasonably?

### Key Principle

**Model generation is not the final step. Model evaluation is essential.**

---

<img width="1920" height="1080" alt="ALPHAFOLD" src="https://github.com/user-attachments/assets/557b8943-02f2-439a-b2d0-e813ff9ca3ff" />

---
# PART J: ALPHAFOLD

## What is AlphaFold?

**AlphaFold** is an AI-based protein structure prediction system developed by Google DeepMind.

It predicts protein structures from amino acid sequence information.

The AlphaFold Protein Structure Database provides large-scale access to predicted protein structures.

### Basic Concept

```text
Protein Sequence
       ↓
AI-Based Prediction
       ↓
Predicted 3D Structure
       ↓
Confidence Assessment
       ↓
Structural Interpretation
```

---

## Why is AlphaFold Important?

Determining protein structures experimentally can be challenging.

AI-based prediction can provide structural hypotheses rapidly for many proteins.

### Applications

AlphaFold predictions can support:

* Protein function studies
* Structural biology
* Disease research
* Drug discovery
* Protein engineering
* Comparative biology

### Important Point

AlphaFold provides predictions, not experimental measurements.

Predicted structures should be interpreted together with confidence information and biological evidence.

---

## AlphaFold Structure Prediction — Basic Workflow

### Step 1

Obtain the protein amino acid sequence.

### Step 2

Search for the protein in the AlphaFold Protein Structure Database.

### Step 3

If a prediction is available, open the corresponding structure page.

### Step 4

Inspect the predicted 3D structure.

### Step 5

Examine confidence information.

### Step 6

Identify domains, structural regions, and possible functional sites.

### Step 7

Use additional biological evidence before making strong functional conclusions.

---

## Understanding AlphaFold Confidence

AlphaFold provides a per-residue confidence measure called **pLDDT**.

The score ranges from:

**0 to 100**

Higher pLDDT generally indicates greater confidence in the local structural prediction.

### General Interpretation

* **High pLDDT:** high confidence in the local structure
* **Intermediate pLDDT:** moderate confidence
* **Low pLDDT:** lower confidence or potentially flexible/disordered region

### Important Point

Confidence can vary across different regions of the same protein.

Therefore, the whole protein should not automatically be treated as equally reliable.

---

## AlphaFold and Experimental Structures

A predicted structure and an experimentally determined structure are not exactly the same thing.

### Experimental Structure

Obtained using experimental structural biology techniques.

Examples include:

* X-ray crystallography
* Nuclear Magnetic Resonance
* Cryo-Electron Microscopy

### Predicted Structure

Generated computationally using a prediction method such as AlphaFold.

### Key Message

Prediction can provide an extremely useful structural hypothesis, but experimental evidence remains important for validation.

---

<img width="1920" height="1080" alt="11" src="https://github.com/user-attachments/assets/f49aeca9-bda3-4b67-8253-c378bb9668bc" />

---
# PART K: HOMOLOGY MODELING VS ALPHAFOLD

## SWISS-MODEL vs AlphaFold

| Feature             | Homology Modeling                                 | AlphaFold                                                |
| ------------------- | ------------------------------------------------- | -------------------------------------------------------- |
| Main idea           | Uses related known structures                     | AI-based structure prediction                            |
| Template dependence | Strongly depends on suitable templates            | Does not require a conventional template in the same way |
| Input               | Protein sequence                                  | Protein sequence                                         |
| Output              | Predicted 3D model                                | Predicted 3D structure                                   |
| Quality assessment  | Essential                                         | Essential                                                |
| Main strength       | Useful when good related structures are available | Powerful prediction across broad protein sequence space  |

### Key Message

Both approaches are computational methods for obtaining structural information.

The appropriate method depends on the protein, available evidence, and research question.

---
<img width="1920" height="1080" alt="12" src="https://github.com/user-attachments/assets/b57381e0-3407-472b-a714-be5488bcfbd3" />

---
# PART L: ACTIVE SITES AND CATALYTIC RESIDUES

## What is an Active Site?

The **active site** is the region of an enzyme where substrate binding and catalytic activity occur.

It is usually formed by specific amino acid residues brought together by protein folding.

### Important Concept

Amino acids that are far apart in the primary sequence can become close together in the 3D structure.

```text
Sequence:
Residue 25
             \
              → 3D Active Site
             /
Residue 150
```

### Key Point

Protein structure is essential for understanding enzyme function.

---

## What are Catalytic Residues?

**Catalytic residues** are amino acids that directly participate in the chemical reaction carried out by an enzyme.

They may:

* Donate or accept protons
* Stabilize reaction intermediates
* Participate in chemical transformations
* Help position the substrate

### Example

An enzyme may contain several residues around a substrate, but only some may directly participate in catalysis.

### Important Distinction

**Active site:** broader functional region.

**Catalytic residues:** specific residues involved directly in catalysis.

---

## Protein–Ligand Interactions

A ligand is a molecule that binds to a protein.

Examples include:

* Substrates
* Inhibitors
* Cofactors
* Drugs

### Important Interactions

Protein-ligand binding can involve:

* Hydrogen bonds
* Ionic interactions
* Hydrophobic interactions
* Van der Waals interactions

### Visualization

A molecular viewer can help identify residues located near a ligand.

---

## Practical Demonstration — Finding an Active Site

### Objective

Use a 3D protein structure to examine a possible active site.

### Step 1

Open a protein structure in PyMOL or UCSF Chimera.

### Step 2

Display the protein using cartoon representation.

### Step 3

Identify the ligand, if present.

### Step 4

Display the ligand using sticks.

### Step 5

Identify amino acid residues near the ligand.

### Step 6

Display these residues using sticks.

### Step 7

Measure relevant distances or inspect possible interactions.

### Step 8

Compare the observed residues with known functional information.

### Interpretation

Residues located near a ligand may contribute to binding or catalysis, but proximity alone does not prove catalytic function.

---
<img width="1920" height="1080" alt="13" src="https://github.com/user-attachments/assets/b9cd8988-b0bd-4acd-8c59-f093321039d8" />

---
# PART M: STRUCTURE COMPARISON

## Comparing Two Protein Structures

Two proteins can be compared using their three-dimensional structures.

### Questions to Ask

* Do they have a similar overall fold?
* Are their domains arranged similarly?
* Are important residues conserved?
* Are active sites positioned similarly?
* Are there structural differences?

### Why Compare Structures?

Structure comparison can reveal relationships that may not be obvious from sequence comparison alone.

---

## Structure–Function Relationship

A protein's function is strongly related to its three-dimensional structure.

### Example

An enzyme requires:

* Correct folding
* Correct active-site shape
* Correct positioning of important residues

If the structure changes significantly, function may also be affected.

### Simple Concept

```text
Sequence
   ↓
Folding
   ↓
3D Structure
   ↓
Active Site
   ↓
Function
```

### Key Message

**Structure provides a bridge between sequence and biological function.**

---

## Reflection Questions and End of Module

### Reflection Questions

1. What are the four levels of protein structure?
2. What is the difference between a protein domain and a motif?
3. Why is secondary structure prediction useful?
4. Why is protein structure visualization important?
5. What is the basic principle of homology modeling?
6. Why is template selection important in SWISS-MODEL?
7. What is the main idea behind AlphaFold?
8. What does pLDDT tell about an AlphaFold prediction?
9. What is the difference between an active site and a catalytic residue?
10. Why should computational protein models be carefully evaluated?

### End of Module 2

**Structural Bioinformatics & Protein Modeling**

**From protein sequence to 3D structure and biological function**
