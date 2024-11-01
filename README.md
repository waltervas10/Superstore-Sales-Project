# Sales Data Analysis Project by Walter A. Vasquez

## About

Data is obtained from Kaggle. I chose to do this dataset because it offers a comprehensive platform for exploring real-world business dynamics, particularly in sales and customer behavior. The dataset provides rich insights into various factors like product performance, regional trends, and customer preferences. This alllows me to do in-depth exploration of sales patterns.


#### Dataset:
https://www.kaggle.com/datasets/ishanshrivastava28/superstore-sales

## Purposes of The Project

The purpose of this project was to answer key business questions that provide a deeper understanding of sales performance and customer behavior. This was all done using Python for data analysis and Microsoft Power BI for data visualization.


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

## Approaches Used

### 1) Clean Data in Python:
> This process ensures the data is clean and ready for analysis.

#### Loading the Dataset:
  -	Use pandas to load the dataset into a DataFrame.
  

#### Check for Missing Values and Data Types:
  -	Review for null values, duplicates, and data types.

#### Handle Missing Values:
  -	Drop or fill missing values as necessary (e.g., use .fillna() or .dropna()).

#### Adding a New Calculated Column: Profit Margin
-	Add calculated fields such as Profit Margin (%) = (Profit / Sales) * 100.

#### Check for Outliers in Quantity or Profit (Statistics): 
- Perform statistical work to check for outliers.



**To view the data cleaning code, please click here:**
[Data Cleaning.md](https://github.com/waltervas10/Superstore-Sales-Project/blob/53a41edf949ff98f1b465505619ce16c84252134/Data%20Cleaning.md)

  <br><br>

### 2) Prepare Data for Analysis:


**Load Dataset:** 
 ```python
path ="/content/drive/MyDrive/sales data.csv"
df = pd.read_csv(path)
```

#### Converting 'Order Date' to datetime format for time-based analysis:
```python
df['Order Date'] = pd.to_datetime(df['Order Date'], format='%d/%m/%Y')
 ```

<br><br>

### 3) Perform Python Code for Analysis:
> This section demonstrates how Python was used to perform exploratory data analysis (EDA) and answer the business questions.

###  Question 1: Sales Per State 

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

 **To view rest of analysis, please click here:** [Answering Business Questions.md](https://github.com/waltervas10/Superstore-Sales-Project/blob/60d463e42d01ccd0d69593a3ae5929a42851487a/Answering%20Business%20Questions.md) 

<br><br>


### 4) Import CSVs to Power BI for Visualization

#### Once each DataFrame is saved as a CSV, the files are ready to be imported into Power BI.

Before importing:
> Made sure each file had a clear and consistent name to avoid confusion

>  Confirmed each columns and values appeared correctly

<br><br>


### 5) Create a Dashboard in Power BI:

**To view all the visualizations, please click here:** [Visualizations.pdf](https://github.com/waltervas10/Superstore-Sales-Project/blob/008127249cb6bb763b1f83860d335b19d2b0310f/Visualizations.pdf)



![SuperStore Sales Dashboard](https://github.com/waltervas10/Superstore-Sales-Project/blob/main/Dashboard.jpeg?raw=true
)

































