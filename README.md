# Charitys-Python-Portfolio
This is the portfolio of python that I learn during Bisc 450C :)

## Using Jupyter Notebooks (1 and 2)

```python
%matplotlib inline
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
sns.set(style = "darkgrid")
```


```python
df = pd.read_csv('/home/student/Desktop/classroom/myfiles/notebooks/fortune500.csv')
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue (in millions)</th>
      <th>Profit (in millions)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1955</td>
      <td>1</td>
      <td>General Motors</td>
      <td>9823.5</td>
      <td>806</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue (in millions)</th>
      <th>Profit (in millions)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>25495</td>
      <td>2005</td>
      <td>496</td>
      <td>Wm. Wrigley Jr.</td>
      <td>3648.6</td>
      <td>493</td>
    </tr>
    <tr>
      <td>25496</td>
      <td>2005</td>
      <td>497</td>
      <td>Peabody Energy</td>
      <td>3631.6</td>
      <td>175.4</td>
    </tr>
    <tr>
      <td>25497</td>
      <td>2005</td>
      <td>498</td>
      <td>Wendy's International</td>
      <td>3630.4</td>
      <td>57.8</td>
    </tr>
    <tr>
      <td>25498</td>
      <td>2005</td>
      <td>499</td>
      <td>Kindred Healthcare</td>
      <td>3616.6</td>
      <td>70.6</td>
    </tr>
    <tr>
      <td>25499</td>
      <td>2005</td>
      <td>500</td>
      <td>Cincinnati Financial</td>
      <td>3614.0</td>
      <td>584</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns = ['year', 'rank', 'company', 'revenue', 'profit']
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>rank</th>
      <th>company</th>
      <th>revenue</th>
      <th>profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1955</td>
      <td>1</td>
      <td>General Motors</td>
      <td>9823.5</td>
      <td>806</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
len(df)
```




    25500




```python
df.dtypes
```




    year         int64
    rank         int64
    company     object
    revenue    float64
    profit      object
    dtype: object




```python
non_numeric_profits = df.profit.str.contains('[^0-9.-]')
df.loc[non_numeric_profits].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>rank</th>
      <th>company</th>
      <th>revenue</th>
      <th>profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>228</td>
      <td>1955</td>
      <td>229</td>
      <td>Norton</td>
      <td>135.0</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>290</td>
      <td>1955</td>
      <td>291</td>
      <td>Schlitz Brewing</td>
      <td>100.0</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>294</td>
      <td>1955</td>
      <td>295</td>
      <td>Pacific Vegetable Oil</td>
      <td>97.9</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>296</td>
      <td>1955</td>
      <td>297</td>
      <td>Liebmann Breweries</td>
      <td>96.0</td>
      <td>N.A.</td>
    </tr>
    <tr>
      <td>352</td>
      <td>1955</td>
      <td>353</td>
      <td>Minneapolis-Moline</td>
      <td>77.4</td>
      <td>N.A.</td>
    </tr>
  </tbody>
</table>
</div>




```python
set(df.profit[non_numeric_profits])
```




    {'N.A.'}




```python
len(df.profit[non_numeric_profits])
```




    369




```python
bin_sizes, _, _=plt.hist(df.year[non_numeric_profits], bins= range(1955, 2006) )
```



![download](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/b5fc3756-8cd2-455a-b7cb-6b093f60f382)


```python
df = df.loc[~non_numeric_profits]
df.profit = df.profit.apply(pd.to_numeric)
```


```python
len(df)
```




    25131




```python
df.dtypes
```




    year         int64
    rank         int64
    company     object
    revenue    float64
    profit     float64
    dtype: object




```python
group_by_year = df.loc[:, ['year', 'revenue', 'profit']].groupby('year')
avgs = group_by_year.mean()
x = avgs.index
y1 = avgs.profit
def plot(x, y, ax, title, y_label):
    ax.set_title(title)
    ax.set_ylabel(y_label)
    ax.plot(x, y)
    ax.margins(x = 0, y =0)
```


```python
fig, ax = plt.subplots()
plot(x, y1, ax, 'Increase in mean Fortune 500 company profits from 1955 to 2005','Profit (millions)')
```


![output_16_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/21234688-f3d2-4fb8-9348-0ba8742e22fc)



```python
y2 = avgs.revenue
fig, ax = plt. subplots()
plot(x, y2, ax, 'Increase in mean Fortune 500 company revenues from 1955 to 2005', 'Revenue (millions)')
```


![output_17_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/374d83eb-2a9a-4c78-abad-060654f422c4)



```python
def plot_with_std(x, y, stds, ax, title, y_label):
    ax.fill_between(x, y - stds, y + stds, alpha = 0.2)
    plot(x, y, ax, title, y_label)
fig, (ax1, ax2) = plt.subplots(ncols=2)
title = 'Increase in mean and std Fortune 500 company %s from 1955 to 2005'
stds1 = group_by_year.std().profit.values
stds2 = group_by_year.std().revenue.values
plot_with_std(x, y1.values, stds1, ax1, title % 'profits', 'Profits (millions)' )
plot_with_std(x, y2.values, stds2, ax2, title % 'revenues', 'Revenue (millions)')
fig.set_size_inches(14,4)
fig.tight_layout()

