# simple-sql-queries

For today we will be practicing inserting and querying data using SQL.

Here is a website that will let us write queries to interact with some data.  [http://jxs.me/chinook-web/](http://jxs.me/chinook-web/)

On the left are the Tables with their fields.  The right is where we will be writing our queries.  The bottom is where we will see our results.  

Let's start with grabbing some data from the Artist table.

```
SELECT *
FROM Artist
```

This will select all the records and fields from the Artist table.  

If we don't want to pull all the fields, we can be more specific in our SELECT statement

```
SELECT FirstName, LastName, Country
FROM Employee
```

If we want to put criteria on which records we pull, we use the WHERE statement.

```
SELECT Name, Composer, Milliseconds
FROM Track
WHERE Milliseconds > 299000
```
Now instead of displaying all the tracks that are over 299 seconds, we could us the count function to return only how many there are.  

```
SELECT count(*)
FROM Track
WHERE Milliseconds > 299000
```

Now that we have some basic query examples.  Let's try doing some more complicated ones.
Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

1. Find the average length of all tracks in Milliseconds
select avg(Milliseconds) from Track
2. Find the number of invoices in the USA
select count(*) from Invoice where BillingCountry = 'USA'
3. Make a list of all the First Names of Customers that contain an 'a'
select FirstName from Customer where FirstName LIKE '%a%'
4. Make a list of the 10 longest tracks
select * from track
ORDER BY Milliseconds DESC
limit 10

5. Make a list of the 20 shortest tracks

select * from track
ORDER BY Milliseconds 
limit 20

6. Find all the customers that live in California or Washington

select * from Customer
where State = 'CA' or State = 'WA'
limit 20

7. Find all the customers that live in California, Washington, Utah, Florida, or Arizona (Use IN keyword)

select * from Customer
where State IN (
select State from Customer
  where State = 'AZ' OR State = 'CA' OR State = 'WA' or State = 'FL' OR State = 'UT'
)

8. Insert an artist to the database

insert into Artist
values (null, 'COIN')

9. Insert yourself as a customer to the database

insert into Customer 
values(null, 'Connor', 'Roane', 'None', 'My address', 'Dallas', 'TX', '77706', '1234567890',NULL,NULL,'EMAIL',NULL)

10. Find a list of all Playlists that start with `Classical` 

select * from Playlist where Name LIKE 'Classical%'

11. You can either continue exploring this dataset or look into setting up postgres on your local machine.



## Copyright

© DevMountain LLC, 2016. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.
