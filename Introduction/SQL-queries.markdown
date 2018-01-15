---
title: SQL Queries
date: 2018-01-14 20:28:00 Z
position: 1
order: 2
parent: /Introduction.markdown
---

# SQL Queries:
**Searching on a specific table:**
Imagine you want to make sure if the NPC 44110 is already spawned in-game or not? Or you need the exact location of the NPC? Or you need to know the NPC respawn time, etc...
So you have to find your creature in this long list
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372057880104534026/5.JPG" alt="" style="width:auto;">
</picture>
But the list is really long and this will take time.
You need a better method called "SQL queries".
It's time to start and write your first line of code
Click on "Query".
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372058231280893953/6.JPG" alt="" style="width:auto;">
</picture>
You will see this window:
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372058297806749716/7.JPG" alt="" style="width:auto;">
</picture>
1. Where you write your queries.
2. Where you see the result.
**SELECT:**
The simple structure of a searching query is like this:
```sql
SELECT * FROM creature WHERE id = 32928;
```
Click on "Execute SQL..." (Marked on the picture below) - Or you can press F9.
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372058914927149056/8.JPG" alt="" style="width:auto;">
</picture>
Using this query you can find all spawned NPCs with 32928.
Explanation:
1. SELECT: It's a Keyword and you have to write it exactly like this.
2. Star symbol: Star mark means "ALL": As you could see in the previous picture you could see "ALL" fields. (Will be explained later).
3. FROM: Another keyword.
4. creature: This is your table name.
5. WHERE: This is another keyword, after "WHERE" you have to write your condition.
6. id = 32928: the condition. For example, if you have too many data on your table and you want to see just data with ID 32928 you have to use conditions and filter the output.
7. ";" : Don't forget to finish all your query lines with";" mark. If you don't put the ";" your query line won't end up.
Example:
Wrong type:
```sql
SELECT * FROM creature WHERE id = 32928
SELECT * FROM creature WHERE id = 32927
This query equals to:
SELECT * FROM creature WHERE id = 32928SELECT * FROM creature WHERE id = 32927
```
Correct type:
```sql
SELECT * FROM creature WHERE id = 32928;
SELECT * FROM creature WHERE id = 32927;
```
More examples:
This will give you all results with GUID 314831:
```sql
SELECT * FROM creature WHERE guid= 314831;
```
Now let's make it complicated for a little bit:
We want to see all creature with "ID: 32928" and "areaId: 148":
```sql
SELECT * FROM creature WHERE id = 32928 AND areaId = 148;
``` 
As you can see here we made two conditions:
1. ID should be 32928.
2. AreaId should be 148.
And we separate these two conditions with "AND".

