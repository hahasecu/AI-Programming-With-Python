
# Statistics from Stock Data

In this lab we will load stock data into a Pandas Dataframe and calculate some statistics on it. We will be working with stock data from Google, Apple, and Amazon. All the stock data was downloaded from yahoo finance in CSV format. In your workspace you should have a file named GOOG.csv containing the Google stock data, a file named AAPL.csv containing the Apple stock data, and a file  named AMZN.csv containing the Amazon stock data. (You can see the workspace folder by clicking on the Jupyter logo in the upper left corner of the workspace.) All the files contain 7 columns of data:

**Date Open High Low Close Adj_Close Volume**

We will start by reading in any of the above CSV files into a DataFrame and see what the data looks like.


```python
# We import pandas into Python
import pandas as pd

# We read in a stock data data file into a data frame and see what it looks like
df = pd.read_csv('./GOOG.csv')

# We display the first 5 rows of the DataFrame
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Adj Close</th>
      <th>Volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2004-08-19</td>
      <td>49.676899</td>
      <td>51.693783</td>
      <td>47.669952</td>
      <td>49.845802</td>
      <td>49.845802</td>
      <td>44994500</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2004-08-20</td>
      <td>50.178635</td>
      <td>54.187561</td>
      <td>49.925285</td>
      <td>53.805050</td>
      <td>53.805050</td>
      <td>23005800</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2004-08-23</td>
      <td>55.017166</td>
      <td>56.373344</td>
      <td>54.172661</td>
      <td>54.346527</td>
      <td>54.346527</td>
      <td>18393200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2004-08-24</td>
      <td>55.260582</td>
      <td>55.439419</td>
      <td>51.450363</td>
      <td>52.096165</td>
      <td>52.096165</td>
      <td>15361800</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2004-08-25</td>
      <td>52.140873</td>
      <td>53.651051</td>
      <td>51.604362</td>
      <td>52.657513</td>
      <td>52.657513</td>
      <td>9257400</td>
    </tr>
  </tbody>
</table>
</div>



We clearly see that the Dataframe is has automatically labeled the row indices using integers and has labeled the columns of the DataFrame using the names of the columns in the CSV files.

# To Do

You will now load the stock data from Google, Apple, and Amazon into separte DataFrames. However, for each stock data you will only be interested in loading the `Date` and `Adj Close` columns into the Dataframe. In addtion, you want to use the `Date` column as your row index. Finally, you want the DataFrame to recognize the dates as actual dates (year/month/day) and not as strings. For each stock, you can accomplish all theses things in just one line of code by using the appropiate keywords in the `pd.read_csv()` function. Here are a few hints:

* Use the `index_col` keyword to indicate which column you want to use as an index. For example `index_col = ['Open']`

* Set the `parse_dates` keyword equal to `True` to convert the Dates into real dates of the form year/month/day

* Use the `usecols` keyword to select which columns you want to load into the DataFrame. For example `usecols = ['Open', 'High']`

Fill in the code below:


```python
# We load the Google stock data into a DataFrame
google_stock = pd.read_csv('./GOOG.csv', index_col=['Date'], parse_dates=True, usecols=['Date', 'Adj Close'])

# We load the Apple stock data into a DataFrame
apple_stock = pd.read_csv('./AAPL.csv', index_col=['Date'], parse_dates=True, usecols=['Date', 'Adj Close'])

# We load the Amazon stock data into a DataFrame
amazon_stock = pd.read_csv('./AMZN.csv', index_col=['Date'], parse_dates=True, usecols=['Date', 'Adj Close'])
```

You can check that you have loaded the data correctly by displaying the head of the DataFrames.


```python
# We display the google_stock DataFrame
google_stock.head()

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
    </tr>
  </tbody>
</table>
</div>




```python
amazon_stock.head(3)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>amazon_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>69.7500</td>
    </tr>
  </tbody>
</table>
</div>




```python
apple_stock.head(3)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>apple_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>3.596616</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>3.293384</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>3.341579</td>
    </tr>
  </tbody>
</table>
</div>



You will now join the three DataFrames above to create a single new DataFrame that contains all the `Adj Close` for all the stocks. Let's start by creating an empty DataFrame that has as row indices calendar days between `2000-01-01`  and `2016-12-31`. We will use the `pd.date_range()` function to create the calendar dates first and then we will create a DataFrame that uses those dates as row indices:


