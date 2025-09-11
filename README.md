<h1 align="center">Shotgun Microbiome Analysis</h1>


<h3 align="center">M. Asaduzzaman Prodhan<sup>*</sup> </h3>


<div align="center"><b> School of Biological Sciences, The University of Western Australia </b></div>


<div align="center"><b> 35 Stirling Highway, Perth, WA 6009, Australia. <sup>*</sup>Correspondence: prodhan82@gmail.com </b></div>


<br />


<p align="center">
  <a href="https://github.com/asadprodhan/How-to-automatically-download-reads-from-the-NCBI-SRA/tree/main#GPL-3.0-1-ov-file"><img src="https://img.shields.io/badge/License-GPL%203.0-yellow.svg" alt="License GPL 3.0" style="display: inline-block;"></a>
  <a href="https://orcid.org/0000-0002-1320-3486"><img src="https://img.shields.io/badge/ORCID-green?style=flat-square&logo=ORCID&logoColor=white" alt="ORCID" style="display: inline-block;"></a>
</p>


<br />


## **INTRODUCTION**


Shotgun metagenomic sequencing is a high-resolution approach to study the microbial communities in complex environments such as soil, water, plants, and the human body. Unlike amplicon sequencing (e.g., 16S rRNA), which targets specific marker genes, shotgun metagenomics approach sequences all genetic material in a sample.


<br />

This allows researchers to:

- Identify microbial taxa down to species or strain level

- Characterize the functional genes, pathways, and metabolic functions of the microbial community

- Detect antimicrobial resistance (AMR) genes, virulence factors, and mobile genetic elements

- Reconstruct metagenome-assembled genomes (MAGs) to study novel microbes


<br />


Shotgun metagenomics combines bioinformatics, statistics, and visualization to answer key biological and ecological questions, such as:


- What organisms are present? 

> To answer this question, you need to analyse the **Taxonomic Composition**


- How diverse is the community? 

> To answer this question, you need to analyse the **Alpha and Beta diversity**


- Which genes and pathways are enriched under different conditions? 

> To answer this question, you need to carry out **Functional Profiling**


- How does the community resist antibiotics or environmental stress? 

> To answer this question, you need to carry out **AMR Analysis**


- Can we reconstruct near-complete microbial genomes from mixed samples? 

> To answer this question, you need to perform *de novo* genome assembly (MAG recovery)


<br />

By integrating quality control, taxonomic classification, diversity metrics, functional profiling, AMR detection, and network analysis, shotgun metagenomics provides a comprehensive view of the microbiome and its role in the corresponding environment.

<br />

This repository provides a brief guide to shotgun metagenomic microbiome analysis.  
It walks through **analysis steps, methods, visualisation techniques, and some examples of relevant hypotheses**.


<br />


## **KEYWORDS**


**Analysis • Methodology • Visualisation • Hypothesis Testing**


<br />


## **CONTENT**


 

<br />


## **1. DATA PROCESSING & QUALITY CONTROL**

**Methodology**

- Check sequencing quality (FastQC, MultiQC)
  
- Trim adapters & low-quality bases (Trimmomatic, fastp)
  
- Remove host DNA by aligning to host genome (Bowtie2, BWA)
  
- Keep high-quality reads for downstream analyses
 

**Visualisations**

- QC plots (per-base quality, GC content)
  

**Hypotheses**

- Are sequencing depth and quality consistent across samples?  

- Do host reads disproportionately affect certain samples?  


<br />


## **2. TAXONOMIC COMPOSITION**

**Methodology**

- Assign taxonomy using k-mer–based (Kraken2, Bracken) or marker-based (MetaPhlAn) classifiers
  
- Generate relative abundance tables at phylum/genus/species levels
  

**Visualisations**

- Stacked barplots of taxa
  
- Heatmaps of abundance

- Krona (interactive) or sunburst charts for hierarchical views 
 

**Hypotheses**

- Do microbial communities differ in composition between groups (e.g., healthy vs diseased or treatment vs control etc)? 
 
- Tests: PERMANOVA, ANOSIM, DESeq2, ANCOM, MaAsLin2


<br />


## **3. DIVERSITY ANALYSES**

**Methodology**

- **Alpha diversity**: Shannon, Simpson, Chao1 indices
 
- **Beta diversity**: Distance matrices (Bray–Curtis, Jaccard, UniFrac)

- Ordination methods: PCoA, PCA, NMDS
 

**Visualisations**

- Boxplots of alpha diversity

- PCoA/PCA ordination plots
 
- Dendrograms

**Hypotheses**

- Is within-sample diversity (alpha) different between groups?  

- Is between-sample variation (beta) greater across conditions?  

- Tests: Mann–Whitney, Kruskal–Wallis, PERMANOVA
  

<br />


## **4. DIFFERENTIAL ABUNDANCE**

**Methodology**

- Normalise counts (library size correction, CLR transformation)
 
- Apply statistical models (DESeq2, LEfSe, ANCOM, MaAsLin2)
 

**Visualisations**

- Volcano plots
 
- Heatmaps of significant taxa
 
- LEfSe cladograms
  

