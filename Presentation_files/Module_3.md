# Module 3: Microbial Genomics, NGS & Transcriptomics

## Part A: Introduction to Microbial Genomics

### Module Title
**Microbial Genomics, NGS & Transcriptomics**

This module introduces computational methods used to study microbial genomes, analyse high-throughput sequencing data, identify genes, investigate gene expression, and study microbial communities directly from environmental samples.

### What Is a Genome?
A genome is the complete set of genetic material present in an organism. In most bacteria and archaea, the genome is primarily composed of DNA and is commonly organized as a circular chromosome, although linear chromosomes also occur.

Some microorganisms also carry plasmids, which are smaller DNA molecules that replicate independently of the chromosome. Plasmids may carry genes associated with antibiotic resistance or other useful traits.

**Example:** A bacterial genome may contain genes required for growth, metabolism, reproduction, and adaptation to environmental conditions.

### What Is Microbial Genomics?
Microbial genomics is the study of the complete genetic material of microorganisms using sequencing and computational analysis.

It helps researchers investigate:
- The genes present in a microorganism.
- Differences between microbial strains.
- Genes associated with antibiotic resistance.
- Evolutionary relationships between microorganisms.
- Genetic adaptations to different environments.

**Example:** Comparing the genomes of two bacterial strains can help identify genes that are present in one strain but absent in the other.

### What Is High-Throughput Sequencing?
High-throughput sequencing, also called next-generation sequencing (NGS) in many contexts, refers to technologies that generate large numbers of DNA or RNA sequence reads in a single experiment.

Traditional sequencing methods generally process fewer DNA fragments at a time. High-throughput platforms can produce millions of reads, depending on the instrument and experimental design.

**Example:** Instead of sequencing one small DNA fragment at a time, a sequencing run can generate data from many fragments of a microbial genome simultaneously.

### What Is a Sequencing Read?
A sequencing read is a sequence of nucleotide bases obtained from a DNA or RNA sequencing experiment.

A read may contain hundreds to thousands of bases, depending on the platform and sequencing method. Many reads are generated from overlapping or different regions of the original genetic material.

Computational tools analyse these reads to reconstruct genomes, identify genes, or measure RNA abundance.

### Why Is Computational Analysis Necessary?
Sequencing produces large amounts of raw data. The data must be checked, processed, compared, and interpreted before meaningful biological conclusions can be drawn.

Computational analysis helps to:
- Detect low-quality reads.
- Remove adapters and unwanted sequences.
- Assemble genomes or map reads to a reference.
- Identify genes and genetic features.
- Estimate gene expression.
- Characterize microbial communities.

## Part B: Sequencing Technologies

### Overview of Sequencing Platforms
Several sequencing technologies are used in microbial genomics. Two important examples are Illumina sequencing and Oxford Nanopore sequencing.

Both can generate DNA sequence data, but they differ in sequencing chemistry, typical read lengths, error patterns, equipment, and data analysis requirements.

The appropriate platform depends on the research question, sample type, budget, and required sequence resolution.

### Illumina Sequencing — Basic Principle
Illumina sequencing commonly uses sequencing by synthesis. DNA fragments are prepared for sequencing, attached to a flow cell, and amplified into clusters. Fluorescently labelled nucleotides are incorporated during sequencing, and the resulting signals are used to determine the base sequence.

Illumina platforms are widely used because they typically provide high per-base accuracy and high sequencing output.

**Example:** Illumina reads can be used to detect small genetic variations or identify genes in a bacterial genome.

### Oxford Nanopore Sequencing — Basic Principle
Oxford Nanopore sequencing passes DNA or RNA molecules through a nanopore. As a molecule moves through the pore, it changes the electrical current. Computational methods interpret these signals to infer the nucleotide sequence.

A major advantage is the ability to generate long reads, depending on the input molecule and sequencing setup. Some workflows can also provide data in near real time.

**Example:** Long reads can help resolve repeated regions in a bacterial genome or connect an antibiotic-resistance gene to a plasmid.

### Illumina vs. Oxford Nanopore