```python
# We create calendar dates between '2000-01-01' and  '2016-12-31'
dates = pd.date_range('2000-01-01', '2016-12-31')

# We create and empty DataFrame that uses the above dates as indices
all_stocks = pd.DataFrame(index = dates)
```

# To Do

You will now join the the individual DataFrames, `google_stock`, `apple_stock`, and `amazon_stock`, to the `all_stocks` DataFrame. However, before you do this, it is necessary that you change the name of the columns in each of the three dataframes. This is because the column labels in the `all_stocks` dataframe must be unique. Since all the columns in the individual dataframes have the same name, `Adj Close`, we must change them to the stock name before joining them. In the space below change the column label `Adj Close` of each individual dataframe to the name of the corresponding stock. You can do this by using the `pd.DataFrame.rename()` function. 


```python
# Change the Adj Close column label to Google
google_stock.rename(columns={'Adj Close': 'google_stock'}, inplace=True)


```


```python
# Change the Adj Close column label to Amazon
amazon_stock.rename(columns={'Adj Close': 'amazon_stock'}, inplace=True)

```


```python


# Change the Adj Close column label to Apple
apple_stock.rename(columns={'Adj Close': 'apple_stock'}, inplace=True)
```


```python
google_stock.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>google_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
    </tr>
  </tbody>
</table>
</div>



You can check that the column labels have been changed correctly by displaying the datadrames


```python
# We display the google_stock DataFrame
amazon_stock.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>amazon_stock</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-03</th>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>69.7500</td>
    </tr>
    <tr>
      <th>2000-01-06</th>
      <td>65.5625</td>
    </tr>
    <tr>
      <th>2000-01-07</th>
      <td>69.5625</td>
    </tr>
  </tbody>
</table>
</div>



Now that we have unique column labels, we can join the individual DataFrames to the `all_stocks` DataFrame. For this we will use the `dataframe.join()` function. The function `dataframe1.join(dataframe2)` joins `dataframe1` with `dataframe2`. We will join each dataframe one by one to the `all_stocks` dataframe. Fill in the code below to join the dataframes, the first join has been made for you:


```python
# We join the Google stock to all_stocks
all_stocks = all_stocks.join(google_stock)

# We join the Apple stock to all_stocks
all_stocks = all_stocks.join(apple_stock)

# We join the Amazon stock to all_stocks
all_stocks = all_stocks.join(amazon_stock)
```

You can check that the dataframes have been joined correctly by displaying the `all_stocks`  dataframe


```python
# We display the google_stock DataFrame
all_stocks.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2000-01-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-02</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2000-01-03</th>
      <td>NaN</td>
      <td>3.596616</td>
      <td>89.3750</td>
    </tr>
    <tr>
      <th>2000-01-04</th>
      <td>NaN</td>
      <td>3.293384</td>
      <td>81.9375</td>
    </tr>
    <tr>
      <th>2000-01-05</th>
      <td>NaN</td>
      <td>3.341579</td>
      <td>69.7500</td>
    </tr>
  </tbody>
</table>
</div>



# To Do

Before we proceed to get some statistics on the stock data, let's first check that we don't have any *NaN* values. In the space below check if there are any *NaN* values in the `all_stocks`  dataframe. If there are any, remove any rows that have *NaN* values:


```python
# Check if there are any NaN values in the all_stocks dataframe
all_stocks.isnull()

