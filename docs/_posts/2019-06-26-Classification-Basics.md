---
layout: post
title: "Classification: Basic Concepts and Techniques"
---
*For this I used this book:
Pan-Ning Tan, Michael Steinbach, Anuj Karpatne, Vipin Kumar. Introduction
to Data Mining, Pearson, 2019.

## Classification

Classification is the act or process of dividing things into groups according to their **type**

### _**Basic Concepts**_

![Classification task]({{site.baseurl}}/images/Classification_task.JPG){:height="120%" width="120%"}

The data for a classification task is a set of instances (records or data you have available).
For each instance, there is a set of attributes that describe the instance (_x_) and a class label (_y_),
they are typically represented as a tuple _(x,y)_.
The attributes can be of any type, but the label must be categorical (discrete or nominal) i.e. they must be a finite set of classes and No relation is implied among nominal values (no ordering or distance measure). This labels are the ones to be predicted later on.

A *classification model* learn the relationship between the set of attributes and the class label. There are different ways to represent this model (Tree, table of probabilities, etc.).
Matemathically, the model is a target function " _f_ " that has as input the attributes and produces as output the predicted class label for that input. So, a model classifies correctly an instance _(x,y)_ if the output of the target function "_f(x)_" is "_y_"

Some examples of classification tasks are:

* Spam filtering --> **attribute:** features of the message. **Class label:** spam or not spam.
* Tumor identification --> **attribute:** features from MRI scans. **Class label:** malignant or benign.

This 2 examples are binary classification problems because the number of class labels are 2. Whenever we have more than 2 classes, then we have a multi-class problem.

A classification model is used as:

* **Predictive model** --> to classify new unlabeled instances (Not seen before).
* **Descriptive model** --> to identify the characteristics that makes a class different from another class.

---

## General Framework for Classification

Classification is the task of assigning labels to unlabeled data instances and a **classifier** is used to perform such task.
The model is created using a given set of instances, known as **training set**, which contains attribute values and class labels for each instance. The way of learning a classification model is known as **learning algorithm**.
The process of classification involves 2 steps: applying the learning algorithm to a training data and learn the model (also known as **induction**), and then applying the model to assign labels to a test data set (also known as **deduction**).

The performance of a classifier can be evaluated by comparing the predicted labels against the true labels of the instances. This information can be analyzed in a table called **Confusion matrix**

|               | Predicted class          |
|               |--------------------------|
|               | Class =1      | Class =2 |
| -------       |:-------------:| --------:|
| Actual class  | right-aligned | $1600    |
|               | centered      |   $12    |
