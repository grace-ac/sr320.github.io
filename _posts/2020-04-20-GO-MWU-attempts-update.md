---
layout: post
title: Trying GO-MWU with 2019 crab data
date: '2020-04-20'
category: bairdi
tags: [GO_MWU]
In this post I'll detail what I've been trying in GO-MWU with the 2019 crab dataset, comparing infected and uninfected crabs. The post will detail progress from most recent attempt to frist attempts. 

## GO-MWU resources: 
- [GO-MWU repo](https://github.com/z0on/GO_MWU)       
- [EIMD analyses repo](https://github.com/eimd-2019/project-EWD-transcriptomics/tree/master/analyses) which lists files used for GO-MWU

GO-MWU requires 2 files from your dataset:     
1. "table of GO annotations for your sequences: two-column (gene id - GO terms), tab-delimited, one line per gene, multiple GO terms separated by semicolon. If you have multiple lines per gene, use nrify_GOtable.pl to merge them."       
2. "table of measure of interest for your sequences: two columns of comma-separated values: gene id, continuous measure of significance such as log(fold-change) or -log(p-value). To perform standard GO enrichment analysis based on Fisher's exact test, use binary measure (1 or 0, i.e., either sgnificant or not). To analyze modules derived from WGCNA, specify 0 for genes not included in the module and the kME value (number between 0 and 1, module membership score) for genes included in the module."

Repo in project-crab for GO-MWU --> [here](https://github.com/RobertsLab/project-crab/tree/master/analyses/GO-MWU)

## Latest attempt (afternoon, April 20, 2020)
GO-MWU only works with list of all gene inputs, not just the DEGs.     

Ran GO-MWU script with the following files (which were made in [this](https://github.com/RobertsLab/project-crab/blob/master/scripts/042020-format-files-for-GO-MWU.Rmd) Rmd:
1. [2019-crab-ALL-geneID-log2fc.csv](https://raw.githubusercontent.com/RobertsLab/project-crab/master/analyses/GO-MWU/2019-crab-ALL-geneID-log2fc.csv) from the list of all 2019 crab genes from `DESeq2` (Steven's script: [here](https://github.com/RobertsLab/project-crab/blob/master/scripts/11-Deseq.Rmd))
2. [crab-GO-annot.tab](https://raw.githubusercontent.com/RobertsLab/project-crab/master/analyses/GO-MWU/crab-GO-annot.tab) from the BLAST output from the full crab transcriptome

GO-MWU script using those two files: [here](https://github.com/RobertsLab/project-crab/blob/master/analyses/GO-MWU/2019-crab-infection-ALL-GO_MWU.R)

It worked!! Found 15 GO terms at 10% FDR, so continuing on to plotting was good to go.      
Plot:      







