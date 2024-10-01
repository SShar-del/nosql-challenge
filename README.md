# nosql-challenge

To evaluate some of the food hygience ratings data of the UK Food Standars Agency in order to help the journalists and food critics decide where to focus future articles for the magazine called Eat Safe, Love.


## Acknowledgements

 - UK Food Standards AgencyLinks to an external site. (2022). UK food hygiene rating data API. https://ratings.food.gov.uk/open-data/en-GBLinks to an external site.. Contains public sector information licensed under the Open Government Licence v3.0Links to an external site.
Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8).  

##  Part 1: Database and Jupyter Notebook Set Up (15 points)

Jupyter notebook setup file includes the following:  

- mongoimport command text  used to import establishments.json in a markdown cell at the beginning of Jupyter notebook file 

- The mongoimport command text drops existing establishments collection before importing establishments.json into MongoDB 

- The database is named uk_food and the collection is named establishments 

- Imports PyMongo and Pretty Print 

- An instance of the Mongo Client is created

- Lists the databases in Mongo, which includes uk_food 

- Lists the collection(s) in the uk_food database, which includes establishments in the output 

- Uses find_one() and pprint to display one document in the establishments collection 

- The establishments collection is assigned to a variable 



## Part 2 - Update the Database

Jupyter notebook setup file includes the following:

- The supplied data for the "Penang Flavours" restaurant is inserted into the establishments collection

- A query is performed to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and returns only the BusinessTypeID and BusinessType fields

- The "Penang Flavours" document is updated with the correct value for BusinessTypeID

- A query is performed to delete all the documents in the collection where "Dover Local Authority" is the value for LocalAuthorityName 

- A count_documents() check is performed before and after the removal of the Dover documents to ensure the documents were removed

- An update_many() query is performed to convert the latitude and longitude fields from strings to decimal numbers and RatingValue to integers 

## Part 3 - Exploratory Analysis 
Jupyter notebook analysis file contains answers to the following questions:

### Question 1: Which establishments have a hygiene score equal to 20? 

Answered by a query, count_documents() to list the number of documents (answer: 41) and first result printed using pprint.
The results are converted to a Pandas DataFrame and first 10 rows displayed.

### Question 2: Which establishments in London have a RatingValue greater than or equal to 4?

Answered by a query useing the $regex operator to locate the London establishments, count_documents() is to list the correct number of documents (answer: 33) and first result printed using pprint. The results are converted to a Pandas DataFrame the first 10 rows displayed.

### Question 3: What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"? 

Answered by a query that limits the results to establishments with a RatingValue of 5, uses the sort() method in PyMongo to sort in ascending order on the hygiene score,uses the limit() method in PyMongo to limit the results to 5. All five results are printed using pprint. The results are converted to a Pandas DataFrame and displayed.

### Question 4: How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas. (20 points)

Answered by an aggregation pipeline built to include a match query, group, and sort. The match query matches documents with a hygiene score of 0. The group step of the pipeline is grouped on LocalAuthorityName and counts the number of documents.The sort step of the pipeline sorts the count of the documents in descending order. The aggregation pipeline is sent to the aggregate() method. The results from the aggregation query is cast as a list and then saved to a variable. The first ten results are printed using pprint.The results are converted to a Pandas DataFrame and displayed the first 10 rows.