# Remove any rows that contain NaN values
all_stocks.dropna(axis=0)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>google_stock</th>
      <th>apple_stock</th>
      <th>amazon_stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2004-08-19</th>
      <td>49.845802</td>
      <td>1.973460</td>
      <td>38.630001</td>
    </tr>
    <tr>
      <th>2004-08-20</th>
      <td>53.805050</td>
      <td>1.979244</td>
      <td>39.509998</td>
    </tr>
    <tr>
      <th>2004-08-23</th>
      <td>54.346527</td>
      <td>1.997236</td>
      <td>39.450001</td>
    </tr>
    <tr>
      <th>2004-08-24</th>
      <td>52.096165</td>
      <td>2.053144</td>
      <td>39.049999</td>
    </tr>
    <tr>
      <th>2004-08-25</th>
      <td>52.657513</td>
      <td>2.123831</td>
      <td>40.299999</td>
    </tr>
    <tr>
      <th>2004-08-26</th>
      <td>53.606342</td>
      <td>2.227291</td>
      <td>40.189999</td>
    </tr>
    <tr>
      <th>2004-08-27</th>
      <td>52.732029</td>
      <td>2.207371</td>
      <td>39.900002</td>
    </tr>
    <tr>
      <th>2004-08-30</th>
      <td>50.675404</td>
      <td>2.192590</td>
      <td>38.310001</td>
    </tr>
    <tr>
      <th>2004-08-31</th>
      <td>50.854240</td>
      <td>2.216367</td>
      <td>38.139999</td>
    </tr>
    <tr>
      <th>2004-09-01</th>
      <td>49.801090</td>
      <td>2.304405</td>
      <td>38.240002</td>
    </tr>
    <tr>
      <th>2004-09-02</th>
      <td>50.427021</td>
      <td>2.291552</td>
      <td>39.180000</td>
    </tr>
    <tr>
      <th>2004-09-03</th>
      <td>49.681866</td>
      <td>2.263920</td>
      <td>38.740002</td>
    </tr>
    <tr>
      <th>2004-09-07</th>
      <td>50.461796</td>
      <td>2.297979</td>
      <td>38.509998</td>
    </tr>
    <tr>
      <th>2004-09-08</th>
      <td>50.819469</td>
      <td>2.335893</td>
      <td>38.009998</td>
    </tr>
    <tr>
      <th>2004-09-09</th>
      <td>50.824436</td>
      <td>2.294122</td>
      <td>38.070000</td>
    </tr>
    <tr>
      <th>2004-09-10</th>
      <td>52.324677</td>
      <td>2.305047</td>
      <td>38.570000</td>
    </tr>
    <tr>
      <th>2004-09-13</th>
      <td>53.402668</td>
      <td>2.287054</td>
      <td>40.009998</td>
    </tr>
    <tr>
      <th>2004-09-14</th>
      <td>55.384777</td>
      <td>2.280628</td>
      <td>42.669998</td>
    </tr>
    <tr>
      <th>2004-09-15</th>
      <td>55.638126</td>
      <td>2.261993</td>
      <td>42.209999</td>
    </tr>
    <tr>
      <th>2004-09-16</th>
      <td>56.616764</td>
      <td>2.335893</td>
      <td>42.570000</td>
    </tr>
    <tr>
      <th>2004-09-17</th>
      <td>58.365391</td>
      <td>2.386659</td>
      <td>42.959999</td>
    </tr>
    <tr>
      <th>2004-09-20</th>
      <td>59.294346</td>
      <td>2.423287</td>
      <td>43.270000</td>
    </tr>
    <tr>
      <th>2004-09-21</th>
      <td>58.539257</td>
      <td>2.442566</td>
      <td>43.290001</td>
    </tr>
    <tr>
      <th>2004-09-22</th>
      <td>58.807514</td>
      <td>2.372521</td>
      <td>41.380001</td>
    </tr>
    <tr>
      <th>2004-09-23</th>
      <td>60.019630</td>
      <td>2.395013</td>
      <td>41.830002</td>
    </tr>
    <tr>
      <th>2004-09-24</th>
      <td>59.527828</td>
      <td>2.396298</td>
      <td>40.939999</td>
    </tr>
    <tr>
      <th>2004-09-27</th>
      <td>58.747902</td>
      <td>2.411721</td>
      <td>39.930000</td>
    </tr>
    <tr>
      <th>2004-09-28</th>
      <td>63.020115</td>
      <td>2.444494</td>
      <td>39.430000</td>
    </tr>
    <tr>
      <th>2004-09-29</th>
      <td>65.116478</td>
      <td>2.485621</td>
      <td>40.840000</td>
    </tr>
    <tr>
      <th>2004-09-30</th>
      <td>64.381264</td>
      <td>2.490119</td>
      <td>40.860001</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2016-11-17</th>
      <td>771.229980</td>
      <td>108.598877</td>
      <td>756.400024</td>
    </tr>
    <tr>
      <th>2016-11-18</th>
      <td>760.539978</td>
      <td>108.707527</td>
      <td>760.159973</td>
    </tr>
    <tr>
      <th>2016-11-21</th>
      <td>769.200012</td>
      <td>110.357010</td>
      <td>780.000000</td>
    </tr>
    <tr>
      <th>2016-11-22</th>
      <td>768.270020</td>
      <td>110.426147</td>
      <td>785.330017</td>
    </tr>
    <tr>
      <th>2016-11-23</th>
      <td>760.989990</td>
      <td>109.863159</td>
      <td>780.119995</td>
    </tr>
    <tr>
      <th>2016-11-25</th>
      <td>761.679993</td>
      <td>110.416275</td>
      <td>780.369995</td>
    </tr>
    <tr>
      <th>2016-11-28</th>
      <td>768.239990</td>
      <td>110.198975</td>
      <td>766.770020</td>
    </tr>
    <tr>
      <th>2016-11-29</th>
      <td>770.840027</td>
      <td>110.090332</td>
      <td>762.520020</td>
    </tr>
    <tr>
      <th>2016-11-30</th>
      <td>758.039978</td>
      <td>109.161880</td>
      <td>750.570007</td>
    </tr>
    <tr>
      <th>2016-12-01</th>
      <td>747.919983</td>
      <td>108.144531</td>
      <td>743.650024</td>
    </tr>
    <tr>
      <th>2016-12-02</th>
      <td>750.500000</td>
      <td>108.549500</td>
      <td>740.340027</td>
    </tr>
    <tr>
      <th>2016-12-05</th>
      <td>762.520020</td>
      <td>107.769203</td>
      <td>759.359985</td>
    </tr>
    <tr>
      <th>2016-12-06</th>
      <td>759.109985</td>
      <td>108.598877</td>
      <td>764.719971</td>
    </tr>
    <tr>
      <th>2016-12-07</th>
      <td>771.190002</td>
      <td>109.665604</td>
      <td>770.419983</td>
    </tr>
    <tr>
      <th>2016-12-08</th>
      <td>776.419983</td>
      <td>110.742218</td>
      <td>767.330017</td>
    </tr>
    <tr>
      <th>2016-12-09</th>
      <td>789.289978</td>
      <td>112.549728</td>
      <td>768.659973</td>
    </tr>
    <tr>
      <th>2016-12-12</th>
      <td>789.270020</td>
      <td>111.907722</td>
      <td>760.119995</td>
    </tr>
    <tr>
      <th>2016-12-13</th>
      <td>796.099976</td>
      <td>113.774490</td>
      <td>774.340027</td>
    </tr>
    <tr>
      <th>2016-12-14</th>
      <td>797.070007</td>
      <td>113.774490</td>
      <td>768.820007</td>
    </tr>
    <tr>
      <th>2016-12-15</th>
      <td>797.849976</td>
      <td>114.396751</td>
      <td>761.000000</td>
    </tr>
    <tr>
      <th>2016-12-16</th>
      <td>790.799988</td>
      <td>114.544907</td>
      <td>757.770020</td>
    </tr>
    <tr>
      <th>2016-12-19</th>
      <td>794.200012</td>
      <td>115.206673</td>
      <td>766.000000</td>
    </tr>
    <tr>
      <th>2016-12-20</th>
      <td>796.419983</td>
      <td>115.512863</td>
      <td>771.219971</td>
    </tr>
    <tr>
      <th>2016-12-21</th>
      <td>794.559998</td>
      <td>115.621513</td>
      <td>770.599976</td>
    </tr>
    <tr>
      <th>2016-12-22</th>
      <td>791.260010</td>
      <td>114.860977</td>
      <td>766.340027</td>
    </tr>
    <tr>
      <th>2016-12-23</th>
      <td>789.909973</td>
      <td>115.088142</td>
      <td>760.590027</td>
    </tr>
    <tr>
      <th>2016-12-27</th>
      <td>791.549988</td>
      <td>115.819054</td>
      <td>771.400024</td>
    </tr>
    <tr>
      <th>2016-12-28</th>
      <td>785.049988</td>
      <td>115.325203</td>
      <td>772.130005</td>
    </tr>
    <tr>
      <th>2016-12-29</th>
      <td>782.789978</td>
      <td>115.295570</td>
      <td>765.150024</td>
    </tr>
    <tr>
      <th>2016-12-30</th>
      <td>771.820007</td>
      <td>114.396751</td>
      <td>749.869995</td>
    </tr>
  </tbody>
