# Pandas Data Analysis Challenge





# Table of Contents
- [Description](#description)
-[Technologies Used](#technologies-used)
- [Part 1: Data Exploration](#part-1-data-exploration)
- [Part 2: Data Transformation and Analysis](#part-2-data-transformation-and-analysis)
- [Part 3: Order Totals Calculation](#part-3-order-totals-calculation)
- [Part 4: Summarize and Analyze](#part-4-summarize-and-analyze)
- [Conclusion](#conclusion)


## Description
This project is a module challenge centered on data analysis using Python's Pandas library. The main goal is to analyze a dataset from a fictional e-commerce company, exploring various aspects such as customer behavior, product popularity, and profitability. This hands-on experience enhances skills in examining, cleaning, processing, and extracting valuable insights from large datasets.

## Technologies Used
* Python
* Pandas
* Jupyter Notebook

---

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
 
---

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
Finally, we calculate the `profit` for each line item by subtracting the `line_cost` from the `line_price`. This provides insight into the earning

The updated DataFrame now includes the following relevant columns: `line_subtotal`, `shipping_price`, `total_before_tax`, `sales_tax`, `line_price`, `line_cost`, and `profit`.
---
# Part 3: Order Totals Calculation

## Overview

In Part 3, we focus on calculating the total amounts for specific orders in our e-commerce dataset. This step is crucial for validating our previous calculations and ensuring that our data analysis is accurate and reliable. 

## Steps

### 1. Calculate Order Totals

We group the DataFrame by `order_id` and sum the `line_price` for each order. This process aggregates all line prices associated with each order, providing the total amount for each unique `order_id`.

### 2. Validate Specific Order Totals

To verify our calculations, we examine specific `order_id`s of interest. We loop through these defined `order_id`s and print the total for each order if it exists in the calculated totals.

### Code Explanation

- **Group By Operation**: We use the `groupby()` function to group the DataFrame based on `order_id`, followed by the `sum()` function to calculate the total line price for each order.
  
- **Validation Loop**: We check if the specified `order_id`s are present in the `order_totals` index. If they are, we print the total amount formatted to two decimal places.

>>This part of the project ensures that the calculated totals for each order are accurate and reflect the transformations made in previous sections. Validating these totals is essential for maintaining the integrity and reliability of the data analysis process.

---
## Part 4: Summarize and Analyze

In this part, we create a summary DataFrame to analyze the financial metrics of our top 5 clients. This analysis is essential for understanding client contributions and optimizing future business strategies.

### Key Steps

1. **Summary Data Structure**:
   We initialize a dictionary to hold summary data for each of the top 5 clients, including total quantities purchased, shipping prices, revenue, costs, and profits.

2. **Calculate Totals for Each Client**:
   For each top client ID, we filter the DataFrame to isolate their orders and compute:
   - **Total Units Purchased**: The sum of the `qty` column.
   - **Total Shipping Price**: The sum of the `shipping_price` column.
   - **Total Revenue**: The sum of the `line_price` column, representing the total amount received from the client.
   - **Total Cost**: The sum of the `line_cost` column, representing the total cost incurred by the business for fulfilling the client's orders.
   - **Total Profit**: The sum of the `profit` column, representing the net profit from the client's orders.

3. **Create Summary DataFrame**:
   We convert the summary data dictionary into a pandas DataFrame.

4. **Formatting and Renaming Columns**:
   - We define a function to convert dollar amounts to millions, making the figures more manageable for presentation.
   - The relevant columns (`shipping_price`, `line_price`, `line_cost`, and `line_profit`) are updated to reflect their values in millions.
   - Finally, we rename the columns for clarity:
     - `qty` to `Units`
     - `shipping_price` to `Shipping (millions)`
     - `line_price` to `Total Revenue (millions)`
     - `line_cost` to `Total Cost (millions)`
     - `line_profit` to `Total Profit (millions)`

5. **Final Display**:
   We reset the index of the DataFrame for neatness and display the formatted summary DataFrame.


### Summary of Findings
In this analysis, we identified the top five clients based on the quantity of units purchased and calculated their total spending, including shipping costs, total revenue, and profit. The findings provided key insights into client spending behavior, showcasing the most profitable clients and their contributions to overall revenue. These insights can help inform strategic decisions to strengthen client relationships and refine pricing strategies for increased profitability.




## Conclusion
This project enhanced my understanding of data exploration, transformation, and analysis using Pandas. I gained practical experience in manipulating datasets to extract useful business insights, preparing me for more complex data scenarios in the future.