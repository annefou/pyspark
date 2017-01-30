---
title: "Introduction to Spark SQL"
teaching: 30
exercises: 15

questions:
- "What is SPARK SQL?"
- "Create a SPARK DataFrame"
- "Query your DataFrame with SQL"
objectives:
- "Learn about SPARK SQL"
keypoints:
- "Spark SQL select"
---

# Spark SQL

**Spark SQL** is a component on top of **Spark Core** that facilitates processing of structured and semi-structured data
and the integration of several data formats as source (Hive, Parquet, JSON).

It allows to transform RDDs using SQL (Structured Query Language).

To start **Spark SQL** within your notebook, you need to create a *SQL context*.

For this exercise, import a JSON file in a new history "World Cup". 
You can find the historical World cup player dataset in JSON format in our Data Library named
"Historical world cup player data  ".

Then create a new python 3 (change kernel if set by default to python 2) jupyter notebook from this file:
 
~~~
from pyspark import SparkContext
from pyspark.sql import SQLContext


sc = SparkContext('local', 'Spark SQL') 
sqlc = SQLContext(sc)
~~~
{: .python}

We can read the JSON file we have in our history and create a DataFrame (*Spark SQL* has a json reader available):
 
~~~
players = sqlc.read.json(get(1))

# Print the schema in a tree format

players.printSchema()

" Select only the "FullName" column
players.select("FullName").show(20)
~~~
{: .python}

~~~
+--------------------+
|            FullName|
+--------------------+
|        Ãngel Bossio|
|        Juan Botasso|
|      Roberto Cherro|
|   Alberto Chividini|
|                    |
|                    |
|       Juan Evaristo|
|      Mario Evaristo|
|     Manuel Ferreira|
|          Luis Monti|
|                    |
|   Rodolfo Orlandini|
|Fernando Paternoster|
|   Natalio Perinetti|
|     Carlos Peucelle|
|     Edmundo Piaggio|
|  Alejandro Scopelli|
|      Carlos Spadaro|
|                    |
|                    |
+--------------------+
only showing top 20 rows
~~~
{: .output}

Then we can create a view of our DataFrame. The lifetime of this temporary table is tied to the SparkSession that was used to create this DataFrame.

~~~
players.registerTempTable("players")
~~~
{: .python}

We can then query our view; for instance to get the names of all the Teams:

~~~
sqlc.sql("select distinct Team from players").show(10)
~~~
{: .python}

~~~
+--------+
|    Team|
+--------+
|England |
|Paraguay|
|     POL|
|  Russia|
|     BRA|
| Senegal|
|  Sweden|
|     FRA|
|     ALG|
|  Spain |
+--------+
only showing top 10 rows
~~~
{: .output}

And have the full SQL possibilities to create SQL query:

~~~
# Select the teams names from 2014 only 
team2014 = sqlc.sql("select distinct Team from players where Year == 2014")
#
# The results of SQL queries are Dataframe objects.
# rdd method returns the content as an :class:`pyspark.RDD` of :class:`Row`.
teamNames = team2014.rdd.map(lambda p: "Name: " + p.Team).collect()
for name in teamNames:
    print(name)
~~~
{: .python}



&nbsp;
&nbsp;
&nbsp;
&nbsp;