```


![output_18_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/2da16979-2a27-4a0a-9755-c1bd1c457df1)



```python

```

## Python Fundamentals

```python
# Any python interpreter can be used as a calculator:
3 + 5 * 4
```




    23




```python
# Lets save a value to a variable
weight_kg = 60
```


```python
print (weight_kg)
```

    60



```python
# Weight0 = valud
# 0weight = invalid
# weight and Weight are different
```


```python
# Types of data
# There are three common types of data
# Integer numbers
# floating point numbers
# Strings
```


```python
weight_kg = 60.3
```


```python
# String comprised of letters
patient_name = "Jon Smith"
```


```python
# String comprised of numbers
patient_id = '001'
```


```python
# Use variables in python

weight_lb = 2.2 * weight_kg

print(weight_lb)
```

    132.66



```python
# Lets add a prefix to our patient id

patient_id = 'inflam_' + patient_id

print(patient_id)
```

    inflam_001



```python
# Let combine print statements

print(patient_id, 'weight in kilograms:', weight_kg)
```

    inflam_001 weight in kilograms: 60.3



```python
# we can call a funtion inside another function

print(type(60.3))

print(type(patient_id))
```

    <class 'float'>
    <class 'str'>



```python
# We can also do calculations inside the print function

print('weight in lbs:', 2.2 * weight_kg)
```

    weight in lbs: 132.66



```python
print(weight_kg)
```

    60.3



```python
weight_kg = 65.0
print('weight in kilograms is now:', weight_kg)
```

    weight in kilograms is now: 65.0







## Analyzing Patient Data Part (1 and 2) 

In this analysis, we looked at inflammation data for multiple patients.
```python
import numpy
```


```python
numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')

```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')

```


```python
print(data)
```

    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]



```python
print(type(data))
```

    <class 'numpy.ndarray'>



```python
print(data.shape)
```

    (60, 40)



```python
print('firt value in data:', data[0,0])
```

    firt value in data: 0.0



```python
print('middle value in data:',data[29,19])
```

    middle value in data: 16.0



```python
print(data[0:4, 0:10])
```

    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]



```python
print(data[5:10, 0:10])
```

    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]



```python
small = data[:3, 36:]
```


```python
print('small is:')
```

    small is:



```python
print(small)
```

    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]



```python
# lets us a numpy function
print(numpy.mean(data))
```

    6.14875



```python
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
print('maximum inflammation:', maxval)
print('minimum inflammation:', minval)
print('standard deviation:', stdval)
```

    maximum inflammation: 20.0
    minimum inflammation: 0.0
    standard deviation: 4.613833197118566



```python
# somtims we want to look at variation in statistical values, such as maximum inflammation per patient,
# or average from day one.

patient_0 = data[0, :] # 0 on the first axis (rows), everthing on the second (columns) 

print('maximum inflammation for patient 0:', numpy.amax(patient_0))
```

    maximum inflammation for patient 0: 18.0



```python
print('maximum inflammation for patient 2:', numpy.amax(data[2,:]))
```

    maximum inflammation for patient 2: 19.0



```python
print(numpy.mean(data, axis = 0))
```

    [ 0.          0.45        1.11666667  1.75        2.43333333  3.15
      3.8         3.88333333  5.23333333  5.51666667  5.95        5.9
      8.35        7.73333333  8.36666667  9.5         9.58333333 10.63333333
     11.56666667 12.35       13.25       11.96666667 11.03333333 10.16666667
     10.          8.66666667  9.15        7.25        7.33333333  6.58333333
      6.06666667  5.95        5.11666667  3.6         3.3         3.56666667
      2.48333333  1.5         1.13333333  0.56666667]



```python
print(numpy.mean(data, axis = 0).shape)
```

    (40,)



```python
print(numpy.mean(data, axis = 1))
```

    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]


## Analyzing Patient Data Part (3)

```python
import numpy
data = numpy.loadtxt(fname= 'inflammation-01.csv', delimiter = ',')
```


```python
import matplotlib.pyplot
image = matplotlib.pyplot.imshow(data)
matplotlib.pyplot.show()
```


![output_1_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/3ddae792-5cb4-46f7-ab9b-3de28b53de11)


```python
# Average inflammation over time

ave_inflammation = numpy.mean(data, axis = 0)
ave_plot = matplotlib.pyplot.plot(ave_inflammation)
matplotlib.pyplot.show()
```


![output_2_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/3d5a9839-59b9-4cd7-a8c2-bd80bbe4a704)



```python
max_plot = matplotlib.pyplot.plot(numpy.amax(data, axis = 0))
matplotlib.pyplot.show()
```


![output_3_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/84551449-e845-4c77-98e8-48fdfd0d0f97)



```python
min_plot = matplotlib.pyplot.plot(numpy.amin(data, axis = 0))
matplotlib.pyplot.show()
```


![output_4_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/d6c9b64d-7c09-47f8-91b4-1a7eb79ce5e0)




