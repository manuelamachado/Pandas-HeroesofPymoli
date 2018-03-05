
# Heroes of Pymoli

1. The typical persona is a young male as the average player is male (82%) and between 15-24 years old (72%).
2. Almost every player is purchasing an item, however, they are not willing to buy a large quantity of items (only two people bought more than 1 item - 2 each).
3. Mourning Blade, despite being more expensive than the average item, is the most popular one but only has 3 purchases.  All other items have been purchased two or fewer times, indicating that players have varying consumer trends.


```python
import pandas as pd
import os
```


```python
purchase_data = ['1']
purchase_data = ['2']

# Get json
purchase_datajson = os.path.join("/Users/manuelamachado/python-challenge/HeroesofPymoli", 'purchase_data' + purchase_data[0] + '.json')


purchasedata = pd.read_json(purchase_datajson)
purchasedata.head()
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>4.49</td>
      <td>Iloni35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>12</td>
      <td>Dawne</td>
      <td>3.36</td>
      <td>Aidaira26</td>
    </tr>
    <tr>
      <th>2</th>
      <td>17</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>2.63</td>
      <td>Irim47</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17</td>
      <td>Male</td>
      <td>123</td>
      <td>Twilight's Carver</td>
      <td>2.55</td>
      <td>Irith83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>22</td>
      <td>Male</td>
      <td>154</td>
      <td>Feral Katana</td>
      <td>4.11</td>
      <td>Philodil43</td>
    </tr>
  </tbody>
</table>
</div>



## Player Count


```python
# Total Number of Players

player_count = len(purchasedata["SN"].unique())

pd.DataFrame({"Total Players":[player_count]})


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
      <th>Total Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>74</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Number of Unique Items

uniq_items = len(purchasedata["Item Name"].unique())  

pd.DataFrame({"Unique Items":[uniq_items]})


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
      <th>Unique Items</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>63</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Average Purchase Price
av_price = purchasedata["Price"].mean()

av_price = pd.DataFrame({"Average Price":[av_price]})

av_price["Average Price"] = av_price["Average Price"].map("${:.2f}".format)

av_price
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
      <th>Average Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>$2.92</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Total Number of Purchases
total_purchase = purchasedata["Price"].count()

pd.DataFrame({"Total Purchases":[total_purchase]})

#total_purchase = pd.DataFrame([purchasedata["Price"].count()], columns = ["Total Purchases"])

#total_purchase
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
      <th>Total Purchases</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>78</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Total Revenue
total_rev = purchasedata["Price"].sum()

total_rev = pd.DataFrame({"Total Revenue":[total_rev]})

total_rev["Total Revenue"] = total_rev["Total Revenue"].map("${:.2f}".format)

total_rev
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
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>$228.10</td>
    </tr>
  </tbody>
</table>
</div>



## Purchasing Analysis (Total)


```python
# Purchasing Analysis

PurchasingAnalysis_table = pd.DataFrame({"Number of Unique Items": uniq_items,
                              "Total Revenue": total_rev,
                              "Number of Purchases": total_purchase,
                              "Average Purchase Price": av_price["Average Price"]})

PurchasingAnalysis_table
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
      <th>Average Purchase Price</th>
      <th>Number of Purchases</th>
      <th>Number of Unique Items</th>
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>$2.92</td>
      <td>78</td>
      <td>63</td>
      <td>$228.10</td>
    </tr>
  </tbody>
</table>
</div>



## Gender Demographics


```python
#Gender Demographics
# Percentage and Count of Male Players/Female Players and Other/Non_Disclosed
gender_df = pd.DataFrame(purchasedata["Gender"].value_counts()) 
gender_df

gender_df.columns=["Total Count"]
gender_df

percent = (gender_df["Total Count"]/78)*100
gender_df["Percentage of Players"] = percent

gender_df["Percentage of Players"] = gender_df["Percentage of Players"].map("{0:.2f}%".format)

gender_df
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
      <th>Total Count</th>
      <th>Percentage of Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>64</td>
      <td>82.05%</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>13</td>
      <td>16.67%</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>1</td>
      <td>1.28%</td>
    </tr>
  </tbody>
</table>
</div>



## Purchase Analysis (Gender)


