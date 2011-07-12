

Abstract
========

* we don't have enough capacity to process all incoming stimuli
* it is thought that attention serves to allocate resources for processing
* attention works as a selection mechanism
* for a long time it was thought that attention is directed by low-level features of the stimulus
* recent research showed that attention might be object-based
* the question is how can we attend to objects before they are recognized?
* Some mid-level features might be used to compute proto-objects
* We want to try to implement a very simple heuristics to compute proto-objects to improve object detection in computer vision.
* to achieve this use the depth information from a 3D Camera
* simple histogram clustering in the depth image
* detection of proto-objects in *interesting* layers of the depth image
* expensive sift feature computation only done on this proto-objects

Introduction
============

* Why attention
    * It is thought that the brain does not have enough capacity, respectively it is not economical to process all incoming information in parallel in depth. The theory says that we have attention as an early selection mechanism
    * quote from koenig lecture
    > Everyone knows what attention is. It is the taking possession of the mind, in clear and vivid form, of one out of what seem several simultaneous possible objects or trains of thought. Focalization, concentration of consciousness are of its essence. It implies withdrawal from some things in order to deal effectively with others, and is a condition which has a real opposite in the confused, dazed, scatterbrain state...  – William James (1890)
    
    * we focus here on visual attention, but of course it involves all sensory modalities
    * Early selection, Broadbent's filter theory
        * 2 stage processing
        * selection is based on physical properties
        * focus (selection of one input channel)
        * semantic interpretation after selection
        * conscious control and that it takes time to shift attention
    * Treismans attenuation

* Different kinds of attention
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
    
Models
------

* Saliency
    * might make sense in free-viewing, but not in task-dependent viewing


* If protoobjects -> how can objects guide attention before we processed that they are objects?

The idea is to use high-level (mid-level) attention in computer vision

Implementation
==============

* some facts on kinect camera (there was an ct article about it)
    * 8 bit RGB-Camera with resolution up to 1280x1024 @ 15 Hz or 640x480 @ 30 Hz
    * 11 bit Depth-Camera with resolution of 640x480
    * Depth sensor range: 0.8m - 3.5m (resolution decreases with distance)
    * the manufacturer provides a SDK

* which frameworks do I us for programming (opencv, numpy, libsiftfast, flann)
* histogram clustering 
    * cite paper (the bad one)
    * simple example for the clustering
* morphological operators in one cluster (certain range of depth)
* extract contours and filter by very basic criteria, e.g. area
* track object
    1. my early solution, compute overlay of shapes
    2. current solution, compute only overlay of bounding boxes
* create patch of stable object and mask the object by contour
* after stable tracking of object for N frames --> compute sift features
* sift features are only computed in area of proto-object
    * faster computation
    * object can be masked with contour ==> less false-positives


Results and Outlook
===================

* sift computation much faster
* tracking of proto-objects based on very simple heuristics is possible
* Ideas for improvement
    * use more advanced object tracking (e.g. Kalman filter )
    * improve the SIFT-feature computation queue (more detailed in todo.md)
    * multiprocess instead of multithread
    * maybe average over frames
    * try using the high-resolution images of the Kinect
    * use color-histogram of objects for rough mapping
    * use neighborhood relation in iterative histogram clustering (mention the problem of objects that spread out over several layers)





Summaries
=========

* Walther und Koch: 
    * Benutzen ein Bottom up modell
    * eigentlich benutzen die doch nur das alte salienzmodel und breiten dann die flaeche in der naehe der salientesten stelle noch ein bischen aus
    <!--
        TODO schauen ob das stimmt
    -->


