---
type: literature
status: checked 
topic: shaders
---
Topic : #shaders 
Tags : #animation #glsl


Source :  [An introduction to Shader Art Coding - YouTube](https://www.youtube.com/watch?v=f4s1h2YETNY)

# Ideas

## Center UV space in center of image
UV (0->1) => `(UV - 0.5) * 2` => UV (-1->1)

## Some useful function
- length(uv) => distance from center 
- step(threshold, x) => 0 if x before threshold 1 after
- smoothstep(threshold1, threshold2, x) => 0 if x <= t1 , lerp [0,1] if t1 < x < t2 , 1 if x >= t2  

## Color palette
[[Shader Color Palette - Procedural gradiant]]

## gsls function visualisation
[Graphtoy](https://graphtoy.com)


Linked Sources :