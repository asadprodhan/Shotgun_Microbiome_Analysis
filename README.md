<h1 align="center">🔬 Shotgun Microbiome Analysis</h1>

<h3 align="center">M. Asaduzzaman Prodhan<sup>*</sup> </h3>

<div align="center"><b> School of Biological Sciences, The University of Western Australia </b></div>
<div align="center"><b> 35 Stirling Highway, Perth, WA 6009, Australia. <sup>*</sup>Correspondence: prodhan82@gmail.com </b></div>

<br />

<p align="center">
  <a href="https://github.com/asadprodhan/How-to-automatically-download-reads-from-the-NCBI-SRA/tree/main#GPL-3.0-1-ov-file"><img src="https://img.shields.io/badge/License-GPL%203.0-yellow.svg" alt="License GPL 3.0"></a>
  <a href="https://orcid.org/0000-0002-1320-3486"><img src="https://img.shields.io/badge/ORCID-green?style=flat-square&logo=ORCID&logoColor=white" alt="ORCID"></a>
</p>

---

## 📖 Introduction

**Shotgun metagenomic sequencing** is a powerful approach to study microbial communities in diverse environments (soil, water, plants, human microbiome).  
Unlike **amplicon sequencing** (e.g., 16S rRNA) that targets specific marker genes, shotgun metagenomics sequences **all genetic material** in a sample.  

This allows us to:

- 🧬 Identify microbes down to **species or strain level**
- ⚙️ Characterize **functional genes, pathways, and metabolic functions**
- 💊 Detect **antimicrobial resistance (AMR) genes** and virulence factors
- 🧩 Reconstruct **metagenome-assembled genomes (MAGs)** to discover novel microbes

---

## ❓ Biological Questions We Can Answer

- **What organisms are present?** → *Taxonomic Composition*  
- **How diverse is the community?** → *Alpha & Beta Diversity*  
- **Which genes/pathways are enriched?** → *Functional Profiling*  
- **How does the community resist antibiotics?** → *AMR Analysis*  
- **Can we recover near-complete genomes?** → *MAG Assembly*  

---

## 🗂️ Table of Contents

