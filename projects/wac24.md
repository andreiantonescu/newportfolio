---
layout: post
slug: wac24
category: project
title: Web Audio Conference @ Purdue University
---

## Overview

In 2024 I attended the [Web Audio Conference @ Purdue University](https://cla.purdue.edu/academic/rueffschool/music/events/conferences-festivals/wac-24/program.html). My main contribution was doing a [workshop](#rnbo-and-p5js-workshop) about [RNBO](https://rnbo.cycling74.com/) and how to integrate it with both vanilla web audio as well as other frameworks. [Particle Music](/projects/musical-web#particle-music) was also presented as a concert screening and installation.

There were several other interesting ideas and experiments explored around networked performance and body gesture tracking.

- [Particle Music](#particle-music-concert-and-installation)
- [RNBO and p5.js Workshop](#rnbo-and-p5js-workshop)
- [Hand Theremin](#hand-theremin)
- [WebAudioXML x RNBO](#webaudioxml-x-rnbo)


## Particle Music, concert and installation

The [generative piece](/projects/musical-web#particle-music) was screened live at the Hansen Theatre @ Purdue University on March 17th. The installation ran throughout the conference in a dark acting classroom, part of the Yue-Kong Pao Hall of Visual and Performing Arts.

![Particle Music Installation](/assets/img/wac24-installation.png)
<div class="caption">Particle Music Installation</div>

![Concert Program](/assets/img/wac24-program.png)
<div class="caption">Concert Program the day Particle Music was screened</div>


## RNBO and p5.js Workshop
I held a workshop around RNBO and Max where I used p5.js for the graphical part. Since there was a mixed group, we started with the basics of each framework and gradually stepped towards the final project: a [Mouse Theremin](https://theremin.superblob.studio/) - to interact with the piece, start the sketch and move the mouse on the screen.

A large focus of the session was using multiple RNBO devices, especially existing plugins, which seemed to be valuable to people that were less familiar with Max. The final project featured a reverberation effect based on the [RNBO Guitar Pedals plugins](https://rnbo.cycling74.com/explore/rnbo-pedals).

![Mouse Theremin screenshot](/assets/img/wac24-theremin.png)
<div class="caption">Mouse Theremin screenshot</div>

We also touched on several examples related to:
- MIDI OUT and dependencies in RNBO, see [Piano Beat](https://piano-beat.superblob.studio/)
- using shaders in p5.js, see [Glitch Beat](https://glitch-beat.superblob.studio/)

For both of the above, start the sketches and press keys on your keyboard to play. Keys 1-8 play a drum kit, the other keys play a pitch shifted piano sample.

![Glitch Beat screenshot](/assets/img/wac24-glitch-beat.png)
<div class="caption">Glitch Beat screenshot</div>

The full code for the workshop is on [Github](https://github.com/andreiantonescu/purdue2024), and the presentation can be read [here](https://docs.google.com/presentation/d/1MZXBpMk2_GLnnaHBRL1urL16UY8f6It-P1WKelSIqlU/edit?usp=sharing).

## Hand Theremin
[Hans Lindetorp](https://github.com/hanslindetorp) held a workshop around [WebAudio XML](https://github.com/hanslindetorp/WebAudioXML) and [MediaPipe](https://developers.google.com/mediapipe), that inspired me to port the Mouse Theremin sketch described above to use hand gesture tracking. This resulted in [Hand Theremin](https://hands.superblob.studio/), which uses the webcam's hand position to control the sound.

![Hand Theremin screenshot](/assets/img/wac24-hands.png)
<div class="caption">Hand Theremin screenshot</div>

## WebAudioXML x RNBO
A sketch around how [WebAudio XML](https://github.com/hanslindetorp/WebAudioXML) and RBNO could be integrated. Made with [Hans Lindetorp](https://github.com/hanslindetorp), code is on [Github](https://github.com/andreiantonescu/WAXML_RNBO).