---
title: Creatures
date: 2018-01-15 05:12:00 Z
position: 1
order: 2
parent: world-of-warcraft.markdown
---

## creature
All spawned creatures(NPCs) are saved into creature table.
A few of these fields are also repeated in table creature_template (we are going to explain about the creature_template table later)
But remember all data from creature table will overwrite the data on the creature_template table.
For example, We have an NPC with flag = 5 on creature_template. Now if we change the NPC flag to 8 in creature table. The value of that flag will be 8 in the end.
It’s time to explain about important fields on creature table.
guid (Primary key): This is a unique number for each spawned creature and we can address the creatures using GUID.
**guid can be in each realm/server** Because as I told you before core will fill the GUID value.
Id: This is the entry of the NPC. You can find it using.NPC info or in WoWhead
http://www.wowhead.com/npc=56041 Id=56041
Map: You can find the map number using .gps command in-game.
Spawnmask/phasemask: This is about phases, We work sometimes with phases.
Note: Sometimes phasing system is just a little bit different is your realm.
If you get targeted with a spell to change your phase to 4 you only will see NPCs in phase 4, If you're in phase 3, you will see NPCs in phase 2 and phase 1(2+1=3).

## Table Name

Content

## Table Name

Content