**Illumina**
- Commonly produces short reads.
- Typically provides high per-base accuracy.
- Useful for variant detection, read mapping, and many genome sequencing projects.
- Repeated regions may be difficult to resolve using short reads alone.

**Oxford Nanopore**
- Can produce long reads.
- Can help resolve repeats and complex genome regions.
- Can support rapid data generation during a run.
- Accuracy depends on the chemistry, basecalling method, and analysis workflow.

Neither platform is best for every experiment. The choice depends on the biological question and the required data quality.

### Why Combine Short and Long Reads?
Short reads can provide accurate base-level information, while long reads can span repeated regions and connect distant parts of a genome.

Combining both types of data can improve genome assembly and help resolve complex regions.

**Example:** Long reads may connect a plasmid resistance gene to the rest of a plasmid, while short reads help refine the nucleotide sequence.

A combined approach is often called hybrid sequencing or hybrid assembly when the reads are used together for genome reconstruction.

## Part C: From Raw Reads to Usable Data

### Slide 12: What Is a FASTQ File?
FASTQ is a common file format used to store sequencing reads together with their base-quality scores.

A typical FASTQ record contains four lines:
1. A read identifier beginning with `@`.
2. The nucleotide sequence.
3. A separator line beginning with `+`.
4. Quality-score characters corresponding to the sequence bases.

FASTQ files are commonly used as the starting point for read quality control and preprocessing.

### Slide 13: What Are Quality Scores?
Sequencing quality scores estimate the confidence associated with individual base calls. They are commonly represented using Phred quality scores.

A higher Phred score indicates a lower estimated probability of a base-calling error.

For example, a Phred score of Q30 corresponds to an estimated error probability of 1 in 1,000 for that base, or 99.9% base-call accuracy under the Phred model.

Quality scores are important because low-quality bases can affect mapping, assembly, and variant detection.

### Slide 14: What Is Quality Control in Sequencing?
Quality control (QC) is the process of checking whether sequencing data meet the requirements for downstream analysis.

Common QC checks include:
- Number of reads generated.
- Read-length distribution.
- Base-quality distribution.
- Adapter contamination.
- GC-content distribution.
- Unexpected contamination or unusual sequence patterns.

QC results help determine whether data are suitable for further processing.

### Slide 15: Adapter Trimming and Read Filtering
Adapters are short artificial DNA sequences introduced during library preparation. They may appear in sequencing reads when the original DNA fragment is shorter than the sequenced region or when adapter sequences are otherwise retained.

Adapter trimming removes these unwanted sequences. Quality filtering may remove reads or bases that do not meet specified criteria.

**Important:** Trimming parameters should be selected carefully. Excessive trimming can remove useful biological sequence information.

### Slide 16: Practical Demonstration — Initial Read Quality Control
**Objective:** Inspect raw sequencing data before further analysis.

**General workflow:**
1. Obtain the sequencing FASTQ files.
2. Run a quality-control tool such as FastQC.
3. Examine per-base quality, read lengths, GC content, and adapter-related warnings.
4. Summarize the results with a tool such as MultiQC when several QC reports are available.
5. Decide whether adapter trimming or quality filtering is necessary.
6. Re-run QC on the processed reads.

**Interpretation:** A report is not simply a pass-or-fail certificate. Warnings should be interpreted in the context of the sequencing technology, library preparation, organism, and research objective.

## Part D: Genome Assembly and Reference Mapping

### Slide 17: What Is Genome Assembly?
Genome assembly is the computational process of reconstructing longer genomic sequences from shorter sequencing reads.

The reads are fragments of the original DNA. Assembly tools identify overlaps or other sequence relationships and combine reads into longer sequences called contigs.

Contigs may be connected into scaffolds when additional information supports their relative order and orientation.

### Slide 18: What Is a Contig?
A contig is a continuous DNA sequence assembled from overlapping sequencing reads without gaps within that sequence.

For example, if several reads overlap across a region of a bacterial chromosome, an assembly program may combine them into one longer contig.

A draft genome may contain several contigs rather than one complete chromosome.

