---
layout: post
title: Visualization of Titanic Disaster using D3
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

In an attempt to experimentize with the visualization tools (Dimple.js, D3.js, visualization design principles, visual encodings, HTML, CSS, SVG) I created a polished data visualization that tells a story about survival rates of Titanic disaster, allowing a reader to explore trends or patterns.


<iframe src="http://bl.ocks.org/oikonang/raw/3ad78d923c28b48947a2eda389677a11/" marginwidth="0" marginheight="0" scrolling="no">
</iframe>


<!--
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
-->
