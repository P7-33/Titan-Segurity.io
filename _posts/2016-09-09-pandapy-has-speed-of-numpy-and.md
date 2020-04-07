---
title: 'PandaPy has the speed of NumPy and the usability of Pandas'
date: 2020-01-25T01:35:00+01:00
draft: false
---

[](https://github.com/firmai/pandapy#pandapy)PandaPy
----------------------------------------------------

**Install**

```
!pip3 install pandapy 
```

**Load**

#### [](https://github.com/firmai/pandapy#why-pandapy)Why PandaPy?

1.  Maintains the full functionality and speed of structured NumPy datatype (eg., `array[col1] + array[col2], or np.log(array[col1]`)
2.  Provides wrapper functions over NumPy to give you the usability of Pandas (eg., `pp.group(array, [col1, col2, col2], ['mean', 'std'], ['Adj_Close','Close'])`
3.  If you need Pandas for speciality functions, you can easily `df = pp.pandas(array)` and back `array = pp.structured(df)`
4.  For simple calculations (i.e, plus, mult, log) PandaPy is 25x - 80x faster than Pandas.
5.  For table functions (i.e., group, pivot, drop, concat, fillna) PandaPy is 5x - 100x times faster than Pandas.
6.  For most use cases, PandaPy is faster than Dask, Modin Ray and Pandas.
7.  The best competing python package for performance on table functions is [datatable](https://github.com/h2oai/datatable), it is 2x - 10x faster than PandaPy.
8.  The problem is that datatable is 5x - 10x slower with simple calculations (plus, mult, returns), it is less intuitive, does not have a large range of functions, have very few complementary libraries, e.g. matplotlib, and doesn't leave you in a Numpy datatype.
9.  For finance applications the speed of simple calculations takes preference over table function speed.
10.  PandaPy is not created to allow you to scale up to clusters for multiple computer processing like Dask, Modin, and Spark, instead it is focused on speed and usability within a single computer's Memory.
11.  Machines are getting large, EC2 X1 has 2TB of RAM and is remarkably affordable. If it can be done on a single machine then it should be done on a single machine. Quoting Dask - "For data that fits into RAM, Pandas can often be faster and easier to use than Dask DataFrame"
12.  If your dataset is very small you can load your data using PandaPy's `read()` function, for medium sized data, it is best to load it with datatable or pyspark and convert it to structured Numpy, if it is large pyspark, Dask, or Modin, if it is very large use pyspark.
13.  Lastly PandaPy can have as input any multidimensional object and does not have to conform to the basic NumPy datatypes. It can include nested datatypes, subarrays, functions as long as each column conforms to the array lenght, this allows for a great amount of flexibility. You can for example, `add(array, "panda function",[[pd for i in range(len(multiple_stocks))]])` to create a list of the panda (pd) module and access it along any index value `array["panda function"][0].read_csv(url)`.

PandaPy software, similar to the original Pandas project, is developed to improve the usability of python for finance. Structured datatypes are designed to be able to mimic ‘structs’ in the C language, and share a similar memory layout. PandaPy currently houses more than 30 functions. Structured NumPy are meant for interfacing with C code and for low-level manipulation of structured buffers, for example for interpreting binary blobs. For these purposes they support specialized features such as subarrays, nested datatypes, and unions, and allow control over the memory layout of the structure.

**Note this is a fledgling project, much room for improvement, all feedback appreciated (issues tab)**

### [](https://github.com/firmai/pandapy#description)Description

* * *

A Structured NumPy Array is an array of structures. NumPy arrays can only contain one data type, but structured arrays in a sense create an array of homogeneous structures. This is done without moving out of NumPy such as is required with Xarray. For structured arrays the data type only has to be the same per column like an SQL data base. Each column can be another multidimensional object and does not have to conform to the basic NumPy datatypes.

PandaPy comes with similar functionality like Pandas, such as groupby, pivot, and others. The biggest benefit of this approach is that NumPy dtype(data type) directly maps onto a C structure definition, so the buffer containing the array content can be accessed directly within an appropriately written C program. If you find yourself writing a Python interface to a legacy C or Fortran library that manipulates structured data, you'll probably find structured arrays quite useful.

### [](https://github.com/firmai/pandapy#additional)Additional

1.  Play around with [speed tests here](https://colab.research.google.com/drive/1JqvplTUUciIw2KGkuoCNv196prl3eoiL) and some more [here](https://colab.research.google.com/drive/1I4sJOM8o4RAqHp3YU1nlx92UxwoC3WB-).
2.  Test and explore the package with this [Google Colab Notebook](https://colab.research.google.com/drive/1j45o36_FFIof9uzp1DoyzxETD4lfpci5).
3.  Get in touch on [LinkedIn](https://www.linkedin.com/company/firmai) or [Twitter](https://twitter.com/dereknow?lang=en).
4.  Use `table(array)` to get a pandas looking table printout

### [](https://github.com/firmai/pandapy#functions)Functions

#### [](https://github.com/firmai/pandapy#pandapy-speed-over-pandas-in-x-eg-dropnarow-30x)PandaPy Speed Over Pandas In (X) e.g., (dropnarow) (30x)

* * *

#### [](https://github.com/firmai/pandapy#array-structure)Array Structure

```
Read In Arrays (read) To Pandas (unstructured) Pandas to Structured (structured) To Unstructured (to_unstruct) To Structured (to_struct) Print Table (table) 
```

#### [](https://github.com/firmai/pandapy#explorative-functions)Explorative Functions

```
Descriptive Statistics (describe) (5x) Correlation Array (corr) (2x) 
```

#### [](https://github.com/firmai/pandapy#finance-functions)Finance Functions

```
Returns (returns) (50x) Portfolio Value (portfolio_value) (50x) Cummulative Value (cummulative_return) (50x) Column Lags (lags) (7x) 
```

#### [](https://github.com/firmai/pandapy#array-functions)Array Functions

```
Drop Null Rows (dropnarow) (30x) Drop Column/s (drop) (100x) Add Column/s (add) (3x) Concatenate (concat) (rows 25x columns 70x) Merge (merge) (2x) Group by (group) (10x) Pivot (pivot) (20x) Fill Nulls (fillna) (20x) Shift Column (shift) (50x) Rename (rename) (500x) 
```

#### [](https://github.com/firmai/pandapy#other-speed-tests)Other Speed Tests

```
Update (array[col] = values) (60x) Addition (array[col] + array[col]) (80x) Multiplication (array[col] * array[col]) (80x) Log (np.log(array[col]) (25x) 
```

_note speed tests done on financial dataset only_

### [](https://github.com/firmai/pandapy#documentation-by-example)Documentation by Example

* * *

**Read In Arrays**

```
# First Example multiple\_stocks \= pp.read('https://github.com/firmai/random-assets-two/blob/master/numpy/multiple\_stocks.csv?raw=true') closing \= multiple\_stocks\[\['Ticker','Date','Adj\_Close'\]\] piv \= pp.pivot(closing,"Date","Ticker","Adj\_Close"); piv closing \= pp.to\_struct(piv, name\_list \= \[x for x in np.unique(multiple\_stocks\["Ticker"\])\]) # Second Example tsla \= pp.read('https://github.com/firmai/random-assets-two/raw/master/numpy/tsla.csv') crm \= pp.read('https://github.com/firmai/random-assets-two/raw/master/numpy/crm.csv') tsla\_sub \= tsla\[\["Date","Adj\_Close","Volume"\]\] crm\_sub \= crm\[\["Date","Adj\_Close","Volume"\]\] crm\_adj \= crm\[\['Date','Adj\_Close'\]\]
```

```
closing 
``````
array([(37.24206924, 100.45429993, 44.57522202, 20.72605705, 130.59109497, 35.80251312, 41.9791832 , 81.51140594, 66.33999634), (35.08446503, 97.62433624, 43.83200836, 20.34561157, 128.53627014, 35.80251312, 41.59314346, 80.89860535, 66.15000153), (35.34244537, 97.63354492, 42.79874039, 19.90727234, 125.76422119, 36.07437897, 40.98268127, 80.28580475, 64.58000183), ..., (21.57999992, 289.79998779, 59.08000183, 11.18000031, 135.27000427, 55.34999847, 158.96000671, 137.53999329, 88.37000275), (21.34000015, 291.51998901, 58.65999985, 11.07999992, 132.80999756, 55.27000046, 157.58999634, 136.80999756, 87.95999908), (21.51000023, 293.6499939 , 58.47999954, 11.15999985, 134.03999329, 55.34999847, 157.69999695, 136.66999817, 88.08999634)], dtype=[('AA', '
```

`**Rename**`

```
pp.rename(closing,["AA","AAPL"],["GAP","FAF"])[:5]
```

```
`array([(37.24206924, 100.45429993, 44.57522202, 20.72605705, 130.59109497, 35.80251312, 41.9791832 , 81.51140594, 66.33999634), (35.08446503, 97.62433624, 43.83200836, 20.34561157, 128.53627014, 35.80251312, 41.59314346, 80.89860535, 66.15000153), (35.34244537, 97.63354492, 42.79874039, 19.90727234, 125.76422119, 36.07437897, 40.98268127, 80.28580475, 64.58000183), (36.25707626, 99.00255585, 42.57216263, 19.91554451, 124.94229126, 36.52467346, 41.50337982, 82.63342285, 65.52999878), (37.28897095, 102.80648041, 43.67792892, 20.15538216, 127.65791321, 36.966465 , 42.72432327, 84.13523865, 66.63999939)], dtype=[('GAP', '`
```

```
`pp.rename(closing,"AA", "GALLY")[:5]`
```

```
`` `array([(37.24206924, 100.45429993, 44.57522202, 20.72605705, 130.59109497, 35.80251312, 41.9791832 , 81.51140594, 66.33999634), (35.08446503, 97.62433624, 43.83200836, 20.34561157, 128.53627014, 35.80251312, 41.59314346, 80.89860535, 66.15000153), (35.34244537, 97.63354492, 42.79874039, 19.90727234, 125.76422119, 36.07437897, 40.98268127, 80.28580475, 64.58000183), (36.25707626, 99.00255585, 42.57216263, 19.91554451, 124.94229126, 36.52467346, 41.50337982, 82.63342285, 65.52999878), (37.28897095, 102.80648041, 43.67792892, 20.15538216, 127.65791321, 36.966465 , 42.72432327, 84.13523865, 66.63999939)], dtype=[('GALLY', '` ``
```

``` `` `**Statistics**` `` ```

```
`` `described = pp.describe(closing)` ``
```

Describe

observations

minimum

maximum

mean

variance

skewness

kurtosis

AA

1258.00

15.97

60.23

31.46

99.42

0.67

\-0.58

AAPL

1258.00

85.39

293.65

149.45

2119.86

0.66

\-0.28

DAL

1258.00

30.73

62.69

47.15

44.33

\-0.01

\-0.78

GE

1258.00

6.42

28.67

18.85

48.45

\-0.25

\-1.54

IBM

1258.00

99.83

161.17

133.35

116.28

\-0.37

0.56

KO

1258.00

32.81

55.35

41.67

28.86

0.80

\-0.05

MSFT

1258.00

36.27

158.96

78.31

1102.21

0.61

\-0.82

PEP

1258.00

78.46

139.30

102.86

229.01

0.63

\-0.32

UAL

1258.00

37.75

96.70

69.22

195.65

0.02

\-1.04

``` `` `**Drop Column/s**` `` ```

```
`` `removed = pp.drop(closing,["AA","AAPL","IBM"]) ; removed[:5]` ``
```

```
``` `` `array([(44.57522202, 20.72605705, 35.80251312, 41.9791832 , 81.51140594, 66.33999634), (43.83200836, 20.34561157, 35.80251312, 41.59314346, 80.89860535, 66.15000153), (42.79874039, 19.90727234, 36.07437897, 40.98268127, 80.28580475, 64.58000183), (42.57216263, 19.91554451, 36.52467346, 41.50337982, 82.63342285, 65.52999878), (43.67792892, 20.15538216, 36.966465 , 42.72432327, 84.13523865, 66.63999939)], dtype={'names':['DAL','GE','KO','MSFT','PEP','UAL'], 'formats':['` `` ```
```

``` `` `**Add Column/s**` `` ```

```
`` `added = pp.add(closing,["GALLY","FAF"],[closing["IBM"],closing["AA"]]); added[:5] ## set two new columns with that two previous columnns` ``
```

```
``` `` `array([(37.24206924, 100.45429993, 44.57522202, 20.72605705, 130.59109497, 35.80251312, 41.9791832 , 81.51140594, 66.33999634, 130.59109497, 37.24206924), (35.08446503, 97.62433624, 43.83200836, 20.34561157, 128.53627014, 35.80251312, 41.59314346, 80.89860535, 66.15000153, 128.53627014, 35.08446503), (35.34244537, 97.63354492, 42.79874039, 19.90727234, 125.76422119, 36.07437897, 40.98268127, 80.28580475, 64.58000183, 125.76422119, 35.34244537), (36.25707626, 99.00255585, 42.57216263, 19.91554451, 124.94229126, 36.52467346, 41.50337982, 82.63342285, 65.52999878, 124.94229126, 36.25707626), (37.28897095, 102.80648041, 43.67792892, 20.15538216, 127.65791321, 36.966465 , 42.72432327, 84.13523865, 66.63999939, 127.65791321, 37.28897095)], dtype=[('AA', '` `` ```
```

``` `` `**Concatenate Arrays by Row**` `` ```

```
`` `concat_row = pp.concat(removed[["DAL","GE"]], added[["PEP","UAL"]], type="row"); concat_row[:5]` ``
```

```
``` `` `array([(44.57522202, 20.72605705), (43.83200836, 20.34561157), (42.79874039, 19.90727234), (42.57216263, 19.91554451), (43.67792892, 20.15538216)], dtype=[('DAL', '` `` ```
```

``` `` `**Concatenate Arrays by Column**` `` ```

```
`` `concat_col = pp.concat(removed[["DAL","GE"]], added[["PEP","UAL"]], type="columns"); concat_col[:5]` ``
```

```
``` `` `array([(44.57522202, 20.72605705, 81.51140594, 66.33999634), (43.83200836, 20.34561157, 80.89860535, 66.15000153), (42.79874039, 19.90727234, 80.28580475, 64.58000183), (42.57216263, 19.91554451, 82.63342285, 65.52999878), (43.67792892, 20.15538216, 84.13523865, 66.63999939)], dtype=[('DAL', '` `` ```
```

``` `` `**Concatenate by Array**` `` ```

```
`` `concat_array = pp.concat(removed[["DAL","GE"]], added[["PEP","UAL"]], type="array"); concat_array[:5]` ``
```

```
``` `` `array([[(44.57522201538086, 20.726057052612305), (43.832008361816406, 20.345611572265625), (42.79874038696289, 19.907272338867188), ..., (59.08000183105469, 11.180000305175781), (58.65999984741211, 11.079999923706055), (58.47999954223633, 11.15999984741211)], [(81.51140594482422, 66.33999633789062), (80.89860534667969, 66.1500015258789), (80.28580474853516, 64.58000183105469), ..., (137.5399932861328, 88.37000274658203), (136.80999755859375, 87.95999908447266), (136.6699981689453, 88.08999633789062)]], dtype=object)` `` ``` 
```

`` `**Concatenate by Melt**` ``

```
`concat_melt = pp.concat(removed[["DAL","GE"]], added[["PEP","UAL"]], type="melt"); concat_melt[:5]`
```

```
`` `array([(44.57522202, 20.72605705), (43.83200836, 20.34561157), (42.79874039, 19.90727234), (42.57216263, 19.91554451), (43.67792892, 20.15538216)], dtype=[('DAL', '` ``
```

``` `` `**Merge Array (inner, outer)**` `` ```

```
`` `merged = pp.merge(tsla_sub, crm_adj, left_on="Date", right_on="Date",how="inner",left_postscript="_TSLA",right_postscript="_CRM"); merged[:5]` ``
```

```
``` `` `array([('2019-01-02', 310.11999512, 135.55000305, 11658600), ('2019-01-03', 300.35998535, 130.3999939 , 6965200), ('2019-01-04', 317.69000244, 137.96000671, 7394100), ('2019-01-07', 334.95999146, 142.22000122, 7551200), ('2019-01-08', 335.3500061 , 145.72000122, 7008500)], dtype=[('Date', '` `` ```
```

``` `` `**Replace Individual Values**` `` ```

```
`` `## More work to done on replace (structured) ## replace(merged,original=317.69000244, replacement=np.nan)[:5]` ``
```

``` `` `**Print Table**` `` ```

Date

Adj\_Close\_TSLA

Adj\_Close\_CRM

Volume

0

2019-01-02

310.120

135.550

11658600

1

2019-01-03

300.360

130.400

6965200

2

2019-01-04

317.690

137.960

7394100

3

2019-01-07

334.960

142.220

7551200

4

2019-01-08

335.350

145.720

7008500

```
`` `### This is the new function that you should include above ### You can add the same peculuarities to remove` ``
```

``` `` `**Add and Concatenate**` `` ```

```
`` `tsla = pp.add(tsla,["Ticker"], "TSLA", "U10") crm = pp.add(crm,["Ticker"], "CRM", "U10") combine = pp.concat(tsla[0:5], crm[0:5], type="row"); combine` ``
```

```
``` `` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, '2019-01-02', 'TSLA'), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, '2019-01-03', 'TSLA'), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, '2019-01-04', 'TSLA'), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, '2019-01-07', 'TSLA'), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , '2019-01-08', 'TSLA'), (136.83000183, 133.05000305, 133.3999939 , 135.55000305, 4783900, 135.55000305, '2019-01-02', 'CRM'), (134.77999878, 130.1000061 , 133.47999573, 130.3999939 , 6365700, 130.3999939 , '2019-01-03', 'CRM'), (139.32000732, 132.22000122, 133.5 , 137.96000671, 6650600, 137.96000671, '2019-01-04', 'CRM'), (143.38999939, 138.78999329, 141.02000427, 142.22000122, 9064800, 142.22000122, '2019-01-07', 'CRM'), (146.46000671, 142.88999939, 144.72999573, 145.72000122, 9057300, 145.72000122, '2019-01-08', 'CRM')], dtype=[('High', '` `` ```
```

```
`` `dropped = pp.drop(combine,["High","Low","Open"]); dropped[:10]` ``
```

```
``` `` `array([(310.11999512, 11658600, 310.11999512, '2019-01-02', 'TSLA'), (300.35998535, 6965200, 300.35998535, '2019-01-03', 'TSLA'), (317.69000244, 7394100, 317.69000244, '2019-01-04', 'TSLA'), (334.95999146, 7551200, 334.95999146, '2019-01-07', 'TSLA'), (335.3500061 , 7008500, 335.3500061 , '2019-01-08', 'TSLA'), (135.55000305, 4783900, 135.55000305, '2019-01-02', 'CRM'), (130.3999939 , 6365700, 130.3999939 , '2019-01-03', 'CRM'), (137.96000671, 6650600, 137.96000671, '2019-01-04', 'CRM'), (142.22000122, 9064800, 142.22000122, '2019-01-07', 'CRM'), (145.72000122, 9057300, 145.72000122, '2019-01-08', 'CRM')], dtype={'names':['Close','Volume','Adj_Close','Date','Ticker'], 'formats':['` `` ```
```

``` `` `**Pivot Array**` `` ```

```
`` `piv = pp.pivot(dropped,"Date","Ticker","Adj_Close",display=True)` ``
```

Adj\_Close

CRM

TSLA

2019-01-02

135.55

310.12

2019-01-03

130.40

300.36

2019-01-04

137.96

317.69

2019-01-07

142.22

334.96

2019-01-08

145.72

335.35

``` `` `**Add New Data types**` `` ```

```
`` `tsla_extended = pp.add(tsla,"Month",tsla["Date"],'datetime64[M]') tsla_extended = pp.add(tsla_extended,"Year",tsla_extended["Date"],'datetime64[Y]')` `` 
```

``` `` `**Update Existing Column**` `` ```

```
`` `## faster method elsewhere year_frame = pp.update(tsla,"Date", [dt.year for dt in tsla["Date"].astype(object)],types="|U10"); year_frame[:5]` ``
```

```
``` `` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, 'TSLA', '2019'), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, 'TSLA', '2019'), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, 'TSLA', '2019'), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, 'TSLA', '2019'), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , 'TSLA', '2019')], dtype=[('High', '` `` ```
```

``` `` `**Group Arrays By**` `` ```

```
`` `grouped = pp.group(tsla_extended, ['Ticker','Month','Year'],['mean', 'std', 'min', 'max'], ['Adj_Close','Close'], display=True)` ``
```

Ticker

Month

Year

Adj\_Close\_mean

Adj\_Close\_std

Adj\_Close\_min

Adj\_Close\_max

Close\_mean

Close\_std

Close\_min

Close\_max

0

TSLA

2019-01-01

2019-01-01

318.494

21.098

287.590

347.310

318.494

21.098

287.590

347.310

1

TSLA

2019-02-01

2019-01-01

307.728

8.053

291.230

321.350

307.728

8.053

291.230

321.350

2

TSLA

2019-03-01

2019-01-01

277.757

8.925

260.420

294.790

277.757

8.925

260.420

294.790

3

TSLA

2019-04-01

2019-01-01

266.656

14.985

235.140

291.810

266.656

14.985

235.140

291.810

4

TSLA

2019-05-01

2019-01-01

219.715

24.040

185.160

255.340

219.715

24.040

185.160

255.340

5

TSLA

2019-06-01

2019-01-01

213.717

12.125

178.970

226.430

213.717

12.125

178.970

226.430

6

TSLA

2019-07-01

2019-01-01

242.382

12.077

224.550

264.880

242.382

12.077

224.550

264.880

7

TSLA

2019-08-01

2019-01-01

225.103

7.831

211.400

238.300

225.103

7.831

211.400

238.300

8

TSLA

2019-09-01

2019-01-01

237.261

8.436

220.680

247.100

237.261

8.436

220.680

247.100

9

TSLA

2019-10-01

2019-01-01

266.355

31.463

231.430

328.130

266.355

31.463

231.430

328.130

10

TSLA

2019-11-01

2019-01-01

338.300

13.226

313.310

359.520

338.300

13.226

313.310

359.520

11

TSLA

2019-12-01

2019-01-01

377.695

36.183

330.370

430.940

377.695

36.183

330.370

430.940

``` `` `**Convert Array to Pandas**` `` ```

```
`` `grouped_frame = pp.pandas(grouped); grouped_frame.head()` ``
```

Ticker

Month

Year

Adj\_Close\_mean

Adj\_Close\_std

Adj\_Close\_min

Adj\_Close\_max

Close\_mean

Close\_std

Close\_min

Close\_max

0

TSLA

2019-01-01

2019-01-01

318.494284

21.098362

287.589996

347.309998

318.494284

21.098362

287.589996

347.309998

1

TSLA

2019-02-01

2019-01-01

307.728421

8.052522

291.230011

321.350006

307.728421

8.052522

291.230011

321.350006

2

TSLA

2019-03-01

2019-01-01

277.757140

8.924873

260.420013

294.790009

277.757140

8.924873

260.420013

294.790009

3

TSLA

2019-04-01

2019-01-01

266.655716

14.984572

235.139999

291.809998

266.655716

14.984572

235.139999

291.809998

4

TSLA

2019-05-01

2019-01-01

219.715454

24.039647

185.160004

255.339996

219.715454

24.039647

185.160004

255.339996

``` `` `**From Pandas to Structured**` `` ```

```
`` `struct = pp.structured(grouped_frame); struct[:5]` ``
```

```
``` `` `rec.array([('TSLA', '2019-01-01T00:00:00.000000000', '2019-01-01T00:00:00.000000000', 318.49428449, 21.09836186, 287.58999634, 347.30999756, 318.49428449, 21.09836186, 287.58999634, 347.30999756), ('TSLA', '2019-02-01T00:00:00.000000000', '2019-01-01T00:00:00.000000000', 307.72842086, 8.05252198, 291.23001099, 321.3500061 , 307.72842086, 8.05252198, 291.23001099, 321.3500061 ), ('TSLA', '2019-03-01T00:00:00.000000000', '2019-01-01T00:00:00.000000000', 277.75713966, 8.92487345, 260.42001343, 294.79000854, 277.75713966, 8.92487345, 260.42001343, 294.79000854), ('TSLA', '2019-04-01T00:00:00.000000000', '2019-01-01T00:00:00.000000000', 266.65571594, 14.98457194, 235.13999939, 291.80999756, 266.65571594, 14.98457194, 235.13999939, 291.80999756), ('TSLA', '2019-05-01T00:00:00.000000000', '2019-01-01T00:00:00.000000000', 219.7154541 , 24.03964724, 185.16000366, 255.33999634, 219.7154541 , 24.03964724, 185.16000366, 255.33999634)], dtype=[('Ticker', 'O'), ('Month', '` `` ```
```

``` `` `**Shift Column**` `` ```

```
`` `pp.shift(merged["Adj_Close_TSLA"],1)[:5]` ``
```

```
``` `` `array([ nan, 310.11999512, 300.35998535, 317.69000244, 334.95999146])` `` ``` 
```

`` `**Multiple Lags for Column**` ``

```
`tsla_lagged = pp.lags(tsla_extended, "Adj_Close", 5); tsla_lagged[:5]`
```

```
`` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, '2019-01-02', 'TSLA', '2019-01', '2019', nan, nan, nan, nan, nan), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, '2019-01-03', 'TSLA', '2019-01', '2019', 310.11999512, nan, nan, nan, nan), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, '2019-01-04', 'TSLA', '2019-01', '2019', 300.35998535, 310.11999512, nan, nan, nan), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, '2019-01-07', 'TSLA', '2019-01', '2019', 317.69000244, 300.35998535, 310.11999512, nan, nan), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , '2019-01-08', 'TSLA', '2019-01', '2019', 334.95999146, 317.69000244, 300.35998535, 310.11999512, nan)], dtype=[('High', '` ``
```

``` `` `**Correlation Array**` `` ```

```
`` `correlated = pp.corr(closing)` ``
```

Correlation

AA

AAPL

DAL

GE

IBM

KO

MSFT

PEP

UAL

AA

1.00

0.21

0.24

\-0.17

0.39

\-0.09

0.05

\-0.04

0.12

AAPL

0.21

1.00

0.86

\-0.83

0.22

0.85

0.94

0.85

0.82

DAL

0.24

0.86

1.00

\-0.78

0.14

0.79

0.86

0.78

0.86

GE

\-0.17

\-0.83

\-0.78

1.00

0.06

\-0.76

\-0.86

\-0.69

\-0.76

IBM

0.39

0.22

0.14

0.06

1.00

0.07

0.15

0.24

0.18

KO

\-0.09

0.85

0.79

\-0.76

0.07

1.00

0.94

0.96

0.74

MSFT

0.05

0.94

0.86

\-0.86

0.15

0.94

1.00

0.93

0.83

PEP

\-0.04

0.85

0.78

\-0.69

0.24

0.96

0.93

1.00

0.75

UAL

0.12

0.82

0.86

\-0.76

0.18

0.74

0.83

0.75

1.00

``` `` `**Log Returns**` `` ```

```
`` `pp.returns(closing,"IBM",type="log")` ``
```

```
``` `` `array([ nan, -0.01585991, -0.02180223, ..., 0.0026649 , -0.0183533 , 0.0092187 ])` `` ``` 
```

`` `**Normal Returns**` ``

```
`loga = pp.returns(closing,"IBM",type="normal"); loga`
```

```
`` `array([ nan, -0.0157348 , -0.02156628, ..., 0.00266845, -0.0181859 , 0.00926132])` `` 
```

`` `**Add Column**` ``

```
`close_ret = pp.add(closing,"IBM_log_return",loga); close_ret[:5]`
```

```
`` `array([(37.24206924, 100.45429993, 44.57522202, 20.72605705, 130.59109497, 35.80251312, 41.9791832 , 81.51140594, 66.33999634, nan), (35.08446503, 97.62433624, 43.83200836, 20.34561157, 128.53627014, 35.80251312, 41.59314346, 80.89860535, 66.15000153, -0.0157348 ), (35.34244537, 97.63354492, 42.79874039, 19.90727234, 125.76422119, 36.07437897, 40.98268127, 80.28580475, 64.58000183, -0.02156628), (36.25707626, 99.00255585, 42.57216263, 19.91554451, 124.94229126, 36.52467346, 41.50337982, 82.63342285, 65.52999878, -0.00653548), (37.28897095, 102.80648041, 43.67792892, 20.15538216, 127.65791321, 36.966465 , 42.72432327, 84.13523865, 66.63999939, 0.02173501)], dtype=[('AA', '` ``
```

``` `` `**Drop Array Rows Where Null**` `` ```

```
`` `close_ret_na = pp.dropnarow(close_ret, "IBM_log_return"); close_ret[:5]` ``
```

```
``` `` `array([(37.24206924, 100.45429993, 44.57522202, 20.72605705, 130.59109497, 35.80251312, 41.9791832 , 81.51140594, 66.33999634, nan), (35.08446503, 97.62433624, 43.83200836, 20.34561157, 128.53627014, 35.80251312, 41.59314346, 80.89860535, 66.15000153, -0.0157348 ), (35.34244537, 97.63354492, 42.79874039, 19.90727234, 125.76422119, 36.07437897, 40.98268127, 80.28580475, 64.58000183, -0.02156628), (36.25707626, 99.00255585, 42.57216263, 19.91554451, 124.94229126, 36.52467346, 41.50337982, 82.63342285, 65.52999878, -0.00653548), (37.28897095, 102.80648041, 43.67792892, 20.15538216, 127.65791321, 36.966465 , 42.72432327, 84.13523865, 66.63999939, 0.02173501)], dtype=[('AA', '` `` ```
```

``` `` `**Portfolio Value from Log Return**` `` ```

```
`` `pp.portfolio_value(close_ret_na, "IBM_log_return", type="log")` ``
```

```
``` `` `array([0.98438834, 0.96338604, 0.95711037, ..., 1.15115429, 1.13040872, 1.14092643])` `` ``` 
```

`` `**Cummulative Value from Log Return**` ``

```
`pp.cummulative_return(close_ret_na, "IBM_log_return", type="log")`
```

```
`` `array([-0.01561166, -0.03661396, -0.04288963, ..., 0.15115429, 0.13040872, 0.14092643])` `` 
```

`` `**Fillna Mean**` ``

```
`pp.fillna(tsla_lagged,type="mean")[:5]`
```

```
`` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, 272.95330665, 272.38631982, 271.75180703, 271.10991915, 270.48587024), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, 310.11999512, 272.38631982, 271.75180703, 271.10991915, 270.48587024), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, 300.35998535, 310.11999512, 271.75180703, 271.10991915, 270.48587024), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, 317.69000244, 300.35998535, 310.11999512, 271.10991915, 270.48587024), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , 334.95999146, 317.69000244, 300.35998535, 310.11999512, 270.48587024)], dtype={'names':['High','Low','Open','Close','Volume','Adj_Close','Adj_Close_lag_1','Adj_Close_lag_2','Adj_Close_lag_3','Adj_Close_lag_4','Adj_Close_lag_5'], 'formats':['` ``
```

``` `` `**Fillna Value**` `` ```

```
`` `pp.fillna(tsla_lagged,type="value",value=-999999)[:5]` ``
```

```
``` `` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, -9.99999000e+05, -9.99999000e+05, -9.99999000e+05, -9.99999000e+05, -999999.), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, 3.10119995e+02, -9.99999000e+05, -9.99999000e+05, -9.99999000e+05, -999999.), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, 3.00359985e+02, 3.10119995e+02, -9.99999000e+05, -9.99999000e+05, -999999.), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, 3.17690002e+02, 3.00359985e+02, 3.10119995e+02, -9.99999000e+05, -999999.), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , 3.34959991e+02, 3.17690002e+02, 3.00359985e+02, 3.10119995e+02, -999999.)], dtype={'names':['High','Low','Open','Close','Volume','Adj_Close','Adj_Close_lag_1','Adj_Close_lag_2','Adj_Close_lag_3','Adj_Close_lag_4','Adj_Close_lag_5'], 'formats':['` `` ```
```

``` `` `**Fillna Forward Fill**` `` ```

```
`` `pp.fillna(tsla_lagged,type="ffill")[:5]` ``
```

```
``` `` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, nan, nan, nan, nan, nan), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, 310.11999512, nan, nan, nan, nan), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, 300.35998535, 310.11999512, nan, nan, nan), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, 317.69000244, 300.35998535, 310.11999512, nan, nan), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , 334.95999146, 317.69000244, 300.35998535, 310.11999512, nan)], dtype={'names':['High','Low','Open','Close','Volume','Adj_Close','Adj_Close_lag_1','Adj_Close_lag_2','Adj_Close_lag_3','Adj_Close_lag_4','Adj_Close_lag_5'], 'formats':['` `` ```
```

``` `` `**Fillna Backward Fill**` `` ```

```
`` `pp.fillna(tsla_lagged,type="bfill")[:5]` ``
```

```
``` `` `array([(315.13000488, 298.79998779, 306.1000061 , 310.11999512, 11658600, 310.11999512, 310.11999512, 310.11999512, 310.11999512, 310.11999512, 310.11999512), (309.3999939 , 297.38000488, 307. , 300.35998535, 6965200, 300.35998535, 310.11999512, 310.11999512, 310.11999512, 310.11999512, 310.11999512), (318. , 302.73001099, 306. , 317.69000244, 7394100, 317.69000244, 300.35998535, 310.11999512, 310.11999512, 310.11999512, 310.11999512), (336.73999023, 317.75 , 321.72000122, 334.95999146, 7551200, 334.95999146, 317.69000244, 300.35998535, 310.11999512, 310.11999512, 310.11999512), (344.01000977, 327.01998901, 341.95999146, 335.3500061 , 7008500, 335.3500061 , 334.95999146, 317.69000244, 300.35998535, 310.11999512, 310.11999512)], dtype={'names':['High','Low','Open','Close','Volume','Adj_Close','Adj_Close_lag_1','Adj_Close_lag_2','Adj_Close_lag_3','Adj_Close_lag_4','Adj_Close_lag_5'], 'formats':['` `` ```
```

``` `` `**Print Table**` `` ```

High

Low

Open

Close

Volume

Adj\_Close

Date

Ticker

Month

Year

Adj\_Close\_lag\_1

Adj\_Close\_lag\_2

Adj\_Close\_lag\_3

Adj\_Close\_lag\_4

Adj\_Close\_lag\_5

0

315.130

298.800

306.100

310.120

11658600

310.120

2019-01-02

TSLA

2019-01-01

2019-01-01

nan

nan

nan

nan

nan

1

309.400

297.380

307.000

300.360

6965200

300.360

2019-01-03

TSLA

2019-01-01

2019-01-01

310.120

nan

nan

nan

nan

2

318.000

302.730

306.000

317.690

7394100

317.690

2019-01-04

TSLA

2019-01-01

2019-01-01

300.360

310.120

nan

nan

nan

3

336.740

317.750

321.720

334.960

7551200

334.960

2019-01-07

TSLA

2019-01-01

2019-01-01

317.690

300.360

310.120

nan

nan

4

344.010

327.020

341.960

335.350

7008500

335.350

2019-01-08

TSLA

2019-01-01

2019-01-01

334.960

317.690

300.360

310.120

nan

``` `` `**Outliers**` `` ```

```
`` `signal = tsla_lagged["Volume"] z_signal = (signal - np.mean(signal)) / np.std(signal)` ``
```

```
`` `tsla_lagged = pp.add(tsla_lagged,"z_signal_volume",z_signal)` ``
```

```
`` `outliers = pp.detect(tsla_lagged["z_signal_volume"]); outliers` ``
```

```
``` `` `[12, 40, 42, 64, 78, 79, 84, 95, 97, 98, 107, 141, 205, 206, 207]` `` ``` 
```

```
`import matplotlib.pyplot as plt plt.figure(figsize=(15, 7)) plt.plot(np.arange(len(tsla_lagged["Volume"])), tsla_lagged["Volume"]) plt.plot(np.arange(len(tsla_lagged["Volume"])), tsla_lagged["Volume"], 'X', label='outliers',markevery=outliers, c='r') plt.legend() plt.show()`
```

`` `[![png](https://github.com/firmai/pandapy/raw/master/PandaPy_files/PandaPy_46_0.png)](https://github.com/firmai/pandapy/blob/master/PandaPy_files/PandaPy_46_0.png)` ``

`` `**Remove Noise**` ``

```
`price_signal = tsla_lagged["Close"] removed_signal = pp.removal(price_signal, 30) noise = pp.get(price_signal, removed_signal)`
```

```
`plt.figure(figsize=(15, 7)) plt.subplot(2, 1, 1) plt.plot(removed_signal) plt.title('timeseries without noise') plt.subplot(2, 1, 2) plt.plot(noise) plt.title('noise timeseries') plt.show()`
```

`` `[![png](https://github.com/firmai/pandapy/raw/master/PandaPy_files/PandaPy_48_0.png)](https://github.com/firmai/pandapy/blob/master/PandaPy_files/PandaPy_48_0.png)` ``

`` `  
  
from Hacker News https://ift.tt/2RjUfit` ``