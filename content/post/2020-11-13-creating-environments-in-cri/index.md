---
title: Creating Environments in CRI
author: Natasha Santhanam
date: '2020-11-13'
slug: creating-environments-in-cri
categories: []
tags: []
description: ''
topics: []
---

1) Create the new environment in the lab share 

```{sh, eval=FALSE}
conda create --prefix /gpfs/data/im-lab/nas40t2/bin/envs/env_name 
```

2) Activate the new environment

```{sh, eval=FALSE}
conda activate env_name
```

3) Install whatever you want in your new environment. Also because the environment is in the labshare, anyone can use it just by calling

```{sh, eval=FALSE}
conda install <software>
conda activate /gpfs/data/im-lab/nas40t2/bin/envs/env_name
```



