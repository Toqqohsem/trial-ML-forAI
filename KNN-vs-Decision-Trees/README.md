
# KNN vs. Decision Trees: Machine Learning

Investigation of the performance of two classification models, k-nearest neighbours and decision trees for two sets of data sets adult.data and bank.data.

## Description

Pre-processing of two data sets from UCI Machine Learning Repository, performing five fold cross validation, and sampling growing subsets of training and validation data. For each data set, performing the two models with the best hyper-parameter on the test set to measure accuracy.

Found that the k-nearest neighbour regression approach achieved worse accuracy than decision trees and was significantly slower to train.


### Result

Since KNN is unsupervised and requires on-spot learning, it results in significantly higher computational complexity and time and is much more expensive than decision trees. For the training of adult.data, KNN took 43 minutes in total to train, while decision trees only took 1 minute.

Decision tree, on the other hand, is supervised, and is faster than KNN. Decision trees are also easy to read and interpret.

The hyperparameter can have an impact on the accuracy for KNN. As shown in the graph the correlation between the value of K and the accuracy of the model is demonstrated clearly, we can see that the best accuracy is achieved around when K = 12 with accuracy of 0.84 on validation set.

The limit on the maximum depth of the decision tree, which is the hyperparameter for decision trees, controls the overall complexity of the decision tree.

As shown in the graph, . Initially, increasing the depth will make the tree better fitted and decrease the entropy cost and increase the accuracy; however, trees that are too deep will overfit the training data, thus performing badly on the test data. The model performed the best when the maximum depth of the tree was around 7 with accuracy of 0.87 on validation set.
```

