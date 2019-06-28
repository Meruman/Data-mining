---
layout: post
title: "Decision Tree Classifier"
include: \usepackage{amsmath}
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

The tree initially contains a single root node that contains all the training instances. If a node contains instances from more than one class, it is expanded using an attribute test condition known as ***splitting criterion***. When we split the node, a child leaf node is created for each outcome of the attribute test condition and the instances of the parent node are distributed to the respective children. This node expansion step can then be recursively applied to each child node, as long as it has labels of more than one class. This stops whenever all the instances of a leaf node have identical class labels. Each leaf node is assigned the most frequent class label of it's instances.

![Hunt's Algorithm]({{site.baseurl}}/images/Hunts_Algorithm.JPG)

### Hunt's algorithm assumptions

* ***Some of the child nodes created can be empty if non of the instances have the particular attribute value***. One way to handle this is to convert this child nodes into root nodes, assigning them the class label that occurs most frequent in the parent's node instances.
* ***If all instances in a node have identical attribute values but different class labels, it is impossible to expand the node***. One way to handle this is to convert this node into a leaf node and assign the most frequent class label of the instances.

---

## Methods for Expressing Attribute Test Conditions

* ***Binary attributes*** --> this generates 2 potential outcomes.

![Binary]({{site.baseurl}}/images/Binary.JPG)

* ***Nominal attributes*** --> Nominal attributes can have many values, so they can be expressed in 2 ways: as a *Multiway split* (or "bushy"), or a *binary split*.

![Multiway_Binary]({{site.baseurl}}/images/Multiway_Binary.JPG)

* ***Ordinal attributes*** --> Can also produce binary or bushy splits, but can only be grouped as long as the grouping does not violate the order property of the attribute values.

![Ordinal]({{site.baseurl}}/images/Ordinal.JPG)

* ***Continuous attributes*** --> 

## Selecting an attribute

### Impurity

Impurity Measure for a Single Node
The impurity of a node measures how dissimilar the class labels are for the data
instances belonging to a common node.

![Impurity_measures]({{site.baseurl}}/images/Impurity_measures.JPG)

![Impurity_comparison]({{site.baseurl}}/images/Impurity_comparison.JPG)

information gain:
![Information_gain]({{site.baseurl}}/images/Information_gain.JPG)

### For attributes with large amount of children and low impurity (Like ID attributes)

There are two ways to overcome this problem. One way is to generate only binary decision trees, thus avoiding the difficulty of handling attributes with varying number of partitions. This strategy is employed by decision tree classifiers such as CART. Another way is to modify the splitting criterion to take into account the number of partitions produced by the attribute. For example, in the C4.5 decision tree algorithm, a measure known as gain ratio is used to compensate for attributes that produce a large number of child nodes. This measure is computed as follows:

![Gain_ratio]({{site.baseurl}}/images/Gain_ratio.JPG)

### Characteristics of Decision Tree Classifiers

* ***Aplicability*** --> Decision trees are a nonparametric approach for building classification models. This approach does not require any prior assumption about the probability distribution governing the class and attributes of the data, and thus, is applicable to a wide variety of data sets. It is also applicable to both categorical and continuous data without requiring the attributes to be transformed into a common representation via binarization, normalization, or standardization. Unlike some binary classifiers, it can also deal with multiclass problems without the need to decompose them into multiple binary classification tasks. Another appealing feature of decision tree classifiers is that the induced trees, especially the shorter ones, are relatively easy to interpret. The accuracies of the trees are also quite comparable to other classification techniques for many simple data sets.
* ***Expressiveness*** --> A decision tree provides a universal representation for discrete-valued functions. In other words, it can encode any function of discrete-valued attributes. This is because every discrete-valued function can be represented as an assignment table, where every unique combination of discrete attributes is assigned a class label. Since every combination of attributes can be represented as a leaf in the decision tree, we can always find a decision tree whose label assignments at the leaf nodes matches with the assignment table of the original function. Decision trees can also help in providing compact representations of functions when some of the unique combinations of attributes can be represented by the same leaf node. Nevertheless, not all decision trees for discrete-valued attributes can be simplified. One notable example is the parity function, whose value is 1 when there is an even number of true values among its Boolean attributes, and 0 otherwise. Accurate modeling of such a function requires a full decision tree with 2^d nodes, where d is the number of Boolean attributes.
* ***Computational Efficiency*** --> Since the number of possible decision trees can be very large, many decision tree algorithms employ a heuristicbased approach to guide their search in the vast hypothesis space. For example, using a greedy, topdown, recursive partitioning strategy for growing a decision tree. For many data sets, such techniques quickly construct a reasonably good decision tree even when the training set size is very large. Furthermore, once a decision tree has been built, classifying a test record is extremely fast, with a worst-case complexity of O(w), where w is the maximum depth of the tree.
* ***Handling Missing Values*** --> A decision tree classifier can handle missing attribute values in a number of ways, both in the training and the test sets. When there are missing values in the test set, the classifier must decide which branch to follow if the value of a splitting node attribute is missing for a given test instance. One approach, known as the probabilistic split method, which is employed by the C4.5 decision tree classifier, distributes the data instance to every child of the splitting node according to the probability that the missing attribute has a particular value. In contrast, the CART algorithm uses the surrogate split method, where the instance whose splitting attribute value is missing is assigned to one of the child nodes based on the value of another non-missing surrogate attribute whose splits most resemble the partitions made by the missing attribute. Another approach, known as the separate class method is used by the CHAID algorithm, where the missing value is treated as a separate categorical value distinct from other values of the splitting attribute. Other strategies for dealing with missing values are based on data preprocessing, where the instance with missing value is either imputed with the mode (for categorical attribute) or mean (for continuous attribute) value or discarded before the classifier is trained. 
  
  During training, if an attribute v has missing values in some of the training instances associated with a node, we need a way to measure the gain in purity if v is used for splitting. One simple way is to exclude instances with missing values of v in the counting of instances associated with every child node, generated for every possible outcome of v. Further, if v is chosen as the attribute test condition at a node, training instances with missing values of v can be propagated to the child nodes using any of the methods described above for handling missing values in test instances.

![Handling_missing]({{site.baseurl}}/images/Handling_missing.JPG)