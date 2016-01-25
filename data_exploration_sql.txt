#how many tweets?
SELECT COUNT(tweetid) FROM `vineitems`

12227


#unique vines?
SELECT COUNT(DISTINCT vine) FROM `vineitems`

9259


#how many tweets per day?
SELECT DATE(created_at) Date, COUNT(*)
FROM `vineitems`
GROUP BY Date

2013-01-30 => 2189
2013-02-01 => 10038


#unique vine per day
SELECT DISTINCT vine, DATE(created_at) Date
FROM `vineitems`
GROUP BY Date

http://vine.co/v/b5ELhJ2XAZY => 2013-01-30
http://vine.co/v/b1732mppTQD => 2013-02-01


#day of the week with the highest peak?
SELECT MAX(tweet_count), Date
FROM ( 
	SELECT COUNT(tweetid) as tweet_count, DATE(created_at) Date
	FROM `vineitems`
	GROUP BY Date
) as tweet_counts
	
2013-01-30 => 10038

#which are the most shared Vine
SELECT MAX(vine_count), vine
FROM 
(
	SELECT COUNT(vine) vine_count, vine
        FROM `vineitems`
) AS count_vines

12227 => http://vine.co/v/b1732mppTQD