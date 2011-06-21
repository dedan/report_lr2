

Attention
=========

What is attention?
------------------

> Everyone knows what attention is. It is the taking possession of the mind, in clear and vivid form, of one out of what seem several simultaneous possible objects or trains of thought. Focalization, concentration of consciousness are of its essence. It implies withdrawal from some things in order to deal effectively with others, and is a condition which has a real opposite in the confused, dazed, scatterbrain state… – William James (1890)

Why attention?
--------------

* We don't have the capacity to process all stimuli to the same extent
* Historically (Broadbent's filter theory - 1958) it is thought that attention serves as early selection.

Different kinds of attention
----------------------------

* bottom-up
    * stimulus dependent
    * low-level features (color, contrast, motion, etc..)
    * saliency as a model
* top-down factors
    * task-dependent
    * high-level features (specific objects / object features, scene structure, etc..)
    * mid-level features (surfaces, boundaries, occlusions, continuation etc..)
        * could serve as an important link
        * might serve as proto-objects
<!--
    TODO maybe show gestalt table here
-->
    * relations between objects or elements in a scene
    * *gist*: meaning of a scene

High-level attention
--------------------

more information on proto-objects
summary of johannes talk


The Idea
========

Use high-level attention in computer vision


Implementation
==============

Kinect Facts
------------

<!--
    TODO bild der kinect einfuegen
-->

* 8 bit RGB-Camera with resolution up to 1280x1024 @ 15 Hz or 640x480 @ 30 Hz
* 11 bit Depth-Camera with resolution of 640x480
* Depth sensor range: 0.8m - 3.5m (resolution decreases with distance)
* the manufacturer provides a SDK


Frameworks I use
----------------

* I decided to develop the application in python because the application logic can be developed much faster then in C/C++ and it is hardly slower because I use wrappers to compiled code for all expensive stuff
* opencv
* numpy
* libsiftfast
* flann


Algorithm and Results
---------------------

* histogram clustering (numpy)
* morphological operators (opencv)
* extract contours (opencv)
* basic filtering of contours (e.g. omit very small)
* object tracking (overlay of bounding boxes - opencv)
* create patch of stable object and mask the object by contour
* compute sift features on masked stable objects (libsiftfast)


Summary and Outlook
===================

* sift computation much faster
* tracking of proto-objects based on very simple heuristics is possible

Ideas for Improvement
---------------------

* improve the SIFT-feature computation queue (more detailed in todo.md)
* multiprocess instead of multithread
* maybe average over frames
* try using the high-resolution images of the Kinect
* use color-histogram of objects for rough mapping