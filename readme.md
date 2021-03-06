﻿# Probably Over-Engineered Procedural Dungeon Generator
~~This is an open-source implementation of a procedural dungeon generator used in TinyKeep game.~~ This procedural dungeon/level generator is inspired by the procedural dungeon generator used in TinyKeep game. The instructions are provided by **u/phidinh6** on Reddit. You can find the post [here](https://www.reddit.com/r/gamedev/comments/1dlwc4/procedural_dungeon_generation_algorithm_explained/).

A game demo that implements this library to showcase it is hosted on itch.io, which you can access [here](https://very-small-dev.itch.io/exploration-game).

# How does it work?
the check mark indicates that it has been implemented. It works by going through several steps;
1. - [x] **Generate Rooms.** This is the most basic step. The room must be randomly generated and coupled tight in a circle. This one uses [Box-Mueller transform](https://en.wikipedia.org/wiki/Box%E2%80%93Muller_transform).
![Step 1 Image](repo_images/step1.png)
2. - [x] **Expand and spread the rooms.** The second step is splitting them all. The rooms that was previously overlapping will be split apart. This way, every room will be distributed around the area. The distance between each other can be adjusted.
![Step 2 Image](repo_images/step2.png)
3. - [x] **Selectively pick the main rooms.** This one depends with how it is implemented. The number used to generate the box will be used for this scenario. We'll pick and use the ones that have certain sizes that the user wants. In this case, the big ones.
![Step 3 Image](repo_images/step3.png)
4. - [ ] **Distribute tunnels accordingly.** This one is self-explanatory. Add the tunnels, or hallways. Depends with how you want to do it.
	1. - [x] **Connect all rooms.** We use [Delaunay Triangulation](https://en.wikipedia.org/wiki/Delaunay_triangulation) to create the tunnels. This way, all the rooms are connected with each other with the tunnels.
	![Step 4 Phase 1 Image](repo_images/step4.1.png)
	2. - [x] **Remove overlapping connections.** This is done to ensure that every relationship does not create a messy-looking tunnel.
	![Step 4 Phase 2 Image](repo_images/step4.2.png)
	3. - [x] **Ensure it does not generate too many tunnels.** We need to make sure that we don't use all the tunnels that exist there. ~~We cut them off with [Minimum Spanning Tree](https://en.wikipedia.org/wiki/Minimum_spanning_tree) to make sure it does not use all the tunnels, but every room are still connected with each other.~~
	![Step 4 Phase 3 Image](repo_images/step4.3.png)
	4. - [x] ~~**Add loops in some areas.** This is done to ensure that the dungeon does not go in straight line. After removing the extra tunnels, we might want to add, say, 15% to 30% amounts of tunnels that was removed previously.~~
	5. - [ ] **Generated tunnels must have L shapes, or similar.** To add a bit of variety, this is added to ensure that the dungeons doesn't look weird in the map. If the user so desires, they can merge the tiny, discarded rooms to create a jagged, messy looks of the tunnel.
	![Step 4 Phase 5 Image](repo_images/step4.5.png)
5. - [x] **Incorporate the tile system.** After the dungeons are produced, it needs to be adjusted so that it is tiled properly. Depending with the size, it can be tiled in many ways. This one is optional for certain procedural generation use cases.
![Step 5 Image](repo_images/step5.png)

# How do I use it?
TODO: Write a guide here.

# License
This library and its demo is licensed under MIT license.