### Slide 19: What Is a Scaffold?
A scaffold is a larger assembly structure that connects contigs in an estimated order and orientation. Gaps may remain between the contigs because the intervening sequence is not fully reconstructed.

Scaffolds provide additional information about genome organization, but a scaffold is not necessarily a continuous, fully resolved DNA sequence.

### Slide 20: What Is de novo Assembly?
De novo assembly reconstructs genomic sequences without relying on a pre-existing reference genome to guide the assembly.

The assembler uses information in the sequencing reads to infer how the fragments fit together.

This approach is useful when:
- The organism has no suitable reference genome.
- The genome differs substantially from available references.
- Researchers want to investigate novel genomic regions.

**Example:** Sequencing an environmental bacterium with no closely related reference genome may require de novo assembly.

### Slide 21: What Is Reference Mapping?
Reference mapping aligns sequencing reads against an existing reference genome or sequence.

The reference provides a coordinate system for determining where reads originate. Mapped reads can then be used to study sequence variation, gene coverage, or other genomic features.

**Example:** Reads from a newly isolated bacterial strain can be mapped against a related reference genome to investigate differences between the strains.

### Slide 22: de novo Assembly vs. Reference Mapping

**de novo assembly**
- Reconstructs sequences from the reads.
- Does not require a reference genome to guide the assembly.
- Can reveal genomic regions absent from known references.
- May be computationally demanding and can be difficult in repetitive regions.

**Reference mapping**
- Aligns reads to an existing reference.
- Makes it easier to analyse differences at known genomic positions.
- Depends on the suitability of the reference.
- May fail to represent novel or highly divergent regions adequately.

The method should be chosen according to the study objective and the availability of an appropriate reference genome.

### Slide 23: What Is Genome Coverage?
Genome coverage describes how much sequencing data are available relative to the size of the genome.

A simplified measure of average sequencing depth is:

Average depth = Total number of sequenced bases ÷ Genome size

For example, if 200 million bases of usable sequence data are generated for a genome of 5 million bases, the nominal average depth is 40×.

Actual usable coverage can be lower because of duplicate reads, uneven coverage, filtering, or reads that do not map to the target genome.

### Slide 24: What Is Assembly Quality?
Assembly quality describes how well an assembly represents the original genome.

Common assessment measures include:
- Total assembly length.
- Number of contigs.
- Contig-length distribution.
- N50.
- Completeness and contamination estimates.
- Agreement with expected genome characteristics.

No single statistic proves that an assembly is correct. Several measures and biological checks should be considered together.

### Slide 25: What Is N50?
N50 is a commonly reported assembly statistic describing contig or scaffold lengths.

To calculate contig N50, contigs are sorted from longest to shortest and their lengths are added until the cumulative length reaches at least 50% of the total assembly length. The length of the contig at that point is the N50.

A higher N50 often indicates a more contiguous assembly, but it does not automatically mean that the assembly is more accurate or complete.

## Part E: Genome Annotation and ORFs

### Slide 26: What Is Genome Annotation?
Genome annotation identifies and describes biological features in a genome sequence.

Structural annotation identifies features such as genes, coding sequences, RNA genes, and other genomic elements.

Functional annotation assigns likely biological roles to identified genes or proteins using evidence such as sequence similarity, conserved domains, and curated databases.

Annotation is a key step in converting an assembled sequence into biologically interpretable information.

### Slide 27: What Is an Open Reading Frame (ORF)?
An open reading frame (ORF) is a stretch of nucleotide sequence that could potentially encode a protein, based on its reading frame and the presence of start and stop codons.

Protein-coding sequences are interpreted in groups of three nucleotides called codons.

An ORF is a candidate for coding potential, not proof that a functional protein is produced. Additional evidence is needed to identify genuine genes confidently.

### Slide 28: Why Are ORFs Important?
ORF identification helps researchers find possible protein-coding regions in newly sequenced genomes.

It is useful for:
- Predicting genes in microbial genomes.
- Identifying candidate proteins.
- Comparing genes between organisms.
- Investigating possible metabolic pathways.
- Detecting candidate resistance or virulence genes.

