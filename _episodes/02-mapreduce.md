---
title: "Map-Reduce in python"
teaching: 20
exercises: 15

questions:
- "What is a lambda function in python?"
- "What is a map-reduce function in python?"
- "How can I write a map-reduce in python?"
objectives:
- "Learn about Lambda function in python"
- "Learn about map-reduce in python"
- "To be able to write your own mapreduce function in python"
keypoints:
- "Use python for writing mapreduce function"
---

# Lambda function in python


Python supports the creation of anonymous functions (i.e. functions defined without a name), using a construct called "lambda". 

Let's take a python function to double the value of a scalar:


~~~
 def f (x): 
   return x**2
~~~
{: .python}

&nbsp;

For instance to use this function:

~~~
 print(f(2))
~~~
{: .python}

&nbsp;

The same function can be written as lambda function:

~~~
 f = lambda x: x**2
~~~
{: .python}

&nbsp;

And you call it:

~~~
 print(f(2))
~~~
{: .python}

&nbsp;

As you can see both functions do exactly the same and can be used in the same ways. 

Note that the lambda definition does not include a "return" statement -- it always contains a single expression 
which is returned. Also note that you can put a lambda definition anywhere a function is expected, 
and you don't have to assign it to a variable at all.

This is not exactly the same as lambda in functional programming languages, but it is a very powerful concept that's well integrated into Python.

It is very often used with map-reduce (even if you can do without) in python and this is why it is shown here.

## To summerize:

**Lambda functions = Anonymous functions**

![LambdaFunction](img/anonymousLambda.png)

> ## Challenge 1
>
> Start by 
>
> > ## Solution to Challenge 1
> >
> > 
> > ~~~
> > 
> > 
> > 
> > ~~~
> > {: .python}
> {: .solution}
{: .challenge}


## Introduction to map reduce in python


> ## Challenge 2
>
> Start by 
>
> > ## Solution to Challenge 2
> >
> > 
> > ~~~
> > 
> > 
> > 
> > ~~~
> > {: .python}
> {: .solution}
{: .challenge}



&nbsp;
&nbsp;
&nbsp;
&nbsp;
