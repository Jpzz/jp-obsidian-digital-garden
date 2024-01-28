---
tags:
  - Unity
  - VR
Environemt: MAC, Unity, Meta Quest3, StandAlone
---
## Hand Tracking

### Setup
#### Package Manager Plugin
- [b] XR Interaction Toolkit
	- Starter Assets
	- Hands Interaction Demo
![](https://i.imgur.com/0aTiRhm.png)

- [b] XR Hands
![](https://i.imgur.com/dl79vPD.png)


#### Project Settings
- [b] OpenXR Android Settings
	- Check Hand Tracking Subsystem
	- Check Meta Hand Tracking Aim
![](https://i.imgur.com/3qgEzjX.png)


#### Upgrade URP Materials
- [b] Select Standard Materials
![](https://i.imgur.com/Izt22aX.png)

- [b] Convert Standard Materials to URP Materials
	- Edit -> Rendering -> Material -> Convert to Built-in Materials to URP 
![](https://i.imgur.com/FPLQFvD.png)


### Test
- [b] Open HandDemoScene
![](https://i.imgur.com/y7kI3X6.png)
- [b] Android Build


### HandVisualize Setup
#### Utilize XR Origin Prefab (Set Locomotion)
- [b] Set up XR Origin Hands (XR Rig) in Hierarchy
![](https://i.imgur.com/Yd3Y3iK.png)

- [b] Add Interaction Manager, Input Manager
![](https://i.imgur.com/QAIe5pd.png)
![](https://i.imgur.com/A3UeF0k.png)

- [b] Add XR EventSystem
![](https://i.imgur.com/TbsKTMG.png)

#### Change XRI Default Settings
- [b] Input Action System Setting
	- Action Assets -> Set XRI Default Input Actions
![](https://i.imgur.com/AVQ4zVM.png)

- [b] Change Input Action Reference in Direct Interactor
	- When using XR Controller, Position Action set XRI LeftHand/Position and XRI RightHand/Position (Input Action Reference)
	- But We use XR Hands, Change Position Action Reference to XRI LeftHand/Pinch Position and XRI RightHand/Pinch Position (Input Action Reference)
![](https://i.imgur.com/fEdUOJG.png)


- [b] Chanage Input Action Reference in Ray Interactor
	- When using XR Controller, Position Action set XRI LeftHand/Position and XRI RightHand/Position (Input Action Reference)
	- But We use XR Hands, Change Position Action Reference to XRI LeftHand/Aim Position and XRI RightHand/Aim Position
	- And Change Rotation Action Reference to XRI LeftHand/Aim Rotation and XRI RightHand/Aim Rotation
![](https://i.imgur.com/Omizzy5.png)


### Setting Interactable Grab Object
#### In Level
- [b] Create Floor
- [b] Create Cube
	- Change object name to 'Interactable Cube'
#### Interactable Cube
- [b] Add Component XR Grab Interactable
![](https://i.imgur.com/np034ac.png)

- [b] Check Use Dynamic Attach in XR Grab Interactable Component
![](https://i.imgur.com/ur30Ob1.png)

- [b] Check Is Kinematic in Rigidbody Component
![](https://i.imgur.com/reU4dvN.png)
