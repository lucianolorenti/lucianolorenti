.. title: YOLO
.. slug: yolo
.. date: 2022-04-11 20:47:23 UTC+02:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. has_math: true


.. contents:: Table of Contents

The year was 2015. We were the adventeures of Michael, Trevor y Franklin,  Adele was releasing 25 and movie reference. 
A group of researchers thought about a way to segemnt .

This is a supervised problem


Datasets
========





VOC2007
-------


Introduction
............

The PASCAL Visual Object Classes Challenge 2007. The goal of this challenge is to recognize objects from a number of visual object classes in realistic scenes (i.e. not pre-segmented objects). It is fundamentally a supervised learning learning problem in that a training set of labelled images is provided. The twenty object classes that have been selected are:

Person: person
Animal: bird, cat, cow, dog, horse, sheep
Vehicle: aeroplane, bicycle, boat, bus, car, motorbike, train
Indoor: bottle, chair, dining table, potted plant, sofa, tv/monitor

One of the objectives of the challenges was to  Predicting the bounding box and label of each part of a person (head, hands, feet)

The training data provided consists of a set of images; each image has an annotation file giving a bounding box and object class label for each object in one of the twenty classes present in the image. Note that multiple objects from multiple classes may be present in the same image.



YOLO V1
=======

The first version of YOLO combined convolutional layers and a fully connected layers with some dropout in the middle.

Pretraining
-----------

Loss
----
YOLO predicts multiple bounding boxes per grid cell. At training time we only want one bounding box predictor to be responsible for each object. We assign one predictor
to be “responsible” for predicting an object based on which prediction has the highest current IOU with the ground truth. This leads to specialization between the bounding box
predictors. Each predictor gets better at predicting certain sizes, aspect ratios, or classes of object, improving overall recall.
IOU.

Note that the loss function only penalizes classification error if an object is present in that grid cell (hence the conditional class probability discussed earlier). It also only penalizes bounding box coordinate error if that predictor is
“responsible” for the ground truth box (i.e. has the highest IOU of any predictor in that grid cell).



.. math::

   \lambda_{ord} \sum\limits_{i=0}^{S^2} \sum\limits_{j=0}^{B}  1_{ij}^{obj} \left[  (x_i - \hat{x}_i )^ 2 + (y_i - \hat{y}_i )^ 2  \right]
   + \lambda_{ord} \sum\limits_{i=0}^{S^2} \sum\limits_{j=0}^{B} 1_{ij}^{obj}



YOLO V2
=======

Anchors
-------


YOLO V3
=======
