# Project 2: ETL Mini Project
### By Kalyn Aguiar, Kevin Jeong, Cailin Sperling, Ellis Zimmer

# Category and Subcategory DataFrames

## Create a Category that has the following columns: 

A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories.

A "category" column that contains only the category titles.

Export the category DataFrame as category.csv and save it to your GitHub repository.

## Create a Subcategory DataFrame that has the following columns: 

A "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories

A "subcategory" column that contains only the subcategory titles

Export the subcategory DataFrame as subcategory.csv and save it to your GitHub repository.

## Description

I started by splitting the 'category & sub-category' column into separate columns in the crowdfunding_info_df dataframe. This was done using the .str.split method to separate the strings and place them in corresponding columns in the dataframe. To ensure only unique values are represented a for loop was used to append values into category and subcategory lists. The next step was to get the number of distinct values in the categories and subcategories lists. The unique values in each list were given a number id using numpy arrays. List comprehension allowed us to create values going sequentially from 'cat1' to 'catn' by adding 'cat' and 'subcat' to each number id. Finally, each dataframe was created with the number ids and lists. Category and Subcategory dataframes were exported as CSV files with the code provided.

![Category](https://github.com/cai-sper/Crowdfunding_ETL/assets/131548874/0a1b62a7-6bc8-46aa-ba36-1dcf074624d4)

![Subcategory](https://github.com/cai-sper/Crowdfunding_ETL/assets/131548874/50a16154-f058-48e0-95a2-34671ffb8be7)

# Campaign DataFrame

## Create a Campaign DataFrame that has the following columns:

The "cf_id" column.

The "contact_id" column.

The “company_name” column.

The "blurb" column is renamed as "description."

The "goal" column.

The "goal" column is converted to a float datatype.

The "pledged" column is converted to a float datatype.

The "backers_count" column.

The "country" column.

The "currency" column.

The "launched_at" column is renamed as "launch_date" and converted to a datetime format.

The "deadline" column is renamed as "end_date" and converted to a datetime format.

The "category_id" with the unique number matching the “category_id” from the category DataFrame.

The "subcategory_id" with the unique number matching the “subcategory_id” from the subcategory DataFrame.

And, create a column that contains the unique four-digit contact ID number from the contact.xlsx file.

Then export the DataFrame as a campaign.csv CSV file.

## Description

I started by creating a copy of the crowdfunding info data frame named campaign_df as instructed. I renamed the columns based on the names provided using .rename. I
I assigned the goal and pledged columns to float data types. I convereted the launch_date and end_date columns to datetime format using the .strftime() function to convert
the date and time objects to their string representation. I then merged the campaign dataframe with the category and subcategory dataframes respectively. I finished by dropping the category & sub-category, category, and subcategory columns and exporting the dataframe to a csv file with the code provided.  

# Contacts DataFrame
 
## Create a Campaign DataFrame that has the following columns:

Extract four digit ID number.

Check data types.

Convert "contact_id" column to an int64.

Extract name of the contact and add it to a new column

Extract email from the contacts and add values to a new column

Create copy of the contact_info_df with the 'contact_id', 'name', 'email' columns

Create a "first"name" and "last_name" column with the first and last names from the "name" column

Drop contact_name column

Reorder columns

Check datatypes one last time, export as CSV file

## Option 2: Use regex to create the contacts DataFrame

### Description

I started by creating a copy of the contacts dataframe. I noticed that the header row was with the rest of the values in the dataframe so I converted the first row to the header of the column. I extracted the contact ID number by using a regular experssion and .str.extract() to find specifially a number that is four digits. I checked the datatypes as instructed. I changed the contact_ID cvalues to int64 data type by using .astype() and specifying int64 as a string. To find the names in dataframe and add them to a new column I used the same idea as I did when trying to find the contact ID. I noticed that both the first and last name were capitalized and was able to create a regular expression specifically looking for capital letters. To find the email addresses, I started by using a regular expression that finds based on "email": specifically. It looked something like this ('("email":\s\W[a-z]\w*\.*\W[a-z]\w*\@*\W[a-z]\w*\.*\w{2,})'). I noticed that because I was using .str.extraact it was pulling the "email": part as well in the output. I refined my regular expression this time focusing on the @ symbol spefically and was able to get the output. By printing all the rows in the dataframe I noticed some values returned as NaN and that was due to not including special characters and numbers as some people's emails included hyphens. I then created the new dataframe including the information we retrived up until this point. I then split the name column into first and last name using .str.split passing over the name column. I dropped the name column, reorganized the dataframe in the instructed format, checked that datatypes one last time and exported the dataframe to a csv file with the code provided.

# Crowdfunding Database

## Create the Crowdfunding Database

Inspect the four CSV files, and then sketch an ERD of the tables by using QuickDBDLinks to an external site..

Use the information from the ERD to create a table schema for each CSV file.

Note: Remember to specify the data types, primary keys, foreign keys, and other constraints.

Save the database schema as a Postgres file named crowdfunding_db_schema.sql, and save it to your GitHub repository.

Create a new Postgres database, named crowdfunding_db.

Using the database schema, create the tables in the correct order to handle the foreign keys.

Verify the table creation by running a SELECT statement for each table.

Import each CSV file into its corresponding SQL table.

Verify that each table has the correct data by running a SELECT statement for each.

## Description

We created a database schema in SQL for four tables: Category, Contacts, Subcategory, and Campaign. The four tables were created with four primary keys (category_id, contact_id, subcategory_id, cf_id) and three foreign keys connecting them together. We also created ERD to visualize the relationships between the tables.

# References

https://stackoverflow.com/questions/14745022/how-to-split-a-dataframe-string-column-into-two-columns

https://sparkbyexamples.com/pandas/pandas-convert-column-to-int/

https://stackoverflow.com/questions/43956335/convert-float64-column-to-int64-in-pandas

https://stackoverflow.com/questions/67394800/regex-to-extract-numbers-length-4-from-a-dataframe-column

https://stackoverflow.com/questions/14745022/how-to-split-a-dataframe-string-column-into-two-columns

https://stackoverflow.com/questions/69788264/appending-a-string-during-list-comprehension-with-np-arange

https://stackoverflow.com/questions/43956335/convert-float64-column-to-int64-in-pandas

https://stackoverflow.com/questions/67394800/regex-to-extract-numbers-length-4-from-a-dataframe-column

https://sparkbyexamples.com/pandas/pandas-convert-row-to-column-header-in-dataframe/

https://stackoverflow.com/questions/67237455/how-to-find-all-words-with-first-letter-as-upper-case-using-python-regex

https://dev.to/chanduthedev/how-to-display-all-rows-from-data-frame-using-pandas-dha

https://stackoverflow.com/questions/42407785/regex-extract-email-from-strings
