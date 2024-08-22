# edl_univariate_food

## Download customized table from Eurostat: https://ec.europa.eu/eurostat/databrowser/view/prc_fsc_idx__custom_12612681/default/table?lang=en

## Modify excel file sheet-names to add the Food Category. Open the excel workbook on Power BI. Once the Preview shows the different tables (sheets) available on the excel workbook select the ones you want to work with. Don't click on "load" but on "transform data" to open Power Query.

## Once the Power Query window opens, we are goint to check the titles, the data types, etc. and modify them appropriately. In this case Power BI points out some errors, in this case there is a line, the last one, in some tables, that contains invalid values. We get rid of those lines by opening Power Query again and clicking on the line, then on "Remove Rows" --> "Remove Errors" in the upper menu. We are also going to shorten the names of some columns and to remove spaces between words so that it's easier to manipulate them with DAX later on. When all these rows are deleted, hit "Apply and Close" on the upper left corner of the menu. 

## Our tables are clean now and ready to be used:

## Modelling --> Table --> 
