# Introduction
The first question you will maybe ask is "What is a database and why we need to know about it?"
A database is a storage where you can save your information on it. information like: "Where the NPC should?", "What is the NPC name?", "What is the modelID of the game object/NPC?", etc...
Each database contains some tables.
"What is a table?"
- It's where you can save your information on it.
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

# Getting started with SQL codes
**Searching on a specific table**
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
