---
id: ai_fundamentals_course
title: Fundamentals of AI
difficulty: intermediate
duration: 5h
---

Introduction
============

When people think of AI, most of them think of **Artificial General Intelligence** (AGI).
An AGI can do everything what humans do (and even better).
But the sad truth is, that mankind is not even close to develop a "real AGI".
Nowadays AI is very focused on some specific use cases, therefore one can speak of an **Artificial Narrow Intelligence** (ANI).
Because you train it on a specific thing its capabilities are limited. If you try to use it for another task, it will not perform like you would expect it.
AI is separated in many subfields, in this lesson we will elaborate on some of them:

- Machine Learning (ML)
- Deep Leaning (DL)
- Computer Vision (CV)
- Natural Language Processing (NLP)

How the fields overlap and are interlinked is conveyed in the following visualization.

<figure
  src="img/ai_ml_dl.png"
  caption="How the AI disciplines are connected and interlinked to each other. [Con21]">
</figure>

Artificial Intelligence is the most general scientific field.
One subfield of Artificial Intelligence is Machine Learning.
It describes algorithms with an ability to learn a task, without being explicitly programmed to do so.
A subfield of Machine Learning is Deep Learning. Most areas of Computer Vision and Natural Language Processing nowadays are part of Deep Learning.
With Deep Learning with help of e.g. convolutional neural networks it is possible to learn and process great amounts of data.


Machine Learning
================

Machine Learning is a subfield of AI.
Machine learning is a process that uses an algorithm to analyze data, learn from the data and make a statement or prediction about it.
Unlike software, which was programmed by hand and performed tasks by specific instructions, the machine can be trained using large amounts of data and algorithms.
This allows it to learn how to perform a task.

Applications
------------

It turned out that one of the best areas of application for machine learning was the Computer Vision program.
However, a lot of manual programming was required for the machine learning to work.
Data Scientists wrote classifiers like Edge Detection Filters.
The program could now figure out where objects began and where they ended, recognize the shape of an object, and recognize the letters STOP.
From this, an algorithm was developed that recognized images and learned what a stop sign is.
That's a good idea, but on days when it was very foggy, for example, or trees partially covered the sign, the algorithm was rarely able to identify the sign.

There are also other important areas where machine leaning is applied. For example, Natural Language Processing where machine learning is being used to recognize spoken words and convert it to text.

Another application of machine learning are product recommendations. Big companies like Google, Amazon or Netflix use it to propose products to users.

Email Spam and Malware Filtering is also utilizing Machine Learning. Gmail is using the following filters: Content Filter, Header filter, General blacklists filter, Rules-based filters and Permission filters. Some machine learning algorithms such as Multi-Layer Perceptron, Decision tree, and Naïve Bayes classifier are used for email spam filtering and malware detection.

Stock market trading is another area where machine learning is used to predict 

These are just some examples of areas where machine learning is being used, there are many other fields where it is utilized, like for example:
- Virtual Personal Assistant (Google assistant, Alexa, Cortana, Siri)
- Medical Diagnosis (helps in finding brain tumors and other brain-related diseases easily)
- Online Fraud Detection (checking whether it is a genuine transaction or a fraud transaction: Feed Forward Neural network are used)

Styles of Machine Learning
--------------------------

There four different styles in machine learning algorithms:

- Unsupervised Learning
- Supervised Learning
- Semi-Supervised Learning
- Reinforced Learning

**Unsupervised Learning** is a type of algorithm that learns patterns from untagged data.
The input data is not labeled, so the result is not known.
Models are created by deriving structural elements in input data. Methods are applied to select special occurrences of patterns in data.
Mathematical processes are applied to reduce the data in redundancy or group them by similarity.
K-Means and Eclat algorithms are being used with this type of ML.
Unsupervised learning is usually being used in:

- Clustering
- Association rule learning
- Dimensionality reduction tasks