```python
fig = matplotlib.pyplot.figure(figsize =(10.0, 3.0))

axes1 = fig.add_subplot(1, 3, 1)
axes2 = fig.add_subplot(1, 3, 2)
axes3 = fig.add_subplot(1, 3, 3)

axes1.set_ylabel('average')
axes1.plot(numpy.mean(data, axis = 0))

axes2.set_ylabel('max')
axes2.plot(numpy.amax(data, axis = 0))

axes3.set_ylabel('min')
axes3.plot(numpy.amin(data, axis = 0))

fig.tight_layout()

matplotlib.pyplot.savefig('inflammation.png')
matplotlib.pyplot.show()
```


![output_5_0](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/9c872d97-f1fd-4922-a29e-244299e95101)





## Storing Values in Lists
```python
odds = [1, 3, 5, 7]
print('odds are:', odds)
```

    odds are: [1, 3, 5, 7]



```python
print('first element:', odds[0])
print('last element:', odds[3])
print('"-1" element:', odds[-1])

```

    first element: 1
    last element: 7
    "-1" element: 7



```python
names = ['Curie', 'Darwing', 'Turing'] # typo in Darwin's name

print('names is originally:', names)

names[1] = 'Darwin' # Correct the name

print('final value of names:', names)
```

    names is originally: ['Curie', 'Darwing', 'Turing']
    final value of names: ['Curie', 'Darwin', 'Turing']



```python
#name = 'Darwin'
#name[0] = 'd'
```


```python
odds.append(11)
print('odds after adding a value:', odds)
```

    odds after adding a value: [1, 3, 5, 7, 11]



```python
removed_element = odds.pop(0)
print('odds after removing the first element:', odds)
print('remove_element:', removed_element)
```

    odds after removing the first element: [3, 5, 7, 11]
    remove_element: 1



```python
odds.reverse()
print('odds after reversing:', odds)
```

    odds after reversing: [11, 7, 5, 3]



```python
odds = [3,5,7]
primes = odds
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```

    primes: [3, 5, 7, 2]
    odds: [3, 5, 7, 2]



```python
odds = [3,5,7]
primes = list(odds)
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```

    primes: [3, 5, 7, 2]
    odds: [3, 5, 7]



```python
binomial_name = 'Drosophila melanogaster'
group = binomial_name[0:10]
print('group:', group)

species = binomial_name[11:23]
print('species:', species)

chromosomes = ['X', 'Y', '2', '3', '4']
autosomes = chromosomes[2:5]
print('autosomes:', autosomes)

last = chromosomes[-1]
print('last:', last)
```

    group: Drosophila
    species: melanogaster
    autosomes: ['2', '3', '4']
    last: 4



```python
date = 'Monday 4 January 2016'
day = date[0:6]
print('Using 0 to begin range:', day)
day = date[:6]
print('Omitting beginning index:', day)
```

    Using 0 to begin range: Monday
    Omitting beginning index: Monday



```python
months = ['jan', 'feb', 'mar', 'apr', 'may', 'jun', 'jul', 'aug', 'sep', 'oct', 'nov', 'dec']
sond = months[8:12]
print('With known last position:', sond)
sond = months[8:len(months)]
print('Using len() to get last entry:', sond)
sond = months[8:]
print('Omitting ending index:', sond)
```

    With known last position: ['sep', 'oct', 'nov', 'dec']
    Using len() to get last entry: ['sep', 'oct', 'nov', 'dec']
    Omitting ending index: ['sep', 'oct', 'nov', 'dec']


## Using Loops

```python
odds = [1, 3, 5, 7]
```


```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5
    7



```python
odds = [1, 3, 5]
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-3-b48c9fadc7bf> in <module>
          3 print(odds[1])
          4 print(odds[2])
    ----> 5 print(odds[3])
    

    IndexError: list index out of range



```python
odds = [1, 3, 5, 7]
for num in odds:
    print(num)
```


```python
odds = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
for num in odds:
    print(num)
```


```python
length = 0
names = ['Curie', 'Darwin', 'Turning']
for variable in names:
    length = length + 1 
print('There are', length, 'names in the list.')    
```


```python
name = "Rosalind"
for name in ['Curie', 'Darwin', 'Turing']:
    print(name)
print('after the loop, name is', name)    
```


```python
print(len([0,1,2,3]))
```


```python
name = ['Curie', 'Darwin', 'Turing']
print(len(name))
```


## Using Multiple Files

```python
import glob
```


```python
print(glob.glob('inflammation*.csv'))
```

    ['inflammation-05.csv', 'inflammation-12.csv', 'inflammation-04.csv', 'inflammation-08.csv', 'inflammation-10.csv', 'inflammation-06.csv', 'inflammation-09.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-11.csv', 'inflammation-03.csv', 'inflammation-02.csv']



```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]
for filename in filenames:
    print(filename)

    data = numpy.loadtxt(fname=filename, delimiter=',')

    fig = matplotlib.pyplot.figure(figsize=(10.0, 3.0))

    axes1 = fig.add_subplot(1, 3, 1)
    axes2 = fig.add_subplot(1, 3, 2)
    axes3 = fig.add_subplot(1, 3, 3)

    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis=0))

    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis=0))

    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis=0))

    fig.tight_layout()
    matplotlib.pyplot.show()
```

   ![output_2_1](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/ea241a8b-c950-473e-b9da-996422cca119)





   ![output_2_3](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/a1feaff5-ae62-4d63-ad3b-ec2ccfe8eeab)





 ![output_2_5](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/8a4b1952-53ed-43d9-8867-4b2b02d6962b)






