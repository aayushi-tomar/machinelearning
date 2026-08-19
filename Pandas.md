What is Pandas
Pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool, built on top of the Python programming language.
https://pandas.pydata.org/about/index.html

Pandas Series
A Pandas Series is like a column in a table. It is a 1-D array holding data of any type.

Importing Pandas:-
import numpy as np
import pandas as pd

Series from lists:-
# string
country = ['India','Pakistan','USA','Nepal','Srilanka']

pd.Series(country)
0       India
1    Pakistan
2         USA
3       Nepal
4    Srilanka
dtype: object

# integers
runs = [13,24,56,78,100]

runs_ser = pd.Series(runs)

# custom index
marks = [67,57,89,100]
subjects = ['maths','english','science','hindi']

pd.Series(marks,index=subjects)
maths       67
english     57
science     89
hindi      100
dtype: int64

# setting a name
marks = pd.Series(marks,index=subjects,name='Nitish ke marks')
marks
maths       67
english     57
science     89
hindi      100
Name: Nitish ke marks, dtype: int64


