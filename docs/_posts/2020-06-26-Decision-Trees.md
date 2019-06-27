---
layout: post
title: "Decision Tree Classifier"
---
*For this I used this book:
Pan-Ning Tan, Michael Steinbach, Anuj Karpatne, Vipin Kumar. Introduction
to Data Mining, Pearson, 2019.

## Decision Tree

A decision tree has 3 types of nodes:

* A **root node**, with no incoming links and zero or more outgoing links.
* **Internal nodes**, they have exactly one incoming link and two or more outgoing links.
* **Leaf Node**, this has exactly one incoming link and no outgoing links.

Every leafnode is associated with a class label, the other nodes contains **attribute test conditions** that usually use one attribute per node.

![Decision tree]({{site.baseurl}}/images/DT.JPG)

---

## A Basic Algorithm to Build a Decision Tree

### Hunt's Algorithm

