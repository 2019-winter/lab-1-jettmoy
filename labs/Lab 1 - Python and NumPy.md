---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Jett
Jett Moy


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np

a = np.full((6, 4), 2)
print(a)
```

## Exercise 2

```python
b = np.ones((6,4)) + np.eye(6, 4) * 2
print(b)
```

## Exercise 3


The number of columns of matrix A must match the number of rows of matrix B. Using the * operator performs element-wise multiplication
and the dot function performs matrix multiplication. 

```python
a = np.full((6, 4), 2)
b = np.ones((6,4)) + np.eye(6, 4) * 2
c = a*b
print(c)
# d = np.dot(a, b)
```

## Exercise 4


The shape of the resulting array from matrix multiplication depends on the length of the rows of the first matrix and the length of the
columns of the second matrix. Transposing A produces a 4x4 matrix and transposing B produces a 6x6 matrix. 

```python
a = np.full((6, 4), 2)
b = np.ones((6,4)) + np.eye(6, 4) * 2
print(np.dot(a.transpose(), b))
print(np.dot(a, b.transpose()))
```

## Exercise 5

```python
def func():
    print('some output')
    
func()
```

## Exercise 6

```python
def arrstats(arr):
    print(arr.mean())
    print(arr.sum())

arr = np.random.rand(3, 2)
arrstats(arr)
```

## Exercise 7

```python
def countOnes(array):
    count = 0
    for x in np.nditer(array):
        if (x == 1):
            count += 1
    return count
            
print(np.eye(4))
print(countOnes(np.eye(4)))
```

```python
def where(cond):
    iterator = np.nditer(cond, flags=['multi_index'])
    for x in iterator:
        if x: 
            print(iterator.multi_index)
                
where(np.eye(4) < 1)
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd

a = pd.DataFrame(np.full((6,4), 2))
print(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = pd.DataFrame(np.ones((6,4)) + np.eye(6, 4) * 2)
print(b)
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
a*b
# a.dot(b)
# matrices not aligned error, different shapes
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def countOnes(dataframe):
    return dataframe.where(dataframe==1, 0).sum().sum()

df = pd.DataFrame(np.eye(4))
print(df)
print(countOnes(df))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df.name
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex',inplace=True)
titanic_df.loc["female"]
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index()
```

```python

```
