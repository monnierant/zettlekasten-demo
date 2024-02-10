---
type: methode
topic: blender
---
- Topic : #blender 
- Tags : #python #vertex-color #mesh

# Idea

```Python
import bpy
import bmesh
import random

SCALE = 2.1
SCALEZ = 6.0

for obj in bpy.context.selected_objects:
	loc = obj.location
	color = ((((loc.x/SCALE)+1)/2), (((loc.y/SCALE)+1)/2), (((loc.z/SCALEZ)+1)/2), random.uniform(0.0,1.0))

	bm = bmesh.new()
	bm.from_mesh(obj.data)
	color_layer = bm.loops.layers.color.new("Col")

	for face in bm.faces:
		for loop in face.loops:
			loop[color_layer] = color

	bm.to_mesh(obj.data)
```



Sources :
[[📺Animal Crossing, wobbly leaves, pivot caching]]

## West : Similar

## East : Opposite

## North : Theme / Question
[[How to create great materials in unreal engine]]

## South : What does it lead to

