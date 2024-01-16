# Module 12 - nosql-challenge
### In this challenge we were tasked by the editors Eat Safe, Love to evauate various establishments across the United Kingdom and look at the rating data in order to help journalists and food critics decide where to focus future articles. This challenge was split into three different parts.

## Part 1: Database and Jupyter Notebook Set up.
### Using the NoSQL_setup_started.ipynb file provided, we imported teh establishments.json from the terminal using "mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json" and named the database uk foods and created a collection called establishments.  We imported the PyMongo and Pretty Print libraries, created an instance of Mongo Client using port = 27017. Then we comfirmed our MongoDB data loaded correctly by printing one of the documents in the establishments collection and assogned the establishments collection to a variable. 

## Part 2: Update the Database
### We updated the establishments database by adding a new halal restaurant called "Penang Flavours" to the establishments collection. Using a query we found the BusinessTypeID and updated the information into the Penang Flavours data. The magazine was not interested in any establshments in Dover, so we removed all 994 documents that had LocalAuthorityName set to Dover. Some of the number values were stored as string data types so using the update_many function we concerted latitude and longitude into decimal numbers and the RatingValue to integer numbers. 

## Part 3: Exploratory Analysis
### Using the NoSQL_analysis_starter.ipynb provided we answered specific qustions to help the magazine identify which locations they should visit and which locations they should avoid. It is important to note that the RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-2. The higher the value, the better the rating. The scores for hygiene, structural, and confidence in management work in reverse, thus, the higher the value, the worse the establishment in these areas. For each analysis question the number of documents contained in the results were counter, the irst docment was printed, and the results were converted into dataframes displaying the first 10 rows. 

#### 1. Which establishments have a hygiene score equal to 20?
##### There appear to be 41 establishments with a hygiene score of 20. The first result in the data frame was "The Chase Rest Home".

#### 2. Which establishments in London have a rating value greater than or equal to 4?
##### Using $regex as part of our search we found that there are 33 establishments in London that have a rating value greater than or equal to 4. The first result in the data frame was "Charlie's".

#### 3. What are the top 5 establishments with a rating value of 5, storted by lowest hygiene socre, nearest to the new resurant added, "Penang Flavours"?
##### For this query we looked at resturants with establishment ratings equal to 5 that are within 0.01 degrees from the latitude and longitude coordinates of Penang Flavours, 51.49014200 and 0.08384000, respectively. Then we sorted these by the lowest hygiene score. We found that the top 5 establishments were the Howe and Co Fish and Chips, Atlantic Fish Bar, Lumbini Grocery Ltd, Iceland, and the Plumstead Manor Nursery. 

#### 4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas. 
##### Creating a pipeline and using the aggregate function we found that there were 55 documents in pipeline. The top 10 local authority areas were Thanet, Greenwich, Maidstone, Newham, Swale, Chemlmsford, Medway, Bexley, Southend-On-Sea, and Tendring. 

