# Perform Python Code for Analysis:
> This section demonstrates how Python was used to perform exploratory data analysis (EDA) and answer the business questions.


## Question 1: Sales per state

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

  

## Question 2: Sales Per Quarter

#### Create a Quarter Column:

```python
df['Quarter'] = df['Order Date'].dt.to_period('Q')
```
- This line adds a new column called **Quarter** to the DataFrame. It converts the Order Date column to a quarterly period format.
- This allows me to group sales data by quarter.

#### Group by Quarter and Calculate Total Sales:

```python
quarter_sales = df.groupby('Quarter').agg(
    total_sales=('Sales', 'sum')
).reset_index()
```

- This line groups the DataFrame by the newly created **Quarter** column.
- For each quarter, it calculates the total sales by summing up the **Sales** column. The result is a new DataFrame ***(quarter_sales)*** that contains two columns: **Quarter** and **total_sales.**
