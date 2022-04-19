---
title: Introduction to AI
---

In this lesson, we'll learn the basics about Artificial Intelligence (AI).

{{< table-of-contents >}}

## General Introduction

When people think of AI, most of them think of **Artificial General Intelligence** (AGI). An AGI can do everything what humans do (and even better). But the sad truth is, that mankind is not even close to develop a "real AGI".
Nowadays AI is very focused to a specific usecase, therefore one can speak of a **Artificial Narrow Intelligence** (ANI). Because you train it on a specific thing its capabilities are limited. If you try to use it for another task, it will not perform like you would expect it.
In this tutorial we will concentrate on ANI.

AI is separated in many subfields, in the following we will elaborate on some of them.

- Machine Learning (ML)
- Deep Leaning (DL)
- Computer Vision (CV)
- Natural Language Processing (NLP)

### Machine Leaning

Machine Learning is a subfield of AI. Machine learning is a process that uses an algorithm to analyze data, learn from the data and make a statement or prediction about it. Unlike software, which was programmed by hand and performed tasks by specific instructions, the machine is trained using large amounts of data and algorithms. This allows her to learn how to perform a task.

The algorithms had been evolved in recent years to include:
- decision trees
- induced logic programs
- clustering
- reinforcement learning
- Bayesian networks
- ...

But none reached the goal of "Artificial General Intelligence" and even “limited AI” was difficult to achieve with early machine learning approaches.

It turned out that one of the best areas of application for machine learning was the Computer Vision program. However, a lot of manual programming was required for the machine learning to work. Data Scientists wrote classifiers like Edge Detection Filters. The program could now figure out where objects began and where they ended, recognize the shape of an object, and recognize the letters STOP. From this, an algorithm was developed that recognized images and learned what a stop sign is. That's a good idea, but on days when it was very foggy, for example, or trees partially covered the sign, the algorithm was rarely able to identify the sign.

### Deep Learning

Artificial neural networks are inspired by the biology and workings of our brain. But unlike the brain, where neurons can connect to any neuron within a given physical distance, the neural network can only do so through separate layers, connections, and directions of data propagation.

For example, take a picture and cut it up into a bunch of pieces. These are recorded in the first level of the neural network. In this first level, individual neurons pass the data to the second level. In the second level, this process is repeated until a final result is produced.

Each neuron assigns a score to its input, whether this is correct or incorrect depends largely on the task to be performed. The final result is then determined by the overall ratings. Think back to the stop sign example. Properties of a stop sign image are sliced ​​up and checked by different neurons - the octagonal shape, the red color, the prominent letters, the size. The job of the neurons is to figure out if it's a stop sign or not. The neural network outputs a probability vector based on the scores. In the stop sign example, the system might conclude that it is 86 percent a stop sign, 7 percent a speedometer, five percent an object stuck in the tree and so on. The network architect then gives the system feedback on what is correct and what is not.

!!!!!!!!!!!!!!!!!!History part needds to be changed!!!!!!!!!!!!!!!!!Neural networks have been around since the early days of AI, the problem was that they were very computationally intensive and therefore practically impossible to implement. A small research group from the University of Toronto, led by Geoffrey Hinton, continues to work on the concept, but it wasn't until the development of the GPUs that they were able to prove it worked.

Take the stop sign example again. The system will often throw out the wrong answer at the beginning because it takes training. The system probably has to see hundreds of thousands or millions of images before the evaluation has matured enough that the result is always correct.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!Deep learning had its breakthrough with the computer scientist Andrew Ng. He enlarged the neural network, increasing levels and neurons, and then fed a large amount of data into the system to train it. So the “deep” in deep learning stands for the large number of levels. 

Nowadays, image recognition by trained machines is already better than humans in some scenarios. One area of ​​application is the identification of indicators for cancer in the blood or tumors on MRI images. Another, very prominent one, are Teslas self driving cars. Which is at the moment only available in the US as a beta tester, but will be available in the future in more and more countries.

### Computer Vision

This section introduces the basic techniques of image-based recognition. Under the computer-aided recognition of images, or Computer Vision, one understands various techniques to locate elements in images or identify and catalog videos. The goal is to use an automated process to gain a visual understanding while distinguishing between relevant and less distinguish relevant information. This is a complex process that otherwise reserved only for the human visual system, part of the nervous system.

Today it is common to train image recognition models, which take an image as a received input and output one or more objects and possibly more recognize attributes. The various objects possible to recognize are in classes assigned. Examples of these images must first be stored in so-called image databases collected. In addition to the class prediction these image recognition models also provide an assessment of the accuracy of the prediction meet. This value can be understood as a kind of probability of prediction and describes how confident the model is that an image becomes a learned class can be assigned.

In general, the recognition systems distinguish between single and multiple recognition. With a single detection, the model says only one class as Prediction for the entire image. Models designed for multiple detection were able to recognize several objects of different classes in one image.
Consequently, information on the localization of the object in the image and confidence needed.

In the [next lecture](../2.ArtificialVision/index.md), we will have a more in dept view, into the details of CV. 

### Natural Language Processing

Natural Language Processing examines how natural language in the form of text or language data can be processed algorithmically with the help of computers. It is the interface between linguistics and computer science. The goal of NLP is the capability of understanding the contents of documents and accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves.

The most common challenges in NLP are:
 - speech recognition
 - natural language understanding
 - natural language generation
