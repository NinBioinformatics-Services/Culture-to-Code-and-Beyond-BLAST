# 🧬 Module 1: Multiple Sequence Alignment & Microbial Taxonomy

[![Topic](https://img.shields.io/badge/Module_1-MSA_%26_Taxonomy-brightgreen?style=for-the-badge)](#)
[![Level](https://img.shields.io/badge/Level-FY_UG_to_Professor-blueviolet?style=for-the-badge)](#)
[![Vibe](https://img.shields.io/badge/Vibe-Gen_Z_Bioinformatics-ff69b4?style=for-the-badge)](#)

---

## 📌 1. Multiple Sequence Alignment (MSA) & Progressive Alignment Algorithms

Sequence alignment represents the ultimate core foundation of computational biology. Aligning biological sequences reveals evolutionary conservation, structural motifs, and functional homology across diverse bacterial and fungal species. While pairwise alignment compares two sequences, **Multiple Sequence Alignment (MSA)** aligns three or more biological sequences simultaneously to identify conserved residue positions and evolutionary insertion-deletion (indel) events.

```
Pairwise Alignment:        Seq A: ATGCGATAC
                           Seq B: AT--GATAC

Multiple Sequence (MSA):   Seq A: ATGCGATAC
                           Seq B: AT--GATAC
                           Seq C: ATGCGCTAC
                           Seq D: ATGTGATAC
                                  *** * *** (Conserved Positions)
```

[![Tutorial](https://img.shields.io/badge/Video_link-will_be_out_soon!-%238A2BE2)](#)

### 🧠 Pairwise Foundation: Global vs. Local Alignment Algorithms
Understanding MSA algorithms requires starting with pairwise alignment dynamic programming foundations:

1. **Needleman-Wunsch Algorithm (Global Alignment)**: Formulated by Needleman and Wunsch (1970), this algorithm optimizes alignment across the entire length of two protein or nucleotide sequences. Dynamic programming matrices calculate match scores, mismatch penalties, and gap penalties, making it ideal for sequences of similar length.
2. **Smith-Waterman Algorithm (Local Alignment)**: Developed by Smith and Waterman (1981), this approach identifies high-scoring local subsequences within longer, divergent sequences. Matrix values lower than zero reset to zero, isolating conserved catalytic sites or active domains without forcing full-length alignment.
3. **Maximal Segment Pair (MSP) & Heuristic Alignment**: Altschul et al. (1990) introduced the Basic Local Alignment Search Tool (BLAST), which calculates Maximal Segment Pair (MSP) scores for rapid sequence database searching. BLAST uses heuristic word-matching seeds to accelerate local similarity identification by orders of magnitude compared to exact dynamic programming.

| Feature | Global Alignment (Needleman-Wunsch) | Local Alignment (Smith-Waterman) | Local Heuristic (BLAST) |
| :--- | :--- | :--- | :--- |
| **Primary Focus** | Entire sequence length | Highly conserved local regions | Rapid database query matching |
| **Algorithm Type** | Dynamic Programming | Dynamic Programming | Heuristic Seed Extension |
| **Best Use Case** | End-to-end homolog comparison | Domain or motif identification | High-throughput search |

### 🚀 Progressive Alignment Approach
Computing exact optimal N-dimensional dynamic programming alignments for $N$ sequences is NP-complete, requiring massive computational complexity. Modern MSA tools utilize **progressive alignment algorithms** :

1. **Calculate Pairwise Distance Matrix**: Calculate all pairwise alignment scores between sequence pairs using global alignment.
2. **Construct Guide Tree**: Build a hierarchical guide tree (e.g., via Neighbor-Joining) based on pairwise dissimilarity matrices.
3. **Progressive Profile Alignment**: Align the most closely related sequences first, building sequence profiles. Gradually add more distant sequences or profiles following guide tree topology until all sequences align.

```
Step 1: Pairwise Distances  -->  Step 2: Guide Tree  -->  Step 3: Progressive Alignment
  [A, B, C, D]                      (A, B)                     Align A & B -> Profile 1
  Distance Matrix                   /    \                     Align C & D -> Profile 2
                                 (C, D)  |                     Align Profile 1 & Profile 2
```

### 🛠️ Industry-Standard MSA Software Tools

#### 1. CLUSTAL Omega (CLUSTAL $\Omega$)
CLUSTAL Omega utilizes seeded guide trees and profile Hidden Markov Models (HMMs) to align hundreds of thousands of sequences efficiently. It provides exceptional scalability for massive microbial datasets.

#### 2. MUSCLE (Multiple Sequence Comparison by Log-Expectation)
MUSCLE improves alignment accuracy by incorporating iterative refinement steps. After initial progressive alignment, MUSCLE calculates distance measures, rebuilds guide trees, and re-aligns profile sub-trees to correct early alignment errors.

#### 3. DECIPHER (`AlignSeqs` in R)
The DECIPHER R package implements local sequence context profiling (`AlignSeqs`) to create multiple sequence alignments for high-throughput 16S rRNA gene profiling. DECIPHER uses shared 5-mer distance matrices and iterative reclustering, providing optimized computational efficiency for amplicon analysis pipelines.

---

**Instructions for Performing MSA using Clustal Omega (Clustal W)**

*Note: If You are working on your own Sequence, then You have to Perform Step 1 and Step 2, If you are working as per demonstrated Video, You have to Download the txt file of sequences, mentioned below, and Directly start with Step 3*


Step 1: Collect Sequences

Obtain several related microbial DNA or protein sequences. [Click here to Download .txt file containing FASTA Sequences, same file is used for Demonstration](https://github.com/NinBioinformatics-Services/Culture-to-Code-and-Beyond-BLAST/blob/006ce941084f12274eb6c66a25a9f278e6d2688d/CCBB_MSA_Protein.txt)

Step 2: Prepare the Sequences

Ensure that the sequences are available in an appropriate format such as FASTA. (If Working on your own Sequence, All the sequences are gathered and prepared in txt file provided earlier!)

Step 3: Open the MSA Tool

Use:

CLUSTAL Omega
or
MUSCLE

Step 4: Submit the Sequences

Paste or upload the FASTA sequences.

Step 5: Run the Alignment

The software compares the sequences and generates an MSA.

---

[![Tutorial](https://img.shields.io/badge/Video_link-will_be_out_soon!-%238A2BE2)](#)

## 🧬 2. Marker Gene Analysis & Microbial Taxonomy

Microbial taxonomy relies on marker gene profiling to classify bacteria, archaea, and fungi without needing unculturable organism isolation.

```
                     Microbial Marker Genes
                               |
        +----------------------+----------------------+
        |                                             |
   Bacterial 16S rRNA                            Fungal ITS Region
   - V4 Hypervariable Region                     - Internal Transcribed Spacer
   - DADA2 Ribosomal Variants (RSVs)             - Species-Level Fungi Identification
   - Taxonomic Classifications                   - Environmental Community Profiling
```

### 🧫 16S rRNA Gene Profiling for Bacterial Taxonomy
The **16S ribosomal RNA (16S rRNA) gene** represents the ultimate gold standard marker for bacterial identification and phylogenetics. 

* **Structural Architecture**: The 16S rRNA molecule forms a structural component of the small ribosomal subunit, catalyzing protein translation and mRNA alignment.
* **Conserved vs. Hypervariable Regions**: The gene contains highly conserved regions interspersed with nine **hypervariable regions (V1-V9)**. Conserved regions allow universal PCR primer annealing, while hypervariable regions contain species-specific sequence signatures.
* **V4 Region Focus**: Illumina MiSeq paired-end sequencing frequently targets the **V4 region** (e.g., 2x250 bp amplicon reads) due to optimal overlap, high taxonomic resolution, and robust community coverage.

```
16S rRNA Gene:
[Conserved]--[V1]--[Conserved]--[V2]--[Conserved]--[V3]--[Conserved]--[V4]--[Conserved]
    ^                                                                     ^
  Universal PCR Primer                                               Target Region
```

### 🍄 ITS Region Profiling for Fungal Taxonomy
For eukaryotic microorganisms such as fungi, 16S rRNA gene resolution is insufficient. Fungal taxonomic profiling relies on the **Internal Transcribed Spacer (ITS)** region:

* **Genomic Organization**: The ribosomal RNA gene cluster contains the 18S, 5.8S, and 28S rRNA genes. The **ITS1** spacer region lies between 18S and 5.8S, while **ITS2** sits between 5.8S and 28S.
* **Hypervariability**: Non-coding ITS spacer regions experience high evolutionary mutation rates, enabling species-level differentiation across fungal phyla (e.g., Ascomycota, Basidiomycota).

### 🔬 High-Resolution Denoising: RSVs/ASVs vs. Traditional 97% OTUs

Historically, amplicon bioinformatics clustered sequencing reads into **Operational Taxonomic Units (OTUs)** based on an arbitrary 97% sequence similarity threshold. However, traditional OTU clustering ignores sequence quality scores, masks fine-scale biological variation, and generates spurious taxa.

Modern workflows utilize high-resolution algorithms like **DADA2** to infer exact **Ribosomal Sequence Variants (RSVs)** or **Amplicon Sequence Variants (ASVs)** :

1. **Probabilistic Noise Modeling**: DADA2 incorporates per-base quality scores and sequence frequencies into a parameterized error model for nucleotide transitions.
2. **Single-Nucleotide Resolution**: DADA2 distinguishes real biological variation differing by a single nucleotide from sequencing error.
3. **Dereplication & Chimera Removal**: Sequences are dereplicated, denoised, merged as paired-end reads, and screened to remove chimeric sequences formed during PCR amplification (`removeBimeraDenovo`).

```
Raw Reads (FASTQ) --> Quality Trimming --> DADA2 Error Model --> RSV Table --> Chimera Removal
                                                                                 |
Taxonomic Assignment (RDP / SILVA) <-- DECIPHER Alignment <-- Phylogenetic Tree <--+
```

### 🏷️ Taxonomic Classification Databases
DADA2 utilizes Naive Bayesian Classifiers (`assignTaxonomy`) to match RSVs against reference database training sets.
* **RDP (Ribosomal Database Project)**: Curated 16S rRNA bacterial reference training sets.
* **SILVA**: Comprehensive, quality-checked database for bacterial, archaeal, and eukaryotic ribosomal RNA.
* **Greengenes**: Dedicated 16S rRNA reference database for microbial taxonomy.

---

[![Tutorial](https://img.shields.io/badge/Video_link-will_be_out_soon!-%238A2BE2)](#)

## 🌳 3. Molecular Phylogenetics & Tree-Building Methods

Molecular phylogenetics reconstructs the evolutionary history and genealogical relationships among microbial species based on molecular sequence alignments.

```
                     Phylogenetic Tree Reconstruction
                                   |
        +--------------------------+--------------------------+
        |                                                     |
  Distance-Based Methods                              Probabilistic Methods
  - Matrix Dissimilarity Calculation                   - Character-Based Substitutions
  - Neighbor-Joining (NJ)                              - Maximum Likelihood (ML)
  - Rapid Tree Construction                            - Evolutionary Models (GTR+G+Inv)
```

### 📊 Tree Architecture and Terminology
* **Nodes**: Represent taxonomic units. **External nodes (tips)** represent observed species/RSVs, while **internal nodes** represent ancestral divergence events.
* **Branches**: Connect nodes; branch lengths reflect evolutionary distance (substitutions per site).
* **Clades**: Monophyletic groups comprising a common ancestor and all descended lineage tips.

### 📐 Distance-Based Method: Neighbor-Joining (NJ)
Distance-based methods convert multiple sequence alignments into pairwise dissimilarity matrices:

* **Distance Matrix Calculation**: Pairwise distances evaluate sequence dissimilarity (e.g., Jaccard distance, Bray-Curtis dissimilarity, or Unifrac distances).
* **Algorithm Mechanics**: The Neighbor-Joining (NJ) algorithm iteratively joins the pair of nodes that minimizes total tree branch length while adjusting for individual lineage evolution rates.
* **Performance**: NJ is computationally fast, serving as an outstanding initial tree topology generator for large microbial census datasets.

### 🎲 Character-Based Method: Maximum Likelihood (ML)
Character-based probabilistic methods examine individual alignment positions to evaluate evolutionary hypotheses:

* **Likelihood Optimization**: Maximum Likelihood (ML) searches for the specific phylogenetic tree topology and branch lengths that maximize the statistical probability of observing the alignment given a substitution model.
* **GTR+G+Invariable Evolutionary Substitution Model**:
  * **GTR (Generalized Time-Reversible)**: Allows symmetric, independent substitution rates between all nucleotide pairs.
  * **+G (Gamma Distribution)**: Models rate variation across different sequence sites.
  * **+Invariable (Invariable Sites)**: Accounts for a proportion of evolutionary frozen, non-changing alignment positions.
* **Workflow Strategy**: Modern tools like `phangorn` build an initial Neighbor-Joining tree, then optimize likelihood parameter space to fit a refined GTR+G+Invariable Maximum Likelihood tree.

```
Neighbor-Joining (NJ) Tree  -->  GTR+G+Invariable Substitution Fit  -->  Maximum Likelihood (ML) Refinement
(Initial Fast Approximation)             (Site Rate Model)                  (Optimized Branch Topology)
```

### 🧪 Distance Matrices & Beta-Diversity Ordination
In microbial ecology workflows (such as `phyloseq` in R), phylogenetic trees enable phylogeny-aware dissimilarity calculations:

* **UniFrac Distance**: Measures unique evolutionary branch lengths unshared between two microbial communities. **Unweighted UniFrac** evaluates community membership presence/absence, whereas **Weighted UniFrac** accounts for relative abundance levels.
* **DPCoA (Double Principal Coordinate Analysis)**: Incorporates phylogenetic distances into biplot ordination, projecting sample differences along evolutionary clades (e.g., distinguishing Bacteroidetes vs. Firmicutes shifts across host age bins).

### 🔁 Bootstrapping for Branch Support Evaluation
To assess the statistical reliability of inferred phylogenetic tree branches, researchers perform **bootstrapping**:

1. **Resampling Alignment Columns**: Pseudo-replicate alignments of equal length are generated by randomly sampling alignment columns with replacement.
2. **Tree Reconstruction**: The phylogenetic tree-building algorithm (NJ or ML) runs on each pseudo-replicate dataset (typically 100 to 1,000 iterations).
3. **Branch Support Calculation**: A bootstrap value (expressed as a percentage) is assigned to each internal node, indicating how frequently that specific clade re-occurs across resampled trees. Values exceeding 70-80% indicate strong statistical support for ancestral branching topology.

---

## 📚 References

1. Altschul, S. F., Gish, W., Miller, W., Myers, E. W., & Lipman, D. J. (1990). Basic local alignment search tool. *Journal of Molecular Biology*, 215(3), 403-410. [PubMed PMID: 2231712].
2. Callahan, B. J., Sankaran, K., Fukuyama, J. A., McMurdie, P. J., & Holmes, S. P. (2016). Bioconductor workflow for microbiome data analysis: from raw reads to community analyses. *F1000Research*, 5, 1492. [PMC PMCID: PMC4955027].
3. Cock, P. J., Fields, C. J., Goto, N., Heuer, M. L., & Rice, P. M. (2010). The Sanger FASTQ file format for sequences with quality scores, and the Solexa/Illumina FASTQ variants. *Nucleic Acids Research*, 38(6), 1767-1771. [PubMed PMID: 20015970].
4. EMBL-EBI Training. (2026). *Phylogenetics: An introduction*. European Bioinformatics Institute.
5. Needleman, S. B., & Wunsch, C. D. (1970). A general method applicable to the search for similarities in the amino acid sequence of two proteins. *Journal of Molecular Biology*, 48(3), 443-453. [PubMed PMID: 5420325].
6. OpenStax. (2016). *Microbiology*. Rice University. (Sections 10.2 Structure and Function of DNA, 10.3 Structure and Function of RNA, 12.2 Visualizing and Characterizing DNA, RNA, and Protein).
7. Smith, T. F., & Waterman, M. S. (1981). Identification of common molecular subsequences. *Journal of Molecular Biology*, 147(1), 195-197. [PubMed PMID: 7265238].