**Supervised Learning** is a task of learning a function which maps an input to an output based on example input-output pairs, it saw (learned) before.
Here the input data is labeled. The model has to be trained before it can be used and give predictions (inference is conducted).
The model needs to be trained as long as it achieves the desired accuracy on data for validation.
It is used with Convolutional neural networks (CNNs) and Linear Regression algorithms.
Supervised learning is usually used to solve the following problems:

- Classification
- Regression

**Semi-Supervised Learning** is a task in machine learning that combines a small amount of labeled data and a large amount of unlabeled data.
Semi-Supervised learning is usually used to solve the following problems:
- Classification
- Regression

**Reinforced Learning** works with a learning argent that learns from its environment.
So, it works on interacting with the environment. The type of input data is not predefined. An agent rewards the model for success and does not reward it for a failure.
There following illustration 

<figure
  src="img/Reinforcement_learning_diagram.svg"
  caption="Diagram showing the components in a typical Reinforcement Learning (RL) system. An agent takes actions in an environment which is interpreted into a reward and a representation of the state which is fed back into the agent. [Meg17]">
</figure>

Algorithms where reinforced learning is applied are Q-Learning and SARSA.
Reinforced Learning learning is usually used to solve the following problems:
- Exploitation 
- Exploration


Deep Learning
=============

Artificial neural networks are inspired by the biology and workings of our brain.
But unlike the brain, where neurons can connect to any neuron within a given physical distance, the neural network can only do so through separate layers, connections, and directions of data propagation.

For example, take a picture and cut it up into a bunch of pieces. These are recorded in the first level of the neural network. In this first level, individual neurons pass the data to the second level. In the second level, this process is repeated until a final result is produced.

Each neuron assigns a score to its input, whether this is correct or incorrect depends largely on the task to be performed. The final result is then determined by the overall ratings. Think back to the stop sign example. Properties of a stop sign image are sliced ​​up and checked by different neurons - the octagonal shape, the red color, the prominent letters, the size. The job of the neurons is to figure out if it's a stop sign or not. The neural network outputs a probability vector based on the scores. In the stop sign example, the system might conclude that it is 86 percent a stop sign, 7 percent a speedometer and so on. The network architect then gives the system feedback on what is correct and what is not.

Neural networks have been known since the early days of AI, the problem was that they were very computationally intensive and therefore practically impossible to implement.  

Nowadays, image recognition by deep learning models is already better than humans in some scenarios. One area of ​​application is the identification of indicators for cancer in the blood or tumors on MRI images. Another, very prominent one, are Tesla's self-driving cars. Which is at the moment only available in the US as a beta tester, but will be available in the future in more and more countries.
In the following there are some more examples named for applications of Deep Learning:
- image and speech recognition
- virtual assistants
- chatbots
- fraud detection
- natural language processing


Computer Vision
===============

This section introduces the basic techniques of image-based recognition.
Under the computer-aided recognition of images, or Computer Vision, one understands various techniques to locate elements in images or identify and catalog videos. 

<figure
  src="img/kite.jpg"
  caption="Example picture of object detection [Rath17].">
</figure>

The goal is to use an automated process to gain a visual understanding while distinguishing between relevant and less distinguish relevant information. This is a complex process that otherwise reserved only for the human visual system, part of the nervous system.
Computer Vision is a subfield of Deep Learning, which is a subfield of Machine Learning, Machine Learning on the other hand belongs to Artificial Intelligence. 
Computer Vision can be also conducted without Deep Learning models. Like to detect edges or select objects from an image. But nowadays it is common that Computer Vision algorithms mainly use Deep Learning models. 

Applications
------------

Here are some examples of the most common applications of CV:

- **face recognition:** detect faces in images
- **object detection:** detect objects in images
- **image classification:** assign class to contents of an image
- **object tracking:** track the same object over time
- **defect detection:** detect defects in a manufacturing process 
- **movement analysis:** measuring technique to detect movements
- **cell classification:** use microscopic images of bio-medical content to interpret cellular mechanisms 


