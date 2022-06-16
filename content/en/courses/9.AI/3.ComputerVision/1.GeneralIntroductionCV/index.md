---
title: General Introduction Computer Vision
---

In this lesson, we'll learn the basics about Computer Vision (CV).


# Computer Vision

## Introduction

This section introduces the basic techniques of image-based recognition. Under the computer-aided recognition of images, or Computer Vision, one understands various techniques to locate elements in images or identify and catalog videos. The goal is to use an automated process to gain a visual understanding while distinguishing between relevant and less distinguish relevant information. This is a complex process that otherwise reserved only for the human visual system, part of the nervous system.

Today it is common to train image recognition models, which take an image as a received input and output one or more objects and possibly more recognize attributes. The various objects possible to recognize are in classes assigned. Examples of these images must first be stored in so-called image databases collected. In addition to the class prediction these image recognition models also provide an assessment of the accuracy of the prediction meet. This value can be understood as a kind of probability of prediction and describes how confident the model is that an image becomes a learned class can be assigned.

In general, the recognition systems distinguish between single and multiple recognition. With a single detection, the model says only one class as Prediction for the entire image. Models designed for multiple detection were able to recognize several objects of different classes in one image.
Consequently, information on the localization of the object in the image and confidence needed.

## Historical Facts

This section is intended to describe the historical development of the methods of image-based recognition. For more than 60 years scientists have been dealing with the subject of using machines to extract the visual meaning of data.

Rosenblatt introduced the perceptron in 1958, it is a simplified artificial one neural network (ANN) and in this context the first representative [Ros58]. The developed "Mark I Perceptron" Machine could already recognize simple digits with an array of 400 photocells. 

Now an example should be mentioned, which has nothing to do with software development. However, this can be seen as an inspiration for the research field and later published work. 
The neurophysiologists David Hubel and Torsten Wiesel [HW59] examined the sensitivity of simpler and more complex ones Neurons in the striped cortex of cats. This was from the point of view of Stimulus orientation or orientation selectivity quantitatively studied. 

![Sensitivity of simpler and more complex ones Neurons.](hubel_cat.jpg)
<p style="text-align: center;">Sensitivity of simpler and more complex ones Neurons [HW59].</p>

The researchers found that there are simple and complex neurons in the primary visual cortex and that visual processing always begins with simple structures such as oriented edges. This means that in the process of image processing initially not holistic objects are recognized, but simple geometries are processed first. The neural networks used today learn the features in the same order.

In 1960, Henry J. Kelley published an important paper that attempted to calculate optimal flight paths of airplanes based on gradients. The findings are used as the basis for backpropagation.

In 1960, the ADALINE model [Som] was presented by Bernard Widrow and ME Hoff, it represents an artificial neural network. This is the first to be commercialized applied, here a real-time echo filtering was carried out with analogue telephones.

In 1963 Lawrence Roberts published "Machine perception of three-dimensional solids" [Rob63]. The aim of this doctoral thesis was to convert 2D photographs to line drawings process, which are then processed into three-dimensional representations will. The real world was reduced to simple geometric figures.

The first working deep learning networks were created by Alexey Ivakhnenko and V.G. Lapa presented. In 1971 they published the first computer-aided identification system called "Alpha".

Another influential contribution was made in 1982 by David Marr, a British Neuroscientist, provided [Mar82]. He proved that seeing in the broadest sense is a hierarchical process. He developed a prototype with which it is possible to  create three-dimensional representations of the environment in order to use them later
to interact. He also developed a CV framework, where algorithms were used are offered, which recognize simple features, i.e. corners and edges. This rudimentary understanding of the scene provided the basis for later work and paved the way for gaining a higher understanding of the scene.

At the same time, the Japanese computer scientist Kunihiko Fukushima developed his own organizing artificial neural network. The network includes simple and complex cells. With the help of the network called "Neocognition".
Patterns are recognized, it consisted of several layers of folding.
A few years later, French scientist Yann LeCun published his changes or additions to Fukushima's convolution layer architecture. He refined the principle of error feedback (backprop-learn). 
After a few years of work in the field, he published "LeNet-5". This may be the first modern convolutional neural network (CNN) be considered. LeNet-5 has been used on a large scale to automate handwritten digits on personal and commercial bank checks in the United States recognize [LBB+98]. A lower threshold of the recognition quality of the bank fixed. *50%* of bank checks must be scanned with an error rate of *1%*, the rest can be rejected by the system and becomes a human recognition assigned editor. This work also advanced the development of the MNIST image database, which is one of the essential image databases.

Just before the year 2000, the focus shifted to image-based recognition. Many researchers stopped reconstructing 3D models and thus no longer followed path suggested by Marr. It now became more feature-oriented Object recognition focused.

An image based recognition is used in many areas today, such as autonomous driving on the road, face recognition in public places, facilities for determining plant species, tagging photos and videos or also in the healthcare system for evaluating visual data. Despite the impressive recent advances, we are not close to a rather all-encompassing
solution not yet close.




## Sources

[Ros58] Rosenblatt, F.: The Perceptron: A Probabilistic Model for Information Storage and Organization in The Brain. In: Psychological Review (1958), page 65–386

[HW59] Hubel, David H. ; Wiesel, Torsten N.: Receptive Fields of Single Neurons in the Cat’s Striate Cortex. In: Journal of Physiology 148 (1959), page 574–591

[Som] Sommer, Gerald: Neuroinformatik. https://www.informatik.uni-kiel.de/inf/Sommer/doc/Downloads/Skripte/neuroskript.pdf

[Rob63] Roberts, Lawrence: Machine Perception of Three-Dimensional Solids. 1963. – ISBN 0–8240–4427–4

[Mar82] Marr, David: Vision: A Computational Investigation into the Human Representation and Processing of Visual Information. USA : Henry Holt and Co., Inc., 1982. – ISBN 0716715678

[LBB+98] LeCun, Yann ; Bottou, Leon ; Bengio, Yoshua ; Haffner, Patrick u. a.: Gradient-based learning applied to document recognition. In: Proceedings of the IEEE 86 (1998), Nr. 11, page 2278–2324

