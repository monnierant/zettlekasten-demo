---
type: tool
topic: shaders
---
Topic : #shaders 
Tags : #procedural #palette #glsl 

# Idea

Code to create a palette base on 4 parameters
```gsls
vec3 palette( in float t, in vec3 a, in vec3 b, in vec3 c, in vec3 d )
{
	return a + b*cos( 6.28318*(c*t+d) );
}
```

use [dev.thi.ng/gradients/](http://dev.thi.ng/gradients/) to find 4 the 4 colors to use as parameters

Some examples can be found in  [Inigo Quilez :: computer graphics, mathematics, shaders, fractals, demoscene and more](https://iquilezles.org/articles/palettes)


Sources :
- [Inigo Quilez :: computer graphics, mathematics, shaders, fractals, demoscene and more](https://iquilezles.org/articles/palettes)
- [dev.thi.ng/gradients/](http://dev.thi.ng/gradients/)

## West : Similar

## East : Opposite

## North : Theme / Question
[[📺An introduction to Shader Art Coding]]

## South : What does it lead to