## Making Choices
```python
import numpy
```


```python
data = numpy.loadtxt(fname='inflammation-01.csv', delimiter=',')

```


```python
max_inflammation_0 = numpy.amax(data, axis=0)[0]

```


```python
max_inflammation_20 = numpy.amax(data, axis=0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('saspictious looking maxima!')
```

    saspictious looking maxima!



```python
max_inflammation_20 = numpy.amax(data, axis=0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
     print('saspictious looking maxima!')
        
elif numpy.sum(numpy.amin(data, axis=0)) == 0:
    print('Minima add up to zero!')
    
else:
        print('Seems OK!')
        
```

    saspictious looking maxima!



```python
data = numpy.loadtxt(fname='inflammation-03.csv', delimiter=',')

max_inflammation_0 = numpy.amax(data, axis=0)[0]

max_inflammation_20 = numpy.amax(data, axis=0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
     print('saspictious looking maxima!')
elif numpy.sum(numpy.amin(data, axis=0)) == 0:
    print('Minima add up to zero! -> HEALTHY PARTICIPANT ALERT!')        

else:
        print('Seems OK!')
```

    Minima add up to zero! -> HEALTHY PARTICIPANT ALERT!


## Functions Part 1 and 2

```python
import numpy
import matplotlib
import matplotlib.pyplot
import glob
```


```python
def visualize(filename):

    data = numpy.loadtxt(fname=filename, delimiter=',')

    fig = matplotlib.pyplot.figure(figsize=(10.0, 3.0))

    axes1 = fig.add_subplot(1, 3, 1)
    axes2 = fig.add_subplot(1, 3, 2)
    axes3 = fig.add_subplot(1, 3, 3)

    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis=0))

    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis=0))

    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis=0))

    fig.tight_layout()
    matplotlib.pyplot.show()
```


```python
def detect_problems(filename):

    data = numpy.loadtxt(fname=filename, delimiter=',')

    if numpy.amax(data, axis=0)[0] == 0 and numpy.amax(data, axis=0)[20] == 20:
        print('Suspicious looking maxima!')
    elif numpy.sum(numpy.amin(data, axis=0)) == 0:
        print('Minima add up to zero!')
    else:
        print('Seems OK!')
```


```python
filenames = sorted(glob.glob('inflammation*.csv'))

for filename in filenames[:3]:
    print(filename)
    visualize(filename)
    detect_problems(filename)
```

    inflammation-01.csv



![output_3_1](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/3d50af8f-fbd7-428b-aa22-6817b8907694)


    Suspicious looking maxima!
    inflammation-02.csv



![output_3_3](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/8a207c8e-a676-44b3-87fa-a6acb0ed3cb7)



    Suspicious looking maxima!
    inflammation-03.csv



