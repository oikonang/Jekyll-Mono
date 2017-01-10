---
layout: post
title: Parsing Reddit Data with Dask
author: Angelos Ikonomakis
---
[figure_1]: ../images/figure_1.png "Figure 1"
[figure_2]: ../images/figure_2.png "Figure 2"
[figure_3]: ../images/figure_3.png "Figure 3"
[figure_4]: ../images/figure_4.png "Figure 4"
[figure_5]: ../images/figure_5.png "Figure 5"
[figure_6]: ../images/figure_6.png "Figure 6"
[figure_7]: ../images/figure_7.png "Figure 7"    

## Overview

In an attempt to play around with medium-sized data, I found a 30GB uncompressed dataset from reddit comments from 01/2015. This post is a step-by-step data exploration on that dataset. Firstly I uploaded the dataset in an Amazon server for learning purposes. Medium-sized datasets are easily managable by normal processing power computer systems. I run both in Amazon EC2 and on my MacBookPro Late 2013, 8GB, i5 and it worked perfectly fine. Secondly, I created a castra file in order to parse the dataset without using RAM at all but only processing power. Then I created a bag-of-words using Dask and then a sentiment analysis of the comments using the LabMT wordlist. Lastly I created a WordCloud for one of the topics just for fun. Enjoy!


## Step 1 - Prepare the remote access

Create instance in AWS amazon server environment and upload the dataset. Make sure to request enough space for the dataset and the castra file to fit in the volume. The castra file will allocate almost the same amount of space as the data file. In our case we will need 30+30=60GB.

<!---your comment goes here 
and here
-->
```python
# Log into the EC2 instance created from a local terminal
ssh -i "~/.ssh/RandomKey.pem" ubuntu@ec2 -54-165-250-39.compute -1. amazonaws.com
```
![alt text][figure_1]

```python
# Upload the dataset to the instance from a local terminal   
scp -i ~/.ssh/RandomKey.pem ~/path_to_datafile/RC_2015 -01.bz2 ubuntu@ec2 -54-165-250-39.compute -1.amazonaws.com:~/data/RC_2015 -01. bz2
```
![alt text][figure_2]

Install dependencies to the instance in order to wrangle the data from distance using the server's processing power. Firstly we need to download Anaconda to the instance.

```python
# Download Anaconda to the server from a server terminal
wget https://repo.continuum.io/archive/Anaconda2-4.2.0-Linux-x86_64. sh
```
![alt text][figure_3]

```python
# Install Anaconda to the instance from a server terminal
bash Anaconda2-4.2.0-Linux-x86_64.sh
```
![alt text][figure_4]


Settle a server **ipython notebook** for remote handling python reports and querying data.

```python
# Open ipython in server environment and do the following command
ipython

# It will prompt a python interactive window that works in the bash environment
# Then create a password by typing the below commands
from IPython.lib import passwd passwd ()

# You will be prompted to enter and verify a password 
# (You should remember it. This will be the password to log to the remote ipython notebook)
# When done copy the generated sha1 key
```
![alt text][figure_5]


Locate the **ipython_notebook_config.py** file in the .jupyter directory of the server and paste the key in the appropriate field along with the rest of the uncommented lines.
```python
# If you don’t already have a ipython_notebook_config.py file create one using the below command 
jupyter notebook --generate -config
```
![alt text][figure_6]

Now the connection is established. 

```python
# Write the below command to launch ipython
ipython notebook
```

You will be prompted to open a browser. You should write    
*https://[ip adress of the server]:[port]*

![alt text][figure_7]

## Step 2 
-----

To be continued..

