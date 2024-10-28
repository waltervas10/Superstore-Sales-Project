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
