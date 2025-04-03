# Instagram-user-analysis
 PROJECT DESCRIPTION- Under this project I have to gain useful insights from the dataset given using MySQL 
Workbench .
 PROJECT APPROACH- The project was made by mysql workbench where the database was created from the 
rawdata given using data extracting queries.
 TECH STACK USED- The tech stack used is MySQL Workbench v8.0.30.0.
 Project Insights 
a) Marketing Analysis 
1. Most Loyal User Reward
Oldest users
 80 Derby_Herzog        2016-05-06 00:14:21
 67 Emilio_Bermier52 2016-05-06 13:04:30
 63 Elenor88                 2016-05-08 01:30:41
 95 Nicole71                 2016-05-09 17:30:22
 38 Jordyn.Jacobson2 2016-05-14 07:56:26
 Code- SELECT*
 FROM users
 ORDER BY created_at
 LIMIT 5;
2. Reminder to inactive users
Identify and remind inactive users to reengage.
 5 Aniya_Hackett
 7 Kasandra_Homenick
 14 Jaclyn81
 21 Rocio33
 24 Maxwell.Halvorson
 25 Tierra.Trantow
 34 Pearl7
 36 Ollie Ledner37
 41 Mckenna17
 45 David. Osinski47
 49 Morgan. Kassuike
 53 Linnea59
 54 Duane60
 57 Julien Schmidt
 66 Mike. Auer39
 68 Franco Keebler64
 71 Nia Haag
 74 Hulda Macejkovic
 75 Leslie67
76 Janelle. Nikolaus81
 80 Darby_Herzog 
81 Esther Zulauf61
 83 Bartholome. Bernhard
 89 Jessyca West
 90 Esmeralda. Mraz57
 91 Bethany20
 Code- SELECT username
 FROM users
 LEFT JOIN photos
         ON users.id=photos.user_id
 WHERE photos.id IS NULL;
 3. Declaring Contest Winner:
 The team started a contest and the user who gets the most likes on a single photo will win the contest now they 
wish to declare the winner.
 Zack Kemmer93 145 https://jarret.name 48
 Code- SELECT
 username,
 photos.id,
 photos.image_url,
 count(likes.user_id) AS total
 FROM photos
INNER JOIN likes
 ON likes.photo_id=photos.id
 INNER JOIN users
 ON photos.user_id = users.id
 GROUP BY photos.id
 ORDER BY total DESC
 LIMIT 1;
 4. Hashtag Research
Identify and suggest the top five most used hashtags.
 Smile 59
 Beach 42
 Party 39
 Fun 38
 Food 24
 Code- SELECT
 tags.tag_name,
 COUNT(*) AS total
 FROM photo_tags
 JOIN tags
 ON photo_tags.tag_id= tags.id 
GROUP BY tags.id
 ORDER BY total DESC
5. Ad Campaign Launch
The team wants to know, which day would be the best day to launch ADs.
 Thursday 16
 Sunday 16
 Code-SELECT
 DAYNAME(created_at) AS day,
 count(*) as total
 FROM users
 GROUP BY day
 ORDER BY total DESC
 LIMIT 2;
 b) Investor Metrices
1. User Engagement
A users avaerage post is more than 2.2.5700
 Code- SELECT
 (SELECT COUNT() FROM photos) / (SELECT COUNT() FROM users) AS avg;
 2. Bots & Fake Accounts- These are some user who can be boat and fake accounts. 
Aniya_Hackett 257
 Bethany20     
Duane60         
   257
  257
Jaclyn81                 
   257
 Janelle. Nikolaus81 257
 Julien_Schmidt        
257
 Leslie67                     
257
 Maxwell.Halvorson 257
 Mckenna17             
 257
 Mike. Auer39           
Nia_Haag                  
Ollie_Ledner37        
Rocio33                     
257
 257
 257
 257
 Code- SELECT user_id, COUNT(*) as num_likes
 FROM likes
 GROUP BY user_id
 HAVING num_likes = (SELECT COUNT() FROM photos); 
SELECT u.username, COUNT() as num_likes
 FROM users u
 JOIN likes I ON u.id = l.user_id
 GROUP BY u.id 
HAVING num likes = (SELECT COUNT(*) FROM photos);
 RESULT- I have gained practical approach towards MySQL through this project.
 This project was really interesting for a person like me