</table>
<p>3115 rows × 3 columns</p>
</div>



Now that you have eliminated any *NaN* values we can now calculate some basic statistics on the stock prices. Fill in the code below


```python
# Print the average stock price for each stock
print('mean:\n ',all_stocks.mean(axis=0))
print()

# Print the median stock price for each stock
print('median:\n ', all_stocks.median())
print()
# Print the standard deviation of the stock price for each stock  
print('std:\n ', all_stocks.std())
print()
# Print the correlation between stocks
print('corr:\n', all_stocks.corr())
```

    mean:
      google_stock    347.420229
    apple_stock      35.222976
    amazon_stock    166.095436
    dtype: float64
    
    median:
      google_stock    286.397247
    apple_stock      17.524017
    amazon_stock     76.980003
    dtype: float64
    
    std:
      google_stock    187.671596
    apple_stock      37.945557
    amazon_stock    189.212345
    dtype: float64
    
    corr:
                   google_stock  apple_stock  amazon_stock
    google_stock      1.000000     0.900242      0.952444
    apple_stock       0.900242     1.000000      0.906296
    amazon_stock      0.952444     0.906296      1.000000


We will now look at how we can compute some rolling statistics, also known as moving statistics. We can calculate for example the rolling mean (moving average) of the Google stock price by using the Pandas `dataframe.rolling().mean()` method. The `dataframe.rolling(N).mean()` calculates the rolling mean over an `N`-day window. In other words, we can take a look at the average stock price every `N`  days using the above method. Fill in the code below to calculate the average stock price every 150 days for Google stock


