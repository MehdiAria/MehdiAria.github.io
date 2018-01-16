---
title: World of Warcraft
date: 2018-01-15 23:43:00 Z
---

# Tutorials
## Creatures

# [creature](https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130150/game\+tele)
All spawned creatures(NPCs) are saved into creature table.
A few of these fields are also repeated in table creature_template (we are going to explain about the creature_template table later)
But remember all data from creature table will overwrite the data on the creature_template table.
For example, We have an NPC with flag = 5 on creature_template. Now if we change the NPC flag to 8 in creature table. The value of that flag will be 8 in the end.

| Fields | Information |
| ------ | ------ |
| guid   | (Primary key) This is a unique number for each spawned creature and we can address the creatures using GUID. **guid can be different to one realm to other** Because as I told you before core will fill the GUID value.|
|   Id   | This is the entry of the NPC. You can find it using.NPC info or in WoWhead. For example, http://www.wowhead.com/npc=56041 Id=56041.|
|Map| You can find the map number using .gps command in-game.|
|Spawnmask| Controls under which difficulties the creature is spawned. And you can combine the values here. For example, 2+8=10 so if you put 10 here the npc will be spawned in 25 normal and heroic modes.|
|phasemask| This field describes all the phases that a creature will appear in. You can change the play's phase by spells. For example, If you get targeted with a spell to change your phase to 1 you only will see NPCs in phase 1, If you're in phase 3, you will see NPCs in phase 2 and phase 1(2+1=3). http://www.wowhead.com/spell=55782/phase-shift-1-foote-steppes|
|Modelid| ModelID/MorphID of the NPC|


## Table Name

table{
    border-collapse: collapse;
    border-spacing: 0;
    border:2px solid #ff0000;
}

th{
    border:2px solid #000000;
}

td{
    border:1px solid #000000;
}

## Table Name

Content


## Game Teleports

If you in-game and use the .tele add and .tele delete commands you can add the new teleport location in your database and all save teleport locations are stored in this table. Read more on [Game Teleports](https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130150/game\+tele).

{:.table}
| Field | Description |
| ----- | ----------- |
| `id` | The ID of the teleport location. This number is unique to every location added. |
| `position_x` | The x-axis coordinate of the teleport location. This can be attained by using the .gps command. |
| `position_y` | The y-axis coordinate of the teleport location. This can be attained by using the .gps command. |
| `position_z` | The z-axis coordinate of the teleport location. This can be attained by using the .gps command. |
| `orientation` | The direction that the player will face after arriving at the teleport location. This can be attained by using the .gps command. (North = 0, South = 3.14159) |
| `map` | The map ID of the location. |
| `name` | A descriptive name for the teleport location. The name cannot have any spaces in it. It is also not recommended to use special characters such as periods, commas, slashes, etc... |

**Example of inserting a teleport into the database;**
```sql
INSERT INTO
```
