class: middle

# Big Data
## Introduction

### Research Bazaar Oslo 2017

Inspired from the [workshop on Data Science with \[a\] spark at CSCS](http://user.cscs.ch/getting_started/tutorials/2016/workshop_on_data_science_with_a_spark/index.html)
<!-- Slides by Anne Fouilloux<br/> -->

.footer[
https://github.com/annefou/pyspark
]

---

layout: true
name: title
class: middle

.footer[
ResBaz 2017
]

---

layout: true
name: content

.footer[
ResBaz 2017
]

---

template: title

## Welcome!

.image20[![ResBaz](../images/ResBazLogo.png)]

The easiest way to **navigate** this slide deck
is **by hitting `[space]` on your keyboard**

You can also navigate with arrow keys, but be careful because some
slides can be nested inside of each other (vertically)

---

template: content

#  Questions

- "What is Spark?"
- "What is PySpark?"

---
template: content

# Objectives
objectives:
- "Learn about the terminology behind Spark, [a]Spark"
- "Learn about Spark context"
- "Learn about RDD (Resilient Distributed Dataset)"

# Keypoints:
- "Spark and RDD"

---
template: title

# What is Spark?

.image20[![SparkLogo](../images/spark-logo.png)] 

When we talk about Spark, we often add "Apache" or just the letter "a" in front of it. 

- [[a]Spark](http://spark.apache.org/) or [Apache Spark](http://spark.apache.org/)
- [Apache Flink](https://flink.apache.org/)

**Spark** is an **open source big data processing framework** that aims to make data processing fast:

- fast to run. 
- fast to write.

It was originally developed in 2009 in UC Berkeley’s AMPLab, and open sourced in 2010 as an *Apache project*. 


---
template: title
#  What is (Py)Spark?

- Spark is a general purpose distributed system
- We often talk about Apache Spark because the Apache project is one of the most active.
- Based on Map-Reduce: programmer provides a map and a reduce function
- Known to be faster then Hadoop Map/Reduce
- Nodes are abstracted: an individual node cannot be addressed
- Network is abstracted: there is only implicit communication
- PySpark is one of the API for Spark...

.image120[![SP](../images/SparkSWLayers.png)]


---
template: title
# Why(Py)Spark?


# Pros

- very simple to write parallelized code (for simple problems...)
- Synchronization points and errors are handled by the framework
- Many useful algorithm are already implemented in Spark

# Cons
- Sometimes difficult to express a problem in map-reduce fashion
- Not as efficient as other programming models such as MPI when a lot of communication is required


---
template: title

# And what about **Apache Flink**?

.image20[![ResBaz](../images/flink-logo.png)]

&nbsp;

[**Apache Flink**](https://flink.apache.org) is another open source for big data processing. There are differences 
between the two projects but this topic is beyond the scope of this lesson.

---
template: title

# How does it work?

The goal is to be able to process your data in parallel
The runtime system consists of a **driver** and **workers** (there are other components such as schedulers, memory manager, but those are details).

# Spark Driver


- Coordinates the work to be done
- Keeps track of tasks
- collect metrics about the tasks (dis IO, memory, etc.)
- communicates with the workers (and the user)


---
template: title

# Worker

- receive tasks to be done from the driver
- store data in memory or on disk
- perform calculations
- return results to the driver

The user's access point to this Spark universe is the **Spark Context** which provides an interface to generate RDDs (Resilient Distributed Dataset).

**The only point of contact with the Spark "universe" is the Spark Context which is the 
programmatic representation of the driver.**

Add a figure here (workers-driver)


---
template: title

# Spark runtime
A few points before we get our feet wet with doing some basic data massaging in Spar...

The Spark runtime can be deployed on:

- s single machine such as your laptop (local)
- a set of pre-defined machines (stand-alone)
- a dedicated Hadoop-aware scheduler (YARN/Mesos)
- "cloud", e.g. Amazon EC2

The development workflow is that you start small (local) and scale up to one of the other solutions, depending on your needs and resources.

Remember that at UIO, we have the Abel cluster where Spark is available. See more information here.

In addition, you can run applications on any of these platforms either

- interactively through a shell (or a jupyter notebook as we do now)
- batch mode

**Often, you don't need to change *any* code to go between these methods of deployment!**

---
template: title
#  Hands-on
