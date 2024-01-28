---
tags:
  - Unreal
  - VR
Environemt: Window PC, Meta Quest3, Oculus Link, Unreal
---
## Interaction Input Setting

### Create Input Action
- [b] Create Input Action
![](https://i.imgur.com/tFABg17.png)


- [b] Right Interact Action & Left Interact Action
![](https://i.imgur.com/sIFydWz.png)
![](https://i.imgur.com/u7itdye.png)

### Adjust Input Action Mapping
- [b] Add IA_InteractL, IA_InteractR (Oculus Touch(L) Trigger, Oculus Touch (R) Trigger)
![](https://i.imgur.com/VGCW4w3.png)


### Scripting Blueprint
#### VR Pawn
- [b] Raycasting Motion Controller Left Aim
![](https://i.imgur.com/LWBW4o5.png)

#### Door Blueprint
- [b] Detach Door Actor
![](https://i.imgur.com/ehDbsrE.jpg)

- [b] Converts this actor into reusable Blueprint Class that can have script behavior
![](https://i.imgur.com/8XMKQKb.png)

- [b] Create Door Blueprint
![](https://i.imgur.com/Ov71qD5.png)

- [b] Modify Door Rotation in BP_InteractDoor
	- Rectangle6646_Pivot Location (0, 0, 0) and Rotation (90, 0, -90)
![](https://i.imgur.com/Aew7Tsc.png)


- [b] Modify Door Rotation, Position in Level
	- BP_InteractDoor Rotation (0, 0, 0)
![](https://i.imgur.com/xwoNWo5.png)

#### Interface Blueprint
- [b] Create Interface Blueprint
- For connect VR Pawn with InteractableDoor blueprint,
![](https://i.imgur.com/YnxhNyj.png)
- Make Interact Function
![](https://i.imgur.com/VQzuy3h.png)

#### VR Pawn Blueprint
- [b] Connect Interact Interface in VR Pawn
- broken node Out Hit, connect Hit Actor to Target
![](https://i.imgur.com/Box5SBh.png)

#### InteractDoor Bluerpint
- [b] Implement Interface in BP_InteratDoor Blueprint
- In Class Settings,
- Implemented Interfaces BP_InteractInterface
![](https://i.imgur.com/2UsWj09.png)


- [b] Implemented Interface Event,
![](https://i.imgur.com/aHA7gXF.png)



- [b] Add Timeline
- Create Timeline Node
- Add Float Track in Timeline Node
![](https://i.imgur.com/LGWIy3Y.png)
![](https://i.imgur.com/Ij8oq9s.png)


- [b] Set Blueprint Node
![](https://i.imgur.com/dE65QQt.png)


#### Create Door Collision
- [b] Create Door Convex Collision
	- Auto Convex Collision
	- Apply
![](https://i.imgur.com/dtQzDKq.jpg)