**Example:** An ORF predicted in a bacterial genome may encode a protein involved in nutrient metabolism, but its function requires further evidence.

### Slide 29: How Are ORFs Identified?
A basic ORF-searching approach examines the possible reading frames of a DNA sequence and looks for stretches that begin with a recognised start codon and end at an in-frame stop codon.

In DNA, commonly recognised start and stop codons include:
- Start: ATG, although alternative start codons occur in some organisms.
- Stop: TAA, TAG, and TGA.

Gene prediction tools use additional information, such as coding patterns and organism-specific features. In microbial genomes, automated annotation pipelines are often used because manual identification is not practical at scale.

### Slide 30: What Is Functional Annotation?
Functional annotation attempts to assign a biological role to a predicted gene or protein.

Evidence may include:
- Similarity to experimentally characterized proteins.
- Conserved protein domains or motifs.
- Protein family membership.
- Known biological pathways.
- Organism-specific information.

Predicted functions should be labelled according to the strength of evidence. A weak similarity does not justify a highly specific functional claim.

### Slide 31: Practical Demonstration — From Reads to Annotated Genome
**Objective:** Understand the stages involved in processing microbial sequencing data.

**General workflow:**
1. Obtain raw FASTQ reads.
2. Check read quality with FastQC.
3. Summarize reports with MultiQC when appropriate.
4. Trim adapters or filter reads if needed.
5. Assemble the genome using an appropriate assembler.
6. Evaluate the assembly using assembly statistics and suitable quality tools.
7. Annotate the assembled genome using a pipeline such as Prokka or Bakta, where appropriate.
8. Examine predicted genes, coding sequences, RNA genes, and functional annotations.

**Expected outputs:** QC reports, cleaned reads, contigs or scaffolds, assembly statistics, annotated genome files, and gene or protein tables.

## Part F: Introduction to Transcriptomics

### Slide 32: What Is Transcriptomics?
Transcriptomics is the study of RNA molecules produced by cells or organisms under particular conditions.

The transcriptome can change with environmental conditions, growth stages, nutrient availability, stress, or infection.

Unlike a genome, which is comparatively stable within a strain, the transcriptome can change substantially depending on when and how the sample is collected.

### Slide 33: What Is Gene Expression?
Gene expression is the process by which information in a gene is used to produce a functional product, such as RNA or protein.

For protein-coding genes, expression commonly involves transcription of DNA into RNA followed by translation of messenger RNA into protein.

Measuring RNA abundance provides information about transcriptional activity, but RNA abundance does not always directly predict protein abundance or activity.

### Slide 34: What Is RNA-Seq?
RNA sequencing (RNA-Seq) is a high-throughput method used to study RNA molecules by sequencing cDNA or, in some workflows, RNA directly.

In a common RNA-Seq workflow, RNA is extracted, a sequencing library is prepared, and sequencing reads are analysed to estimate transcript abundance or compare gene expression between conditions.

RNA-Seq can identify expressed genes, compare expression levels, and reveal transcriptional responses to different treatments.

### Slide 35: Why Is RNA-Seq Useful in Microbiology?
RNA-Seq can help researchers investigate how microorganisms respond to changes in their environment.

Examples include:
- Bacterial responses to antibiotic exposure.
- Gene expression during nutrient limitation.
- Changes in gene expression during infection.
- Responses to heat, cold, or oxidative stress.
- Differences between growth conditions.

**Example:** Comparing bacterial cultures grown with and without an antibiotic can reveal genes whose RNA abundance changes during exposure. Such changes can suggest biological responses, but do not alone prove that a gene causes resistance.

### Slide 36: Basic RNA-Seq Workflow
A typical RNA-Seq workflow includes:

1. Design biological conditions and replicates.
2. Collect samples consistently.
3. Extract RNA.
4. Assess RNA quality and quantity.
5. Prepare sequencing libraries.
6. Sequence the libraries.
7. Perform read-level quality control.
8. Trim or filter reads if required.
9. Map reads to a reference genome or transcriptome, or use a suitable alternative when no reference is available.
10. Generate a gene-level count matrix.
11. Perform statistical differential expression analysis.
12. Interpret the results using biological knowledge and suitable functional analyses.

