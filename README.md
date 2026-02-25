# Transcription-Guided BGC Border Refinement

This repository contains a Jupyter notebook implementing transcription-guided refinement of biosynthetic gene cluster (BGC) boundaries using RNA-seq expression data.

## Overview

Biosynthetic gene clusters (BGCs) are initially defined using antiSMASH-predicted genomic regions. However, predicted borders do not always reflect transcriptionally coherent units. This workflow refines BGC boundaries by integrating:

- Genomic position  
- Gene functional annotation (biosynthetic classification)  
- RNA-seq expression profiles (logTPM across multiple conditions)  

The method identifies genes that are transcriptionally coordinated with biosynthetic core genes and redefines cluster borders accordingly.

## Method Summary

1. **Seed definition**  
   Biosynthetic genes within each antiSMASH region are grouped into core seed blocks based on genomic proximity.

2. **Cluster eigengene calculation**  
   The mean expression profile of each seed block is calculated to represent the transcriptional behavior of the biosynthetic core.

3. **Expression-based extension**  
   Neighboring genes are incorporated if they:
   - Are detectably expressed  
   - Show strong co-expression with the core (Pearson correlation threshold)

4. **Genomic continuity constraints**  
   Extension is restricted to preserve local genomic structure, and small internal gaps are bridged to maintain biologically meaningful cluster architecture.

The resulting refined BGC definitions represent transcriptionally supported cluster boundaries.

## Repository Contents

- `BGC_refinement_github.ipynb` – Complete workflow for BGC border refinement

## Input Requirements

The notebook expects a gene-level table containing:

- Gene identifiers  
- Genomic coordinates  
- antiSMASH region assignments  
- Functional annotation (biosynthetic classification)  
- logTPM expression values across conditions  

## Output

- Gene-level table with refined BGC identifiers  
- Refined cluster boundaries for downstream analyses  

## Reproducibility

The version used in the associated manuscript is archived on Zenodo (DOI: *add DOI here*).
