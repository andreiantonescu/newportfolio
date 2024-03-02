---
layout: post
category: project
title: Tangled - Generative Art project
---
![Tangled – outputs from the Rinkeby test network](/assets/img/tangled-header.png)
<div class="caption">Tangled – outputs from the Rinkeby test network</div>

## Overview
- [Transaction Hashes](#transaction-hashes)
- [Knots](#knots)
- [Working with Color](#working-with-color)
- [Blobs](#blobs)
- [Hurdles](#hurdles)
- [Outro](#outro)

<br>
This is a story of how my first generative art project on the blockchain was born – Tangled, launched on September 17 2021, at 11 am CT on [Art Blocks](https://www.artblocks.io/collections/presents/projects/0xa7d8d9ef8d8ce8992df33d8b8cf4aebabd5bd270/132).

It has not been a straightforward project and there were many pivots along the way – I could say, pun intended, that the road to the final version of the project was quite tangled 🙂.


## Transaction Hashes
Tangled evolved from an exploration of the transaction’s hash. Besides using it as an input for a pseudo-random number generator, I wanted to use parts of the hash as literally as possible.

```0xdc57d9ad96a09f2cac30eba70af2dea145039ed7a293837048dc5723ab8bfbf9```
<div class="caption">A transaction hash</div>

The first idea that came to mind was to transpose pairs of the hash into enlarged ‘pixels’ on the screen. I used the first 25 bytes of the hash to create a 5 by 5 grid, with each byte determining the brightness of the monochrome pixels.

![Example outputs for mapping the first 25 bytes of the hash into a 5×5 grid](/assets/img/tangled-chess-examples.png)
<div class="caption">Example outputs for mapping the first 25 bytes of the hash into a 5×5 grid</div>

It looked like some sort of alien chessboard, but it reminded me of another project I’ve been working on for some time, [Pixel Music](https://pixelmusic.app/) – a sequencer based on image data – that creates a similar-looking grid based on an input image and plays notes determined by the properties of each pixel.

I hooked up ToneJS and quickly began experimenting in this area. I mapped each pixels’ brightness value to a hearable MIDI note and played it on a fixed frequency. Pretty rough, but getting some techno/old-school arcade game vibes here.

<div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/918650320?badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="Early Tangled Experiment"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
<div class="caption">Rough hash sequencer</div> 

## Knots
I planned to use the rest of the 7 bytes for controlling aspects of the composition and tonality, but the background chessboard was slowly fading in my preferences. Although similar to [Pixel Music](https://pixelmusic.app/), there we have a direct relationship between the image you load and the grid it creates.

In the current case, it seemed much more artificial, so I started exploring other ways of visualizing that data coupled with the sound. I thought about mapping the bytes of the hash to points on the screen, and here is where we start to see the first relationships to Tangled.

<div style="padding:100.26% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/918653798?badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="Early Tangled design"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
<div class="caption">Drawing sound through bezier curves</div>

This stage took a while. There were lots of elements I could experiment with: colors, the position of points, the shape of curves, synths, sound effects, scales, etc. Even though the outputs kept me engaged, I ultimately started feeling like I was going in circles.

Whenever I find myself in such a place, I remember that constraints help in the creative process, so I decided to start cutting off elements, starting with the sound. Although music and sound design are passions of mine, they introduced too many variables that I could play with here. Looking back, I think it was a healthy decision.

Another area where I restrained myself was around the number of lines drawn on the screen. This looked off initially but helped me have the idea of connecting the lines to each other, to give more coherence. A debug view from that period looked something like this:

![Debug view showing the individual curves and their anchor and control points](/assets/img/tangled-debug.png)
<div class="caption">Debug view showing the individual curves and their anchor and control points</div>

The first concept of Tangled was posted online in March 2021 (they were named ‘Crypto Knots’ then), and looked something like this:

![First ‘Crypto Knots’ I posted on Instagram in March 2021](/assets/img/tangled-first-knots.png)
<div class="caption">First ‘Crypto Knots’ I posted on Instagram in March 2021</div>

## Working with Color
I started working more seriously on color next, which was a way bigger topic than I originally anticipated. For the outputs above, I simply had an array of 10-11 colors from which I selected 2 when building the output.

As you can imagine, not all combinations looked nice. I switched to building standalone palettes from which to choose, but since I was drawing only two elements on the screen, I had to be extra careful to make sure each possible combination had enough contrast and ‘spark’ to it.

I built out combination tables to test all the possible variants. One iteration of this (although not the final version) is shown below. This was a very strenuous process of sampling the colors and testing each iteration individually.

![Combination table of initial color schemes](/assets/img/tangled-colortable.png)
<div class="caption">Combination table of initial color schemes</div>

Around this point, I was onboarded by the Art Blocks team to Rinkeby (Ethereum test network), and the first test mints were created.

![First test mints from the Rinkeby test network](/assets/img/tangled-testmints.jpg)
<div class="caption">First test mints from the Rinkeby test network</div>

I loved the color schemes I created and, while I liked the test outputs, I felt I was not using the color schemes to their full potential. One reason for this was that I was using only 2 elements on the screen, so essentially roughly 80% of the colors remained unused.

## Blobs
This is where the blobs on the background start fitting in. I wanted to introduce another element to ‘ground’ the strings and to introduce more color variation, while also keeping the original idea of using hash data as literally as possible.

To have some connection with the strings, I decided to use the anchor points of the bezier curves to draw a geometry behind them. I chose the anchor points in order to have a resemblance to the strings, but not be 1:1 with them, since they were further deformed by the control points.

More technically, the blobs are constructed based on the convex hull of the anchor points used to draw the strings. I used this approach to get a full, nice-looking shape.

At this point, I started to reintroduce some variation regarding the number of strings drawn on the screen.

![First iterations with blobs and with varying number of strings drawn](/assets/img/tangled-blobs.jpg)
<div class="caption">First iterations with blobs and with varying number of strings drawn</div>

After all this, I finally reached a stage where I thought the project was well shaped, had enough variation for the number of editions I was aiming at, and the remaining work that ensued was mostly around refinements.

I reintroduced a subtle animation to better take advantage of the medium and to have the blobs and strings look more ‘alive’. I liked the impression this gives that they are constantly trying to untangle, only to fail and start over again.

<div style="padding:100% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/918657074?badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="Tangled early animation"></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

## Hurdles
At this point, I was happy with the outputs. Things seemed to converge in the right direction and I had the launch scheduled with the Art Blocks team. 

Then, some speculation arose regarding the similarity of Tangled with the first project of EthBlockArt. Of course, I did not find the projects similar and dismissed the claims.

However, since EthBlockArt allowed the collector to manipulate the end result, some of the actual minted pieces for that project did indeed seem similar to Tangled, as opposed to the standard output that system gave – a thing I discovered following this discussion.

While I still viewed the two projects conceptually and stylistically as being very different, I decided to postpone the project and iterate more on a differentiation point. 

After several iterations that didn’t quite hit the spot, I converged on drawing multiple lines alongside the initial paths carved by the previous version of the project. This felt like the right decision immediately.

![New iteration with multiple lines drawn alongside initial paths](/assets/img/tangled-new.jpeg)
<div class="caption">New iteration with multiple lines drawn alongside initial paths</div>

In this way, I felt I could put the color palettes even more into play. Several weeks followed on improving this version and the sense of tangledness of the whole piece. The animation was altered to give the perception of a restless yarn ball that endlessly tries to untangle.

Going to smaller line dimensions also meant more problems. In short, if you are working on a project that involves drawing in the browser, avoid subpixel lines. Browsers handle this differently and lead to all sorts of errors. I ended up drawing all lines at least 1px, and for the cases where I had to go thinner, I achieved a similar effect by lowering the opacity (thanks nonfigurativ for the tip). 

## Outro
This was a long write-up – thanks for hanging in this far. There were a lot of roadblocks along the way, but ultimately I think that these only made the project evolve and get to a better state.

Going from a glitchy music-playing chessboard to the outputs above, I hope it inspires artists starting out in this area to keep iterating and pushing forward. The creative process is nourished by constraints and project ideas can come from unexpected places.

Finally, to support this space, 25% of all proceeds have been donated to the Art Blocks Foundation for Generative Art. Happy to be a part of this!

I'll leave you with some screenshot details of the project:

![Tangled Details](/assets/img/tangled-final-1.png)
<br>
![Tangled Details](/assets/img/tangled-final-2.png)
<br>
![Tangled Details](/assets/img/tangled-final-3.png)
<br>
![Tangled Details](/assets/img/tangled-final-4.png)
<br>
![Tangled Details](/assets/img/tangled-final-5.png)