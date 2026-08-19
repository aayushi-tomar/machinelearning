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

# with 2 cols
vk = pd.read_csv('/content/kohli_ipl.csv',index_col='match_no',squeeze=True)
vk
match_no
1       1
2      23
3      13
4      12
5       1
       ..
211     0
212    20
213    73
214    25
215     7
Name: runs, Length: 215, dtype: int64

movies = pd.read_csv('/content/bollywood.csv',index_col='movie',squeeze=True)
movies
movie
Uri: The Surgical Strike                     Vicky Kaushal
Battalion 609                                 Vicky Ahuja
The Accidental Prime Minister (film)         Anupam Kher
Why Cheat India                            Emraan Hashmi
Evening Shadows                           Mona Ambegaonkar
                                              ...       
Hum Tumhare Hain Sanam                   Shah Rukh Khan
Aankhen (2002 film)                     Amitabh Bachchan
Saathiya (film)                             Vivek Oberoi
Company (film)                                Ajay Devgn
Awara Paagal Deewana                        Akshay Kumar
Name: lead, Length: 1500, dtype: object

Series methods:-
# head and tail
subs.head()
0    48
1    57
2    40
3    43
4    44
Name: Subscribers gained, dtype: int64

vk.head(3)
match_no
1     1
2    23
3    13
Name: runs, dtype: int64

vk.tail(10)
match_no
206     0
207     0
208     9
209    58
210    30
211     0
212    20
213    73
214    25
215     7
Name: runs, dtype: int64

# value_counts -> movies
movies.value_counts()
Akshay Kumar        48
Amitabh Bachchan    45
Ajay Devgn          38
Salman Khan         31
Sanjay Dutt         26
                    ..
Diganth              1
Parveen Kaur         1
Seema Azmi           1
Akanksha Puri        1
Edwin Fernandes      1
Name: lead, Length: 566, dtype: int64

# sort_values -> inplace
vk.sort_values(ascending=False).head(1).values[0]
113

vk.sort_values(ascending=False)
match_no
128    113
126    109
123    108
164    100
120    100
      ... 
93       0
211      0
130      0
8        0
135      0
Name: runs, Length: 215, dtype: int64

# sort_index -> inplace -> movies
movies.sort_index(ascending=False,inplace=True)
movies
movie
Zor Lagaa Ke...Haiya!            Meghan Jadhav
Zokkomon                       Darsheel Safary
Zindagi Tere Naam           Mithun Chakraborty
Zindagi Na Milegi Dobara        Hrithik Roshan
Zindagi 50-50                      Veena Malik
                                   ...        
2 States (2014 film)              Arjun Kapoor
1971 (2007 film)                Manoj Bajpayee
1920: The Evil Returns             Vicky Ahuja
1920: London                     Sharman Joshi
1920 (film)                   Rajniesh Duggall
Name: lead, Length: 1500, dtype: object

vk.sort_values(inplace=True)
vk
match_no
87       0
211      0
207      0
206      0
91       0
      ... 
164    100
120    100
123    108
126    109
128    113
Name: runs, Length: 215, dtype: int64

Series Maths Methods:-
# count
vk.count()
215

# sum -> product
subs.sum()
49510

# mean -> median -> mode -> std -> var
subs.mean()
print(vk.median())
print(movies.mode())
print(subs.std())
print(vk.var())
24.0
0    Akshay Kumar
dtype: object
62.6750230372527
688.0024777222343

# min/max
subs.max()
396

# describe
subs.describe()
count    365.000000
mean     135.643836
std       62.675023
min       33.000000
25%       88.000000
50%      123.000000
75%      177.000000
max      396.000000
Name: Subscribers gained, dtype: float64
