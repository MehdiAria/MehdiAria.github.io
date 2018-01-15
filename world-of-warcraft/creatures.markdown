---
title: Creatures
date: 2018-01-15 05:12:00 Z
position: 1
order: 2
parent: world-of-warcraft.markdown
---

## [creature](https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130150/game\+tele)
All spawned creatures(NPCs) are saved into creature table.
A few of these fields are also repeated in table creature_template (we are going to explain about the creature_template table later)
But remember all data from creature table will overwrite the data on the creature_template table.
For example, We have an NPC with flag = 5 on creature_template. Now if we change the NPC flag to 8 in creature table. The value of that flag will be 8 in the end.

| Fields | Information |
| ------ | ------ |
| Entry  | The NPC ID, just like ID in creature table. Because they are linked. Entry in creature_template is a primary key and in creature table, the field name will be ID and it’s a foreign key.

## Table Name

Content

## Table Name

Content