```python
#Purchase Analysis (Gender)
#Unique Count
unique_count = purchasedata.groupby(["Gender"])["SN"].nunique()

# Purchase Count by gender
grouped_purch_c = purchasedata.groupby(["Gender"]).count()["Price"].rename("Purchase Count")

# Average Purchase Price
grouped_purch_a = purchasedata.groupby(["Gender"]).mean()["Price"].rename("Average Value")

# Total Purchase Value
grouped_purch_v = purchasedata.groupby(["Gender"]).sum()["Price"].rename("Purchase Value")

# Normalized Totals
normalized_total = grouped_purch_v / unique_count

#Table Frame
gender_pa_table = pd.DataFrame({"Normalized Total": normalized_total, 
                            "Purchase Count": grouped_purch_c, 
                            "Total Purchase Value": grouped_purch_v, 
                            "Average Purchase Value": grouped_purch_a})

gender_pa_table["Average Purchase Value"]  = gender_pa_table["Average Purchase Value"].map("${:.2f}".format)
gender_pa_table["Normalized Total"] = gender_pa_table["Normalized Total"].map("${:.2f}".format)
gender_pa_table["Total Purchase Value"] = gender_pa_table["Total Purchase Value"].map("${:.2f}".format)


gender_pa_table
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
      <th>Average Purchase Value</th>
      <th>Normalized Total</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>$3.18</td>
      <td>$3.18</td>
      <td>13</td>
      <td>$41.38</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>$2.88</td>
      <td>$3.08</td>
      <td>64</td>
      <td>$184.60</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>$2.12</td>
      <td>$2.12</td>
      <td>1</td>
      <td>$2.12</td>
    </tr>
  </tbody>
</table>
</div>



## Age Demographics


```python
# Age Demographics

# The below each broken into bins of 4 years (i.e. <10, 10-14, 15-19, etc.)
bins = [0 ,10 ,15 ,20 ,25 ,30 ,35 ,40 ,45]
Age_ranges = ['0-10','10-14','15-19','20-24','25-29','30-34','35-39', '40-45']

pd.cut(purchasedata["Age"], bins, labels = Age_ranges).head()

purchasedata["Age Range"] = pd.cut(purchasedata["Age"],bins,labels = Age_ranges)
purchasedata.head()

#Group by Age Range
group = purchasedata.groupby("Age Range")

# Purchase Count
sn_count = purchasedata.groupby(["Age Range"]).count()["Age"]
sn_count

# Average Purchase Value
average_price = purchasedata.groupby(["Age Range"]).mean()["Price"]
average_price

# Total Purchase Value
total_purch_v = purchasedata.groupby(["Age Range"]).sum()["Price"]
total_purch_v

# Normalized Totals
normalized_total = total_purch_v /sn_count

table = pd.DataFrame({"Purchase Count": sn_count, 
                      "Total Purchase Value": total_purch_v, 
                      "Average Purchase Value": average_price,
                      "Normalized Total": normalized_total})

table["Average Purchase Value"] = table["Average Purchase Value"].map("${:.2f}".format)
table["Normalized Total"] = table["Normalized Total"].map("${:.2f}".format)
table["Total Purchase Value"] = table["Total Purchase Value"].map("${:.2f}".format)


table
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
      <th>Average Purchase Value</th>
      <th>Normalized Total</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Age Range</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0-10</th>
      <td>$2.76</td>
      <td>$2.76</td>
      <td>5</td>
      <td>$13.82</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>$3.05</td>
      <td>$3.05</td>
      <td>4</td>
      <td>$12.21</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>$2.73</td>
      <td>$2.73</td>
      <td>20</td>
      <td>$54.69</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>$3.04</td>
      <td>$3.04</td>
      <td>33</td>
      <td>$100.42</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>$2.69</td>
      <td>$2.69</td>
      <td>4</td>
      <td>$10.77</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>$2.35</td>
      <td>$2.35</td>
      <td>7</td>
      <td>$16.47</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>$3.94</td>
      <td>$3.94</td>
      <td>5</td>
      <td>$19.72</td>
    </tr>
    <tr>
      <th>40-45</th>
      <td>$nan</td>
      <td>$nan</td>
      <td>0</td>
      <td>$0.00</td>
    </tr>
  </tbody>
</table>
</div>



## Top Spenders


```python
# Top Spenders
# Identify the the top 5 spenders in the game by total purchase value, then list (in a table):

# Purchase Count top 5
grouped_top_c = purchasedata.groupby(["SN"]).count()["Price"].rename("Purchase Count")

# Average Purchase Price
grouped_top_a = purchasedata.groupby(["SN"]).mean()["Price"].rename("Average Value")

# Total Purchase Value
grouped_top_v = purchasedata.groupby(["SN"]).sum()["Price"].rename("Purchase Value")



top_table = pd.DataFrame({"Purchase Count": grouped_top_c, 
                            "Total Purchase Value": grouped_top_v, 
                            "Average Purchase Value": grouped_top_a})

top_table["Average Purchase Value"] = top_table["Average Purchase Value"].map("${:.2f}".format)
top_table["Total Purchase Value"] = top_table["Total Purchase Value"].map("${:.2f}".format)

top_table.sort_values("Total Purchase Value", ascending=False).head(5)
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
      <th>Average Purchase Value</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Sundaky74</th>
      <td>$3.71</td>
      <td>2</td>
      <td>$7.41</td>
    </tr>
    <tr>
      <th>Aidaira26</th>
      <td>$2.56</td>
      <td>2</td>
      <td>$5.13</td>
    </tr>
    <tr>
      <th>Eusty71</th>
      <td>$4.81</td>
      <td>1</td>
      <td>$4.81</td>
    </tr>
    <tr>
      <th>Chanirra64</th>
      <td>$4.78</td>
      <td>1</td>
      <td>$4.78</td>
    </tr>
    <tr>
      <th>Alarap40</th>
      <td>$4.71</td>
      <td>1</td>
      <td>$4.71</td>
    </tr>
  </tbody>
</table>
</div>



## Most Popular Items


```python
# Most Popular Items
# Identify the 5 most popular items by purchase count, then list (in a table):

