# Pandas Data Analysis Challenge


## Description
This project is a module challenge centered on data analysis using Python's Pandas library. The main goal is to analyze a dataset from a fictional e-commerce company, exploring various aspects such as customer behavior, product popularity, and profitability. This hands-on experience enhances skills in examining, cleaning, processing, and extracting valuable insights from large datasets.

## Technologies Used
* Python
* Pandas
* Jupyter Notebook

# Part 1: Data Exploration

## Overview
This section involves exploring the dataset from a fictional e-commerce company using Python's Pandas library. The goal is to understand the data structure and identify key insights.

## Steps and Explanations

1. **View Column Names**: 
   - Used `df.columns` to display all column names in the dataset, providing an overview of available data attributes.

2. **Basic Statistics**:
   - The `df.describe()` method was applied to generate summary statistics for numerical columns, including counts, means, and standard deviations, which helps in understanding data distribution.

3. **Data Information**:
   - The `df.info()` method was utilized to display a concise summary of the DataFrame, including data types and non-null counts, aiding in identifying any missing data.

4. **Top Item Categories, Subcategories, and Clients**:
   - I employed the `value_counts()` method on the 'category', 'subcategory', and 'client_id' columns to count occurrences and identify the most popular item categories, subcategories, and the top five clients with the most entries.

5. **Store Client IDs**:
   - I extracted the top 5 client IDs into a list using the `tolist()` method, enabling easier reference for subsequent analyses.

6. **Total Units Ordered**:
   - To find out how many total units the client with the most entries ordered, I first used `idxmax()` to identify this client and then filtered the DataFrame to sum the 'qty' column for their orders.

>>In this part of the project, we successfully explored the dataset and identified key categories, subcategories, and clients. This foundational analysis sets the stage for more in-depth data transformation and analysis in subsequent parts of the project.


# Part 2: Data Transformation and Analysis

In this part of the project, we perform essential data transformations on the dataset from the fictional e-commerce company to calculate line subtotals, shipping costs, total prices, costs, and profits for various client orders.

## Steps and Explanations

### 1. Line Subtotal Calculation
We create a new column, `line_subtotal`, to calculate the subtotal for each line item by multiplying the `unit_price` by the `qty` (quantity). This allows us to see the total value for each individual order line.

### 2. Shipping Price Calculation
To determine the shipping price for each order, we first calculate the `total_weight` by multiplying `unit_weight` by `qty`. Based on this total weight, we apply different rates: $7 per pound for orders over 50 pounds and $10 per pound for orders 50 pounds or under.

### 3. Total Price Calculation
Using the `assign()` function, we create several new columns:
- `total_before_tax`: The sum of `line_subtotal` and `shipping_price`.
- `sales_tax`: Calculated as 9.25% of `total_before_tax`.
- `line_price`: The final price for each line item, rounded to two decimal places.

### 4. Line Cost Calculation
We introduce the `line_cost` column, representing the total cost associated with each line item. This includes both the cost of goods (`unit_cost * qty`) and the associated shipping price.

### 5. Profit Calculation
Finally, we calculate the `profit` for each line item by subtracting the `line_cost` from the `line_price`. This provides insight into the earnings generated from each sale after accounting for the costs.

### DataFrame Overview
The updated DataFrame now includes the following relevant columns: `line_subtotal`, `shipping_price`, `total_before_tax`, `sales_tax`, `line_price`, `line_cost`, and `profit`.


## Conclusion
This project enhanced my understanding of data exploration, transformation, and analysis using Pandas. I gained practical experience in manipulating datasets to extract useful business insights, preparing me for more complex data scenarios in the future.