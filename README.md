# Superstore Sales Project

## About

Data is obtained from Kaggle. I chose to do this dataset because it offers a comprehensive platform for exploring real-world business dynamics, particularly in sales and customer behavior. The dataset provides rich insights into various factors like product performance, regional trends, and customer preferences. This alllows me to do in-depth exploration of sales patterns.


#### Dataset:
https://www.kaggle.com/datasets/ishanshrivastava28/superstore-sales

## Purposes of The Project

The purpose of this project was to answer key business questions that provide a deeper understanding of sales performance and customer behavior. This was all done using Python for data analysis and PowerBI for data visualization.


### Business Questions To Answer:

**1.	Sales per State:** Which states generate the highest total sales?

**2.	Sales per Quarter:** What are the seasonal trends in sales over time?

**3.	Top 10 Most Profitable Products:** Which products bring the most profit?

**4.	Least Profitable Products:** Which products are causing losses and need review?

**5.	Most Profitable Categories:** Which categories yield the highest profit?

**6.	Least Profitable Categories:** Which categories are underperforming?

**7.	Top 10 Best-Selling Products:** Which products have the highest quantity sold?

**8.	Customer Segments with Highest Sales:** Which customer segments bring in the most revenue?

**9.	Repeat Customers and Their Impact on Sales:** How loyal are customers, and what is their impact on total sales?

## Approach Used

### Data Cleaning and Preparation in Python:
> This process ensures the data is clean and ready for analysis.

> Check ________ for code

#### Load the Dataset:
  -	Use pandas to load the dataset into a DataFrame.
  
  -	Review for null values, duplicates, and data types.

#### Check for Outliers:
  -	Inspect columns like Quantity, Profit, and Price for unusual entries.

#### Handle Missing Values:

  -	Drop or fill missing values as necessary (e.g., use .fillna() or .dropna()).

#### Calculate Key Metrics:

-	Add calculated fields such as Profit Margin (%) = (Profit / Sales) * 100.

### Perform Python Code for Analysis:
> This section demonstrates how Python was used to perform exploratory data analysis (EDA) and answer the business questions.

#### Import Pandas as pd
**Load Dataset:**
  df = pd.read_csv('/mnt/data/your_dataset.csv')

  

#### Convert 'Order Date' to datetime format for time-based analysis:
df['Order Date'] = pd.to_datetime(df['Order Date'], format='%d/%m/%Y')



### Question 1: Sales per state

#### Calculating Sales per State:

```python
state_sales = df.groupby('State').agg(
    total_sales=('Sales', 'sum')
).reset_index()

print(state_sales)
state_sales.to_csv('state_sales.csv', index=False)  


```
This groups the data by each unique state in the **State** column and calculates the sum of the **Sales** column for each state, storing the result in a new DataFrame **state_sales** with columns:

- **State:** Each unique state in the data.
- **total_sales:** The sum of sales for each state.

**Printing the DataFrame:**

```python
print(state_sales)
```
- This prints the **state_sales** DataFrame to the console, showing the total sales per state.

**Exporting the Data for PowerBI:**
```python
state_sales.to_csv('state_sales.csv', index=False)
```
- This saves the **state_sales** DataFrame as a CSV file named ***state_sales.csv***
- The CSV file can be used in Power BI to create a map visualization, showing sales per state.























