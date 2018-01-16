---
title: Creatures
date: 2018-01-16 00:25:00 Z
published: false
parent: world-of-warcraft.markdown
---

# Creatures

## [Creature Table](https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130150/game\+tele)
All spawned creatures(NPCs) are saved into creature table.
A few of these fields are also repeated in table creature_template (we are going to explain about the creature_template table later)
But remember all data from creature table will overwrite the data on the creature_template table.
For example, We have an NPC with flag = 5 on creature_template. Now if we change the NPC flag to 8 in creature table. The value of that flag will be 8 in the end.

{:.table}
| Field | Description |
| ----- | ----------- |
| guid   | (Primary key) This is a unique number for each spawned creature and we can address the creatures using GUID. **guid can be different to one realm to other** Because as I told you before core will fill the GUID value.|
|   Id   | This is the entry of the NPC. You can find it using.NPC info or in WoWhead. For example, http://www.wowhead.com/npc=56041 Id=56041.|
|Map| You can find the map number using .gps command in-game.|
|Spawnmask| Controls under which difficulties the creature is spawned. And you can combine the values here. For example, 2+8=10 so if you put 10 here the npc will be spawned in 25 normal and heroic modes.|
|phasemask| This field describes all the phases that a creature will appear in. You can change the play's phase by spells. For example, If you get targeted with a spell to change your phase to 1 you only will see NPCs in phase 1, If you're in phase 3, you will see NPCs in phase 2 and phase 1(2+1=3). http://www.wowhead.com/spell=55782/phase-shift-1-foote-steppes|
|Modelid| ModelID/MorphID of the NPC|
