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

The tree initially contains a single root node that is associated with all the training instances. If a node is associated with instances from more than one class, it is expanded using an attribute test condition known as ***splitting criterion***. When we split the node, a child leaf node is created for each outcome of the attribute test condition and the instances of the parent node are distributed to the respective children. This node expansion step can then be recursively applied to each child node, as long as it has labels of more than one class. This stops whenever all the instances of a leaf node have identical class labels. Each leaf node is assigned the most frequent class label of it's instances.

![Hunt's Algorithm]({{site.baseurl}}/images/Hunts_Algorithm.JPG)

### Hunt's algorithm assumptions

* ***Some of the child nodes created can be empty if non of the instances have the particular attribute value***. One way to handle this is to convert this child nodes into root nodes, assigning them the class label that occurs most frequent in the parent's node instances.
* ***If all instances in a node have identical attribute values but different class labels, it is impossible to expand the node***. One way to handle this is to convert this node into a leaf node and assign the most frequent class label of the instances.

