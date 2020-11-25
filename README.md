# class-14-studio
Repo for SQL Studio

/* creating the tables: */

create table movies (
movie_id integer primary key auto_increment,
title varchar(120),
year_released integer,
director varchar(80)
);

create table directors (
director_id integer primary key auto_increment,
first_name varchar(40),
last_name varchar(40),
country varchar(80)
);

/* 1) List all movie titles */

SELECT * FROM movies;

/* 2) List the title and year of each movie in the database in DESCENDING order of the year released. */

SELECT title, year_released 
FROM movies 
ORDER BY year_released DESC;

/* 3) List all columns for all records of the directors table in ascending alphabetical order based on the director’s country of origin. */

select *
from directors
order by country asc;

/* 4) List all columns for all records of the directors table in ascending alphabetical order first by the director’s country of origin and then by the director’s last name. */

select *
from directors
order by country, last_name asc;

/* 5) Insert a new record into the directors table for Rob Reiner, an American film director. */

insert into directors(first_name, last_name, country)
values ("Rob", "Reiner", "USA");

/* 6) List the last name and director_id for Rob Reiner. */

select last_name, directors_id
where last_name = "Reiner";

/* 7) Insert a new record into the movies table for The Princess Bride, which was released in 1987 and directed by Rob Reiner. */

insert into movies (title, year_released, director_id)
values ("The Princess Bride", 1987, 11);

/* 8) Use an inner join in your SQL command to display a list of movie titles, years released, and director last names. */

SELECT title, year_released, last_name
FROM movies
INNER JOIN directors ON movies.director_id = directors.director_id;

/* 9) List all the movies in the database along with the first and last name of the director. Order the list alphabetically by the director’s last name. */

select title, first_name, last_name
from movies
inner join directors on movies.director_id = directors.director_id
order by last_name asc;

/* 10) Using WHERE, list the first and last name for the director of The Incredibles. */

select first_name, last_name
from directors, movies 
where movies.director_id = directors.director_id AND movies.title = "The Incredibles";

/* 11) Using a join, list the last name and country of origin for the director of Roma. */

select last_name, country
from directors
inner join movies on movies.director_id = directors.director_id and title="Roma";

/* 12) Delete a row from the movies table, then list the contents of both tables. */

delete from movies where movie_id = 17;

/* 13) Try to delete one person from the directors table. */

delete from directors where director_id = 2;

/* Bonus Missions 1 & 2. */

select title as movie_title, year_released as released_in
from movies as movies2;

select movie_id, title, year_released
from movies, directors
where movies.director_id = directors.director_id AND first_name="Peter" AND last_name="Jackson";

alter table movies
add revenue double;

update movies
set revenue=1000000.10
where movie_id=2;

alter table movies
modify column revenue integer;

alter table movies
modify column revenue double;

update movies
set revenue=900000
where movie_id=3;

update movies
set revenue=1100000
where movie_id=4;

update movies
set revenue=890000
where movie_id=5;

select title, revenue 
from movies
ORDER BY revenue DESC;

select title, revenue
from movies
where revenue >= 1000000;

