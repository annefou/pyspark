---
title: "Introduction to UIO galaxy eduPortal"
teaching: 10
exercises: 5


questions:
- "How to find your way around UIO galaxy eduPortal?"
- "How to interact with python/pyspark jupyter notebook?"
objectives:
- "To gain familiarity with the various panes in the UIO galaxy eduPortal"
- "To gain familiarity with the buttons and options in the pySpark jupyter notebook"
- "To be able to manage your Galaxy history"
keypoints:
- "Use UIO Galaxy eduPortal to start a pySpark jupyter notebook"
- "Start a pySpark jupyter notebook from the UIO Galaxy eduPortal."
---

## Motivation

You have been using python for analyzing your data but considering the growth in volume and complexity 
you are now willing to make a further step.  This lesson will teach you how to start using PySpark and 
introduce you to the map-reduce programming model.

## Before starting the workshop

To ease our work and avoid installing Spark on your laptop, we will be using the [UIO Galaxy eduPortal](https://geoportal-jupyter01.hpc.uio.no/).
If you haven't received a login and password yet, don't panic. This can be handled in few minutes during the workshop.

&nbsp;

**Remark**: without changing your pySpark code, you can scale up to hundred processors on UIO HPC abel... For more information 
[see](http://www.uio.no/english/services/it/research/hpc/abel/help/software/Spark.html)


## Introduction to UIO Galaxy eduPortal

We'll be using [UIO Galaxy eduPortal](https://geoportal-jupyter01.hpc.uio.no/): [Galaxy](https://galaxyproject.org/) is an open source,
web-based platform for data intensive that has been initially developed for biomedical research. 

Galaxy is a scientific workflow, data integration, and data and analysis persistence and publishing platform that aims to 
make data intensive accessible to research scientists that do not have extensive computer programming experience.
To learn more, take one of our [Galaxy tours](https://usegalaxy.org/tours).

** For most of the images below, you can click to view a short video or get detailed documentation on the corresponding subject.**

---

***Login panel***
![GalaxyLogin](/img/GalaxyLogin.png)

---

**Basic layout**
![GalaxyLWelcome](/img/GalaxyWelcome.png)

---

***Get help***
[![GalaxyHelp](/img/GalaxyHelp.png)](https://wiki.galaxyproject.org/Learn)

---

**Upload data**
[![GalaxyUpload](/img/GalaxyUpload.png)](https://vimeo.com/120901536)

---

**Share Data**
[![GalaxyShare](/img/GalaxyShare.png)](https://vimeo.com/75934770)

---

***Data Libraries***
[![GalaxyDataLibraries](/img/GalaxyDataLibraries.png)](https://wiki.galaxyproject.org/Admin/DataLibraries/Libraries)

---

**Navigate histories**
[![GalaxyHistories](/img/GalaxyHistories.png)](https://vimeo.com/76020876)

---

## Introduction to pySpark jupyter notebook

**Start a pyspark jupyter notebook**

A Jupyter notebook can be started either existing dataset in your History or you can use our jupyter notebook template for python 3.

- Click on "**Shared Data**", then on "**Data Libraries**" and finally on "**Jupyter notebooks**".
- Tick the box "**template_ipython3.ipynb**" and then "**to History**".
- Once imported go to your current History and open your notebook 

[![GalaxyHistories](/img/GalaxyJupyter.png)](https://github.com/bgruening/galaxy-ipython)

---

Then you should get:

![GalaxyHistories](/img/GalaxyJupyterWelcome.png)

&nbsp;
&nbsp;
&nbsp;
&nbsp;