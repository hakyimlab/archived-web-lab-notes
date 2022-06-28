---
title: BioMart Basics
author: Sabrina
date: '2022-06-28'
slug: query-gene-annotations-from-biomart
categories:
  - cheatsheet
tags: []
---

## About BioMart

BioMart is a database containing Ensembl annotations of genes across many species and builds. To query data, you first pick one the databases:
1. Ensembl Genes
2. Ensembl Variation
3. Ensembl Variation
4. Vega

We typically uses only the Ensembl Genes database, which lists all genes for the selected species and build, along with their positions, alternate names, and other descriptions.

## Querying Gene Annotations

The full tutorial is [online](https://useast.ensembl.org/info/data/biomart/how_to_use_biomart.html). Here's a quick [example](example_query.R).