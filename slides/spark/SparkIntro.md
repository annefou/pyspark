class: middle

# Big Data
## Introduction

### Research Bazaar Oslo 2017

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

- "What is (Py)Spark?"
- "How does it work?"
- "What is a Resilient Distributed Dataset (RDD)?"

---
template: content

# Objectives

- "Learn about the terminology behind Spark, [a]Spark"
- "Understand how Spark works"
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


We often talk about Apache Spark because the Apache project is one of the most active.

---
template: title
#  What are the main characteristics of (Py)Spark?

- Spark is a general purpose distributed system
- Nodes are abstracted: an individual node cannot be addressed
- Network is abstracted: there is only implicit communication
- Based on Map-Reduce: programmer provides a map and a reduce function
- Known to be faster then Hadoop Map/Reduce
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

# How does it work?

The goal is to be able to process your data in parallel thanks to the Spark runtime system.
It consists of a **driver** and **workers** (there are other components such as schedulers, 
memory manager, but those are details).

.image80[![SP](../images/SparkRuntime.png)]


---
template: title

# Spark Driver


- Coordinates the work to be done
- Keeps track of tasks
- collect metrics about the tasks (disk IO, memory, etc.)
- communicates with the workers (and the user)


---
template: title

# Spark Worker

- receive tasks to be done from the driver
- store data in memory or on disk
- perform calculations
- return results to the driver


---
template: title

# Spark deployment

The Spark runtime can be deployed on:

- s single machine such as your laptop (local)
- a set of pre-defined machines (stand-alone)
- a dedicated Hadoop-aware scheduler (YARN/Mesos)
- "cloud", e.g. Amazon EC2

&nbsp; 

The development workflow is that you start small (local) and scale up to one of the other solutions, depending on your needs and resources.


Remember that at [UIO](http://www.uio.no), we have the [Abel cluster](http://www.uio.no/english/services/it/research/hpc/abel/) 
where [Spark](http://www.uio.no/english/services/it/research/hpc/abel/help/software/Spark.html) is available. 

&nbsp; 

**Often, you don't need to change *any* code to go between these methods of deployment!**

---
template: title

# Resilient Distributed Dataset

Another important building block of every Spark application is what we call the "**Resilient Distributed Dataset**".

- Resilient, i.e. fault-tolerant and is able to rebuild data upon failure.
- Distributed with data residing on multiple nodes in a cluster. The RDD keeps track of data distribution across the work.
- Dataset is a collection of partitioned data with primitive values or values of values, e.g. tuples or other objects (that represent records of the data you work with).

Users write applications that feed data into RDDs and each worker will work on a part of an RDD.

And something to remember:
- A RDD is **immutable**

To *modify* it, a new RDD needs to be created. That is very helpful for **reproducibility**!

---
template: title

# RDD Architecture

- When you load a file into Spark, it becomes a RDD.
- Then the driver will distribute *chuncks* to workers
- RDD can be **cached** (*saved in memory*; useful for iterating over the RDD)
.image60[![RDD](../images/RDD.png)]


---
template: title

# RDD transformations/actions

Once an RDD is created, it is **immutable**. To work on the data, you can create a new one via transformations and actions.

# Transformations include:

- **map**: the most basic component of map/reduce with 1:1 correspondance to the original data
- **flatMap**: returns a number of items different from the original data
- **filter**: only keep those elements for which the filter function is TRUE
- **distinct**: only retain the unique elements of the entire RDD
- **reduceByKey**: group elements by key and keep the data distributed
- **mapPartitions**: similar to map but done on a per-partition basis (requires a generator function)
- **sortBy**: sort using the provided function

Transformations are only executed once an action is performed and therefore only if a transformation is required. 
It is called **lineage**.


---
template: title

# Actions include

- **collect**: pulls all elements of the RDD to the driver (often a bad idea...)
- **collectAsMap**: like collect but returns a dictionary to the driver which makes it easy to lookup the keys
- **reduce**: reduces the entire RDD to a single value
- **countByKey/countByValue**
- **take**: yields a desired number of items to the driver
- **first**: returns the first element of the RDD to the driver (useful to inspect your data)

---
template: title
#  Hands-on
