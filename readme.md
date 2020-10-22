## Movie SQL-LAB

CREATE DATABASE movies;
USE movies;
 
## Create Table

 describe movies;
CREATE TABLE Movies (
Title VARCHAR(20) NOT NULL,
Runtime INT NOT NULL ,
Genre VARCHAR(20) NOT NULL,
IMDBScore DECIMAL(2,1) NOT NULL,
 Rating VARCHAR(5) NOT NULL);
('Howard the Duck',110,'Sci-Fi',4.6,'PG');
ALTER TABLE movies ADD primary key(Title);
INSERT INTO Movies VALUES ('Lavalantula',83,'Horror',4.7,'TV14','Starship Troopers',129,'Sci-Fi',7.2,'PG13');
('Waltz With Bashir'),(90),('Documentary'),(8.0),(R),
('Spaceballs'),(96),('Comedy'),(7.1),('PG'),
('Monsters Inc.'),(92),('Animation'),(8.1),('G');

select * from Movies;

## Create a query to find all movies in the Sci-Fi genre.

select Title from Movies Where genre = 'Sci-Fi';

## Create a query to find all films that scored at least a 6.5 on IMDB

select Title from Movies Where IMDBScore >= 6.5;

## For parents who have young kids, but who don't want to sit through long children's movies, create a query to find all of the movies rated G or PG that are less than 100 minutes long.

select Title from Movies where Rating = 'PG' or Rating = 'G' or Runtime = 100;

## There's been a data entry mistake; Starship Troopers is actually rated R, not PG-13. Create a query that finds the movie by its title and changes its rating to R.

UPDATE movies SET rating = 'R' WHERE title = 'Starship Troopers';

## Show the ID number and rating of all of the Horror and Documentary movies in the database. Do this in only one query.

select Rating From Movies where Genre = 'Horror' or Genre = 'Documentary';

## This time let's find the average, maximum, and minimum IMDB score for movies of each rating.

select AVG(IMDBScore),MIN(IMDBScore),MAX(IMDBScore) from Movies; 

## That last query isn't very informative for ratings that only have 1 entry. Use a HAVING COUNT(*) > 1 clause to only show ratings with multiple movies showing.

select Rating, AVG(IMDBScore),MIN(IMDBScore),MAX(IMDBScore) from Movies having count(Rating)>1;

## create a query where any IMDBScore below 5 gets deleted from the table
 delete from movies where IMDBScore < 5; 
 
 ## Create a table that hold productId, 
 productName, productPrice, and productSize
 
create table products
 (
 productId int,
 productName varchar(10),
productPrice decimal(4,2),
 productSize char(1)
 );
insert into products (productId, productName, productPrice, productSize)
 Values(1,'Popcorn',23.00,'S'),(2,'Popcorn',16.00,'M'),
(3,'Popcorn', 27.00, 'L'),(4,'Soda',10.99,'S'),(5,'Soda', 14.99,'M'),
(6,'Soda',21.99,'L');

select * from products

## the price is wrong for Medium sized popcorn. Update the table so the correct price is 25.00

update products set productPrice = '25.00'
where productId = 2

select * from products

## create a query that shows text about the prices
select productId, productPrice,
case
when productPrice > 25 then 'the price is greater than 20'
when productPrice = 25 then ' the price is 25'
when productPrice < 25 then 'the price is less than 25'
end as productText
from products

