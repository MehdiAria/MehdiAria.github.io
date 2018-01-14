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