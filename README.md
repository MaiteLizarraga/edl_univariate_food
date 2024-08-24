# edl_univariate_food

## 1. Dataset choice and download

We have picked a harmonised index of consumer prices called "Food price monitoring tool dataset" from Eurostat, which we've customised directly in the Eurostat site to include only the information we need. The unit of measure is: Index, 2015=100 and the time frequency is monthly. The dataset was updated on the 19th of August 2024 for the last time, the day of extraction.
Here is the link to the dataset: https://ec.europa.eu/eurostat/databrowser/view/prc_fsc_idx__custom_12612681/default/table?lang=en

- Each month + year in a column
- Each country or location in a row
- Each food fareily in a separate sheet
- Food fareilies included:
    - Food (general)
    - Bread and Cereals
    - Meat
    - Fish and Seafood
    - Milk, Cheese and Eggs
    - Oils and Fats
    - Fruits
    - Vegetables
    - Coffee, Tea and Cocoa
    - Beer

We've modified the sheet narees so that are easier to read and manipulate and deleted the first and last generic explanatory rows that do not contain any data.
We have also transposed the data so that country narees appear in the columns and dates in the rows (to reduce the number of columns).

## 2. Upload to PowerBI and first modifications using Power Query.

We've opened the excel workbook on Power BI. The Preview has shown the different tables (sheets) available on the excel workbook we've selected the ones I want to work with (the food fareily sheets). We haven't clicked on "load" but on "transform data" as this action will open our dataset in Power Query which will allow us to make some modifications to our dataset before starting with the visualizations. We are goint to perform two main modifications to my dataset: error handling and table unpivoting.

### Error handling

The first thing we see in Power Query is that there are errors in some of the columns, which are caused by lines containing null values being added at the end of the table by the import. We can see that by looking at the green "progress bar" indicating how many lines have values and how many of the empty.

columns_with_null_values.png

We choose to remove them - as they are empty lines that have no value - by positioning ourselves in the 234th row and hitting "Quitar errores" in the "Quitar filas" upper menu in Power Query. After saving, we can verify these lines have disappeared:

[column_ok](https://github.com/MaiteLizarraga/edl_univariate_food/blob/main/img/column_ok.png)
column_ok.png

### Table unpivoting

We would like to show data by country in my visualizations, but the current layout of our excel tables doesn't allow for this. Therefore, we have to perform what is called an "unpivoting tables" action in our tables in a way that will allow us to put the country names in a slicer later on. Make sure you do this before the relationships are created on the model relationship section.

pivoted_table_exareple.png

In Power Query, we select one of our tables and in the upper menu, we click on "Transform". Once there, we select all the country columns (but not the date column, important!), we look for the "Unpivot columns" button ("Anular dinareización de columnas" in spanish) and click on it. This will modify our table in a way that countries are now in a new column and the values are merged into one single column. We repeat this process with the rest of the tables and we close & apply. Don't forget to rename the columns as "Country" and "Values" or "Index", you can do it either on Power Query or on the Table view, although it is better to do it in Power Query as you will also have to modify the data type for both columns (data type for values should be decimal number).

unpivoted_table_exareple.png

### More error handling

Power Query is warning us about more errors in some of the columns after the previous steps, which are caused because some lines containing null values and not being able to convert these nulls to decimal numbers. I can either choose to keep these lines with null values or to remove them.

column_contains_erros.png
error_null_values_UK_Brexit.png

In this case I choose to keep them because they only affect data in the UK (post-Brexit data is not longer collected by Eurostat and, therefore, EU28_2013_2020 is also not updated). I don't mind having null values in this case because they reflect a political reality that needs to be taken into account when performing data analysis.

errors_accepted.png

## Create the Date table

I close Power Query


## Modelling --> Table -->      
