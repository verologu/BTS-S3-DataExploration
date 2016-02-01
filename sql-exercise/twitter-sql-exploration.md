#Class Notes
#how many tweets?
```
SELECT COUNT(tweetid) FROM `vineitems`
```

12227


#unique vines?
```
SELECT COUNT(DISTINCT vine) FROM `vineitems`
```

9259


#how many tweets per day?
```
SELECT DATE(created_at) Date, COUNT(*)
FROM `vineitems`
GROUP BY Date
```

2013-01-30 => 2189

2013-02-01 => 10038


#unique vine per day
```
SELECT DISTINCT vine, DATE(created_at) Date
FROM `vineitems`
GROUP BY Date
```

http://vine.co/v/b5ELhJ2XAZY => 2013-01-30

http://vine.co/v/b1732mppTQD => 2013-02-01


#day of the week with the highest peak?
```
SELECT MAX(tweet_count), Date
FROM ( 
	SELECT COUNT(tweetid) as tweet_count, DATE(created_at) Date
	FROM `vineitems`
	GROUP BY Date
) as tweet_counts
```

2013-01-30 => 10038

#which are the most shared Vine
```
SELECT MAX(vine_count), vine
FROM 
(
	SELECT COUNT(vine) vine_count, vine
        FROM `vineitems`
) AS count_vines
```

12227 => http://vine.co/v/b1732mppTQD

<br>
<br>
#***Homework: SQL exercise
##### (After inserting more data in DB)
#How many tweets?
```
SELECT COUNT(tweetid) FROM `vineitems`
```

34059

#How many VINE URLs? Unique VINE URLs?
SELECT COUNT(vine) FROM `vineitems`

34059

#How many tweets are original?
```
SELECT COUNT(*)
FROM `vineitems`
WHERE mex NOT LIKE 'RT%'
```

25546

#Among the retweets, how many times a tweet has been retweeted in average?

#How many tweets for each day? In average?
```
SELECT DATE(created_at) Date, COUNT(*)
FROM `vineitems`
GROUP BY Date
```

  Date		 |  #tweets
 ----------  | ----------
2013-01-30	 | 	2189
2013-02-01	 | 	10038
2013-02-06	 | 	4565
2013-02-09 	 |	3677
2013-02-13 	 |	4558
2013-02-16   | 	3543
2013-02-17 	 |	1790
2013-02-20 	 |	3699



#Day of the week with highest volume of traffic?

#Which are the most popular hashtags?

#Rank the VINE URLs by popularity

#Add the link of the 3 most popular VINE videos in your database
