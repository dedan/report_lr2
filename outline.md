

outline of the report
=====================

Idee: 
Das Gehirn hat wohl nicht genug kapazität um alle einströmenden Informationen in gleicher Tiefe zu verarbeiten. Wir denken es dass Aufmerksamkeit dazu dient die im Gehirn verfügbaren resourcen möglichst effizient zu verteilen. Ein bekanntes Model zur Verteilung der Aufmerksamkeit ist das Salienzmodel von Itti und Koch. Neuere Forschungen (Walter) zeigen dass es nicht nur low-level salienz gibt, sondern schon sehr früh unsere Aufmerksamkeit auf Objekte gelenkt wird, sogenannte Protoobjekte. Wir haben uns also überlegt wie wir möglichst simpel (einfache Heuristik) eine suche nach protoobjekten implementieren können um dann nur in diesen vorselektierten Bereichen die rechnerisch Aufwändigen Analysen zur Objektsuche auszuführen.

Hierzu benutzen wir nun eine 3D Kamera. Das Tiefenbild dient uns als einfache Heuristik mit der Annahme dass Objekte von starken "Tiefengradienten" eingefasst sind.

first parallel stage, later serial processing

look what I wrote for my A&C summaries

spotlight


free viewing macht salienz sinn, sonst ist aufmerksamkeit wohl eher task abhaengig.


Summaries
=========

* Walther und Koch: 
    * Benutzen ein Bottom up modell


Ausblick, weitere Ideen
=======================

* walther und koch benutzen den bekannten saliency map ansatz um die fläche von protoobjekten zu finden. Das könnte man bestimmt schön kombinieren. Wir könnten ja z.B. unseren Tiefengradienten als eine der Saliency maps nehmen. Vielleicht sogar noch mit hohem gewicht, weil es so ein guter ansatz ist. Dann über andere maps aber z.b. auch farb homogenität und ähnliches mit einfließen lassen.
* schauen was da noch alles in der todo liste steht


Struktur
========

Introduction
------------

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

* Different kinds of attention
    * low-level, mid-level or high-level features
    * different models of attention? (saliency, protoobjects)

* If protoobjects -> how can objects guide attention before we processed that they are objects?

Implementation
--------------

* some facts on kinect camera (there was an ct article about it)
* which frameworks do I us for programming (opencv, numpy, libsiftfast, flann)
* histogram clustering 
    * cite paper (the bad one)
    * simple example for the clustering
* morphological operators in one cluster (certain range of depth)
* extract contours and filter by very basic criteria, e.g. area
* track object
    1. my early solution, compute overlay of shapes
    2. current solution, compute only overlay of bounding boxes
* after stable tracking of object for N frames --> compute sift features
* sift features are only computed in area of proto-object
    * faster computation
    * object can be masked with contour ==> less false-positives


Summary and Outlook
-------------------

* sift computation much faster
* tracking of proto-objects based on very simple heuristics is possible
* Ideas for improvement
    * improve the SIFT-feature computation queue (more detailed in todo.md)
    * multiprocess instead of multithread
    * maybe average over frames
    * try using the high-resolution images of the Kinect
    * use color-histogram of objects for rough mapping





