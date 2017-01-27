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

.image20[![ResBaz](/slides/images/ResBazLogo.png)]

The easiest way to **navigate** this slide deck
is **by hitting `[space]` on your keyboard**

You can also navigate with arrow keys, but be careful because some
slides can be nested inside of each other (vertically)

---

template: content

#  Questions

- Why Big Data?
- What is Big Data?
- How to deal with Big Data?

---
template: content

# Objectives

- Understand what is Big Data
- Understand the need of parallelism 
- Learn about map-reduce 


---
template: content

# Why Big Data?

Credit: [Mapped: The climate change conversation on Twitter](https://www.carbonbrief.org/mapped-the-climate-change-conversation-on-twitter)

.image80[[![BD](/slides/images/BDWhy.png)](http://sna-analysis.s3.amazonaws.com/zoomify/cc-me-31mar.htm)]

[//]: # ---
[//]: # template: content

[//]: # # Why Big Data?

[//]: # Relationships and its adjacency matrix

[//]: # .image80[[![BD](/slides/images/BDWhy2.png)](https://www.youtube.com/watch?v=J8baiKYJHMc&t=802s)]

---
template: content

# What is Big Data?

Let's start with a video...

[![BDYT](/slides/images/BigDataYT.png)](https://www.youtube.com/watch?v=PI7SLOovO5c)

---
template: content

# Big Data - 3V

.image80[![BD3V](/slides/images/BDVVV.png)]

Terry Speed, 2014: 
"... big data refers to things one can do at a large scale, that cannot be done
at a smaller one, to extract new insights, or create new forms and value, in ways that
change markets, organizations, the relationships between governments, citizen and more."


---
template: content

# Really Big?

**Big** is a fast moving target: kilobytes, megabytes,
gigabytes, terabytes, petabytes, exabytes, zettabytes, ...

.image60[![BD](/slides/images/BigData.png)] 

=  **Big data can be "small"... but typically is complex, unstructured, distributed**

So instead of talking about 3V we often talk about 4V, adding **veracity**...

---
template: content

# Big Data life cycle

&nbsp;
.image120[[![BDLC](/slides/images/BDlifecycle.png)](http://www.journaldev.com/8795/introduction-to-hadoop)]

&nbsp;

*value chain*: information - knowledge - decisions - actions


**Statistics** are very important for Big data!

---
template: content

# What to do with big data?

When our problems are too big problems to solve on our laptops...

- Analyze web site data from [Common Crawl Web Corpus](http://commoncrawl.org/) (about 540 TB)
- 24h Weather forecasting produces large amount of data and needs to be accurate and done in less than 24h...

&nbsp;


==> **PARALLELISM**

And not only with respect to computing power
- but also disk space
- memory space, and
- network bandwidth

==> Multiple parallel programming models but we will talk about one only!

---
template: title
#  Map-reduce programming model

![SP](/slides/images/map-reduce.png)



---
template: title
#  Hands-on



---
<!-- REFERENCES -->

# References


- [http://spark.apache.org/docs/latest/api/python/index.html](http://spark.apache.org/docs/latest/api/python/index.html)

- [http://spark.apache.org/docs/latest](http://spark.apache.org/docs/latest)

- [https://github/holdenk/intro-to-pyspark-demos](https://github/holdenk/intro-to-pyspark-demos)

- [http://bit.ly/PySparkIntroExamples](http://bit.ly/PySparkIntroExamples)
- [http://bit.ly/learningSparkExamples](http://bit.ly/learningSparkExamples)
