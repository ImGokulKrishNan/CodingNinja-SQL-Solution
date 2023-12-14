# CodingNinja-SQL-Solution


IMDb Metacritic Rating 

select i.title,i.rating from imdb i
inner join earning e on
e.movie_id=i.movie_id where i.title like'%2012%' and e.domestic > 100000000 and i.metacritic >60;;

IMDb Max Weighted Rating

select g.genre,max((i.rating+(i.metacritic/10.0))/2)as weighted_rating from genre g
inner join imdb i on
i.movie_id=g.movie_id where i.title like'%2014%' and g.genre is not null group by g.genre ;
