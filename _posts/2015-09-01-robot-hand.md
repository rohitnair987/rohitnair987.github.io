---
layout      : post
title       : "Robot Hand - Graph Search Algorithms"
excerpt     : "Indiana University Bloomington"
project     : true
folder      : robot-hand
git         : https://github.com/rohitnair987/Artificial_Intelligence/blob/master/Robot_World/Robot_Block_Movement_Automation.py
startDate   : August 2015
endDate     : September 2015
tag:
- Python
- Artificial Intelligence
- Search
- Breadth First Search
- Depth First Search
- Heuristics
- Best First Search
comments    : false
---

## Problem:
We have to control a robot hand which can move up, down, right or left. Aim is to pick up item A and place it box A, item B in box B and so on.

<br />
### Solution:
* Greedy: We started with the basic greedy approach where we move the hand till we reach the items and then the boxes.
* BFS: Explore the map breadth-wise
* DFS: Explore the map depth-wise
* Best First: Use heuristics to judge which action will take us closest to the goal position