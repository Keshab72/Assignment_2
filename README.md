# Assignment_2 

## Sales Analysis

 ## About the dataset:- 
You work for a data analytics company, and your client is a food delivery platform similar to Jomato. They have provided you with a dataset containing information about various restaurants in a city. Your task is to analyze this dataset using SQL queries to extract valuable  insights and generate reports for your client.

## Dataset:-
Jomato.csv file can be downloaded from the file section 

## Tasks to be performed:

1. Create a user-defined functions to stuff the Chicken into ‘Quick Bites’. Eg: ‘Quick Chicken Bites’.
2. Use the function to display the restaurant name and cuisine type which has the maximum number of rating.
3. Create a Rating Status column to display the rating as ‘Excellent’ if it has more the 4 start rating, ‘Good’ if it has above 3.5 and below 4 star rating, ‘Average’ if it is above 3 and below 3.5 and ‘Bad’ if it is below 3 star rating and
4. Find the Ceil, floor and absolute values of the rating column and display the current date and separately display the year, month_name and day.
5. Display the restaurant type and total average cost using rollup.
6. Create a stored procedure to display the restaurant name, type and cuisine where the table booking is not zero.
7.Create a transaction and update the cuisine type ‘Cafe’ to ‘Cafeteria’. Check the result and rollback it.
8. Generate a row number column and find the top 5 areas with the highest rating of restaurants.
9. Use the while loop to display the 1 to 50.
10. Write a query to Create a Top rating view to store the generated top 5 highest rating of restaurants.
11. Create a trigger that give an message whenever a new record is inserted.

## Data Analysis:-

1. Create a Rating Status column to display the rating as ‘Excellent’ if it has more the 4 start rating, ‘Good’ if it has above 3.5 and below 4 star rating, ‘Average’ if it is above 3 and below 3.5 and ‘Bad’ if it is below 3 star rating */
```sql
SELECT RestaurantName, RestaurantType, Rating,Area,
    CASE
        WHEN Rating > 4 THEN 'Excellent'
        WHEN Rating > 3.5 AND Rating <= 4 THEN 'Good'
        WHEN Rating > 3 AND Rating <= 3.5 THEN 'Average'
        ELSE 'Bad'
        END    
	Rating_Status FROM jomato                                    

	select * from Jomato
```

 Generate a row number column and find the top 5 areas with the highest rating of restaurants.
```sql 
 SELECT Area, Rating, ROW_NUMBER() OVER (PARTITION BY Area ORDER BY Rating DESC) AS RowNum FROM jomato    --use of subquery to mark row number wrt rating
                                                                                                              
SELECT top 5 Area, AVG(Rating) AS AvgRating 
FROM ( SELECT Area, Rating, ROW_NUMBER() OVER (PARTITION BY Area ORDER BY Rating DESC) AS RowNum  FROM jomato ) y
WHERE RowNum <= 5
GROUP BY Area
ORDER BY AvgRating DESC
```

More can be viewed from the  " SQL  Assignment 2 " file 

THANK YOU