Now we want to see all NPCs with ID 24248 and ID 36597
```sql
SELECT * FROM creature WHERE id IN (24248, 36597);
```
As you can see here we are using "IN" instead of = mark.
We can even add more IDs. For example: 
```sql
SELECT * FROM creature WHERE id IN (24248, 36597,32928);
```
There are many other keywords you can use in your condition.
For example Or, Not, etc...
We want to see the position_x for NPC 36597:
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372066688029425666/9.JPG" alt="" style="width:auto;">
</picture>
Here you will see some problem with the result!
We have many fields and have to scroll right and left to find the position_x value.
There is a simple solution to this problem:
As you understood before * means "ALL".
Now we are going to change it:
```sql
SELECT position_x FROM creature WHERE id = 36597;
```
As you can see here we used position_x instead of (*) star mark because we just want to see the value of position_x, not all fields.
We can even combine.
For example, we need position_x, position_y, position_z of NPC 36597:
```sql
SELECT position_x,position_y,position_z FROM creature WHERE id = 36597;
```
As you can see here we separate field names with a "," and we can add many fields like that.
Now you can combine every I told you so far and create your own queries.
Attention: I would highly recommend you to use )`'( in your queries to avoid possible collisions.
For example, we want to make the last query look better and avoid the possible collisions:
```sql
SELECT `position_x`,`position_y`,`position_z` FROM `creature` WHERE (`id` = '36597');
```
Attention to the marks.
Use ` on table names and field names.
Use ' on numeric values, and you can use " for text string values.
Try to separate the condition with )(.
here you can find more information about SELECT:
[https://www.w3schools.com/sql/sql_select.asp](https://www.w3schools.com/sql/sql_select.asp)

**Editing data in a specific table:**
In order to edit rows (Field values), we use "UPDATE".
The simple structure of query is like this:
```sql
UPDATE `creature` SET `spawntimesecs`='60' WHERE (`ID`='56509');
```
1. UPDATE: It's a keyword just like SELECT, FROM, etc...
2. creature: Table name.
3. SET: another keyword.
4. spawntimesecs='60': The field name you want to change and the value you want to set into the field.
Note: If you are going to set a string text into the field I would recommend you to use "".
For example, SET name="Firestorm"
However '' is working as well, but better to use "".
'' is for characters and "" is for a text string.
6. (ID='56509'): It's our condition, conditions have explained before. It's just the same.
This will change spawntimesecs to 60 whenever the NPC ID is 56509.
Another example:
This will change position_z to -0.113633 and position_y to -96.8534 for all NPCs with ID 32928:
```sql
UPDATE `creature` SET `position_y`='-96.8534', `position_z`='-0.113633' WHERE (`id`='32928');
```
As you can see we can separate fields with a "," and we can add even more fields like this.

**Adding new row to a specific table:**
We use INSERT in order to add a new row in our table.
Here is the simple structure:
```sql
INSERT INTO `creature` (`guid`, `id`,`spawntimesecs`) VALUES ('2999945', '500','20');
```
1. INSERT INTO: Keyword.
2. creature: Table name.
3. (guid, id,spawntimesecs): The fields you want to fill, you can add more or fewer fields and you should separate them with a ",".
4. VALUES: Keyword.
5. ('2999945', '500','20'): the values you want to set into mentioned fields.
As you can see in creature table there are many other fields but we didn't use them, we just used 3 fields. guid, id, and spawntimesecs.
The question is "What happened to other fields like Map, position_x, ZoneId, etc...?"
The answer is pretty simple, the default value. There is a default value for each field. usually, the default value is 0, -1 or 1.
So if you don't mention a field you will have a default value on it but it's not the same for all fields and all tables, sometimes you have to fill the field.
However, there are many other structures for INSERT.
For example:
```sql
INSERT INTO `creature` (`guid`, `id`, `map`, `zoneId`, `areaId`, `spawnMask`, `phaseMask`, `PhaseId`, `PhaseGroup`, `modelid`, `equipment_id`, `position_x`, `position_y`, `position_z`, `orientation`, `spawntimesecs`, `spawndist`, `currentwaypoint`, `curhealth`, `curmana`, `MovementType`, `npcflag`, `unit_flags`, `dynamicflags`, `ScriptName`, `VerifiedBuild`) VALUES 
('2999945', '500', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0');
```
Here you will mention all fields and this query is too long and this will take time to write it, but the output is same as previous method.
Check this query:
```sql
UPDATE `creature` SET `spawntimesecs`='60' WHERE (`ID`='56509');
```
We have more than one creature with ID 56509, And this query will change spawntimesecs of all creatures to 60.
Sometimes especially when we are adding some creatures we have to do hundreds of INSERTs, this will be hard to write queries in this case and this takes too much time.
Again there are many methods and structures for it.
The first method is to repeat the SQL lines 100 times. And you will have 100 queries like this:
But you can also make it just with one single query:
```sql
INSERT INTO `creature` (`guid`, `id`, `map`, `zoneId`, `areaId`, `spawnMask`, `phaseMask`, `PhaseId`, `PhaseGroup`, `modelid`, `equipment_id`, `position_x`, `position_y`, `position_z`, `orientation`, `spawntimesecs`, `spawndist`, `currentwaypoint`, `curhealth`, `curmana`, `MovementType`, `npcflag`, `unit_flags`, `dynamicflags`, `ScriptName`, `VerifiedBuild`) VALUES 
('2999945', '500', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0'),
('2999946', '500', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0'),
('2999947', '501', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0'),
('2999948', '500', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0');
```
As you can see this time we used didn't repeat the field names and we used a "," after each row, but still we have to use ";" in the end of query.
and we can even add more line like that.
You may ask what is the difference between this method (One query) and the previous method (multiple queries)?
The answer depends on table and data you use, but usually, one query method is faster. However, this will consume more RAM.
All these lines should be added to the same table, in other words, you can't add rows like that to more than one table.
Here GUID is the primary key and you have to always search for a free number for it, otherwise, you will get an error when you want to execute the query.
Some people will use random big numbers, But it's not logical. Because will have to find many random numbers.
So what we have to do?
As I told before there is a default value for each field. It's the same for GUID.
When you INSERT something, try to don't fill the GUID and leave it "NULL". Because it's auto-fill and automatically you will have the lowest unique value in this field.
Note: NULL means nothing. Exactly nothing, not even 0, not even an empty space.
"How can we do the INSERT in the correct way?"
There two methods:
First method:
```sql
INSERT INTO `creature` (`guid`, `id`, `map`, `zoneId`, `areaId`, `spawnMask`, `phaseMask`, `PhaseId`, `PhaseGroup`, `modelid`, `equipment_id`, `position_x`, `position_y`, `position_z`, `orientation`, `spawntimesecs`, `spawndist`, `currentwaypoint`, `curhealth`, `curmana`, `MovementType`, `npcflag`, `unit_flags`, `dynamicflags`, `ScriptName`, `VerifiedBuild`) VALUES 
('', '500', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0');
```
GUID value is NULL in this case. It's '' and'' means NULL.
Second method:
```sql
INSERT INTO `creature` (`id`, `map`, `zoneId`, `areaId`, `spawnMask`, `phaseMask`, `PhaseId`, `PhaseGroup`, `modelid`, `equipment_id`, `position_x`, `position_y`, `position_z`, `orientation`, `spawntimesecs`, `spawndist`, `currentwaypoint`, `curhealth`, `curmana`, `MovementType`, `npcflag`, `unit_flags`, `dynamicflags`, `ScriptName`, `VerifiedBuild`) VALUES 
('500', '0', '0', '0', '1', '1', '0', '0', '0', '0', '0', '0', '0', '0', '120', '0', '0', '1', '0', '0', '0', '0', '0', '', '0');
```
Thi time GUID field name doesn't even exist on field names so it will be given a default unique value and also considered NULL.
There is a difference between first and second method on the first method you will get warnings because you actually mentioned the field name but you didn't put anything on it. that's I would recommend you to use the second method.
**Deleting data in a specific table:**
This one really simple and it's just like SELECT.
For example, we want to DELETE all creatures in-game with NPC ID 32890:
```sql
DELETE FROM creature WHERE (`Id` = '32890');
```
Compare it to SELECT:
```sql
SELECT * FROM creature WHERE (`Id` = '32890');
```
It's quite simple.
As you see we can just replace "SELECT *" with "DELETE".
And again we can change conditions too.

**Standards:**
If you are going to release your SQL codes with others you should remember some standards.
Simply, open a text editor, write queries on it and save the file with.SQL suffix. For example test.SQL
You can also use Notepad++
Important: In your file always DELETE everything you want to INSERT before the INSERT.
Look this INSERT code:
```sql
INSERT INTO `creature` (`id`,`map`) VALUES ('400' , '530');
```
If you add this to your file and execute the file twice, you will get an error.
Or this will add another creature you don't need it at all.
So you have to use DELETE before this code and remove the possible duplicated one.
Like this:
```sql
DELETE FROM `creature` WHERE (`id` = '400');
INSERT INTO `creature` (`id`,`map`) VALUES ('400' , '530'); 
```
**Sorting and limiting the resoult:**
Imagine you want to see all creatures on creature table from lowest NPC ID to highest NPC ID:
```sql
SELECT * FROM `creature` ORDER BY `id`;
```
As you can the sorting is based on id field and ORDER BY is a new keyword here.
Sometimes we have two creatures with the same ID.
For example, we want to see all creatures on creature table from lowest NPC ID to highest NPC ID and if we have same NPC ID on some creatures second sort priority should be areaId:
```sql
SELECT * FROM `creature` ORDER BY `id`,`areaId`;
```
Also, we can add more fields, just need to separate them with a ",".
Attention: This will sort the results, not the table itself.
"What if we want to see the results from highest ID to lowest ID?"
We can just add a "DESC":
```sql
SELECT * FROM `creature` ORDER BY `id` DESC;
```
DESC stands for descending and will reverse the result.
We can still add conditions:
This show all creatures with ID 1412 and also will sort the result.
```sql
SELECT * FROM `creature` WHERE `id` = 1412 ORDER BY `guid`;
```
***Limiting:***
When are using SELECT and searching in a table especially in a large table like creature table, you will see many rows each time you search.
You can use LIMIT to make limitations.
This will show you only 5 creatures with NPC ID 1412:
```sql
SELECT * FROM `creature` WHERE `id` = 1412 LIMIT 5;
```
Imagine you have many duplicated numbers on a column (Like spawntimesecs on creature table, there are many 120, 300, etc...). And you want to see each number just once, also you want to sort the results. In other words, you want to delete duplicated numbers in results and sort the results.
For example, you have:
```
3
2
3
4
5
3
1
```
And you want it like this:
```
1
2
3
4
5
```
It's pretty simple.
Here we need to use GROUP BY, like this:
```sql
SELECT * FROM `creature` GROUP BY `spawntimesecs`;
```
Again just like ORDER BY you can add your own conditions.
This one will sort the results based on position_x for all creatures with ID 6491, also this will remove all duplicated numbers on position_x in your SELECT results.
```sql
SELECT * FROM `creature` WHERE `id` = 6491 GROUP BY `position_x`;
```
Also just like ORDER BY you can add DESC to the query.
As you can see there is a difference between ORDER BY and GROUP BY. both of them will sort the result but GROUP BY will also hide the duplicated query results.
**Variables:**
A dish, a container. Imagine you have a container you can always fill it with some stuff and move these stuff from a container or another one.
These containers should save all their data on memory and this will consume your RAM space.
There are many types of containers so there are many types of variables.
How to use a variable:
```sql
SET @Myvariable = 100;
```
SET: Keyword to assign a value to the variable.
@Myvariable: Variable name, must start with @, can't use the forbidden stuff such as a free space.
= 100: the value you want to set to the variable.
Note: you can also re-assign another value to the variable:
```sql
SET @Myvariable = 100;
SET @Myvariable = 200;
```
Now the value of @Myvariable will be 200 because we just did an overwriting.
"What's the point of using variables?"
Check the query here:
```sql
SET @Myvariable = 15197;
SELECT * FROM `creature` WHERE `id` = @Myvariable;
```
instead of using values in SQL queries we can use variables.
You can also use mathematical stuff on variables:
```sql
SET @Myvariable1 = 1500;
SET @Myvariable2 = 197;
SET @Myvariable3 = @Myvariable2 + @Myvariable1;
```
Here the value of @Myvariable will be 15197.
**Commenting:**
If you know other programming languages it's really easy for you to understand this part.
Imagine you wrote an SQL file with more than 1K SQL lines, you give the file to another person and he should also add or edit some queries. In this case, you have to add some texts/notes on your it, we call these notes comments.
When you are executing your queries the comment part will **not** execute.
**Using comments:**
There are two methods:
First method:
```sql
-- This is the note we were talking about it.
```
Second method:
```sql
/*
This is the note we were talking about it.
*/
```
Obviously, the second method is better to use for multiline comments and the first one is better for a single line of comment:
```sql
-- Note is here
-- test note
-- comment here
```
```sql
/* Note is here
test note
comment here */
```
