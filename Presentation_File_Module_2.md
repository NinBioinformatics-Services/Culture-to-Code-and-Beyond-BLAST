# Module 2: Structural Bioinformatics & Protein Modeling

## Slide 1: Module Title

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

# PART A: BASICS OF PROTEINS

## Slide 2: What is a Protein?

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

Insulin is a protein hormone involved in regulating blood glucose.

### Key Idea

**Protein sequence → Protein structure → Protein function**

---

## Slide 3: What is an Amino Acid?

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

## Slide 4: Protein Sequence

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

## Slide 5: From Protein Sequence to Structure

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

# PART B: LEVELS OF PROTEIN STRUCTURE

## Slide 6: Four Levels of Protein Structure

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

## Slide 7: Primary Structure

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

## Slide 8: Secondary Structure

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

## Slide 9: Alpha Helix

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

## Slide 10: Beta Sheet

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

## Slide 11: Loops and Turns

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

## Slide 12: Tertiary Structure

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

## Slide 13: Quaternary Structure

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

# PART C: DOMAINS AND MOTIFS

## Slide 14: What is a Protein Domain?

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

## Slide 15: Why are Protein Domains Important?

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

## Slide 16: What is a Protein Motif?

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

## Slide 17: Domain vs Motif

| Feature   | Domain                                  | Motif                                        |
| --------- | --------------------------------------- | -------------------------------------------- |
| Size      | Usually larger                          | Usually shorter                              |
| Structure | Can form an independent structural unit | Often a short sequence/structural pattern    |
| Function  | May perform a specific function         | May indicate a functional or binding feature |
| Detection | Sequence/structure databases            | Sequence/structure patterns                  |

### Key Message

Domains and motifs provide useful clues about protein function.

---

# PART D: SECONDARY STRUCTURE PREDICTION

## Slide 18: What is Secondary Structure Prediction?

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

## Slide 19: Why Predict Secondary Structure?

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

# PART E: STRUCTURAL BIOINFORMATICS

## Slide 20: What is Structural Bioinformatics?

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

## Slide 21: Why Study Protein Structure?

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

# PART F: PROTEIN STRUCTURE VISUALIZATION

## Slide 22: What is Protein Structure Visualization?

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

## Slide 23: Common Protein Visualization Tools

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

## Slide 24: PyMOL — Basic Introduction

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

## Slide 25: UCSF Chimera — Basic Introduction

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

## Slide 26: Practical Demonstration — Viewing a Protein Structure

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

# PART H: HOMOLOGY MODELING

## Slide 28: What is Homology Modeling?

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

## Slide 29: Why is Homology Modeling Useful?

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

## Slide 30: Basic Steps of Homology Modeling

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

# PART I: SWISS-MODEL

## Slide 31: What is SWISS-MODEL?

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

## Slide 32: Template Selection in SWISS-MODEL

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

## Slide 33: Target–Template Alignment

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

## Slide 34: Model Quality Evaluation

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

# PART J: ALPHAFOLD

## Slide 35: What is AlphaFold?

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

## Slide 36: Why is AlphaFold Important?

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

## Slide 37: AlphaFold Structure Prediction — Basic Workflow

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

## Slide 38: Understanding AlphaFold Confidence

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

## Slide 39: AlphaFold and Experimental Structures

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

# PART K: HOMOLOGY MODELING VS ALPHAFOLD

## Slide 40: SWISS-MODEL vs AlphaFold

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

# PART L: ACTIVE SITES AND CATALYTIC RESIDUES

## Slide 41: What is an Active Site?

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

## Slide 42: What are Catalytic Residues?

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

## Slide 43: Protein–Ligand Interactions

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

## Slide 44: Practical Demonstration — Finding an Active Site

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

# PART M: STRUCTURE COMPARISON

## Slide 45: Comparing Two Protein Structures

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

## Slide 46: Structure–Function Relationship

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

# PART N: COMPLETE PRACTICAL WORKFLOW

## Slide 47: Practical Workflow — Protein Sequence to Structure

### Overall Workflow

```text
Protein Sequence
       ↓
Sequence Analysis
       ↓
Domain / Motif Identification
       ↓
Known Structure Search
       ↓
     ┌───────────────┐
     ↓               ↓
Known Structure   No Suitable Structure
     ↓               ↓
Visualization    Structure Prediction
     ↓               ↓
PyMOL/Chimera    SWISS-MODEL / AlphaFold
     ↓               ↓
Structural Analysis
       ↓
Active Site / Ligand Analysis
       ↓
Functional Interpretation
```

### Main Learning Goal

Move from a simple protein sequence toward a biologically meaningful structural interpretation.

---

## Slide 48: Complete Demonstration — SWISS-MODEL and AlphaFold

### Part A: SWISS-MODEL

1. Select a protein sequence.
2. Submit the sequence to SWISS-MODEL.
3. Examine available templates.
4. Compare template quality and sequence similarity.
5. Select an appropriate template.
6. Generate the homology model.
7. Examine model quality.
8. Visualize the model.
9. Inspect important residues or regions.

### Part B: AlphaFold

1. Obtain the same protein sequence.
2. Search the AlphaFold Protein Structure Database.
3. Open the predicted structure.
4. Examine the 3D model.
5. Inspect pLDDT confidence.
6. Identify high- and low-confidence regions.
7. Compare the predicted structure with the SWISS-MODEL model.
8. Examine possible functional regions.

### Discussion

Ask:

* Are the overall folds similar?
* Which regions differ?
* Which regions have high confidence?
* Are functional residues located in reliable regions?
* What additional evidence would be needed?

---

# PART O: IMPORTANT CONCEPTUAL POINTS

## Slide 49: Key Takeaways

### Protein Structure

Proteins have primary, secondary, tertiary, and sometimes quaternary structure.

### Domains and Motifs

Domains and motifs provide important clues about protein organization and function.

### Visualization

PyMOL and UCSF Chimera allow protein structures to be explored in three dimensions.

### Homology Modeling

SWISS-MODEL can build a protein model using suitable known structures as templates.

### AlphaFold

AlphaFold provides AI-based protein structure predictions from amino acid sequence information.

### Active Sites

The active site is the region involved in substrate binding and enzyme activity.

### Catalytic Residues

Specific residues within or around the active site can directly participate in catalysis.

### Final Principle

**Sequence → Structure → Active Site → Function**

---

## Slide 50: Reflection Questions and End of Module

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

### Final Workflow

```text
PROTEIN SEQUENCE
       ↓
STRUCTURAL ORGANIZATION
       ↓
DOMAINS + MOTIFS
       ↓
STRUCTURE VISUALIZATION
       ↓
HOMOLOGY MODELING / ALPHAFOLD
       ↓
MODEL CONFIDENCE
       ↓
ACTIVE SITE
       ↓
CATALYTIC RESIDUES
       ↓
FUNCTIONAL INTERPRETATION
```

### End of Module 2

**Structural Bioinformatics & Protein Modeling**

**From protein sequence to 3D structure and biological function**