**Hypotheses**

- Which taxa are enriched or depleted under certain conditions?  


<br />



## **5. FUNCTIONAL PROFILING**


**Methodology**

- Assign gene families (eggNOG, KEGG orthologs)
  
- Aggregate into pathways (MetaCyc, KEGG modules)
 
- Quantify pathway abundances (HUMAnN3)
 

**Visualisations**

- Heatmaps of pathway abundance
  
- Barplots of differential pathways
 
- Bubble plots for enrichment
 

**Hypotheses**

- Do microbial functions differ significantly between conditions?  

- Are certain metabolic pathways enriched in disease states? 
 
- Tests: GSEA, Fisher’s exact, regression models
 

<br />


## **6. ANTIMICROBIAL RESISTANCE (AMR) ANALYSIS**


**Methodology**

- Map reads/contigs against AMR gene databases (CARD, ResFinder, ARG-ANNOT, MEGARes)
  
- Quantify resistance genes by class and mechanism
  
- Normalise by sequencing depth (RPKM, CPM)
  

**Visualisations**

- Barplots of AMR gene classes
 
- Heatmaps of resistance genes across samples
 
- Network diagrams of AMR gene–taxa associations


**Hypotheses**

- Are AMR genes more abundant in treatment vs control groups? 
 
- Do certain environments (e.g., hospital wastewater vs soil) carry distinct AMR profiles?  

- Tests: DESeq2, MaAsLin2, correlation with metadata


<br />


## **7. Metagenome-Assembled Genomes (MAGs)**


**Methodology**

- Assemble reads (MEGAHIT, metaSPAdes)
 
- Bin contigs (MetaBAT, MaxBin, CONCOCT)
 
- Assess quality (CheckM, BUSCO)
  
- Annotate taxonomy & function


**Visualisations**

- Phylogenetic trees of MAGs
 
- Completeness vs contamination scatterplots
  
- Heatmaps of genome abundance


**Hypotheses**

- Are specific genomes enriched in certain environments? 
 
- Do MAGs carry unique functions or AMR genes?
- 

<br />


## **8. CORRELATION & NETWORK ANALYSIS**

**Methodology**

- Correlate taxa/functions with metadata (Spearman, Pearson, SparCC)
 
- Build co-occurrence networks
  

**Visualisations**

- Correlation heatmaps
  
- Microbial association networks
  

**Hypotheses**

- Do certain microbes co-occur or exclude each other? 
 
- Are microbial associations altered under specific conditions?
- 

<br />


## **9. MACHINE LEARNING & PREDICTIVE MODELLING**

**Methodology**

- Feature selection (taxa, pathways)
  
- Train classifiers (Random Forest, SVM, neural networks)
 
- Evaluate with cross-validation
 

**Visualisations**

- ROC and PR curves
  
- Feature importance plots
  

**Hypotheses**

- Can microbiome features predict host phenotype or environment?
  
- Which features are most predictive?  

<br />


## **SUMMARY**


### **1. Do taxa differ between groups?**

> Community Composition Analysis   


### **2. Are alpha/beta diversity metrics significantly different?**

> Diversity Analysis

  
### **3. Which microbes or functions are enriched/depleted?**

> Differential Abundance Analysis
 
 
### **4. Do metabolic pathways differ across microbiomes?** 

> Functional Profiling


### **5. Are resistance genes more prevalent in certain environments?**

> AMR Analysis
 

### **6. Do co-occurrence patterns change?**

> Ecological Interactions Analysis
 
 
### **7. Can microbiome profiles classify or predict phenotypes?**

> Prediction  

<br />


## **Matrix: Analysis → Methodology → Visualisation → Hypotheses**


| Analysis Step | Methodology | Visualisations | Hypotheses Tested |
|---------------|-------------|----------------|-------------------|
| **QC & Preprocessing** | FastQC, Trimmomatic, Bowtie2 | QC plots, barplots | Are samples of equal quality & depth? |
| **Taxonomic Composition** | Kraken2, MetaPhlAn | Stacked barplots, heatmaps, Krona | Do community structures differ between groups? |
| **Diversity** | Shannon/Simpson, Bray–Curtis, UniFrac | Boxplots, PCoA, dendrograms | Are alpha/beta diversities different? |
| **Differential Abundance** | DESeq2, LEfSe, ANCOM | Volcano plots, heatmaps, cladograms | Which taxa/functions differ by condition? |
| **Functional Profiling** | HUMAnN3, KEGG, eggNOG | Heatmaps, barplots, bubble plots | Do pathways differ significantly between groups? |
| **AMR Profiling** | CARD, ResFinder, MEGARes | Barplots, heatmaps, networks | Are AMR genes enriched in certain environments? |
| **MAGs** | MEGAHIT, MetaBAT, CheckM | Trees, scatterplots, heatmaps | Are specific genomes enriched/unique? |
| **Correlation & Networks** | Spearman, SparCC | Heatmaps, networks | Do microbes co-occur/exclude across conditions? |
| **Machine Learning** | Random Forest, SVM | ROC/PR curves, feature plots | Can microbiomes predict phenotypes? |

<br />

