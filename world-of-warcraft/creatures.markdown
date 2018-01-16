---
title: Creatures
date: 2018-01-16 00:25:00 Z
position: 0
parent: world-of-warcraft.markdown
hide: true
---

# Creatures

## Creatures Table

All spawned creatures (non-player characters) are saved into creature table. A few of these fields are also repeated in table creature_template (we are going to explain about the creature_template table later).

But remember all data from creature table will overwrite the data on the creature_template table. For example, We have an NPC with flag = 5 on creature_template. Now if we change the NPC flag to 8 in creature table. The value of that flag will be 8 in the end.

{:.table}
| Field | Description |
| ----- | ----------- |
| guid   | (Primary key) This is a unique number for each spawned creature and we can address the creatures using GUID. **guid can be different in each realm/server** As explained before GUID is auto-fill and you can just leave this field NULL.|
|   Id   | This is the entry of the NPC. You can find it using.NPC info or in WoWhead. For example, http://www.wowhead.com/npc=56041 Id=56041.|
|Map| You can find the map number using .gps command in-game.|
|Spawnmask| Controls under which difficulties the creature is spawned. And you can combine the values here. For example, 2+8=10 so if you put 10 here the npc will be spawned in 25 normal and heroic modes.|
|phasemask| This field describes all the phases that a creature will appear in. You can change the play's phase by spells. For example, If you get targeted with a spell to change your phase to 1 you only will see NPCs in phase 1, If you're in phase 3, you will see NPCs in phase 2 and phase 1(2+1=3). http://www.wowhead.com/spell=55782/phase-shift-1-foote-steppes|
|Modelid| ModelID/MorphID of the NPC|
|Equipment_id| (Foreign key) this field can link your table to |
|Position_x, position_y, position_z| The exact position of the creature in-game.|
|Spawntimesecs| The spawn time of the creature (In seconds)|
|Spawndist| The maximum distance for the creature to walk around with random movements(only works if the creature has MovementType = 1 in creature table or creature_template table)|
|curhealth| The health that the creature will spawn with.|
|curmana| The mana that the creature will spawn with.|
|MovementType| There are 3 possible numbers for this field. 0= the NPC will just stay and won’t move, 1=Random movement and 2= Waypoint movement: The NPC will move in a specified line|
|InhabitType| Controls where the creature can move and attack.(You can combine)|
|Npcflag/unit_flags/dynamicflags |Some special flags. For example you make the creature to be quest giver with npc falgs. |
| Map | You can find the map number using .gps command in-game.|


## CREATURE_TEMPLATE Table.
This template table has whole the data about one creatures. When you want to add npc with creature table or in-game you have to make sure if the creature existing in this table. Creature_template is a template for creatures you spawn them in creature table. When you spawn a creature in-game or with creature table they inherit their field values from creature_template. But if you change anything on creatures table this will be overwritten for that specified creature with specified GUID.
{:.table}
| Field | Description |
| ----- | ----------- |
| Entry | (primary key)The NPC ID, just like ID in creature table. Because they are linked. |
| difficulty_entry_1-3 | The Id of the creature in different difficulties (Used for loot stuff). |  | KillCredit1-3 | When you kill the NPC you will get that credit ID (Used for quests). | 
| modelid1-3 | A modelID(morph ID) of the creature. | 
| name | The creature's name | 
| Subname | the subname of the creature. Will appear on <Subname here> | 
| IconName | Used to tell the player what kind of NPC is this. For example, when you mouse over on some creatures the cursor icon will be changed to a winged shoe. | 
| gossip_menu_id | This is a foreign for gossip menus (When you click on some creatures a window will appear with some texts and options we call that gossip menu) | 
| minlevel- maxlevel | The minimum and maximum level of the creature. | 
| Exp |  Can take values from 0 to 2 you can check the creature_classlevelstats table | 
| Faction_A and faction_H | In some databases, you have just one "Faction" and in other DBs you have both. It’s the faction ID of the creature | 
| Npcflag | This field controls a falg about the NPC to make it repairer, vendor, etc.. You can combine values here.For example, if the NPC is a quest giver and repairer you have to put 4098 (4096 for repairer and 2 for quest giver) | 
| Speed_walk, speed_run | Controls how fast the creature can run/walk | 
| Scale | Controls the size of the creature appears in-game | 
| Rank | The rank of the creature. You can change the respawn of the creature here. | 
| Dmgschool | creature's damage type. For example shadow, holy, etc... | 

## Example.
Content.
