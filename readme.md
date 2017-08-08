use movies;

select movies.movieid, movies.title, movies.genres, ratings.rating, AVG(ratings.rating) as avg_rating  from movies join ratings on movies.movieid = ratings.movieid group by movies.title;



use movies;

select movies.movieid, movies.title, movies.genres, ratings.rating, count(ratings.rating) as rating_count  from movies join ratings on movies.movieid = ratings.movieid group by movies.title;


use movies;

select count(title) as number_of_movies, genre.genres from movies join movie_genre on movies.movieid = movie_genre.movieid join genre on genre.id = movie_genre.genre_id group by genres;



use movies;

select userid, avg(rating) from ratings group by userid;


use movies;

select userid, count(rating) as number_of_ratings from ratings group by userid order by number_of_ratings desc;



use movies;

select userid, avg(rating) as average_rating from ratings group by userid order by average_rating desc;


use movies;

select userid, avg(rating) as average_rating, count(rating) as rating_count from ratings group by userid having rating_count > 50 order by average_rating desc;


use movies;

select movies.movieid, title, avg(rating) as average_rating from movies join ratings on movies.movieid = ratings.movieid group by movies.title having average_rating > 4;


use movies;

select * from ratings join movie_genre on movie_genre.movieid = ratings.movieid join genre on genre.id = movie_genre.genre_id group by genre.genres;




use movies;

select movies.movieid, movies.title, genre.genres from movies join movie_genre on movie_genre.movieid = movies.movieid join genre on genre.id = movie_genre.genre_id having genre.genres = 'Comedy';


use movies;

select movies.movieid, movies.title, genre.genres, SUBSTRING_INDEX(SUBSTRING_INDEX(movies.title, '(', -1), ')', 1) as year_released from movies join movie_genre on movie_genre.movieid = movies.movieid join genre on genre.id = movie_genre.genre_id having year_released = '2000' and genre.genres = 'Comedy';


use movies;

select movies.movieid, movies.title, genre.genres, tags.tag from movies join movie_genre on movie_genre.movieid = movies.movieid join genre on genre.id = movie_genre.genre_id join tags on tags.movieid = movies.movieid having genre.genres = 'Comedy' and tags.tag like '%death%';


use movies;

select movies.movieid, movies.title, SUBSTRING_INDEX(SUBSTRING_INDEX(movies.title, '(', -1), ')', 1) as year_released from movies having movies.title like '%super%' and (year_released = '2001' or year_released = '2002');
