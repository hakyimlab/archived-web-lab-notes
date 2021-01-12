---
title: PsychENCODE Models
author: Sabrina Mi
date: '2020-12-21'
slug: psychencode-models
categories: []
tags:
  - analysis
---

Gandal et al generated transcriptome prediction models that are available on [PsychENCODE](http://resource.psychencode.org/Datasets/Derived/PEC_TWAS_weights.tar.gz).

We used the weights they generated from the elastic net method and reformated it into a model compatible with PrediXcan software ([code](https://hakyimlab.github.io/psychencode/generate_weights.html)). We also calculated covariances between variants ([code](https://hakyimlab.github.io/psychencode/calculate_covariances.html)). 
The models can be downloaded [here](https://uchicago.app.box.com/s/du6f4z1zcgtn2v5gqms8kjajt1lsaprh).

We validated the model by running PrediXcan on 1000G genotypes PsychENCODE, GTEx v7 Brain Cortex, and GTEx v7 Whole Blood tissue models, and then comparing the correlation between predicted gene expression and observed expression from GEUVADIS.
The results can be found [here](test_alcdep.html).

Next, we compared PsychENCODE S-PrediXcan association results with GTEx v7 Brain Cortex and Whole Blood tissue models from the Walters Group Schizophrenia GWAS. 
The results can be found [here](test_scz_clozuk_pgc.html).

The original PsychENCODE model was defined in hg19, but we also lifted it over to hg38. We validated it by comparing S-PrediXcan associations results from the original hg19, lifted over hg38, and GTEx v8 mashr Brain Cortex models on the Schizophrenia GWAS.
The steps to lift over the model and the validation results are [here](psychencode_hg38_validation.html).


