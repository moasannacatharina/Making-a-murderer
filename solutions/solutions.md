# Solutions

#### Spoiler alert! Don't read this unless you intend to see all the answers to the mystery.
##### This is meant as a step-by-step guide on how to solve the mystery, for those who want/need it:

<br>

1. With the story plot information given from the 'README.md', you will be handed a clue to fetch a ```crime_scene_report``` dated ```2018-07-07```.
*Following query can be used:*
```sql
SELECT * from crime_scene_reports
WHERE date="2018-07-07";
```
<br>

2. In the report a cat with a big nose was spotted. This should lead you to search for that very ```distinct_quality``` from the ```cats``` table.
*Following query can be used:*
```sql
SELECT * from cats
WHERE distinct_features="big nose";
```
<br>

3. After the cat with the big nose (Brandy Stanlake) has been found in the ```cats``` table - you'll be able to see what ```cat_id``` Brandy has and therefore be able to search for them back in the ```crime_scene_reports``` table.
*Following query can be used:*
```sql
SELECT * from interviews
WHERE cat_id=349;
```
<br>

4. According to Brandy's ```statement``` he pretty much says that he doesn't know anything but that the interviewer should talk to a cat who wears glasses.
He also mentions that one might find them by grouping all cats by gender.
*To figure this out, following query can be used:*
```sql
SELECT *
FROM cats
GROUP BY gender;
```
<br>

5. The query will give you three hits. One of which has ```wears sunglasses``` as their ```distinct_features``` .
Considering what's been said by Brandy, you should repeat the same type of search as you've done earlier except this time in regards to the cat (Rip Yallop) and their statement in ```interviews```.
*This query can be used:*
```sql
SELECT * from interviews
WHERE cat_id=209;
```
<br>

6. Through Rip's statement you'll want to look for a cat called ```Short Valley Medium```. Same procedure goes here. First you'll have to search their name in the ```cats```table followed by using their "id"/"cat_id" to able to read their statement in ```ìnterviews```
*Following queries will get you on the right path*
```sql
SELECT * 
FROM cats
WHERE name="Short Valley Medium";
```
*Then:*
```sql
SELECT * 
FROM interviews
WHERE cat_id=380;
```
<br>

7. This is the hardest "code to crack". Through Short Valley Medium's statement (which was made *before* Yam-Yam's even disappeared:scream_cat: w00t?!) you're able to figure out the remaining clues.
She is trying to say that you should select three columns: ```apartment_check_in_time``` + ```number_of_bedrooms``` and ```encrypted```.
Create an ```ÌNNER JOIN``` and in order to be able to specify the correct row you also need to ad the ```SSN``` value that she mentions.
*This query can be used*
```sql
SELECT hacker_kitty_data.apartment_check_in_time, apartments.number_of_bedrooms, hacker_kitty_data.encrypted
FROM apartments
INNER JOIN hacker_kitty_data
ON hacker_kitty_data.apartment_id = apartments.id
WHERE hacker_kitty_data.SSN = 55085;
```
<br>

8. In order to get the correct password you'll have to use simple math addition by taking the value listed on ```apartment_check_in_time```which is 24 and then just add the value next to it listed in ```number_of_bedrooms```which is 4. 24 + 4 = 28. **28 is the magic password!**
If you click the encrypted box, a hidden [**url**](https://tools.knowledgewalls.com/online-secret-message-encoder-decoder?mi=WkxaSG5ZeEpabjg1d2MvSk9wejJYZz09Ojq6p34z97EEz3KL9lGwX2ri) will reveal itself. Type in the password, press the 'Decode' button and see what unfolds and you will finally be able to see what this ending has in store.

###### Thanks for playing! Take care! :smiley_cat:
