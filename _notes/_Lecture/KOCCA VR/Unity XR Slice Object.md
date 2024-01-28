---
tags:
  - Unity
  - VR
Environemt: MAC, Unity, Meta Quest3, StandAlone
---
## Slice Object
### Using Ezy Slice Plugin
- [b] Download Ezy Slice
	- https://github.com/DavidArayan/ezy-slice
![](https://i.imgur.com/mfxRtck.png)

- [b] Unzip Ezy Slice project, Drag files into Unity project
	- EzySlice folder
![](https://i.imgur.com/7M3F84g.png)


### Slice Setting
#### In Level
- [b] Create Cube and rename target
- [b] Create Plane and rename Debug plane
![](https://i.imgur.com/HFS1Jed.png)



- [b] Place SaberModel Prefab in Level
![](https://i.imgur.com/6pwLZ4P.png)


#### Saber Model
- [b] Create Custom Script, SliceObject
- [b] Write SliceObject 
``` CSharp
using System;  
using System.Collections;  
using System.Collections.Generic;  
using EzySlice;  
using UnityEngine;  
  
public class SliceObject : MonoBehaviour  
{  
    public GameObject target;  
    public Transform debugPlane;  
	public Material crossSectionMat;
  
    private void Update()  
    {        
	    if (Input.GetKeyDown(KeyCode.Space))  
	        Slice(target);  
    }  
    public void Slice(GameObject target)  
    {        
	    SlicedHull hull = target.Slice(debugPlane.position, debugPlane.up);  
  
        if (hull != null)  
        {            
	        GameObject upperHull = hull.CreateUpperHull(target, crossSectionMat);  
			GameObject lowerHull = hull.CreateLowerHull(target, crossSectionMat);  
			Destroy(target);
        }    
    }    
}

```

- [b] Set Reference in SliceObject Component and Play
![](https://i.imgur.com/tBEBljO.png)

- [b] Add Rigidbody Explosion code in Sliced Object (upper, lower hull)