The exact workflow depends on the organism, library preparation method, reference availability, and research question.

### Slide 37: What Is Differential Gene Expression?
Differential gene expression analysis identifies genes whose measured RNA abundance differs between experimental conditions.

For example, researchers may compare gene expression in bacteria exposed to a stress condition with expression in an untreated control group.

Statistical analysis helps distinguish expression differences supported by the data from changes that could plausibly arise from biological or technical variation.

### Slide 38: What Is a Control Group?
A control group provides a baseline for comparison.

In an RNA-Seq experiment, the control may represent an untreated condition, a standard growth condition, or another scientifically appropriate reference state.

Experimental and control samples should be collected and processed consistently. Biological replicates are important for estimating natural variation between samples.

### Slide 39: What Are Biological Replicates?
Biological replicates are independent biological samples representing the same experimental condition.

For example, independently grown bacterial cultures treated under the same conditions can serve as biological replicates.

Replicates help estimate biological variation and improve the reliability of statistical comparisons. Repeated sequencing of the same library is not equivalent to collecting independent biological replicates.

### Slide 40: What Is a Count Matrix?
A count matrix is a table containing the number of sequencing reads assigned to each gene in each sample.

Rows usually represent genes, and columns represent samples.

A simplified example:

| Gene | Control 1 | Control 2 | Treated 1 | Treated 2 |
|---|---:|---:|---:|---:|
| Gene A | 100 | 110 | 250 | 240 |
| Gene B | 300 | 290 | 280 | 310 |
| Gene C | 20 | 25 | 8 | 10 |

These are illustrative counts. The table alone is not enough to establish statistical significance because sample variation, sequencing depth, and the analysis model must also be considered.

### Slide 41: What Are Fold Change and Log2 Fold Change?
Fold change describes the ratio of expression between two conditions.

For example, if a gene has an estimated expression level of 200 in the treated condition and 100 in the control condition, the fold change is 2.

Log2 fold change is the base-2 logarithm of that ratio:
- Log2 fold change = +1 means a twofold increase.
- Log2 fold change = 0 means no change in the ratio.
- Log2 fold change = −1 means the expression ratio is one-half, or a twofold decrease.

In actual RNA-Seq analysis, fold changes are generally calculated from normalized expression estimates using a statistical model, rather than by comparing raw counts alone.

### Slide 42: What Is a p-Value and Adjusted p-Value?
A p-value measures how compatible the observed data are with a specified statistical null hypothesis under the assumptions of the test.

RNA-Seq studies often test thousands of genes simultaneously. Multiple-testing correction is therefore needed to reduce the expected proportion of false discoveries among declared significant results.

An adjusted p-value or false discovery rate (FDR) measure helps account for multiple comparisons.

A small adjusted p-value supports a statistical difference under the analysis model, but does not by itself establish biological importance or causation.

### Slide 43: Practical Demonstration — RNA-Seq Differential Expression
**Objective:** Understand how expression changes are identified between two conditions.

**General workflow:**
1. Obtain RNA-Seq FASTQ files from control and treated samples.
2. Perform read quality control.
3. Map reads to a suitable reference or use an appropriate alternative workflow.
4. Generate a gene-level count matrix.
5. Use a differential expression package such as DESeq2 for count-based analysis.
6. Specify the experimental design and compare the conditions.
7. Examine log2 fold changes, adjusted p-values, and expression patterns.
8. Identify candidate genes for further biological interpretation.

**Interpretation:** A gene with a positive log2 fold change has higher estimated expression in the numerator condition of the defined comparison. A negative value indicates lower estimated expression. The comparison direction must always be checked.

## Part G: Metagenomics and Microbial Sampling

### What Is Metagenomics?
Metagenomics is the study of genetic material recovered directly from an environmental or community sample, without requiring every microorganism to be cultured separately.

It is useful for investigating microbial communities that include organisms that are difficult or impossible to grow using standard laboratory methods.

