---
title: Biobank Japan Data in CRI
author: Sabrina Mi
date: '2022-01-02'
slug: biobank-japan-data-in-cri
categories: []
tags: []
---

**BBJ data directory:** `\gpfs/data/im-lab/nas40t2/Data/BBJ`

I first downloaded and decrypted Biobank Japan data ([instructions](http://127.0.0.1:4321/post/2020/07/30/downloading-data-from-biobank-japan/)), then organized into subdirectories `BBJ-genotypes-decrypted` and `BBJ-phenotypes-decrypted`, in their original form.

## Phenotypes

**BBJ phenotypes file:** `gpfs/data/im-lab/nas40t2/Data/BBJ/BBJ-phenotypes.csv`

The original BBJ phenotype data, in `BBJ-phenotypes-decrypted`, was structured so that individual data for each phenotype was in a different folder. For convenience, I combined all the phenotypes in one table, `BBJ-phenotypes.csv`. The file `BBJ-phenotype-list.txt` contains all the phenotypes and their folder names ([download](BBJ-phenotype-list.txt))

I created the combined phenotype file with the following [script](process-phenotypes.py):

```
python3 process-phenotypes.py --BBJ_folder /Users/sabrinami/BBJ/BBJ-phenotypes \
--phenotype_mapping /Users/sabrinami/Github/analysis-sabrina/BBJ-data-processing/BBJ-phenotype-list.txt \
--output /Users/sabrinami/Github/analysis-sabrina/BBJ-data-processing/BBJ-phenotypes.csv
```