```python
# We compute the rolling mean using a 150-Day window for Google stock
rollingMean = all_stocks['apple_stock'].rolling(3, center=True).mean()
print(rollingMean)
```

    2000-01-01           NaN
    2000-01-02           NaN
    2000-01-03           NaN
    2000-01-04      3.410526
    2000-01-05      3.229123
    2000-01-06      3.196992
    2000-01-07           NaN
    2000-01-08           NaN
    2000-01-09           NaN
    2000-01-10           NaN
    2000-01-11      2.974086
    2000-01-12      2.963376
    2000-01-13      3.045710
    2000-01-14           NaN
    2000-01-15           NaN
    2000-01-16           NaN
    2000-01-17           NaN
    2000-01-18           NaN
    2000-01-19      3.470101
    2000-01-20      3.549089
    2000-01-21           NaN
    2000-01-22           NaN
    2000-01-23           NaN
    2000-01-24           NaN
    2000-01-25      3.520306
    2000-01-26      3.560469
    2000-01-27      3.446674
    2000-01-28           NaN
    2000-01-29           NaN
    2000-01-30           NaN
                     ...    
    2016-12-02           NaN
    2016-12-03           NaN
    2016-12-04           NaN
    2016-12-05           NaN
    2016-12-06    108.677895
    2016-12-07    109.668900
    2016-12-08    110.985850
    2016-12-09           NaN
    2016-12-10           NaN
    2016-12-11           NaN
    2016-12-12           NaN
    2016-12-13    113.152234
    2016-12-14    113.981910
    2016-12-15    114.238716
    2016-12-16           NaN
    2016-12-17           NaN
    2016-12-18           NaN
    2016-12-19           NaN
    2016-12-20    115.447016
    2016-12-21    115.331784
    2016-12-22    115.190211
    2016-12-23           NaN
    2016-12-24           NaN
    2016-12-25           NaN
    2016-12-26           NaN
    2016-12-27           NaN
    2016-12-28    115.479942
    2016-12-29    115.005841
    2016-12-30           NaN
    2016-12-31           NaN
    Freq: D, Name: apple_stock, Length: 6210, dtype: float64


We can also visualize the rolling mean by plotting the data in our dataframe. In the following lessons you will learn how to use **Matplotlib** to visualize data. For now I will just import matplotlib and plot the Google stock data on top of the rolling mean. You can play around by changing the rolling mean window and see how the plot changes. 


```python
# this allows plots to be rendered in the notebook
%matplotlib inline 

# We import matplotlib into Python
import matplotlib.pyplot as plt


# We plot the Google stock data
plt.plot(all_stocks['google_stock'])

# We plot the rolling mean ontop of our Google stock data
plt.plot(rollingMean)
plt.legend(['Google Stock Price', 'Rolling Mean'])
plt.show()
```


![png](output_28_0.png)

