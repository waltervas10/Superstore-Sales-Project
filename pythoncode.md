# Performing Python Code for Analysis:
**This section demonstrates how Python was used to perform exploratory data analysis (EDA) and answer the business questions.**

##  Question 1: Sales Per State 

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

<br><br><br>


##  Question 2: Sales Per Quarter
```python
df['Quarter'] = df['Order Date'].dt.to_period('Q')

quarter_sales = df.groupby('Quarter').agg(
    total_sales=('Sales', 'sum')
).reset_index()

print(quarter_sales)
quarter_sales.to_csv('quarter_sales.csv', index=False)  
```
### Breakdown:
#### Creating a Quarter Column:

```python
df['Quarter'] = df['Order Date'].dt.to_period('Q')
```
- This line adds a new column called **Quarter** to the DataFrame. It converts the Order Date column to a quarterly period format. This allows me to group sales data by quarter.

#### Grouping by Quarter and Calculate Total Sales:

```python
quarter_sales = df.groupby('Quarter').agg(
    total_sales=('Sales', 'sum')
).reset_index()
```

- This line groups the DataFrame by the newly created **Quarter** column.
- For each quarter, it calculates the total sales by summing up the **Sales** column. The result is a new DataFrame ***(quarter_sales)*** that contains two columns: **Quarter** and **total_sales.**

<br><br><br>


## Question 3: Top 10 Most Profitable Products

```python

top_profitable_products = df.groupby('Product Name').agg(
    total_profit=('Profit', 'sum')
).sort_values(by='total_profit', ascending=False).head(10).reset_index()

print(top_profitable_products)
```
### Breakdown:
#### Grouping by Product Name and Calculate Total Profit:

```python
top_profitable_products = df.groupby('Product Name').agg(
    total_profit=('Profit', 'sum')
```
- This line groups the DataFrame by the **Product Name** column
- It calculates the total profit for each product by summing the **Profit** column.

#### Sorting by Total Profit:

```python
).sort_values(by='total_profit', ascending=False).head(10).reset_index()
```
- This line sorts the resulting DataFrame in the descending order based on the ***total_profit*** values. 
- Top 10 products with the highest total profits will appear at the top of the DataFrame.

<br><br><br>



## Question 4: Least Profitable Products

```python
least_profitable_products = df.groupby('Product Name').agg(
    total_profit=('Profit', 'sum')
).sort_values(by='total_profit').head(10).reset_index()

print(least_profitable_products)
```
### Breakdown:
#### Grouping by Product Name and Calculating Total Profit:

```python
least_profitable_products = df.groupby('Product Name').agg(
    total_profit=('Profit', 'sum')
```

- This line groups the DataFrame (df) by the **Product Name** column.
- It calculates the total profit for each product by summing the values in the Profit column

#### Selecting Top 10 Least Profitable Products:
```python
).sort_values(by='total_profit').head(10).reset_index()
```
- This line sorts the top 10 resulting DataFrame in ascending order based on the **total_profit** values.
- This means that products with the lowest total profits will appear at the top of the DataFrame.


<br><br><br>


## Question 5: Most Profitable Categories

```python
most_profitable_categories = df.groupby('Category').agg(
    total_profit=('Profit', 'sum')
).sort_values(by='total_profit', ascending=False).reset_index()

print(most_profitable_categories)
```
### Breakdown:
#### Grouping by Category and Calculating Total Profit:

```python
most_profitable_categories = df.groupby('Category').agg(
    total_profit=('Profit', 'sum')
```
- This line groups the DataFrame (df) by the **Category** column.
- This calculates the total profit for each category by summing the values in the **Profit** column. 

#### Sorting by Total Profit in Descending Order:

```python
).sort_values(by='total_profit', ascending=False).reset_index()
```
- This line sorts the resulting DataFrame in descending order based on the ***total_profit*** values.
- Categories with the highest total profits will appear at the top.

<br><br><br>


## Question 6: Least Profitable Categories

