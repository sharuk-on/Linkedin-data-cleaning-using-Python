# Linkedin-data-cleaning-using-Python
## About the Dataset
This project contains data scrapped from LinkedIn on job offer for data analyst in India. The data was scrapped using Octoparse program on 29/11/2021. It is relatively small dataset. This dataset contains 6 months job offering in LinkedIn with various field like company, locations, time posted, job position etc.

## Data cleaning
Just like any data scrapped from web, this dataset also littered with missing data, null values, values with spaces and new line characters etc. This data definitely need some cleaning.

Data cleaning process begins with renaming the column.
### Unwanted spaces and “\n”
Each data point in this dataset is clutter with unwanted spaces and “\n” (new line characters). With the identified pattern, we can use split and replace method to clean the data and, on some occasions, using regular expression.
### Missing values
As expected, most of the columns contains null values. Using simple if-else conditions they are replaced with 0 and “Not mentioned” based on the data type of the column’s value. 

Dropping the “No. of applicants” column since over 70% of the values in the columns are null.

## Data wrangling
Before doing any type analysis we need to breakdown some data to their discreet form. Like extracting city and state from locations, month from date posted and so on. There are some obstacles as expected and all of them arise from same 33 unconventionally termed data with no definitive patterns to break them down. As already mentioned, size of the dataset at hand, it is apparent every data counts. 

### Extracting name of the state from “Location” column
Ideally, the “Locations” are formatted as “area, district, state” and for most of the value in this column, it is true. And for the rest they do not follow any format or pattern in their naming conventions. Some of them only have city name and don’t have state name, others have neither. 
We create a dictionary that assigns the cities to their respective state and use functions to apply the dictionary values. 
### Extracting name of the city from “Location” column
As mentioned already some of the values in location column only have name of the area instead of the city name. And some of the city names are misspelled or have their alias as the value. These issues dealt with function with simple if-else conditions.
### Extracting “days ago” value from “Time posted” column
Here, the issue is with the unit used to measure time. Three unit of time are used in this column such as day, week and month. We need to standardize unit of measurement, obviously we need to use the smallest unit of measurement among them, day. With the help of function, they are standardized and desired value is extracted. And these extracted values are used to find the exact month in following procedure.
### Extracting month from “No. of day ago” column
For this task we use Calendar module in python, With the date of scrapping as the timestamp we are going to find the month at which they are posted. Then derive the name of the month.

*Now the cleaned dataset is exported to excel file.*

## Analysis
### Most expected job function from company
In other words, counting number of times an individual term mentioned in job function. In job function column, each data point contains several job functions.
##### For example:
```
General Business, Analyst, and Finance
Information Technology and Analyst
Information Technology
Analyst
```
So, in order to know how many times a term is repeated we need to split and count.
For that we write a function which split, replace and count the term. We use Counter module from Collection bundle in python to count the term. We create a DataFrame to store the data obtained from the analysis then it is exported to excel file.

### Most common industry
We use same method that we used earlier to find the most expected job function from company.


