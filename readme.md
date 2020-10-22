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














 


 