```python
least_profitable_categories = df.groupby('Category').agg(
    total_profit=('Profit', 'sum')
).sort_values(by='total_profit').reset_index()

print(least_profitable_categories)
```
### Breakdown:

#### Grouping by Category and Calculating Total Profit:

```python
least_profitable_categories = df.groupby('Category').agg(
    total_profit=('Profit', 'sum')
```
- This line groups the DataFrame (df) by the Category column.
- This calculates the total profit for each category by summing up the values in the Profit column.

#### Sorting by Total Profit in Ascending Order:

```python
).sort_values(by='total_profit').reset_index()
```

- This line sorts the resulting DataFrame in ascending order based on the ***total_profit*** values.
- Categories with the lowest total profits will appear at the top.

<br><br><br>

## Question 7: Top 10 Best Selling Products

```python
top_selling_products = df.groupby('Product Name').agg(
    total_quantity=('Quantity', 'sum')
).sort_values(by='total_quantity', ascending=False).head(10).reset_index()

print(top_selling_products)
```
### Breakdown:

#### Grouping by Product Name and Calculating Total Quantity Sold:

```python
top_selling_products = df.groupby('Product Name').agg(
    total_quantity=('Quantity', 'sum')
```
- This line groups the DataFrame (df) by the **Product Name** column.
- This calculates the total quantity sold for each product by summing the values in the **Quantity** column.

#### Selecting Top 10 Best-Selling Products:

```python
).sort_values(by='total_quantity', ascending=False).head(10).reset_index()
```
- This line sorts the resulting DataFrame in descending order based on ***total_quantity.***
- This retrieves the top 10 products from the sorted DataFrame, representing those with the highest total quantities sold.

<br><br><br>

## Question 8: Customer Segments with Highest Sales

```python
segment_sales = df.groupby('Segment').agg(
    total_sales=('Sales', 'sum')
).sort_values(by='total_sales', ascending=False).reset_index()

print(segment_sales)
```
### Breakdown:

#### Grouping by Segment and Calcultaing Total Sales:

```python
segment_sales = df.groupby('Segment').agg(
    total_sales=('Sales', 'sum')
```
- This line groups the DataFrame (df) by the **Segment** column.
- It calculates the total sales for each segment by summing the values in the **Sales** column.

#### Selecting Segments with Highest Total Sales:

```python
).sort_values(by='total_sales', ascending=False).reset_index()
```

- This line sorts the resulting DataFrame in descending order based on total_sales.
- Segments with the highest total sales will appear at the top.


<br><br><br>


## Question 9: Repeat Customers and Their Impact on Sales

```python
repeat_customers = df.groupby('Customer ID').agg(
    order_count=('Order ID', 'nunique'),
    total_sales=('Sales', 'sum')
).sort_values(by='order_count', ascending=False).reset_index()

print(repeat_customers.head(10))  
```

## Breakdown:

#### Grouping by Customer ID and Calculating Order Count and Total Sales:

```python
repeat_customers = df.groupby('Customer ID').agg(
    order_count=('Order ID', 'nunique'),
    total_sales=('Sales', 'sum')
```

- This line groups the DataFrame (df) by the **Customer ID** column.
- It calculates two metrics for each customer:
  - **order_count:** The number of unique orders placed by each customer, using the ***nunique*** function on the **Order     ID** column.
  - **total_sales:** The total sales for each customer, calculated by summing the **Sales** column.
 
#### Selecting Customers with Highest Number of Unique Orders:

```python
).sort_values(by='order_count', ascending=False).reset_index()
```

- This line sorts the resulting DataFrame by ***order_count*** in descending order.
- Customers with the highest number of unique orders (i.e., repeat customers) will appear at the top.

#### Printing the Top 10 Repeat Customers:

```python
print(repeat_customers.head(10))
```
- This line prints the top 10 repeat customers based on their order count and total sales.
- This allows me to see customers with the most orders and the sales they generated.















