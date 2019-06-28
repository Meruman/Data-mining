---
layout: post
title: "Overfitting"
include: \usepackage{amsmath}
---
*For this I used this book:
Pan-Ning Tan, Michael Steinbach, Anuj Karpatne, Vipin Kumar. Introduction
to Data Mining, Pearson, 2019.

## Model Overfitting

Even if a model fits well over the training data, it can still show poor generalization performance, a phenomenon known as model overfitting.
Model overfitting is the phenomena where, in the pursuit of minimizing the training error rate, an overly complex model is selected that captures specific patterns in the training data but fails to learn the true nature of relationships between attributes and class labels in the overall data.

### Reasons for overfitting

* **Limited Training Size** a training set consisting of a finite number of instances can only provide a limited representation of the overall data. Hence, it is possible that the patterns learned from a training set do not fully represent the true patterns in the overall data.
* **High Model Complexity** an overly complex model also has a tendency to learn specific patterns in the training set that do not generalize well over unseen instances, One measure of model complexity is the number of “parameters” that need to be inferred from the training set. For example, in the case of decision tree induction, the attribute test conditions at internal nodes correspond to the parameters of the model that need to be inferred from the training set. A decision tree with larger number of attribute test conditions (and consequently more leaf nodes) thus involves more “parameters” and hence is more complex. Given a class of models with a certain number of parameters, a learning algorithm attempts to select the best combination of parameter values that maximizes an evaluation metric (e.g., accuracy) over the training set. If the number of parameter value combinations (and hence the complexity) is large, the learning algorithm has to select the best combination from a large number of possibilities, using a limited training set.
Un modelo elige la mejor combinacion de parametros que da el mejor resultado, entonces si tenemos pocos training instances, y muchos parametros, puede que el algoritmo elija "Al azar" una combinacion de parametros que da muy buenos resultados para esos training instances, pero puede que en el futuro con mas instances, no genere muy buenos resultados.
Cuando tenemos muchos atributos irrelevantes, el modelo los usa y causa overfit, ya que solo aprende la mejor combinacion de todos esos atributos irrelevantes, para el training set, pero al momento de probarlo con un test set tendremos un error mayor ya que no nos enfocamos en los atributos relevantes.

## Model selection

we want to select the model that shows lowest generalization error rate. The process of selecting a model with the right level of complexity, which is expected to generalize well over unseen test instances, is known as model selection.

### Using a Validation Set

Note that we can always estimate the generalization error rate of a model by using “out-of-sample” estimates, i.e. by evaluating the model on a separate validation set that is not used for training the model.
Given a training set D.train, we can partition D.train into two smaller subsets, D.tr and D.val, such that D.tr is used for training while D.val is used as the validation set. For example, two-thirds of D.train can be reserved as D.tr for training, while the remaining one-third is used as D.val for computing validation error rate.
one limitation of this approach is that it is sensitive to the sizes of D.tr and D.val, obtained by partitioning D.train. If the size of D.tr is too small, it may result in the learning of a poor classification model with substandard performance.
On the other hand, if the size of D.val is too small, the validation error rate might not be reliable for selecting models, as it would be computed over a small number of instances.

## Complexity in DT

Let k be the number of leaf nodes and Ntrain be the number of training instances. The complexity of a decision tree can then be described as k/Ntrain.

![GenError]({{site.baseurl}}/images/GenError.JPG)

where err(T) is the training error of the decision tree and Ω is a hyperparameter that makes a trade-off between reducing training error and minimizing model complexity, Ω can be viewed as the relative cost of adding a leaf node relative to incurring a training error. the above approach for estimating generalization error rate is also termed as the **pessimistic error estimate**. It is called pessimistic as it assumes the generalization error rate to be worse than the training error rate.
simply using the training error rate as an estimate of the generalization error rate is called the **optimistic error estimate**.
