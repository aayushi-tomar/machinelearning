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

Series from dict:-
marks = {
    'maths':67,
    'english':57,
    'science':89,
    'hindi':100
}

marks_series = pd.Series(marks,name='nitish ke marks')
marks_series
maths       67
english     57
science     89
hindi      100
Name: nitish ke marks, dtype: int64

Series Attributes:-
# size
marks_series.size
4

# dtype
marks_series.dtype
dtype('int64')

# name
marks_series.name
nitish ke marks

# is_unique
marks_series.is_unique

pd.Series([1,1,2,3,4,5]).is_unique
false

# index
marks_series.index
Index(['maths', 'english', 'science', 'hindi'], dtype='object')

runs_ser.index
RangeIndex(start=0, stop=5, step=1)

# values
marks_series.values
array([ 67,  57,  89, 100])

Series using read_csv:-
# with one col
subs = pd.read_csv('/content/subs.csv',squeeze=True)
subs
0       48
1       57
2       40
3       43
4       44
      ... 
360    231
361    226
362    155
363    144
364    172
Name: Subscribers gained, Length: 365, dtype: int64