1. [Data Processing & Quality Control](#1-data-processing--quality-control)  
2. [Taxonomic Composition](#2-taxonomic-composition)  
3. [Diversity Analyses](#3-diversity-analyses)  
4. [Differential Abundance](#4-differential-abundance)  
5. [Functional Profiling](#5-functional-profiling)  
6. [Antimicrobial Resistance (AMR) Analysis](#6-antimicrobial-resistance-amr-analysis)  
7. [Metagenome-Assembled Genomes (MAGs)](#7-metagenome-assembled-genomes-mags)  
8. [Correlation & Network Analysis](#8-correlation--network-analysis)  
9. [Machine Learning & Predictive Modelling](#9-machine-learning--predictive-modelling)  
10. [Summary](#summary)  
11. [Matrix Overview](#matrix-analysis--methodology--visualisation--hypotheses)  

---

## **1. Data Processing & Quality Control**

**Methodology**  
- Check read quality → *FastQC, MultiQC*  
- Trim adapters & low-quality reads → *Trimmomatic, fastp*  
- Remove host DNA → *Bowtie2, BWA*  
- Keep only **high-quality reads**  

**Visualisations**  
- QC plots: base quality, GC content  

**Hypotheses**  
- Is sequencing depth consistent across samples?  
- Are host reads disproportionately removed in some samples?  

---

## **2. Taxonomic Composition**

**Methodology**  
- Assign taxonomy:  
  - *k-mer classifiers*: Kraken2, Bracken  
  - *marker-based*: MetaPhlAn  
- Generate abundance tables  

**Visualisations**  
- Stacked barplots  
- Heatmaps  
- Krona or sunburst charts  

**Hypotheses**  
- Do microbial communities differ between healthy vs diseased (or treatment vs control)?  
- Tests: PERMANOVA, ANOSIM, DESeq2, ANCOM, MaAsLin2  

---

## **3. Diversity Analyses**

**Methodology**  
- **Alpha diversity**: Shannon, Simpson, Chao1  
- **Beta diversity**: Bray–Curtis, Jaccard, UniFrac  
- Ordination: PCoA, PCA, NMDS  

**Visualisations**  
- Boxplots of alpha diversity  
- PCoA/PCA scatterplots  
- Dendrograms  

**Hypotheses**  
- Is within-sample diversity different between groups?  
- Is between-sample variation higher across conditions?  
- Tests: Mann–Whitney, Kruskal–Wallis, PERMANOVA  

---

## **4. Differential Abundance**

**Methodology**  
- Normalise counts (e.g., CLR, library-size correction)  
- Identify enriched taxa → *DESeq2, LEfSe, ANCOM, MaAsLin2*  

**Visualisations**  
- Volcano plots  
- Heatmaps of significant taxa  
- LEfSe cladograms  

**Hypotheses**  
- Which taxa are enriched/depleted under specific conditions?  

---

## **5. Functional Profiling**

**Methodology**  
- Annotate gene families: eggNOG, KEGG  
- Map to pathways: MetaCyc, KEGG modules  
- Quantify pathway abundance → *HUMAnN3*  

**Visualisations**  
- Heatmaps of pathways  
- Barplots of enriched functions  
- Bubble plots for enrichment  

**Hypotheses**  
- Do functions differ across groups?  
- Are certain metabolic pathways enriched in disease?  
- Tests: GSEA, Fisher’s exact, regression models  

---

## **6. Antimicrobial Resistance (AMR) Analysis**

**Methodology**  
- Screen reads/contigs → AMR databases (*CARD, ResFinder, ARG-ANNOT, MEGARes*)  
- Quantify resistance by class/mechanism  
- Normalise counts (RPKM, CPM)  

**Visualisations**  
- Barplots of AMR gene classes  
- Heatmaps of AMR distribution  
- Networks: AMR genes ↔ taxa  

**Hypotheses**  
- Are AMR genes enriched in treated vs untreated samples?  
- Do hospital wastewater and soil carry distinct AMR profiles?  
- Tests: DESeq2, MaAsLin2, correlation analyses  

---

## **7. Metagenome-Assembled Genomes (MAGs)**

**Methodology**  
- Assembly → MEGAHIT, metaSPAdes  
- Binning → MetaBAT, MaxBin, CONCOCT  
- Quality check → CheckM, BUSCO  
- Annotation → taxonomy + functions  

**Visualisations**  
- Phylogenetic trees  
- Completeness vs contamination plots  
- Abundance heatmaps  

**Hypotheses**  
- Are certain genomes enriched in specific environments?  
- Do MAGs reveal novel functions or AMR genes?  

---

## **8. Correlation & Network Analysis**

**Methodology**  
- Correlate microbes/functions with metadata → *Spearman, Pearson, SparCC*  
- Build **co-occurrence networks**  

**Visualisations**  
- Correlation heatmaps  
- Microbial interaction networks  

**Hypotheses**  
- Do microbes co-occur or exclude each other?  
- Are microbial networks altered under stress/disease?  

---

## **9. Machine Learning & Predictive Modelling**

**Methodology**  
- Feature selection: taxa, pathways  
- Train classifiers: Random Forest, SVM, Neural Networks  
- Cross-validation for performance  

**Visualisations**  
- ROC & PR curves  
- Feature importance plots  

**Hypotheses**  
- Can microbiome features predict phenotype or environment?  
- Which features are most predictive?  

---

## **Summary**

- **Taxonomic Composition** → Do communities differ?  
- **Diversity** → Are alpha/beta diversity metrics significantly different?  
- **Differential Abundance** → Which microbes/functions are enriched?  
- **Functional Profiling** → Do pathways differ across groups?  
- **AMR Analysis** → Are resistance genes more prevalent in certain environments?  
- **Networks** → Do co-occurrence patterns change?  
- **Prediction** → Can microbiomes classify phenotypes?  

---

## **Matrix: Analysis → Methodology → Visualisation → Hypotheses**

| Analysis Step | Methodology | Visualisations | Hypotheses |
|---------------|-------------|----------------|-------------|
| **QC & Preprocessing** | FastQC, Trimmomatic, Bowtie2 | QC plots, barplots | Are samples of equal quality & depth? |
| **Taxonomy** | Kraken2, MetaPhlAn | Barplots, heatmaps, Krona | Do communities differ between groups? |
| **Diversity** | Shannon, Simpson, Bray–Curtis, UniFrac | Boxplots, PCoA, dendrograms | Are alpha/beta diversities different? |
| **Differential Abundance** | DESeq2, LEfSe, ANCOM | Volcano plots, heatmaps, cladograms | Which taxa/functions differ? |
| **Functional Profiling** | HUMAnN3, KEGG, eggNOG | Heatmaps, barplots, bubbles | Do pathways differ? |
| **AMR Profiling** | CARD, ResFinder, MEGARes | Barplots, heatmaps, networks | Are AMR genes enriched? |
| **MAGs** | MEGAHIT, MetaBAT, CheckM | Trees, scatterplots, heatmaps | Are specific genomes enriched? |
| **Networks** | SparCC, Spearman | Heatmaps, networks | Do microbes co-occur/exclude? |
| **Machine Learning** | Random Forest, SVM | ROC curves, feature plots | Can microbiomes predict phenotypes? |

---

## 🔑 Keywords

**Analysis • Methodology • Visualisation • Hypothesis Testing**

---
