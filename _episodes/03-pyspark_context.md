---
title: "Introduction to (Py)Spark"
teaching: 20
exercises: 15

questions:
- "What is [a]Spark and PySpark?"
- "How to use PySpark?"
- "How to define a Spark context?"
- "How can I create a RDD (Resilient Distributed Dataset)?"
objectives:
- "Learn about the terminology behind Spark, [a]Spark"
- "Learn about Spark context"
- "Learn about RDD"
keypoints:
- "Spark and RDD"
---

# Introduction to [a]Spark / PySpark   ([**Slides**](../slides/spark))

**Spark** is a general purpose cluster computing framework:
- it provides efficient in-memory computations for large data sets 
- it distributes **computation** and **data** across multiple computers. 

## Data Distribution

To distribute data, Spark uses a framework called *Resilient Distributed Datasets* (**RDDs**). 

![RDD](../slides/images/RDD.png)

For instance, if you read a file with Spark, it will automatically create a RDD. 

But a RDD is **immutable** *object* so to modify it a new RDD needs to be created. 

That is very helpful for **reproducibility**!

## Computation Distribution

To distribute computation, Spark API (Application Program Interface) available in multiple programming
languages (Scala, Java, Python and R) provides several operators such as map and reduce. 

**Spark Core** contains the basic functionality of Spark; in particular the APIs that define RDDs and the 
operations and actions that can be undertaken upon them (map, filter, reduce, etc.). 

The rest of Spark's libraries are built on top of the RDD and Spark Core:

- **Spark SQL** for SQL and structured data processing.  Every database table is represented as an RDD and Spark SQL queries are transformed into Spark operations.
- **MLlib** is a library of common machine learning algorithms implemented as Spark operations on RDDs. This library contains scalable learning algorithms like classifications, regressions, etc. 
that require iterative operations across large data sets. 
- **GraphX** is a collection of algorithms and tools for manipulating graphs and performing parallel graph operations 
and computations. 

- **Spark Streaming** for scalable, high-throughput, fault-tolerant stream processing of real-time data. 


![SP](../slides/images/SparkSWLayers.png)

The Spark API for python can be found [here](https://spark.apache.org/docs/2.0.2/api/python/index.html).

&nbsp;

# Spark Execution: Spark Context

Spark applications are run as independent sets of processes, coordinated by a **Spark Context** in a driver program.

![SP](../slides/images/SparkRuntime.png)

It may be automatically created (for instance if you call pyspark from the shells (the Spark context is then called *sc*).

But it must be defined in your jupyter notebook:

~~~
from pyspark import SparkContext
sc = SparkContext('local', 'pyspark tutorial') 
~~~
{: .python}

&nbsp;

- the driver (first argument) can be **local[*]**, **spark://", **yarn**, etc.
- the second argument is the application name and is a human readable string you choose.

&nbsp;

> ## Deployment of Spark:
> 
> It can be deployed on:
> 
> - a single machine such as your laptop (local)
> - a set of pre-defined machines (stand-alone)
> - a dedicated Hadoop-aware scheduler (YARN/Mesos)
> - "cloud", e.g. Amazon EC2
>
> The development workflow is that you start small (local) and scale up to one of the other solutions, depending on your needs and resources.
>
>
> At [UIO](http://www.uio.no), we have the [Abel cluster](http://www.uio.no/english/services/it/research/hpc/abel/) 
> where [Spark](http://www.uio.no/english/services/it/research/hpc/abel/help/software/Spark.html) is available. 
> 
> 
> **Often, you don't need to change *any* code to go between these methods of deployment!**
>
{: .callout}

~~~
from pyspark import SparkContext
sc = SparkContext('local', 'pyspark tutorial') 
from numpy import random
NUM_SAMPLES=1000000
def sample(p):
    x, y = random.random(), random.random()
    return 1 if x*x + y*y < 1 else 0
count = sc.parallelize(range(0, NUM_SAMPLES)).map(sample).reduce(lambda a, b: a + b)
print((4.0 * count / NUM_SAMPLES))
~~~
{: .python}

# Create a RDD from a file

# map/reduce

# Spark SQL

# MLlib

# GraphX

# Spark Streaming

> ## Challenge 
>
>  
>
> ~~~
> 
> ~~~
> {: .python}
>
>
> > ## Solution to Challenge 1
> > 
> >
> > ~~~
> > 
> > ~~~
> > {: .python}
> {: .solution}
{: .challenge}


&nbsp;
&nbsp;
&nbsp;
&nbsp;
