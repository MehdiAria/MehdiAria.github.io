---
title: Introduction
date: 2018-01-14 03:51:00 Z
Field name:
  Key: 
---

# Introduction
The first question you will maybe ask is "What is a database and why we need to know about it?"
A database is a storage where you can save your information on it. information like: "Where the NPC should?", "What is the NPC name?", "What is the modelID of the game object/NPC?", etc...
Each database contains some tables.
"What is a table?"
It's where you can save your information on it.
For example, if you want to see a table:
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372053253653004288/2.JPG" alt="" style="width:auto;">
</picture>
Here you can find many tables, such as creature, gameobject, conditions, etc...
Now click on a table, for example, click on creature table:
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372054036267925504/3.JPG" alt="" style="width:auto;">
</picture>
On the red marked part, you can see the "Columns" or better to say "Fields".
"What is a field?"
A field is a set of data values of a particular simple type, one for each row of the table.
And between all fields on a table, we have an important field and call that "Key".
What is a key?
A key is a field but it's a <unique filed>. which means, you can't have duplicate value in this filed.
Here in this picture, you can see the key filed, it's marked with a colored key.
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372054594022277130/10.JPG" alt="" style="width:auto;">
</picture>
If you need a better explanation click on "Data":
<picture>
<img src="https://cdn.discordapp.com/attachments/369829063877066752/372055326482235403/4.JPG" alt="" style="width:auto;">
</picture>
Is this screenshot you can see all data on creature table.
Guid, Id, Map, ZoneId, etc.. are fields.
For example, in the screenshot, you can find information about NPC with GUID (Key) 260000 and ID 32928. (Position_X, Position_Y, Position_Z, spawntimesec, etc..).
As you can see there GUID is the key because it's unique for example we can't have two NPCs with GUID 260007.
GUID and ID, Right? If you don't know just ask me.
ID and GUID both are unique numbers, ID in creature table is the NPC ID you see in-game, you can use the ID to add a new NPC for example. But what if you have more than 1000 NPCs in-game with same NPC ID? How do you want to address one of them? We use GUID to address all spawned NPCs in-game. For example, if we have 1000 NPCs in-game with same NPC ID and we want to address and delete one of them we use GUID because GUID is unique"

## Getting started with SQL codes
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
SELECT * FROM creature WHERE id = 32928;
SELECT * FROM creature WHERE id = 32927;
=
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
https://www.w3schools.com/sql/sql_select.asp