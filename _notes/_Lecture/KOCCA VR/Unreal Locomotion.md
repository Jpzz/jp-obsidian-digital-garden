---
tags:
  - Unreal
  - VR
Environemt: Window PC, Meta Quest3, Oculus Link, Unreal
---
## Locomotion

### Locomotion
- [b] Create Input Action
![](https://i.imgur.com/2j774wc.png)

- [b] Locomotion Input Action Settings
![](https://i.imgur.com/0EJzhWg.png)


### Smooth Turn
- [b] Create Input Action
![](https://i.imgur.com/2j774wc.png)

- [b] Smooth Turn Input Action Settings
![](https://i.imgur.com/951YWCa.png)

### Input Mapping
- [b] Add Input Action Mapping in IMC_Default
![](https://i.imgur.com/2uzH6fY.png)



- [b] IMC_Default Settings
	- Add IA_SmoothMove, Setting using Controller Device (Oculus Touch (L) Thumbstick Y-Axis)
	- Add IA_SmoothTurn, Setting using Controller Device (Oculus Touch (R) Thumbstick X-Axis)
![](https://i.imgur.com/qbTnzQK.png)




### VR Pawn Setting
<mark style="background: #BBFABBA6;">Change Actor Type, Pawn to Character</mark>
![](https://i.imgur.com/EvyC4fF.png)

- [b] Select Class Settings
![](https://i.imgur.com/iZzIdA5.png)
- [b] Change Parent Class Pawn to Character
![](https://i.imgur.com/kHIDMme.png)


<mark style="background: #BBFABBA6;">Scripting Blueprints</mark>
- [b] Disconnect, Snap Turn Blueprint pin 
![](https://i.imgur.com/F4JgjAV.png)

- [b] Disconnect, Teleport Blueprint pin
![](https://i.imgur.com/U2RAAe0.png)

- [b] Create IA_SmoothMove
	- Add Movement Input
	- Camera Forward Vector
![](https://i.imgur.com/i4Tl7dL.png)


- [b] Create IA_SmoothTurn
	- Add Actor World Rotation
![](https://i.imgur.com/5F8H5IC.png)


- [b] Uncheck Use Controller Rotation Yaw 
![](https://i.imgur.com/wO4sKcg.png)

