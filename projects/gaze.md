---
layout: post
category: project
title: RGB Webcam gaze tracker
---

This was my Master's dissertation thesis, where I looked at how we can determine gaze based only on webcam RGB data. I used various heuristics such as:
- determining the outer edges of the eyes
- determining the eye center by means of gradients

**Tech Stack**
- C++
- OpenCV (Computer Vision library)
- OpenFrameworks (as a general C++ wrapper and helper)
- Intel TBB (for parallel processing)
- Awesomium (for embedding the web browser used for usability testing)

**Outcomes**
- the tool successfully tracked the gaze of participants on desktop computers, after a short calibration period
- it had sufficient accuracy for use in low resolution web usability tracking

![Accuracy Tests](/assets/img/gaze-heatmap.jpeg)
<div class="caption">Example website gaze heatmap. Website sections were divided based on a low resolution grid, that could accommodate the tracking accuracy of the system</div>

![Accuracy Tests](/assets/img/gaze-accuracy-1.png)
<div class="caption">Accuracy tests on middle-bottom section of screen</div>

![Accuracy Tests](/assets/img/gaze-accuracy-2.png)
<div class="caption">Accuracy tests on left-bottom section of screen</div>