# Item ID
# Item Name

# Purchase Count
user_count = pd.DataFrame(purchasedata.groupby(["Item ID", "Item Name"])["Price"].count())

# Total Purchase Value
user_total = pd.DataFrame(purchasedata.groupby(["Item ID", "Item Name"])["Price"].sum())

# Item Price
user_average = pd.DataFrame(purchasedata.groupby(["Item ID", "Item Name"])["Price"].mean())

table = pd.DataFrame({"Purchase Count": user_count ['Price'], 
                     "Item Price": user_average ['Price'],
                     "Total Purchase Value": user_total ['Price']})

table["Item Price"] = table["Item Price"].map("${:.2f}".format)
table["Total Purchase Value"] = table["Total Purchase Value"].map("${:.2f}".format)


table= table.sort_values(["Purchase Count"], ascending=False)

table[['Purchase Count','Item Price','Total Purchase Value']].head(5)
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
      <th></th>
      <th>Purchase Count</th>
      <th>Item Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>94</th>
      <th>Mourning Blade</th>
      <td>3</td>
      <td>$3.64</td>
      <td>$10.92</td>
    </tr>
    <tr>
      <th>90</th>
      <th>Betrayer</th>
      <td>2</td>
      <td>$4.12</td>
      <td>$8.24</td>
    </tr>
    <tr>
      <th>111</th>
      <th>Misery's End</th>
      <td>2</td>
      <td>$1.79</td>
      <td>$3.58</td>
    </tr>
    <tr>
      <th>64</th>
      <th>Fusion Pummel</th>
      <td>2</td>
      <td>$2.42</td>
      <td>$4.84</td>
    </tr>
    <tr>
      <th>154</th>
      <th>Feral Katana</th>
      <td>2</td>
      <td>$4.11</td>
      <td>$8.22</td>
    </tr>
  </tbody>
</table>
</div>



## Most Profitable Items


```python
# Most Profitable Items
# Identify the 5 most profitable items by total purchase value, then list (in a table):

# Item ID
# Item Name

# Purchase Count
user_count = pd.DataFrame(purchasedata.groupby(["Item ID", "Item Name"])["Price"].count())

#Total Purchase Value
user_total = pd.DataFrame(purchasedata.groupby(["Item ID", "Item Name"])["Price"].sum())

# Item Price
user_average = pd.DataFrame(purchasedata.groupby(["Item ID", "Item Name"])["Price"].mean())

table = pd.DataFrame({"Purchase Count": user_count ['Price'], 
                     "Item Price": user_average ['Price'],
                     "Total Purchase Value": user_total ['Price']})

table["Item Price"] = table["Item Price"].map("${:.2f}".format)
table["Total Purchase Value"] = table["Total Purchase Value"].map("${:.2f}".format)

table= table.sort_values(["Total Purchase Value"], ascending=False)

table[['Purchase Count','Item Price','Total Purchase Value']].head()
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
      <th></th>
      <th>Purchase Count</th>
      <th>Item Price</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>117</th>
      <th>Heartstriker, Legacy of the Light</th>
      <td>2</td>
      <td>$4.71</td>
      <td>$9.42</td>
    </tr>
    <tr>
      <th>93</th>
      <th>Apocalyptic Battlescythe</th>
      <td>2</td>
      <td>$4.49</td>
      <td>$8.98</td>
    </tr>
    <tr>
      <th>90</th>
      <th>Betrayer</th>
      <td>2</td>
      <td>$4.12</td>
      <td>$8.24</td>
    </tr>
    <tr>
      <th>154</th>
      <th>Feral Katana</th>
      <td>2</td>
      <td>$4.11</td>
      <td>$8.22</td>
    </tr>
    <tr>
      <th>180</th>
      <th>Stormcaller</th>
      <td>2</td>
      <td>$2.77</td>
      <td>$5.54</td>
    </tr>
  </tbody>
</table>
</div>