Different recognition types 
--------------------------

Today it is common to train image recognition models, which take an image as a received input and output one or more objects and possibly more recognize attributes. The various objects possible to recognize are in classes assigned. Examples of these images must first be stored in so-called image databases collected. In addition to the class prediction these image recognition models also provide an assessment of the accuracy of the prediction meet. This value can be understood as a kind of probability of prediction and describes how confident the model is that an image becomes a learned class can be assigned.

In general, the recognition systems distinguish between single and multiple recognition. With a single detection, the model says only one class as Prediction for the entire image. Models designed for multiple detection were able to recognize several objects of different classes in one image.
Consequently, information on the localization of the object in the image and confidence needed.

Natural Language Processing
===========================

Natural Language Processing (NLP) examines how natural language in the form of text or spoken language data can be processed algorithmically with the help of computers. It is a subfield of Artificial Intelligence and shares some techniques with Machine Learning and also the subfield Deep Learning. This relationship is illustrated in the following schematic:

<figure
  src="img/nlp_machinelearning.png"
  alt="How is NLP interlinked with AI, ML and DL"
  caption="How is Natural Language Processing interlinked with Artificial Intelligence, Machine Learning and Deep Learning [Bala21].">
</figure>

It is the interface between linguistics and computer science. The goal of NLP is the capability of understanding the contents of documents and accurately extract information and insights contained in the documents as well as categorize and organize the documents themselves. 

Goals in NLP
------------

The common goals or challenges of natural language processing are discussed in the following:
 - speech recognition
 - natural language understanding
   - Segmentation of previously captured speech into single words and phrases
   - Recognizing the basic forms of words and acquiring grammatical information
   - Recognizing the functions of individual words in the sentence (subject, verb, object, article, etc.)
   - Extraction of the meaning of sentences and parts of sentences
   - Recognizing sentence contexts and sentence relationships
 - natural language generation

Applications
------------

 In the following there are some applications of NLP named and shortly explained.

- **Speech recognition**: recognize spoken words
- **Chatbots**: provide automated answers to frequently asked customer questions, rather simple, canned answers
- **Question-Answer Systems**: like chatbots, but more sophisticated, with good language understanding 
- **Translation**: translate spoken and written text to another language
- **Sentiment Analysis**: interpret and analyze emotions in text, like articles or politician speeches
- **Automatic text summarization**: summarizes a long article or text to a shorter version
- **Grammar checking**: correcting grammatical errors in a text
- **Text classification**: assigning tags to articles to according to content and semantics
- **Named Entity Recognition**: like text classification and similar to sentiment analysis, tries to understand content of named entity: 
  - Example: *Elon Musk* [person] founder of *Tesla* [company] is buying *Twitter* [company] for *$44 billion* [monetary value].


Sources
--------

[Con17] Prof. Congduc Pham, WAZIUP Online Course: Fundamentals of Artificial Intelligence, https://cpham.perso.univ-pau.fr/LORA/HUBIQUITOUS/solution-lab/arduino-lora-tutorial/iot-courses/F-AI-1_Introduction.pdf, Version 2017

[Meg17] Megajuice, Reinforcement learning diagram, https://commons.wikimedia.org/wiki/File:Reinforcement_learning_diagram.svg, Version 2017

[Bala21] Ximena Bolaños, Natural Language Processing and Machine Learning, https://www.encora.com/insights/natural-language-processing-and-machine-learning, Version: September 29, 2021

[Rath17] Huang J, Rathod V, Sun C, Zhu M, Korattikara A, Fathi A, Fischer I, Wojna Z, Song Y, Guadarrama S, Murphy K, "Speed/accuracy trade-offs for modern convolutional object detectors." https://github.com/tensorflow/models/tree/master/research/object_detection Version: CVPR 2017

[Brow14] Jason Brownlee, "Applied Machine Learning Process" https://machinelearningmastery.com/process-for-working-through-machine-learning-problems/ Version 2019
