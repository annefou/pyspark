---
title: "Map-filter-Reduce in python"
teaching: 20
exercises: 15

questions:
- "What is a lambda function in python?"
- "What is a map-filter-reduce function in python?"
- "How can I use map-filter-reduce in python?"
objectives:
- "Learn about Lambda function in python"
- "Learn about map, filter and reduce in python"
- "To be able to write your own python code using map, filter and reduce"
keypoints:
- "Use python for writing map, filter and reduce"
---

# Lambda function in python


Python supports the creation of anonymous functions (i.e. functions defined without a name), using a construct called "lambda". 

The general structure of a lambda function is:

~~~
 lambda <args>: <expr>
~~~
{: .bash}

&nbsp;

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

~~~
 4
~~~
{: .output}

&nbsp;

The same function can be written as lambda function:

~~~
 g = lambda x: x**2
~~~
{: .python}

&nbsp;

And you call it:

~~~
 print(g(2))
~~~
{: .python}

~~~
 4
~~~
{: .output}

&nbsp;

As you can see **both functions do exactly the same** and can be **used in the same ways**. 


- Note that the lambda definition does not include a "return" statement -- it always contains a single expression which is returned. 
- Also note that you can put a lambda definition anywhere a function is expected, and you don't have to assign it to a variable at all.
- Lambda functions come from functional programming languages and the Lambda Calculus. Since they are so small they may be written on a single line.
- This is not exactly the same as lambda in functional programming languages, but it is a very powerful concept that's well integrated into Python.


&nbsp;

> ## Conditional expression in Lambda functions
> You can use conditional expression in a lambda function or/and have more than one input argument.
> 
> For example:
>
> ~~~
> f = lambda x,y: ["PASS",x,y] if x>3 and y<100 else ["FAIL",x,y]
> ~~~
> {: .python}
>
> ~~~
> print(f(4,50))
> ~~~
> {: .python}
>
> ~~~
> ['FAIL', 4, 200]
> ~~~
> {: .output}
{: .callout}

&nbsp;


> ## Challenge 1
>
> Start by defining a variable pairs
>
> ~~~
> pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
> ~~~
> {: .python}
>
> Write a Lambda function and use it to sort pairs by key using their names.
> You will be using the list.sort() method of a list. It modifies the list in-place (here pairs)and
> has a key parameter to specify a function to be called on each list element prior to making comparisons.
> The value of the key parameter is a function that takes a single argument and returns a key to use for sorting purposes. 
> Define this function as a Lambda function. 
>
> > ## Solution to Challenge 1
> > The function we wish to pass to the sort() method should return the name (as a string) for each pair.
> > Once passed to the sort() method, it is called exactly once for each input record.
> >
> > ~~~
> > pairs.sort(key=lambda pair: pair[1])
> > ~~~
> > {: .python}
> {: .solution}
{: .challenge}

**It is very often used with map-reduce (even if you can do without) in python and this is why it is shown here.**

## To summerize:

**Lambda functions = Anonymous functions**

![LambdaFunction](../img/anonymousLambda.png)


# map, filter and reduce in python

## Map

Map takes a function f and an array as input parameters and outputs an array where f is applied to every element. 
In this respect, using map is equivalent to for loops.

For instance, to convert a list of temperatures in Celsius to a list of temperature in Kelvin:

~~~
 temp_c = [10, 3, -5, 25, 1, 9, 29, -10, 5]
 temp_K = list(map(lambda x: x + 273.15, temp_c))
 list(temp_K)
~~~
{: .python}

&nbsp;

map() is a function with two arguments:

~~~
r = map(func, seq)
~~~
{: .bash}

The first argument *func* is the name of a function and the second a sequence (e.g. a list) *seq*. 
*map()* applies the function *func* to all the elements of the sequence *seq*. 
It returns a new list with the elements changed by *func*.

>
> ## Challenge 2
>
> Let's define a list of words:
> list_words = ["big","small", "able", "about", "hairdresser", "laboratory"]
> 
> Use a map function to print the number of character of each word:
> 
> > ## Solution to Challenge 2
> > 
> > ~~~
> > print(list(map(len,list_words)))
> > ~~~
> > {: .python}
> {: .solution}
{: .challenge}

## Filter

As the name suggests, *filter* can be used to filter your data. It tests each element of your input data and returns 
a subset of it for which a condition given by a function is TRUE. It does not modify your input data.
~~~
numbers = range(-15, 15)
less_than_zero = list(filter(lambda x: x < 0, numbers))
print(less_than_zero)
~~~
{: .python}
~~~
[-15, -14, -13, -12, -11, -10, -9, -8, -7, -6, -5, -4, -3, -2, -1] 
~~~
{: .output}

>
> ## Challenge 3
>
> Reuse *numbers* and extract all the odd numbers:
>
> numbers = range(-15, 15)
>
> > ## Solution to Challenge 3
> > 
> > ~~~
> > odd_numbers = list(filter(lambda x: x%2==1, numbers))
> > print(odd_numbers)
> > ~~~
> > {: .python}
> > ~~~
> > [-15, -13, -11, -9, -7, -5, -3, -1, 1, 3, 5, 7, 9, 11, 13]
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

## Reduce

Reduce takes a function f and an array as input. The function f gets two input parameters that work on individual elements of the array. Reduce combines every two elements of the array using the function f. 
Let's take an example:

~~~
# we define a list of integers
numbers = [1, 4, 6, 2, 9, 10]
# Define a new function combine
# Convert x and y to strings and create a tuple from x,y
def combine(x,y):
  return "(" + str(x) + ", " + str(y) + ")"

# Use reduce to apply combine to numbers
from functools import reduce

print(numbers)
reduce(combine,numbers)

~~~
{: .python}

- To use the python *reduce* function, you need to import it from *functools*.
- To define combine, we haven't used a lambda function. With a Lambda function, we would have:

~~~
# we define a list of integers
numbers = [1, 4, 6, 2, 9, 10]

# Use reduce to combine numbers
from functools import reduce

print(numbers)
reduce(lambda x,y: "(" + str(x) + ", " + str(y) + ")",numbers)
~~~
{: .python}

>
> ## Challenge 4
> Let's define a string variable *sentence*:
>
> ~~~
> sentence = "Dis-moi ce que tu manges, je te dirai ce que tu es."
> ~~~
>  {: .python}
> Compute the number of words in *sentence* 
>
> > ## Solution to Challenge 4
> > 1. First we remove punctuations from the sentence. 
> > 2. Then we split the resulting sentence and *map* 1 to each word of the sentence.
> > 3. The last step is to sum up to find the number of words in the sentence:
> > 
> > ~~~
> > import string
> > string.punctuation
> > no_punctuation=sentence.translate(str.maketrans("","",string.punctuation))
> > 
> > reduce(lambda x,y: x+y, map(lambda x: 1, no_punctuation.split()))
> > 
> > ~~~
> > {: .python}
> {: .solution}
> Apply it to an entire text to compute the total number of words of the text you upload yourself in your Galaxy history. 
> Or use pre-loaded book available under the Data libraries available on the UIO Galaxy eduPortal (Share data --> Data Libraries).
{: .challenge}

&nbsp;

> ## Remarks
> The execution order for the reduce is straightforward here because everything is executed sequentially, meaning one after the other but we will
> see it is very different for Spark or any other parallel reduce.
{: .callout}

&nbsp;
&nbsp;
&nbsp;
