---
title: ukbREST SQLite Setup
author: Sabrina Mi
date: '2022-08-28'
slug: ukbrest-sqlite-setup
categories:
  - installlation
  - how to
tags: []
---

> This post explains 1) how to query UKBREST and 2) how to create an sqlite database from the postgres database.

The version of ukbREST that runs on SQLite is kept [HERE](https://github.com/sabrina-mi/ukbrest). If you come across an existing ukbrest repo in CRI, it might be the original version.

# Preliminary steps

install conda environement using the https://github.com/hakyimlab/ukbrest/blob/master/environment.yml

```
TODO: add conda command that would create the environment using the yml file
```

# Querying ukbREST

Start the server by specifying the full path to the SQLite file as the DB URI. 

```{bash, eval=FALSE}
conda activate ukbrest
export UKBREST_DB_URI="sqlite:////gpfs/data/ukb-share/sql/ukbrest.db"
cd /gpfs/data/ukb-share/sql/ukbrest
/gpfs/data/im-lab/nas40t2/lab_software/miniconda/envs/ukb_env/bin/python \
-m ukbrest.app \
--db-uri sqlite:////gpfs/data/ukb-share/sql/ukbrest.db \
--debug

```

If program looks like it's hanging and prints something like the line below, the server is running and ready to be queried.

```
2022-08-28 20:57:36,753 - werkzeug - INFO -  * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

Flask defaults to `http://127.0.0.1:5000/`, so if you see the error, 
`OSError: [Errno 98] Address already in use`, it means that some other server is running on port 5000. You'll need to find the other process and kill it.



Open up a new terminal, or if you've started the server in CRI, login in a new window. Here's an example query from a [YAML file](example/test.yaml):

```
$ cat test.yaml 
samples_filters:
  - eid not in (select eid from withdrawals)
  - eid > 0
data:
  cause_of_death: c40001_0_0
  
```

```
curl -X POST \
  -H "Accept: text/csv" \
  -F file=@"test.yaml" \
  -F section="data" \
  http://127.0.0.1:5000/ukbrest/api/v1.0/query \
  > test.csv
  
```

Or column query:
```
curl -G \
-HAccept:text/csv \
"http://127.0.0.1:5000/ukbrest/api/v1.0/phenotype" \
--data-urlencode "columns=c3_0_0" > column_query.csv

```
The following error prints after querying if you are running the original version of ukbREST. Replacing with the updated branch and restarting the server should do the trick.

# Generating the sqlite database from the postgres 
database (this needs to be done once in bionimbus)

We generated the SQLite file from the Postgres database that was already loaded with data in Bionimbus. The script `pg2sqlite.py` takes a list of table names in the Postgres database and copies them to `ukbrest.db`. I've added it to the Github, in `migration/pg2sqlite.py`, but the SQLite path and Postgres URI are hard-coded, if you plan to use it.

```
conda activate ukbrest
cd /mnt/sql
python pg2sqlite.py tables.txt
## find this code here https://github.com/sabrina-mi/ukbrest/blob/master/migration/pg2sqlite.py
```
We decided to copy the Postgres database, rather than loading data the documented way, because the jobs were extremely slow to finish in CRI. However, when we periodically update withdrawal tables, or if we were to download new data, we would load the data directly from those CSVs. 

# Update withdrawal list

```
export UKBREST_DB_URI="sqlite:////mnt/sql/ukbrest.db"
export UKBREST_WITHDRAWALS_PATH="/mnt/data/withdrawals/"
cd /mnt/software/ukbrest
python -m ukbrest.load_data \
 --load-withdrawals \
 --withdrawals-dir /mnt/data/withdrawals/ \
 --db-uri sqlite:////mnt/sql/ukbrest.db \
 --debug
 ```
 
If you are loading new phenotype data in CRI, it gets a little complicated. The main difference is that we have to break up each CSV into multiple jobs, so that CRI doesn't kill it for taking too long. The directory `/gpfs/data/ukb-share/sql/test` includes example PBS scripts to split CSVs into tables with 750 columns (`test_split.sh`) and load the smaller file into `test.db` (`test_load.sh`).





