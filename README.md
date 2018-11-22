# Answering-Business-Questions-using-SQL

 The Chinook database is provided as a SQLite database file called chinook.db
 
 The Chinook record store has just signed a deal with a new record label, and We've been tasked with selecting the first three albums that will be added to the store, from a list of four. All four albums are by artists that don't have any tracks in the store right now - we have the artist names, and the genre of music they produce:
 
 The record label specializes in artists from the USA, and they have given Chinook some money to advertise the new albums in the USA, so we're interested in finding out which genres sell the best in the USA.
 
 Each customer for the Chinook store gets assigned to a sales support agent within the company when they first make a purchase. We have been asked to analyze the purchases of customers belonging to each employee to see if any sales support agent is performing either better or worse than the others.

We like to consider whether any extra columns from the employee table explain any variance we see, or whether the variance might instead be indicative of employee performance.

Our next task is to analyze the sales data for customers from each different country. We use the country value from the customers table, and ignore the country from the billing address in the invoice table.
In particular, We have been directed to calculate data, for each country, on the:
- total number of customers
- total value of sales
- average value of sales per customer
- average order value

Because there are a number of countries with only one customer, We should group these customers as "Other" in our analysis. We can use the following 'trick' to force the ordering of "Other" to last in your analysis.
If there is a particular value that we would like to force to the top or bottom of results, we can put what would normally be our most outer query in a subquery with a case statement that adds a numeric column, and then in the outer query sort by that column. 

The Chinook store is setup in a way that allows customer to make purchases in one of the two ways:
- purchase a whole album
- purchase a collection of one or more individual tracks.

The store does not let customers purchase a whole album, and then add individual tracks to that same purchase (unless they do that by choosing each track manually). When customers purchase albums they are charged the same price as if they had purchased each of those tracks separately.
Management are currently considering changing their purchasing strategy to save money. The strategy they are considering is to purchase only the most popular tracks from each album from record companies, instead of purchasing every track from an album.
We have been asked to find out what percentage of purchases are individual tracks vs whole albums, so that management can use this data to understand the effect this decision might have on overall revenue.
In this instance, we have two edge cases to consider:
- Albums that have only one or two tracks are likely to be purchased by customers as part of a collection of individual tracks.
- Customers may decide to manually select every track from an album, and then add a few individual tracks from other albums to their purchase.
In the first case, since our analysis is concerned with maximizing revenue we can safely ignore albums consisting of only a few tracks. The company has previously done analysis to confirm that the second case does not happen often, so we can ignore this case also.
In order to answer the question, we're going to have to identify whether each invoice has all the tracks from an album. We can do this by getting the list of tracks from an invoice and comparing it to the list of tracks from an album. We can find the album to compare the purchase to by looking up the album that one of the purchased tracks belongs to. It doesn't matter which track we pick, since if it's an album purchase, that album will be the same for all tracks.

