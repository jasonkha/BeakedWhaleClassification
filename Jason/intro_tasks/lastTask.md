# Study materials about KNN with AdaBoost

*Your last task is to study materials about KNN with AdaBoost. One of the papers that useful to read is: Experiments with a New Boosting Algorithm by Yoav Freund.*

AdaBoost constructs a classified as a linear combination of weak classifiers. Initially, all training points are weighted equally. But after each iteration, the points that were misclassified more often are given a higher weight, while the easier points are given lower weight. This boosting approach forces the weak learning algorithm to perform better on the hardest data points. Also, the combined hypothesis of many weak learners in boosting reduces the variance while also reducing the bias.

Freund's experiment attempted to speed up the nearest-neighbors algorithm with boosting by reducing the number of distance calculations. The dataset is from the US Postal Service and consists of 9707 training samples and 2007 test samples of handwritten digits. AdaBoost KNN outperformed condensed nearest neighbors and the strawman algorithms on the training and test sets when trained on more than 1170 samples.
