## All About Pandas for Data Science [Basics + Advanced]

## Basics of Pandas for Data Science 

Pandas is a popular Python package for data science, and with good reason: it offers powerful, expressive and flexible data structures that make data manipulation and analysis easy, among many other things.

### Import

```
import pandas as pd
import numpy as np
```

### Create a DataFrame

DataFrames in Python are very similar: they come with the [Pandas](http://pandas.pydata.org/) library, and they are defined as two-dimensional labeled data structures with columns of potentially different types.

In general, you could say that the Pandas DataFrame consists of three main components: the data, the index, and the columns.

```
df=pd.DataFrame(np.arange(0,20).reshape(5,4),index=["r1","r2","r3","r4","r5"],columns=["c1","c2","c3","c4"])
```

### Print Head

```
print(df.head())
```

Output:

```
    c1  c2  c3  c4
r1   0   1   2   3
r2   4   5   6   7
r3   8   9  10  11
r4  12  13  14  15
r5  16  17  18  19
```

### Store as CSV

```
df.to_csv("testscv.csv")
```

### Accessing Element and Printing its type

```
#accessing elements
#1. loc 2. iloc
#single row or column will be treated as series
#and more than that treated as dataframe
print(df.loc["r2"],"\n",type(df.loc["r2"]))
```

Output:

```
c1    4
c2    5
c3    6
c4    7
Name: r2, dtype: int64 
 <class 'pandas.core.series.Series'>
```

### Slicing

```
print(df.iloc[:,:])

print(type(df.iloc[:,:]))
```

Output:

```
    c1  c2  c3  c4
r1   0   1   2   3
r2   4   5   6   7
r3   8   9  10  11
r4  12  13  14  15
r5  16  17  18  19
<class 'pandas.core.frame.DataFrame'>
```

### Convert To array

```
#converting to array

df.iloc[:,:].values
```

Output:

```
array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11],
       [12, 13, 14, 15],
       [16, 17, 18, 19]])
```

### Find Unique Values

```
#unique values find
print(df['c1'].value_counts(),end="\n") #number of occurences in column

print(df["c1"].unique(),end="\n") #which values are unique

print(df.isnull().sum()) #check null values
```

Output:

```
12    1
4     1
16    1
8     1
0     1
Name: c1, dtype: int64
[ 0  4  8 12 16]
c1    0
c2    0
c3    0
c4    0
dtype: int64
```

#### Now We will move to little Advance

### Read CSV

```
#read sv

df=pd.read_csv("https://cdn.wsform.com/wp-content/uploads/2020/06/color_srgb.csv")
print(df.head())
```

Output:

```
     Name      HEX               RGB
0   White  #FFFFFF  rgb(100,100,100)
1  Silver  #C0C0C0     rgb(75,75,75)
2    Gray  #808080     rgb(50,50,50)
3   Black  #000000        rgb(0,0,0)
4     Red  #FF0000      rgb(100,0,0)
```

### Print Info

```
df.info()
```

Output:

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 16 entries, 0 to 15
Data columns (total 3 columns):
 #   Column  Non-Null Count  Dtype 
---  ------  --------------  ----- 
 0   Name    16 non-null     object
 1   HEX     16 non-null     object
 2   RGB     16 non-null     object
dtypes: object(3)
memory usage: 512.0+ bytes
```

### Describe DataFrame

```
df.describe()
```

Output:

```
Name	HEX	RGB
count	16	16	16
unique	16	16	16
top	Blue	#000080	rgb(0,100,100)
freq	1	1	1
```

### Read from Strings

```
#read data 
from io import StringIO
data=('c1,c2,c3\n'
    'x,y,1\n'
    'a,b,2\n'
    'c,d,3\n')

pd.read_csv(StringIO(data)
```

Output:

```
	c1	c2	c3
0	x	y	1
1	a	b	2
2	c	d	3
```

### Read Specific column

```
#read specific column
df=pd.read_csv(StringIO(data),usecols=["c1","c3"])
print(df)
```

Output:

```
  c1  c3
0  x   1
1  a   2
2  c   3
```

Save file again, yes you can :

```
df.to_csv("test.csv")
```

### Save with Specific Data Type

```
#save with specific datatype

dx=pd.read_csv(StringIO(data),dtype=object)

print(dx)
```

Output:

```
  c1 c2 c3
0  x  y  1
1  a  b  2
2  c  d  3
```

#### acces data u can check now it is string-Object

```
dx["c1"] [1] #acces data u can check now it is string-Object
```

Output:

```
'a'
```

### Assign Different Datatype to different Columns

```
#assign diff datatype to diff columns
dy=pd.read_csv(StringIO(data),dtype={"c1":object,"c3":int})

print(dy)#show csv file
print(dy["c1"][1],type(dy["c1"][1]))
print(dy["c3"][1],type(dy["c3"][1]))


```

Output:

check data type In output:

```
  c1 c2  c3
0  x  y   1
1  a  b   2
2  c  d   3
a <class 'str'>
2 <class 'numpy.int64'>
```

#### check all dtypes at once

```
dy.dtypes
```

Output:

```
c1    object
c2    object
c3     int64
dtype: object
```

### Give Index

```
#give index...
data = ('index,a,b,c\n'
           '4,apple,bat,5.7\n'
            '8,orange,cow,10')
pd.read_csv(StringIO(data),index_col=0)
```

Output:

```
a	b	c
index			
4	apple	bat	5.7
8	orange	cow	10.0
```

In:

```
data = ('a,b,c\n'
           '4,apple,bat,\n'
            '8,orange,cow,')
pd.read_csv(StringIO(data)) #see this
```

Output:

```
	a	b	c
4	apple	bat	NaN
8	orange	cow	NaN
```

Solution for this

```
pd.read_csv(StringIO(data),index_col=False) #solution
```

Output:

```
a	b	c
0	4	apple	bat
1	8	orange	cow
```

### Quoting and Escape Characters¶. Very useful in NLP

```
## Quoting and Escape Characters¶. Very useful in NLP

data = 'a,b\n"hello, \\"Bob\\", nice to see you",5'
pd.read_csv(StringIO(data),escapechar='\\')
```

Output:

```
a	b
0	hello, "Bob", nice to see you	5
```

### URL to CSV

```
## URL to CSV

df=pd.read_csv('https://download.bls.gov/pub/time.series/cu/cu.item',
                 sep='\t')
df.head()
```

Output:

```
	item_code	item_name	display_level	selectable	sort_sequence
0	AA0	All items - old base	0	T	2
1	AA0R	Purchasing power of the consumer dollar - old ...	0	T	399
2	SA0	All items	0	T	1
3	SA0E	Energy	1	T	374
4	SA0L1	All items less food	1	T	358
```

### Convert Json to csv

```
df1.to_csv('wine.csv')
```

### Convert Json to different json formats¶

```
print(df.to_json(orient="index"))
print(df.to_json(orient="records"))#see differnce how json key-value pair is there
```

Output:

```
{"0":{"0":1,"1":14.23,"2":1.71,"3":2.43,"4":15.6,"5":127,"6":2.8,"7":3.06,"8":0.28,"9":2.29,"10":5.64,"11":1.04,"12":3.92,"13":1065},"1":{"0":1,"1":13.2,"2":1.78,"3":2.14,"4":11.2,"5":100,"6":2.65,"7":2.76,"8":0.26,"9":1.28,"10":4.38,"11":1.05,"12":3.4,"13":1050},"2":{"0":1,"1":13.16,"2":2.36,"3":2.67,"4":18.6,"5":101,"6":2.8,"7":3.24,"8":0.3,"9":2.81,"10":5.68,"11":1.03,"12":3.17,"13":1185},"3":{"0":1,"1":14.37,"2":1.95,"3":2.5,"4":16.8,"5":113,"6":3.85,"7":3.49,"8":0.24,"9":2.18,"10":7.8,"11":0.86,"12":3.45,"13":1480},"4":{"0":1,"1":13.24,"2":2.59,"3":2.87,"4":21.0,"5":118,"6":2.8,"7":2.69,"8":0.39,"9":1.82,"10":4.32,"11":1.04,"12":2.93,"13":735},"5":{"0":1,"1":14.2,"2":1.76,"3":2.45,"4":15.2,"5":112,"6":3.27,"7":3.39,"8":0.34,"9":1.97,"10":6.75,"11":1.05,"12":2.85,"13":1450},"6":{"0":1,"1":14.39,"2":1.87,"3":2.45,"4":14.6,"5":96,"6":2.5,"7":2.52,"8":0.3,"9":1.98,"10":5.25,"11":1.02,"12":3.58,"13":1290},"7":{"0":1,"1":14.06,"2":2.15,"3":2.61,"4":17.6,"5":121,"6":2.6,"7":2.51,"8":0.31,"9":1.25,"10":5.05,"11":1.06,"12":3.58,"13":1295},"8":{"0":1,"1":14.83,"2":1.64,"3":2.17,"4":14.0,"5":97,"6":2.8,"7":2.98,"8":0.29,"9":1.98,"10":5.2,"11":1.08,"12":2.85,"13":1045},"9":{"0":1,"1":13.86,"2":1.35,"3":2.27,"4":16.0,"5":98,"6":2.98,"7":3.15,"8":0.22,"9":1.85,"10":7.22,"11":1.01,"12":3.55,"13":1045},"10":{"0":1,"1":14.1,"2":2.16,"3":2.3,"4":18.0,"5":105,"6":2.95,"7":3.32,"8":0.22,"9":2.38,"10":5.75,"11":1.25,"12":3.17,"13":1510},"11":{"0":1,"1":14.12,"2":1.48,"3":2.32,"4":16.8,"5":95,"6":2.2,"7":2.43,"8":0.26,"9":1.57,"10":5.0,"11":1.17,"12":2.82,"13":1280},"12":{"0":1,"1":13.75,"2":1.73,"3":2.41,"4":16.0,"5":89,"6":2.6,"7":2.76,"8":0.29,"9":1.81,"10":5.6,"11":1.15,"12":2.9,"13":1320},"13":{"0":1,"1":14.75,"2":1.73,"3":2.39,"4":11.4,"5":91,"6":3.1,"7":3.69,"8":0.43,"9":2.81,"10":5.4,"11":1.25,"12":2.73,"13":1150},"14":{"0":1,"1":14.38,"2":1.87,"3":2.38,"4":12.0,"5":102,"6":3.3,"7":3.64,"8":0.29,"9":2.96,"10":7.5,"11":1.2,"12":3.0,"13":1547},"15":{"0":1,"1":13.63,"2":1.81,"3":2.7,"4":17.2,"5":112,"6":2.85,"7":2.91,"8":0.3,"9":1.46,"10":7.3,"11":1.28,"12":2.88,"13":1310},"16":{"0":1,"1":14.3,"2":1.92,"3":2.72,"4":20.0,"5":120,"6":2.8,"7":3.14,"8":0.33,"9":1.97,"10":6.2,"11":1.07,"12":2.65,"13":1280},"17":{"0":1,"1":13.83,"2":1.57,"3":2.62,"4":20.0,"5":115,"6":2.95,"7":3.4,"8":0.4,"9":1.72,"10":6.6,"11":1
```

Note: The output is big printing half here.........

check [This link for full Output](https://github.com/saurabhthesuperhero/BasicsOfMachineLearning/blob/master/pandas_practice_easy.ipynb)

### Reading HTML content

```
url = 'https://www.fdic.gov/bank/individual/failed/banklist.html'

dfs = pd.read_html(url)

dfs[0]
```

Output:

```
Bank Name	City	ST	CERT	Acquiring Institution	Closing Date
0	The First State Bank	Barboursville	WV	14361	MVB Bank, Inc.	April 3, 2020
1	Ericson State Bank	Ericson	NE	18265	Farmers and Merchants Bank	February 14, 2020
2	City National Bank of New Jersey	Newark	NJ	21111	Industrial Bank	November 1, 2019
3	Resolute Bank	Maumee	OH	58317	Buckeye State Bank	October 25, 2019
4	Louisa Community Bank	Louisa	KY	58112	Kentucky Farmers Bank Corporation	October 25, 2019
...	...	...	...	...	...	...
556	Superior Bank, FSB	Hinsdale	IL	32646	Superior Federal, FSB	July 27, 2001
557	Malta National Bank	Malta	OH	6629	North Valley Bank	May 3, 2001
558	First Alliance Bank & Trust Co.	Manchester	NH	34264	Southern New Hampshire Bank & Trust	February 2, 2001
559	National State Bank of Metropolis	Metropolis	IL	3815	Banterra Bank of Marion	December 14, 2000
560	Bank of Honolulu	Honolulu	HI	21029	Bank of the Orient	October 13, 2000
561 rows × 6 columns
```

Input:

```
url_mcc = 'https://en.wikipedia.org/wiki/Mobile_country_code'
dfs = pd.read_html(url_mcc, match='Country', header=0)


type(dfs)#list
dfs[0] #type of dfs[0] is dataframe
```

Output:

```
	Mobile Country Code	Country	ISO 3166	Mobile Network Codes	National MNC authority	Remarks
0	289	A Abkhazia	GE-AB	List of Mobile Network Codes in Abkhasia	NaN	MCC is not listed by ITU
1	412	Afghanistan	AF	List of Mobile Network Codes in Afghanistan	NaN	NaN
2	276	Albania	AL	List of Mobile Network Codes in Albania	NaN	NaN
3	603	Algeria	DZ	List of Mobile Network Codes in Algeria	NaN	NaN
4	544	American Samoa (United States of America)	AS	List of Mobile Network Codes in American Samoa	NaN	NaN
...	...	...	...	...	...	...
247	452	Vietnam	VN	List of Mobile Network Codes in the Vietnam	NaN	NaN
248	543	W Wallis and Futuna	WF	List of Mobile Network Codes in Wallis and Futuna	NaN	NaN
249	421	Y Yemen	YE	List of Mobile Network Codes in the Yemen	NaN	NaN
250	645	Z Zambia	ZM	List of Mobile Network Codes in Zambia	NaN	NaN
251	648	Zimbabwe	ZW	List of Mobile Network Codes in Zimbabwe	NaN	NaN
252 rows × 6 columns
```

### Reading Excel files

```
df_excel=pd.read_excel('https://file-examples.com/wp-content/uploads/2017/02/file_example_XLS_10.xls')

df_excel.head()
```

Output:

```
	0	First Name	Last Name	Gender	Country	Age	Date	Id
0	1	Dulce	Abril	Female	United States	32	15/10/2017	1562
1	2	Mara	Hashimoto	Female	Great Britain	25	16/08/2016	1582
2	3	Philip	Gent	Male	France	36	21/05/2015	2587
3	4	Kathleen	Hanner	Female	United States	25	15/10/2017	3549
4	5	Nereida	Magwood	Female	United States	58	16/08/2016	2468
```

### Pickling

```
df_excel.to_pickle('df_excel')
df=pd.read_pickle('df_excel')

df.head()
```

Output:

```
	0	First Name	Last Name	Gender	Country	Age	Date	Id
0	1	Dulce	Abril	Female	United States	32	15/10/2017	1562
1	2	Mara	Hashimoto	Female	Great Britain	25	16/08/2016	1582
2	3	Philip	Gent	Male	France	36	21/05/2015	2587
3	4	Kathleen	Hanner	Female	United States	25	15/10/2017	3549
4	5	Nereida	Magwood	Female	United States	58	16/08/2016	2468
```

