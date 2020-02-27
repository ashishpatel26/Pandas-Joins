This is practice notebook you can fork star and use this notebook for your use. For More Read this Article: https://www.analyticsvidhya.com/blog/2020/02/joins-in-pandas-master-the-different-types-of-joins-in-python/

# Different Types of Join Example for Practice.


```python
import pandas as pd
```


```python
product=pd.DataFrame({
    'Product_ID':[101,102,103,104,105,106,107],
    'Product_name':['Watch','Bag','Shoes','Smartphone','Books','Oil','Laptop'],
    'Category':['Fashion','Fashion','Fashion','Electronics','Study','Grocery','Electronics'],
    'Price':[299.0,1350.50,2999.0,14999.0,145.0,110.0,79999.0],
    'Seller_City':['Delhi','Mumbai','Chennai','Kolkata','Delhi','Chennai','Bengalore']
})
```


```python
product
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>1</th>
      <td>102</td>
      <td>Bag</td>
      <td>Fashion</td>
      <td>1350.5</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
    </tr>
    <tr>
      <th>4</th>
      <td>105</td>
      <td>Books</td>
      <td>Study</td>
      <td>145.0</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>5</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
    </tr>
  </tbody>
</table>
</div>



### Inner Join

![](https://cdn.analyticsvidhya.com/wp-content/uploads/2020/02/jip14-300x204.png)

> ***Inner join is the most common type of join you’ll be working with. It returns a dataframe with only those rows that have common characteristics.***


```python
customer=pd.DataFrame({
    'id':[1,2,3,4,5,6,7,8,9],
    'name':['Olivia','Aditya','Cory','Isabell','Dominic','Tyler','Samuel','Daniel','Jeremy'],
    'age':[20,25,15,10,30,65,35,18,23],
    'Product_ID':[101,0,106,0,103,104,0,0,107],
    'Purchased_Product':['Watch','NA','Oil','NA','Shoes','Smartphone','NA','NA','Laptop'],
    'City':['Mumbai','Delhi','Bangalore','Chennai','Chennai','Delhi','Kolkata','Delhi','Mumbai']
})
customer
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
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Product_ID</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>101</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Aditya</td>
      <td>25</td>
      <td>0</td>
      <td>NA</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>106</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Isabell</td>
      <td>10</td>
      <td>0</td>
      <td>NA</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>103</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>104</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>Samuel</td>
      <td>35</td>
      <td>0</td>
      <td>NA</td>
      <td>Kolkata</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>Daniel</td>
      <td>18</td>
      <td>0</td>
      <td>NA</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>107</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product,customer,on='Product_ID')
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>4</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product,customer,left_on='Product_name',right_on='Purchased_Product')
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
      <th>Product_ID_x</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Product_ID_y</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>101</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>103</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>104</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>106</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>4</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>107</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product,customer,how='inner',left_on=['Product_ID','Seller_City'],right_on=['Product_ID','City'])
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
  </tbody>
</table>
</div>



### Full Join in Pandas