Common sample sources include soil, freshwater, marine water, wastewater, sediments, and host-associated microbial communities.

### Why Is Metagenomics Important?
Traditional culture-based approaches recover only the organisms that grow under the selected laboratory conditions.

Metagenomics can reveal a broader view of microbial diversity and functional potential in a sample.

It can help researchers investigate:
- Which microorganisms may be present.
- Which genes occur within a community.
- Potential metabolic capabilities.
- Antibiotic-resistance genes.
- Microbial responses to environmental changes.

DNA-based metagenomics reveals genetic potential; it does not automatically prove that every detected gene is expressed or active.

### What Is Metagenomic Sampling?
Metagenomic sampling is the planned collection of material from a microbial community for DNA-based analysis.

Sampling decisions influence the quality and interpretation of the results. Researchers should define the study objective, select suitable locations and times, collect biological replicates when appropriate, and use consistent procedures.

Relevant metadata may include sample location, collection time, temperature, pH, environmental conditions, treatment, and sample handling.

### Why Are Controls and Contamination Checks Important?
Environmental and low-biomass samples can contain DNA introduced during collection, extraction, or library preparation.

Controls help identify potential sources of contamination. Depending on the study, these may include extraction blanks, negative controls, positive controls, and technical controls.

Consistent sample handling, suitable storage, clean equipment, and documented procedures help improve reliability.

A sequence detected in a sample should not automatically be assumed to originate from the target microbial community without considering possible contamination.

### Basic Metagenomic Analysis Workflow
A typical metagenomic workflow includes:

1. Define the research question and sampling design.
2. Collect representative samples and record metadata.
3. Extract community DNA.
4. Prepare sequencing libraries.
5. Generate sequencing reads.
6. Perform quality control and read preprocessing.
7. Analyse taxonomic composition using suitable reference databases and tools.
8. Optionally assemble reads to reconstruct longer sequences.
9. Predict and annotate genes.
10. Analyse functional potential and compare samples.
11. Interpret results while considering sampling, database, and contamination limitations.

Taxonomic profiling and assembly-based functional analysis answer related but different questions. Not every project requires both approaches.

## Part H: Integrated Practical Pipeline

### Complete High-Throughput Sequencing Pipeline
A simplified microbial genomics pipeline can be represented as:

**Research question → Sample collection → DNA extraction → Sequencing → FASTQ files → Quality control → Read preprocessing → Genome assembly or reference mapping → Gene prediction and annotation → Biological interpretation**

For transcriptomics, the workflow branches into RNA extraction, RNA-Seq library preparation, read mapping or quantification, count-matrix generation, and differential expression analysis.

For metagenomics, the workflow emphasizes community sampling, contamination controls, taxonomic profiling, and analysis of community-level functional potential.

The pipeline must be adapted to the sample type and research objective. No single workflow is appropriate for every sequencing experiment.

### Key Takeaways and Reflection Questions
**Key Takeaways**
- Microbial genomics studies the genetic material of microorganisms.
- Illumina and Oxford Nanopore differ in their sequencing approaches and typical read characteristics.
- Quality control is essential before downstream analysis.
- De novo assembly reconstructs sequences without a reference guiding the assembly, whereas reference mapping aligns reads to an existing sequence.
- Genome annotation identifies genomic features and predicts their functions.
- RNA-Seq measures RNA abundance and can support differential expression analysis.
- Metagenomics investigates genetic material recovered from microbial communities.
- Results must be interpreted with appropriate quality checks, controls, statistics, and biological context.

**Reflection Questions**
1. Why is sequencing quality control necessary before genome assembly?
2. When might long-read sequencing be more useful than short-read sequencing?
3. What is the difference between de novo assembly and reference mapping?
4. Why does an identified ORF not automatically prove that a functional protein is produced?
5. How can RNA-Seq help investigate microbial responses to environmental stress?
6. Why are biological replicates important in differential expression analysis?
7. How does metagenomics help study microorganisms that cannot be cultured easily?
8. Why are contamination controls important in metagenomic studies?
