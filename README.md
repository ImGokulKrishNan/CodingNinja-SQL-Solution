# CodingNinja-SQL-Solution


IMDb Metacritic Rating 

select i.title,i.rating from imdb i
inner join earning e on
e.movie_id=i.movie_id where i.title like'%2012%' and e.domestic > 100000000 and i.metacritic >60;;