![](https://cdn.analyticsvidhya.com/wp-content/uploads/2020/02/jip15-300x197.png)

> ***Full Join, also known as Full Outer Join, returns all those records which either have a match in the left or right dataframe.***


```python
pd.merge(product,customer,on='Product_ID',how='outer')
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1.0</td>
      <td>Olivia</td>
      <td>20.0</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>102</td>
      <td>Bag</td>
      <td>Fashion</td>
      <td>1350.5</td>
      <td>Mumbai</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5.0</td>
      <td>Dominic</td>
      <td>30.0</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6.0</td>
      <td>Tyler</td>
      <td>65.0</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>4</th>
      <td>105</td>
      <td>Books</td>
      <td>Study</td>
      <td>145.0</td>
      <td>Delhi</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3.0</td>
      <td>Cory</td>
      <td>15.0</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9.0</td>
      <td>Jeremy</td>
      <td>23.0</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>Aditya</td>
      <td>25.0</td>
      <td>NA</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>Isabell</td>
      <td>10.0</td>
      <td>NA</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>Samuel</td>
      <td>35.0</td>
      <td>NA</td>
      <td>Kolkata</td>
    </tr>
    <tr>
      <th>10</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>Daniel</td>
      <td>18.0</td>
      <td>NA</td>
      <td>Delhi</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product,customer,on='Product_ID',how='outer',indicator=True)
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
      <th>_merge</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1.0</td>
      <td>Olivia</td>
      <td>20.0</td>
      <td>Watch</td>
      <td>Mumbai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>1</th>
      <td>102</td>
      <td>Bag</td>
      <td>Fashion</td>
      <td>1350.5</td>
      <td>Mumbai</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>left_only</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5.0</td>
      <td>Dominic</td>
      <td>30.0</td>
      <td>Shoes</td>
      <td>Chennai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6.0</td>
      <td>Tyler</td>
      <td>65.0</td>
      <td>Smartphone</td>
      <td>Delhi</td>
      <td>both</td>
    </tr>
    <tr>
      <th>4</th>
      <td>105</td>
      <td>Books</td>
      <td>Study</td>
      <td>145.0</td>
      <td>Delhi</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>left_only</td>
    </tr>
    <tr>
      <th>5</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3.0</td>
      <td>Cory</td>
      <td>15.0</td>
      <td>Oil</td>
      <td>Bangalore</td>
      <td>both</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9.0</td>
      <td>Jeremy</td>
      <td>23.0</td>
      <td>Laptop</td>
      <td>Mumbai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>Aditya</td>
      <td>25.0</td>
      <td>NA</td>
      <td>Delhi</td>
      <td>right_only</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>Isabell</td>
      <td>10.0</td>
      <td>NA</td>
      <td>Chennai</td>
      <td>right_only</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>Samuel</td>
      <td>35.0</td>
      <td>NA</td>
      <td>Kolkata</td>
      <td>right_only</td>
    </tr>
    <tr>
      <th>10</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>Daniel</td>
      <td>18.0</td>
      <td>NA</td>
      <td>Delhi</td>
      <td>right_only</td>
    </tr>
  </tbody>
</table>
</div>



### Left Join in Pandas

![](https://cdn.analyticsvidhya.com/wp-content/uploads/2020/02/jip16-300x203.png)

> ***Left join, also known as Left Outer Join, returns a dataframe containing all the rows of the left dataframe.***


```python
pd.merge(product,customer,on='Product_ID',how='left', indicator=True)
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
      <th>_merge</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1.0</td>
      <td>Olivia</td>
      <td>20.0</td>
      <td>Watch</td>
      <td>Mumbai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>1</th>
      <td>102</td>
      <td>Bag</td>
      <td>Fashion</td>
      <td>1350.5</td>
      <td>Mumbai</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>left_only</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5.0</td>
      <td>Dominic</td>
      <td>30.0</td>
      <td>Shoes</td>
      <td>Chennai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6.0</td>
      <td>Tyler</td>
      <td>65.0</td>
      <td>Smartphone</td>
      <td>Delhi</td>
      <td>both</td>
    </tr>
    <tr>
      <th>4</th>
      <td>105</td>
      <td>Books</td>
      <td>Study</td>
      <td>145.0</td>
      <td>Delhi</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>left_only</td>
    </tr>
    <tr>
      <th>5</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3.0</td>
      <td>Cory</td>
      <td>15.0</td>
      <td>Oil</td>
      <td>Bangalore</td>
      <td>both</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9.0</td>
      <td>Jeremy</td>
      <td>23.0</td>
      <td>Laptop</td>
      <td>Mumbai</td>
      <td>both</td>
    </tr>
  </tbody>
</table>
</div>



### Right Join in Pandas

![](https://cdn.analyticsvidhya.com/wp-content/uploads/2020/02/jip17-300x198.png)

> ***Right join, also known as Right Outer Join, is similar to the Left Outer Join. The only difference is that all the rows of the right dataframe are taken as it is and only those of the left dataframe that are common in both.***


```python
pd.merge(product,customer,on='Product_ID',how='right', indicator= True)
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
      <th>_merge</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>Watch</td>
      <td>Mumbai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>1</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>2</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>Smartphone</td>
      <td>Delhi</td>
      <td>both</td>
    </tr>
    <tr>
      <th>3</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>Oil</td>
      <td>Bangalore</td>
      <td>both</td>
    </tr>
    <tr>
      <th>4</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
      <td>both</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2</td>
      <td>Aditya</td>
      <td>25</td>
      <td>NA</td>
      <td>Delhi</td>
      <td>right_only</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4</td>
      <td>Isabell</td>
      <td>10</td>
      <td>NA</td>
      <td>Chennai</td>
      <td>right_only</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7</td>
      <td>Samuel</td>
      <td>35</td>
      <td>NA</td>
      <td>Kolkata</td>
      <td>right_only</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8</td>
      <td>Daniel</td>
      <td>18</td>
      <td>NA</td>
      <td>Delhi</td>
      <td>right_only</td>
    </tr>
  </tbody>
</table>
</div>



### Handling Redundancy/Duplicates in Joins


```python
product_dup=pd.DataFrame({'Product_ID':[101,102,103,104,105,106,107,103,107],
                          'Product_name':['Watch','Bag','Shoes','Smartphone','Books','Oil','Laptop','Shoes','Laptop'],
                          'Category':['Fashion','Fashion','Fashion','Electronics','Study','Grocery','Electronics','Fashion','Electronics'],
                          'Price':[299.0,1350.50,2999.0,14999.0,145.0,110.0,79999.0,2999.0,79999.0],
                          'Seller_City':['Delhi','Mumbai','Chennai','Kolkata','Delhi','Chennai','Bengalore','Chennai','Bengalore']})
```


```python
product_dup
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>1</th>
      <td>102</td>
      <td>Bag</td>
      <td>Fashion</td>
      <td>1350.5</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
    </tr>
    <tr>
      <th>4</th>
      <td>105</td>
      <td>Books</td>
      <td>Study</td>
      <td>145.0</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>5</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
    </tr>
    <tr>
      <th>7</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>8</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product_dup,customer,how='inner',on='Product_ID')
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>4</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>5</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product_dup.drop_duplicates(),customer,how='inner',on='Product_ID')
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>4</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(product_dup,customer,how='inner',on='Product_ID',validate='many_to_many')
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
      <th>Product_ID</th>
      <th>Product_name</th>
      <th>Category</th>
      <th>Price</th>
      <th>Seller_City</th>
      <th>id</th>
      <th>name</th>
      <th>age</th>
      <th>Purchased_Product</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>101</td>
      <td>Watch</td>
      <td>Fashion</td>
      <td>299.0</td>
      <td>Delhi</td>
      <td>1</td>
      <td>Olivia</td>
      <td>20</td>
      <td>Watch</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>1</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>2</th>
      <td>103</td>
      <td>Shoes</td>
      <td>Fashion</td>
      <td>2999.0</td>
      <td>Chennai</td>
      <td>5</td>
      <td>Dominic</td>
      <td>30</td>
      <td>Shoes</td>
      <td>Chennai</td>
    </tr>
    <tr>
      <th>3</th>
      <td>104</td>
      <td>Smartphone</td>
      <td>Electronics</td>
      <td>14999.0</td>
      <td>Kolkata</td>
      <td>6</td>
      <td>Tyler</td>
      <td>65</td>
      <td>Smartphone</td>
      <td>Delhi</td>
    </tr>
    <tr>
      <th>4</th>
      <td>106</td>
      <td>Oil</td>
      <td>Grocery</td>
      <td>110.0</td>
      <td>Chennai</td>
      <td>3</td>
      <td>Cory</td>
      <td>15</td>
      <td>Oil</td>
      <td>Bangalore</td>
    </tr>
    <tr>
      <th>5</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
    <tr>
      <th>6</th>
      <td>107</td>
      <td>Laptop</td>
      <td>Electronics</td>
      <td>79999.0</td>
      <td>Bengalore</td>
      <td>9</td>
      <td>Jeremy</td>
      <td>23</td>
      <td>Laptop</td>
      <td>Mumbai</td>
    </tr>
  </tbody>
</table>
</div>


