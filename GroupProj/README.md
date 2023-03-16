# Group Project Documentation: Ken Kobayashi

pass: beantown

The structure of the performance was to separate each member to a specific kind of sound, like instruments in a band.
I was in charge of the hydra performance.

We had two sections in our structure: a rhythmic section based on printer sounds, and a creepy, ambient section. Dante was tasked with moving the sections along.

We did a estuary session together the day before to make this all clear.

Mostly all of my code that I used for the performance is taken from the code snippets below. They are all code that I either made while coding as a group or code that I stole from the sandbox during group sessions.

I found the limitations of Estuary were restrictive, but consistent. Feedback didn't work, any math was out of the window, and expressions were not available.

Replacing feedback wasn't bad, as blending two sources together was enough. Replacing math, such as sine waves weren't bad either, as I found arrays with smoothing was much more powerful.

The printer section sounded very glitchy and syncopated, so I used more particle like, glitchy visuals. The code can be found below, maked "Syncopated glitchyness".

The ambient section sounded like a haunted house level in a mario game. I wanted a creepy vibe. I start with "orange pixelation modulation" with "fade in fade out snippet", slowly evolving into "orange pixelation with more stuff". This includes changing pixelation, fading to black and back, stuttering brightness, stuttery movement, and so on. Everything was made to be creepy and stuttery.

At the end, I was tasked to make the visuals go crazy while the music faded out. For this I cranked the saturation and brightness, and made the fade to black less black.

I made sure to keep my code documented to an extent, and made sure I understood each snippet enough to improvise adjustments, as its no fun just copy pasting the same thing over and over.



## CODE

### Modulating purple and black keleid
```
voronoi(10, 0.1)
.color(0.3,0.0,0.5)
.rotate(90,0.15)
.modulate(noise(0.3),1)
.kaleid(8)
.luma(0.1,1)
.out(o1);

render(o1)
```


### Red Swiping with blue bubbles
```
gradient([5,6,10]).scrollX(0.4,1).color(0.4,0.1,0)
.blend(voronoi(5,0.1).posterize(5).color(0,0.2,0.5))
.out(o1);

render(o1)
```

### Blue and Green Circle Particles

```
osc(10,-0.25,1).color(0,0.3,1).saturate(2).kaleid(50)
  .mask(noise(25,2).modulateScale(noise(0.25,0.05)))
  .modulateScale(osc(6,-0.5,2).kaleid(50))
  .mult(osc(3,-0.25,2).kaleid(50))
  .scale(0.5,0.5,0.75)
  .out(o1);

render(o1)
```

### Orange pixelation modulation

```
osc(6, 0, 0.8)
  .color(0.7, 0.4,.20)
  .rotate(0.92, 0.3)
  .pixelate([20, 50, 7, 5, 7, 8, 10, 20, 50].fast(10), 10)
  .mult(osc(40, 0.03).thresh(0.4).rotate(0, -0.02))
  .out(o1);

render(o1)
```

### orange pixelation with more stuff

```
osc(6, 0, 0.8)
  .color([0.2,0.7].smooth().fast(0.5), [0.4,0.9,0.2].smooth().fast(2.5),[.90,0.1,0.4].smooth())
  .rotate(2, 0.15)
  .pixelate([20, 50, 7, 5, 7, 8, 10, 20, 50].fast(10), 10)
  .mult(osc(40, [0.05,0.2]).thresh(0.4).rotate(0, -0.02))

.mask(
solid(0,0,0)
.invert([0,1].smooth())
//causes stutter
.posterize([1,5,20,30,300].smooth(),0.5)
.contrast([1,1.7,1,1.5,1].smooth())
.luma([0, 0.1, 0.05, -0.1].smooth().fast(1.5)
)
)
//tiling
//.modulateRepeat(osc(10),[0].smooth(),[0].smooth().fast(0.8),0.2,0.2)
.scrollX(0.7,0.2)

//transition out effects
.saturate([1].smooth().fast(10))
.brightness(0)
.out(o1);
```

### Color Disk changin every downbeat

```
noise(18)
  .colorama([0.8,9,0.22,0.5])
  .posterize(2)
  .kaleid([50, 80, 30])
  .mask(
    shape(25, 0.25).modulateScale(
      noise(400.5, 0.5)
    )
  )
  .mask(shape(400, 1, 2.125))
  .modulateScale(osc(6, 0.125, 0.05).kaleid(50))
  .mult(osc(20, 0.05, 2.4).kaleid(50), 0.25)
  .scale(1.75, 0.65, 0.5)
  .modulate(noise(0.5))
  .saturate(3)
  .posterize(4, 0.2)
  .scale([1.5,0.9,0.5,1.2])
  .out(o1);

render(o1)
```

### Noisy sparkles with pixelated rainbow

```
gradient(1.5).mask(voronoi(),3,0.5).invert([0]).color(0.3,0.5,0.3).pixelate(300,20).modulatePixelate(noise(200,0.5),100).hue(-0.1).out(o1);

render(o1)
```


### Syncopated glitchyness

```
noise(20,1)
.thresh(0.95,0.1)
.blend(
noise(20,2)
.thresh([0.9,0.7].fast(0.95),0.1)
.colorama([0.2,0.05,0.3,0.15].fast(0.95))
.saturate(10),
0.3
)
.out(o1);
```


### Fade in and out mask snippet

.mask(
solid(0,0,0)
.invert([0,1].smooth())
)

### Deafult version on glitchyness, white particles overlayed with blue pixels

```
noise(20,1)
.thresh(0.95,0.1)
.blend(
noise(20,2)
.thresh([0.9,0.9].fast(1),0.1)
.pixelate([20,20],[20,20])
.color(0.1,0.2,0.5)
.colorama(0)
.saturate(10)
.scrollX(5,0),
0.1
)
.out(o1);
```


### Ambient section

```
osc(6, 0, 0.8)
  .color([0.2,0.7].smooth().fast(0.5), [0.4,0.9,0.2].smooth().fast(2.5),[.90,0.1,0.4].smooth())
  .rotate(2, 0.15)
  .pixelate([20, 50, 7, 5, 7, 8, 10, 20, 50].fast(10), 10)
  .mult(osc(40, [0.05,0.2]).thresh(0.4).rotate(0, -0.02))

.mask(
solid(0,0,0)
.invert([0,1].smooth())
//causes stutter
.posterize([1,5,20,30,300].smooth(),0.5)
.contrast([1,1.7,1,1.5,1].smooth())
.luma([0, 0.1, 0.05, -0.1].smooth().fast(1.5)
)
//tiling
)
//.modulateRepeat(osc(10),[0].smooth(),[0].smooth().fast(0.8),0.2,0.2)
.scrollX(0.7,0.2)

//transition out effects
.saturate([1].smooth().fast(10))
.brightness(-0.1)
.out(o1);
```