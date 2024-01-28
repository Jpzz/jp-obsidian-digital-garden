---
tags:
  - Unreal
  - VR
Environemt: Window PC, Meta Quest3, Oculus Link, Unreal
---
## Widget Interaction in VR

#### Widget Blueprint
- [b] Widget Blueprint
![](https://i.imgur.com/IIfFXEL.png)

- [b] Make Canvas in Widget
	- Drag & Drop Canvas Panel
![](https://i.imgur.com/MVVEAJV.png)

- [b] Make Button in canvas
![](https://i.imgur.com/QyfSafE.png)


#### ElementUI Actor Blueprint
- [b] Create Element UI Blueprint
![](https://i.imgur.com/FcPPKTs.png)

- [b] Add Widget Actor
![](https://i.imgur.com/cFPki6S.png)
- [b] Set Widget Class
	- WB_Interact
![](https://i.imgur.com/Jd2uxVB.png)

- [b] Place ElementUI Blueprint in Level
![](https://i.imgur.com/abq8imh.png)

- [b] Set Widget Collision
- Collision Presets Change Custom
- Object Type Change World Dynamic
- Trace Responses 3D Widget Block

![](https://i.imgur.com/QgaZjs0.png)


#### VR Pawn
- [b] Set WidgetInteractionRight Details
	- Interaction Trace Channel change World Dynamic
![](https://i.imgur.com/TZUuwbd.png)

- [b] Show Debug
	- Show ray
![](https://i.imgur.com/ycIhNJc.png)

- [b] IA_InteractR
	- InteractR Started Node, Completed Node
	- Press Pointer Key, Key binding LeftMouse Button
	- Release Pointer Key, Key binding RightMouse Button
![](https://i.imgur.com/AhOVso6.png)


#### WB_Interact Blueprint
- [b] Button Events
- On Pressed, On Hovered, On Unhovered
![](https://i.imgur.com/Xg221Nq.png)

- [b] Change Button Color when hovered, unhovered, pressed button
![](https://i.imgur.com/pHPJ6GS.png)



### Change Day or Night

#### WB_Interact
- [b] Create Press Button Event (Day or Night Button)
- [b] Create Event Dispatcher
	- Rename DayorNightDispatcher
![](https://i.imgur.com/4aBspy4.png)

- [b] Connect DayorNightDispatcher to On Clicked
	- Event Dispatcher Call type
![](https://i.imgur.com/xq7J9Na.png)


#### INTERFACE_DayorNight
- [b] Create Interface Blueprint
	- Rename INTERFACE_DayorNight
![](https://i.imgur.com/2f3UmYc.png)

- [b] Create Function DayorNight
![](https://i.imgur.com/MdAIlru.png)


#### BP_ElementUI
- [b] Create Cast To WB_Interact
	- promote WB Interact variables
![](https://i.imgur.com/sWJxv3N.png)


- [b] Bind Event to DayorNight Dispatcher
- [b] DayorNightDispatcher_Event connect to DayorNight Interface
	- Create 'LightingSystem' variables
	- Connect LightingSystem
![](https://i.imgur.com/eiR1mnI.png)


#### BP_LightingSystem
- [b] Create Blueprint
	- Rename BP_LightingSystem
![](https://i.imgur.com/im3zNFA.png)

- [b] Add Direction Light, Exponential HeightFog, Sky atmosphere, Skylight, Volumetric Cloud
![](https://i.imgur.com/elLrLaO.png)
![](https://i.imgur.com/XiPQZYO.png)


- [b] Implement Interface in Class Settings
	- Implement Interface INTERFACE_DayorNight
![](https://i.imgur.com/E0iwjxl.png)

- [b] Implement event DayorNight
![](https://i.imgur.com/OrCm1Lp.png)

- [b] Create Timeline
	- Flip Flop Connect Play and Reverse Timeline
![](https://i.imgur.com/V4Tk9Lm.png)

- [b] Set Timeline Node
	- Set Keyframe
![](https://i.imgur.com/4T6ZerJ.png)

- [b] Set Relative Rotation
- [b] Make Variables DayRotator, NightRotator
![](https://i.imgur.com/cIqLv1q.png)

- [b] Make Lerp node
	- Day Rotator, Night Rotator
![](https://i.imgur.com/49mn2Ef.png)
