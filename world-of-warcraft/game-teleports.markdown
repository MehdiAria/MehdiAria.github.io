---
title: Game Teleports
date: 2018-01-15 23:44:00 Z
position: 0
parent: world-of-warcraft.md
---

## [Game Teleports](https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130150/game\+tele)

If you in-game and use the .tele add and .tele delete commands you can add the new teleport location in your database and all save teleport locations are stored in this table.\
{:.table}
| Fields | Information |
| ------ | ------ |
| id | The ID of the teleport location. This number is unique to every location added. |
| position_x | The x-axis coordinate of the teleport location. This can be attained by using the .gps command. |
| position_y | The y-axis coordinate of the teleport location. This can be attained by using the .gps command. |
| position_z | The z-axis coordinate of the teleport location. This can be attained by using the .gps command. |
| orientation | The direction that the player will face after arriving at the teleport location. This can be attained by using the .gps command. (North = 0, South = 3.14159) |
| map | The map ID of the location. |
| name | A descriptive name for the teleport location. The name cannot have any spaces in it. It is also not recommended to use special characters such as periods, commas, slashes, etc... |

## Example of a Query
```sql
INSERT INTO
```