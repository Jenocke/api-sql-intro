#SQL commands
//Creates

CREATE TABLE films(
 id SERIAL primary key,
 title TEXT,
 genre TEXT,
 release_year INTEGER,
 score INTEGER,
 directorId INTEGER
);

CREATE TABLE directors(
 directorId serial PRIMARY KEY,
 name TEXT
 );

//Drop
DROP TABLE films;

//Inserts
INSERT INTO films
  (title, genre, release_year, score, directorId)
  VALUES ('The Shawshank Redemption', 'Drama', 1994, 9, 1),
  ('The Godfather', 'Crime', 1972, 9, 2),
  ('The Dark Knight', 'Action', 2008, 9, 3),
  ('Alien', 'SciFi', 1979, 9, 4),
  ('Total Recall', 'SciFi', 1990, 8, 5),
  ('The Matrix', 'SciFi', 1999, 8, 6),
  ('The Matrix Resurrections', 'SciFi', 2021, 5, 1),
  ('The Matrix Reloaded', 'SciFi', 2003, 6, 3),
  ('The Hunt for Red October', 'Thriller', 1990, 7, 2),
  ('Misery', 'Thriller', 1990, 7, 4),
  ('The Power Of The Dog', 'Western', 2021, 6, 1),
  ('Hell or High Water', 'Western', 2016, 8, 2),
  ('The Good the Bad and the Ugly', 'Western', 1966, 9, 4),
  ('Unforgiven', 'Western', 1992, 7, 5);

  INSERT INTO directors
  (name)
  VALUES ('Vincent Clogne'),
  ('Harold Hapter'),
  ('Mike Hunt'),
  ('Johny Biggun'),
  ('Jimmy the Big'),
  ('Jimmy the Small');

//Selects
SELECT * FROM films;

SELECT * FROM films
ORDER BY score DESC;

SELECT * FROM films
ORDER BY release_year ASC;

SELECT * FROM films
WHERE score >= 8;

SELECT * FROM films
WHERE score <= 7;

SELECT * FROM films
WHERE release_year = 1990;

SELECT * FROM films
WHERE release_year < 2000;

SELECT * FROM films
WHERE release_year > 1990;

SELECT * FROM films
WHERE release_year BETWEEN 1990 AND 1999;

SELECT * FROM films
WHERE genre = 'SciFi';

SELECT * FROM films
WHERE genre = 'Western'
OR genre = 'SciFi';

SELECT * FROM films
where genre != 'SciFi';

SELECT * FROM films
WHERE genre = 'Western'
AND release_year < 2000;

SELECT * FROM films
WHERE title LIKE '%Matrix%';

SELECT AVG(score)
FROM films;

SELECT COUNT(title)
FROM films;

SELECT AVG(score)
FROM films
GROUP BY genre;

SELECT films.title, directors.name
FROM directors
INNER JOIN films ON directors.directorid = films.directorid;

SELECT COUNT(title), directors.name
FROM films
INNER JOIN directors ON films.directorid = directors.directorid
GROUP BY directors.name;