![output_3_5](https://github.com/Charity-Scott/Python-Portfolio/assets/134242562/ba0ce017-8500-4e80-aed9-bcfb95be6f21)


    Minima add up to zero!



## Functions Part 3
```python
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
z = numpy.zeros((2,2))
print(offset_mean(z, 3))
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-2-d85844a15494> in <module>
    ----> 1 z = numpy.zeros((2,2))
          2 print(offset_mean(z, 3))


    NameError: name 'numpy' is not defined



```python
import numpy

```


```python
data = numpy.loadtxt(fname='inflammation-01.csv', delimiter=',')
print(offset_mean(data, 0))
```


```python
print('original min, mean, and max are:', numpy.amin(data), numpy.mean(data), numpy.amax(data))
offset_data = offset_mean(data, 0)
print('min, mean, and max of offset data are:',
      numpy.amin(offset_data),
      numpy.mean(offset_data),
      numpy.amax(offset_data))
```


```python
print('std dev before and after:', numpy.std(data), numpy.std(offset_data))
```


```python
print('difference in standard deviations before and after:',
      numpy.std(data) - numpy.std(offset_data))
```


```python
# offset_mean(data, target_mean_value):
# return a new array containing the original data with its mean offset to match the desired value.
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data
       with its mean offset to match the desired value."""
    return (data - numpy.mean(data)) + target_mean_value
```


```python
help(offset_mean)
```


```python
def offset_mean(data, target_mean_value):
    """Return a new array containing the original data
       with its mean offset to match the desired value.

    Examples
    --------
    >>> offset_mean([1, 2, 3], 0)
    array([-1.,  0.,  1.])
    """
    return (data - numpy.mean(data)) + target_mean_value

help(offset_mean)
```



## functions Part 4

```python
import numpy

```


```python
numpy.loadtxt('inflammation-01.csv', delimiter=',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
def offset_mean(data, target_mean_value=0.0):
    """Return a new array containing the original data
       with its mean offset to match the desired value, (0 by default).

    Examples
    --------
    >>> offset_mean([1, 2, 3])
    array([-1.,  0.,  1.])
    """
    return (data - numpy.mean(data)) + target_mean_value
```


```python
test_data = numpy.zeros((2, 2))
print(offset_mean(test_data, 3))
```

    [[3. 3.]
     [3. 3.]]



```python
more_data = 5 + numpy.zeros((2, 2))
print('data before mean offset:')
print(more_data)
print('offset data:')
print(offset_mean(more_data))
```

    data before mean offset:
    [[5. 5.]
     [5. 5.]]
    offset data:
    [[0. 0.]
     [0. 0.]]



```python
def display(a=1, b=2, c=3):
    print('a:', a, 'b:', b, 'c:', c)

print('no parameters:')
display()
print('one parameter:')
display(55)
print('two parameters:')
display(55, 66)
```

    no parameters:
    a: 1 b: 2 c: 3
    one parameter:
    a: 55 b: 2 c: 3
    two parameters:
    a: 55 b: 66 c: 3



```python
print('only setting the value of c')
display(c=77)
```

    only setting the value of c
    a: 1 b: 2 c: 77



```python
help(numpy.loadtxt)
```

    Help on function loadtxt in module numpy:
    
    loadtxt(fname, dtype=<class 'float'>, comments='#', delimiter=None, converters=None, skiprows=0, usecols=None, unpack=False, ndmin=0, encoding='bytes', max_rows=None)
        Load data from a text file.
        
        Each row in the text file must have the same number of values.
        
        Parameters
        ----------
        fname : file, str, or pathlib.Path
            File, filename, or generator to read.  If the filename extension is
            ``.gz`` or ``.bz2``, the file is first decompressed. Note that
            generators should return byte strings for Python 3k.
        dtype : data-type, optional
            Data-type of the resulting array; default: float.  If this is a
            structured data-type, the resulting array will be 1-dimensional, and
            each row will be interpreted as an element of the array.  In this
            case, the number of columns used must match the number of fields in
            the data-type.
        comments : str or sequence of str, optional
            The characters or list of characters used to indicate the start of a
            comment. None implies no comments. For backwards compatibility, byte
            strings will be decoded as 'latin1'. The default is '#'.
        delimiter : str, optional
            The string used to separate values. For backwards compatibility, byte
            strings will be decoded as 'latin1'. The default is whitespace.
        converters : dict, optional
            A dictionary mapping column number to a function that will parse the
            column string into the desired value.  E.g., if column 0 is a date
            string: ``converters = {0: datestr2num}``.  Converters can also be
            used to provide a default value for missing data (but see also
            `genfromtxt`): ``converters = {3: lambda s: float(s.strip() or 0)}``.
            Default: None.
        skiprows : int, optional
            Skip the first `skiprows` lines, including comments; default: 0.
        usecols : int or sequence, optional
            Which columns to read, with 0 being the first. For example,
            ``usecols = (1,4,5)`` will extract the 2nd, 5th and 6th columns.
            The default, None, results in all columns being read.
        
            .. versionchanged:: 1.11.0
                When a single column has to be read it is possible to use
                an integer instead of a tuple. E.g ``usecols = 3`` reads the
                fourth column the same way as ``usecols = (3,)`` would.
        unpack : bool, optional
            If True, the returned array is transposed, so that arguments may be
            unpacked using ``x, y, z = loadtxt(...)``.  When used with a structured
            data-type, arrays are returned for each field.  Default is False.
        ndmin : int, optional
            The returned array will have at least `ndmin` dimensions.
            Otherwise mono-dimensional axes will be squeezed.
            Legal values: 0 (default), 1 or 2.
        
            .. versionadded:: 1.6.0
        encoding : str, optional
            Encoding used to decode the inputfile. Does not apply to input streams.
            The special value 'bytes' enables backward compatibility workarounds
            that ensures you receive byte arrays as results if possible and passes
            'latin1' encoded strings to converters. Override this value to receive
            unicode arrays and pass strings as input to converters.  If set to None
            the system default is used. The default value is 'bytes'.
        
            .. versionadded:: 1.14.0
        max_rows : int, optional
            Read `max_rows` lines of content after `skiprows` lines. The default
            is to read all the lines.
        
            .. versionadded:: 1.16.0
        
        Returns
        -------
        out : ndarray
            Data read from the text file.
        
        See Also
        --------
        load, fromstring, fromregex
        genfromtxt : Load data with missing values handled as specified.
        scipy.io.loadmat : reads MATLAB data files
        
        Notes
        -----
        This function aims to be a fast reader for simply formatted files.  The
        `genfromtxt` function provides more sophisticated handling of, e.g.,
        lines with missing values.
        
        .. versionadded:: 1.10.0
        
        The strings produced by the Python float.hex method can be used as
        input for floats.
        
        Examples
        --------
        >>> from io import StringIO   # StringIO behaves like a file object
        >>> c = StringIO(u"0 1\n2 3")
        >>> np.loadtxt(c)
        array([[0., 1.],
               [2., 3.]])
        
        >>> d = StringIO(u"M 21 72\nF 35 58")
        >>> np.loadtxt(d, dtype={'names': ('gender', 'age', 'weight'),
        ...                      'formats': ('S1', 'i4', 'f4')})
        array([(b'M', 21, 72.), (b'F', 35, 58.)],
              dtype=[('gender', 'S1'), ('age', '<i4'), ('weight', '<f4')])
        
        >>> c = StringIO(u"1,0,2\n3,0,4")
        >>> x, y = np.loadtxt(c, delimiter=',', usecols=(0, 2), unpack=True)
        >>> x
        array([1., 3.])
        >>> y
        array([2., 4.])
    




## Defensive Programming

```python
numbers = [1.5, 2.3, 0.7, 0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive values'
    total += num
print('total is:', total)
```

    total is: 8.901



```python
def normalize_rectangle(rect):
    """Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis.
    Input should be of the format (x0, y0, x1, y1).
    (x0, y0) and (x1, y1) define the lower left and upper right corners
    of the rectangle, respectively."""
    assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'

    dx = x1 - x0
    dy = y1 - y0
    if dx > dy:
        scaled = dy / dx
        upper_x, upper_y = 1.0, scaled
    else:
        scaled = dx / dy
        upper_x, upper_y = scaled, 1.0

    assert 0 < upper_x <= 1.0, 'Calculated upper X coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper Y coordinate invalid'

    return (0, 0, upper_x, upper_y)
```


```python
 print(normalize_rectangle( (0.0, 1.0, 2.0, 5.0) ))
```

    (0, 0, 0.5, 1.0)



```python
print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0) ))
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-7-f7e0d48bdfd0> in <module>
    ----> 1 print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0) ))
    

    <ipython-input-3-cd70c9fa4ab2> in normalize_rectangle(rect)
          6     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          7     x0, y0, x1, y1 = rect
    ----> 8     assert x0 < x1, 'Invalid X coordinates'
          9     assert y0 < y1, 'Invalid Y coordinates'
         10 


    AssertionError: Invalid X coordinates



```python
print(normalize_rectangle( (0.0, 0.0, 1.0, 5.0) ))
```


```python
print(normalize_rectangle( (0.0, 0.0, 5.0, 1.0) ))
```

## Transcribing DNA into RNA

```python
# Prompt the user to enter the input fasta file name

input_file_name = input("Enter the name of the input fasta file: ")

```

    Enter the name of the input fasta file:  BUB1.txt



```python
# Open the input fasta file and read the DNA sequence

with open(input_file_name, "r") as input_file:
    dna_sequence = ""
    for line in input_file:
        if line.startswith(">"): 
            continue
        dna_sequence += line.strip()

```


```python
# Transcribe the DNA to RNA
rna_sequence = ""
for nucleotide in dna_sequence:
    if nucleotide == "T":
        rna_sequence += "U"
    else:
        rna_sequence += nucleotide
```


```python
# Promt the user to enter the output file name

output_file_name = input("Enter the name of the output file: ")
```

    Enter the name of the output file:  BUB1_RNA.txt



```python
# Save the RNA sequence to a text file
with open(output_file_name, "w") as output_file:
    output_file.write(rna_sequence)
    print("the RNA sequence has been saved to {output_file_name}")
```

    the RNA sequence has been saved to {output_file_name}



```python
print(rna_sequence)
```

    AUGGCGGCGGUGAAGAAGGAAGGGGGUGCUCUGAGUGAAGCCAUGUCCCUGGAGGGAGAUGAAUGGGAACUGAGUAAAGAAAAUGUACAACCUUUAAGGCAAGGGCGGAUCAUGUCCACGCUUCAGGGAGCACUGGCACAAGAAUCUGCCUGUAACAAUACUCUUCAGCAGCAGAAACGGGCAUUUGAAUAUGAAAUUCGAUUUUACACUGGAAAUGACCCUCUGGAUGUUUGGGAUAGGUAUAUCAGCUGGACAGAGCAGAACUAUCCUCAAGGUGGGAAGGAGAGUAAUAUGUCAACGUUAUUAGAAAGAGCUGUAGAAGCACUACAAGGAGAAAAACGAUAUUAUAGUGAUCCUCGAUUUCUCAAUCUCUGGCUUAAAUUAGGGCGUUUAUGCAAUGAGCCUUUGGAUAUGUACAGUUACUUGCACAACCAAGGGAUUGGUGUUUCACUUGCUCAGUUCUAUAUCUCAUGGGCAGAAGAAUAUGAAGCUAGAGAAAACUUUAGGAAAGCAGAUGCGAUAUUUCAGGAAGGGAUUCAACAGAAGGCUGAACCACUAGAAAGACUACAGUCCCAGCACCGACAAUUCCAAGCUCGAGUGUCUCGGCAAACUCUGUUGGCACUUGAGAAAGAAGAAGAGGAGGAAGUUUUUGAGUCUUCUGUACCACAACGAAGCACACUAGCUGAACUAAAGAGCAAAGGGAAAAAGACAGCAAGAGCUCCAAUCAUCCGUGUAGGAGGUGCUCUCAAGGCUCCAAGCCAGAACAGAGGACUCCAAAAUCCAUUUCCUCAACAGAUGCAAAAUAAUAGUAGAAUUACUGUUUUUGAUGAAAAUGCUGAUGAGGCUUCUACAGCAGAGUUGUCUAAGCCUACAGUCCAGCCAUGGAUAGCACCCCCCAUGCCCAGGGCCAAAGAGAAUGAGCUGCAAGCAGGCCCUUGGAACACAGGCAGGUCCUUGGAACACAGGCCUCGUGGCAAUACAGCUUCACUGAUAGCUGUACCCGCUGUGCUUCCCAGUUUCACUCCAUAUGUGGAAGAGACUGCACGACAGCCAGUUAUGACACCAUGUAAAAUUGAACCUAGUAUAAACCACAUCCUAAGCACCAGAAAGCCUGGAAAGGAAGAAGGAGAUCCUCUACAAAGGGUUCAGAGCCAUCAGCAAGCGUCUGAGGAGAAGAAAGAGAAGAUGAUGUAUUGUAAGGAGAAGAUUUAUGCAGGAGUAGGGGAAUUCUCCUUUGAAGAAAUUCGGGCUGAAGUUUUCCGGAAGAAAUUAAAAGAGCAAAGGGAAGCCGAGCUAUUGACCAGUGCAGAGAAGAGAGCAGAAAUGCAGAAACAGAUUGAAGAGAUGGAGAAGAAGCUAAAAGAAAUCCAAACUACUCAGCAAGAAAGAACAGGUGAUCAGCAAGAAGAGACGAUGCCUACAAAGGAGACAACUAAACUGCAAAUUGCUUCCGAGUCUCAGAAAAUACCAGGAAUGACUCUAUCCAGUUCUGUUUGUCAAGUAAACUGUUGUGCCAGAGAAACUUCACUUGCGGAGAACAUUUGGCAGGAACAACCUCAUUCUAAAGGUCCCAGUGUACCUUUCUCCAUUUUUGAUGAGUUUCUUCUUUCAGAAAAGAAGAAUAAAAGUCCUCCUGCAGAUCCCCCACGAGUUUUAGCUCAACGAAGACCCCUUGCAGUUCUCAAAACCUCAGAAAGCAUCACCUCAAAUGAAGAUGUGUCUCCAGAUGUUUGUGAUGAAUUUACAGGAAUUGAACCCUUGAGCGAGGAUGCCAUUAUCACAGGCUUCAGAAAUGUAACAAUUUGUCCUAACCCAGAAGACACUUGUGACUUUGCCAGAGCAGCUCGUUUUGUAUCCACUCCUUUUCAUGAGAUAAUGUCCUUGAAGGAUCUCCCUUCUGAUCCUGAGAGACUGUUACCGGAAGAAGAUCUAGAUGUAAAGACCUCUGAGGACCAGCAGACAGCUUGUGGCACUAUCUACAGUCAGACUCUCAGCAUCAAGAAGCUGAGCCCAAUUAUUGAAGACAGUCGUGAAGCCACACACUCCUCUGGCUUCUCUGGUUCUUCUGCCUCGGUUGCAAGCACCUCCUCCAUCAAAUGUCUUCAAAUUCCUGAGAAACUAGAACUUACUAAUGAGACUUCAGAAAACCCUACUCAGUCACCAUGGUGUUCACAGUAUCGCAGACAGCUACUGAAGUCCCUACCAGAGUUAAGUGCCUCUGCAGAGUUGUGUAUAGAAGACAGACCAAUGCCUAAGUUGGAAAUUGAGAAGGAAAUUGAAUUAGGUAAUGAGGAUUACUGCAUUAAACGAGAAUACCUAAUAUGUGAAGAUUACAAGUUAUUCUGGGUGGCGCCAAGAAACUCUGCAGAAUUAACAGUAAUAAAGGUAUCUUCUCAACCUGUCCCAUGGGACUUUUAUAUCAACCUCAAGUUAAAGGAACGUUUAAAUGAAGAUUUUGAUCAUUUUUGCAGCUGUUAUCAAUAUCAAGAUGGCUGUAUUGUUUGGCACCAAUAUAUAAACUGCUUCACCCUUCAGGAUCUUCUCCAACACAGUGAAUAUAUUACCCAUGAAAUAACAGUGUUGAUUAUUUAUAACCUUUUGACAAUAGUGGAGAUGCUACACAAAGCAGAAAUAGUCCAUGGUGACUUGAGUCCAAGGUGUCUGAUUCUCAGAAACAGAAUCCACGAUCCCUAUGAUUGUAACAAGAACAAUCAAGCUUUGAAGAUAGUGGACUUUUCCUACAGUGUUGACCUUAGGGUGCAGCUGGAUGUUUUUACCCUCAGCGGCUUUCGGACUGUACAGAUCCUGGAAGGACAAAAGAUCCUGGCUAACUGUUCUUCUCCCUACCAGGUAGACCUGUUUGGUAUAGCAGAUUUAGCACAUUUACUAUUGUUCAAGGAACACCUACAGGUCUUCUGGGAUGGGUCCUUCUGGAAACUUAGCCAAAAUAUUUCUGAGCUAAAAGAUGGUGAAUUGUGGAAUAAAUUCUUUGUGCGGAUUCUGAAUGCCAAUGAUGAGGCCACAGUGUCUGUUCUUGGGGAGCUUGCAGCAGAAAUGAAUGGGGUUUUUGACACUACAUUCCAAAGUCACCUGAACAAAGCCUUAUGGAAGGUAGGGAAGUUAACUAGUCCUGGGGCUUUGCUCUUUCAGUGA




## Translating RNA into Protein

```python
# Prompt the user to enter the input RNA file name

input_file_name = input("Enter the name of the input RNA file:")

```

    Enter the name of the input RNA file: BUB1_RNA.txt



```python
# Open the input RNA file and read the RNA sequence

with open(input_file_name, "r") as input_file:
    rna_sequence = input_file.read().strip()
```


```python
# Define the codon table

codon_table = {
    "UUU": "F", "UUC": "F", "UUA": "L", "UUG": "L",
    "CUU": "L", "CUC": "L", "CUA": "L", "CUG": "L",
    "AUU": "I", "AUC": "I", "AUA": "I", "AUG": "M",
    "GUU": "V", "GUC": "V", "GUA": "V", "GUG": "V",
    "UCU": "S", "UCC": "S", "UCA": "S", "UCG": "S",
    "CCU": "P", "CCC": "P", "CCA": "P", "CCG": "P",
    "ACU": "T", "ACC": "T", "ACA": "T", "ACG": "T",
    "GCU": "A", "GCC": "A", "GCA": "A", "GCG": "A",
    "UAU": "Y", "UAC": "Y", "UAA": "*", "UAG": "*",
    "CAU": "H", "CAC": "H", "CAA": "Q", "CAG": "Q",
    "AAU": "N", "AAC": "N", "AAA": "K", "AAG": "K",
    "GAU": "D", "GAC": "D", "GAA": "E", "GAG": "E",
    "UGU": "C", "UGC": "C", "UGA": "*", "UGG": "W",
    "CGU": "R", "CGC": "R", "CGA": "R", "CGG": "R",
    "AGU": "S", "AGC": "S", "AGA": "R", "AGG": "R",
    "GGU": "G", "GGC": "G", "GGA": "G", "GGG": "G",
}
```


```python
# Translate RNA to protein

protein_sequence = " "
for i in range(0, len(rna_sequence), 3):
    codon = rna_sequence[i:i+3]
    if len(codon) == 3:
        amino_acid = codon_table[codon]
        if amino_acid == "*":
            break
        protein_sequence += amino_acid    
```


```python
# Prompt the user to enter the output file name

output_file_name = input("Enter the name of the output file: ")

```

    Enter the name of the output file:  BUB1_Protein.txt



```python
# Save the protein sequence to a text file

with open(output_file_name, "w") as output_file:
    output_file.write(protein_sequence)
    print(f"The protein sequence has been saved to {output_file_name}" )
```

    The protein sequence has been saved to BUB1_Protein.txt



```python
print(protein_sequence)
```

     MAAVKKEGGALSEAMSLEGDEWELSKENVQPLRQGRIMSTLQGALAQESACNNTLQQQKRAFEYEIRFYTGNDPLDVWDRYISWTEQNYPQGGKESNMSTLLERAVEALQGEKRYYSDPRFLNLWLKLGRLCNEPLDMYSYLHNQGIGVSLAQFYISWAEEYEARENFRKADAIFQEGIQQKAEPLERLQSQHRQFQARVSRQTLLALEKEEEEEVFESSVPQRSTLAELKSKGKKTARAPIIRVGGALKAPSQNRGLQNPFPQQMQNNSRITVFDENADEASTAELSKPTVQPWIAPPMPRAKENELQAGPWNTGRSLEHRPRGNTASLIAVPAVLPSFTPYVEETARQPVMTPCKIEPSINHILSTRKPGKEEGDPLQRVQSHQQASEEKKEKMMYCKEKIYAGVGEFSFEEIRAEVFRKKLKEQREAELLTSAEKRAEMQKQIEEMEKKLKEIQTTQQERTGDQQEETMPTKETTKLQIASESQKIPGMTLSSSVCQVNCCARETSLAENIWQEQPHSKGPSVPFSIFDEFLLSEKKNKSPPADPPRVLAQRRPLAVLKTSESITSNEDVSPDVCDEFTGIEPLSEDAIITGFRNVTICPNPEDTCDFARAARFVSTPFHEIMSLKDLPSDPERLLPEEDLDVKTSEDQQTACGTIYSQTLSIKKLSPIIEDSREATHSSGFSGSSASVASTSSIKCLQIPEKLELTNETSENPTQSPWCSQYRRQLLKSLPELSASAELCIEDRPMPKLEIEKEIELGNEDYCIKREYLICEDYKLFWVAPRNSAELTVIKVSSQPVPWDFYINLKLKERLNEDFDHFCSCYQYQDGCIVWHQYINCFTLQDLLQHSEYITHEITVLIIYNLLTIVEMLHKAEIVHGDLSPRCLILRNRIHDPYDCNKNNQALKIVDFSYSVDLRVQLDVFTLSGFRTVQILEGQKILANCSSPYQVDLFGIADLAHLLLFKEHLQVFWDGSFWKLSQNISELKDGELWNKFFVRILNANDEATVSVLGELAAEMNGVFDTTFQSHLNKALWKVGKLTSPGALLFQ


