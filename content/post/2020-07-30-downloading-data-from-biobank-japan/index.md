---
title: Downloading Data from Biobank Japan
author: ''
date: '2020-07-30'
slug: downloading-data-from-biobank-japan
categories:
  - how_to
tags: []
---


The same info can be found at this page, https://www.ddbj.nig.ac.jp/jga/download-e.html, but the steps may be slightly different because we applied for Biobank Japan data before they integrated with the D-way system.


Register a user account:
1. A D-way account should have been created for you, with your username and password sent in an email. If not, create an account here: https://ddbj.nig.ac.jp/D-way/contents/general/reserve_account_page
2. **Add UChicago as your organization**: Log in with D-way account, https://ddbj.nig.ac.jp/D-way/. Click the account tab at the top right corner, and at the bottom, type "The University of Chicago" in Center Full Name. Once selected, center name autofills with "U_CHICAGO". 
3. **Register your public key**: You may need to click update and refresh for the Public Key box to appear at the bottom. You will need to copy your public key to an unhidden folder, `cp ~/.ssh/id_rsa.pub ~/Desktop`, before selecting for upload. If you do not find a file named `id_rsa.pub` in `.ssh`, create a public key with `ssh-keygen -t rsa`.


Download Data:
1. Connect to JGA server: `sftp -i id_rsa -P 443 <D-way username>@jga-gw.ddbj.nig.ac.jp` 
2. `cd controlled-access/download/jga/`
3. Download: `get -r J-DU999991` (downloads locally, will update with instructions to download directly to Bionimbus)

-[ ] ADD HOW TO DECRYPT HERE
