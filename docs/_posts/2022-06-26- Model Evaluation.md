---
layout: post
title: " Model Evaluation"
include: \usepackage{amsmath}
---
*For this I used this book:
Pan-Ning Tan, Michael Steinbach, Anuj Karpatne, Vipin Kumar. Introduction
to Data Mining, Pearson, 2019.

## Model Evaluation

### Holdout Method

the labeled set D is randomly partitioned into two disjoint sets, called the training set D.train and the test set D.test. A classification model is then induced from D.train, and its error rate on D.test, errtest is used as an estimate of the generalization error rate. The proportion of data reserved for training and for testing is typically at the discretion of the analysts, e.g., two-thirds for training and one-third for testing.
The holdout method can be repeated several times to obtain a distribution of the test error rates, an approach known as **random subsampling** or repeated holdout method.

### Cross-Validation

method that aims to make
effective use of all labeled instances in D for both training and testing.

![Cross_validation]({{site.baseurl}}/images/Cross_validation.JPG)

The k-fold cross-validation method generalizes this approach by segmenting the labeled data D (of size N) into k equal-sized partitions (or folds).
During the ith run, one of the partitions of D is chosen as D.test(i) for testing, while the rest of the partitions are used as D.train(i) for training. A model m(i) is learned using D.train(i) and applied on D.test(i) to obtain the sum of test errors, errsum(i). This procedure is repeated k times. The total test
error rate, errtest, is then computed as

![CrossError]({{site.baseurl}}/images/CrossError.JPG)

In the extreme case, when k = N, every run uses exactly one data instance for testing and the remainder of the data for testing. This special case of k-fold cross-validation is called the **leave-one-out** approach. This approach has the advantage of utilizing as much data as possible for training. However,leaveone-out can produce quite misleading results in some special scenarios and can be computationally expensive for large data sets as the cross-validation procedure needs to be repeated N times.

### Bootstrap

The methods presented so far assume that the training records are sampled without replacement. As a result, there are no duplicate records in the training and test sets. In the bootstrap approach, the training records are sampled with replacement; i.e., a record already chosen for training is put back into the original pool of records so that it is equally likely to be redrawn.
