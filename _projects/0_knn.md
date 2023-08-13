---
layout: page
title: K-Nearest Neighbour (KNN) from scratch 
description: Writing KNN functions from scratch to classify abalone into different classes based on their age.
img: 
importance: 1
category: coursework
---

### TL;DR
Writing KNN algorithms to classify abalone based on their age with an accuracy of 27.614% (n=20). The low accuracy may be due to imbalanced data set as 17 of 29 classes have less than a hundred data points resulting in insufficient data to train the model accurately. Data originates from [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Abalone).

Refer to [k-nearest-neigbour github repo](https://github.com/Mono-PQ/course_work/tree/main/4_k-nearest-neighbours) for more details.

### Introduction
**Classification** problem refers to grouping similar data or classifying data by specific categories using a predetermined set of features. The output of a classification problem has discrete value represented by an integer. 

In this project, we'll attempt to classify the age of abalone into 15 classes (i.e., rings) using the following features. 

|Features|Data Type|Measures|Description|
|--------|---------|--------|-----------|
|Sex|Nominal|M, F, I (Infant)|Nil|
|Length|Continuous|mm|Longest shell measurement|
|Diameter|Continuous|mm|Perpendicular to length|
|Height|Continuous|mm|With meat in shell|
|Whole weight|Continuous|grams|Whole abalone|
|Shucked weight|Continuous|grams|Weight of meat|
|Viscera weight|Continuous|grams|Gut weight (after bleeding)|
|Shell weight|Continuous|grams|After being dried|

<br>

### K-Nearest Neighbours (KNN) 
The KNN algorithm assumes that similar data points exist in close proximity. The neighbouring data points are used to predict the outcome of the the new data point by choosing the most common categories for classification problems or mean of the neighbours for regression problems. `K` represents the number of neighbours used to predict the outcome.

$$
EuclideanDistance = d(p,q) = \sqrt{(p_1 - q_1)^2 + (p_2 - q_2)^2 + ... + (p_n - q_n)^2}
$$

Normalisation of data points when using KNN for prediction is important to ensure that the distance is not being influenced by features with higher scale of measurements that could result in misclassifications. KNN is distance dependent, where more weight is given to higher scaled feature. 

Python code for KNN algorithm, train-test-split and K-fold:
{% raw %}
```python
import numpy as np

def loadData(filename):
    # Load data from file into X
    X = []
    count = 0
    
    text_file = open(filename, "r")
    lines = text_file.readlines()
        
    for line in lines:
        X.append([])
        words = line.split(",")
        # Convert values of the first attribute into float
        for word in words:
            if (word=='M'):
                word = 0.333
            if (word=='F'):
                word = 0.666
            if (word=='I'):
                word = 1
            X[count].append(float(word))
        count += 1
    
    return np.asarray(X)

def testNorm(X_norm):
    xMerged = np.copy(X_norm[0])
    # Merge datasets
    for i in range(len(X_norm)-1):
        xMerged = np.concatenate((xMerged,X_norm[i+1]))
    print(np.mean(xMerged,axis=0))
    print(np.sum(xMerged,axis=0))

def dataNorm(X): 
    # Normalise data points for first 8 columns
    for i in range(0, 8): 
        col = X[:,i]
        max_val = col.max() 
        min_val = col.min() 
        X[:,i] = (col-min_val)/(max_val-min_val)
    return X

def splitTT(X_norm, percentTrain): 
    # Split dataset into train and test set based on the percentTrain specified
    # Random shuffling of data before splitting
    np.random.shuffle(X_norm)
    # Get index to split the data and slice the dataset based on the index
    index = round(len(X_norm)*percentTrain)
    X_train, X_test = X_norm[:index,:], X_norm[index:,:]
    X_split = [X_train, X_test]
    return X_split

def splitCV(X_norm, k): 
    # Partition dataset into k-folds based on k (i.e., number of partitions) specified
    # Random shuffling of data before partitioning
    np.random.shuffle(X_norm)
    X_split = []
    # Get the approx. size for each fold
    size = round(len(X_norm)/k)
    # Partition the data based on the size. The remaining data points will be added to the arrays 
    # and attempt to make the size of each array equal. Remaining data points would be left unused. 
    for i in range(k): 
        X_split.append(X_norm[:size,:])
        X_norm = X_norm[size:,:]
    # If there are limited data points, the following code could be use to add the remaining data points 
    # to the partitions: (Extra)
    # if len(X_norm) != 0:
    #     i = 0
    #     for elem in X_norm:
    #         X_split[i] = list(X_split[i])
    #         X_split[i].append(elem)
    #         X_split[i] = np.array(X_split[i])
    #         i+=1
    return X_split

def knn(X_train, X_test, K): 
    predictions = []
    # Generate prediction for X_test
    for row in X_test:
        # Calculate the distance of the data points in X_train for each data point in X_test 
        distances = []
        for row_train in X_train:
            distance = 0
            # Calculated distance based on Euclidean distance
            for i in range(len(row)-1):
                distance += (row[i] - row_train[i])**2
            distance = np.sqrt(distance)
            distances.append((row_train, distance))
        # Sort the distances for the data point of X_test
        distances.sort(key=lambda elem: elem[1])
        # Get the "K" (specified number of neighbours) and predict the class for that data point
        neighbours = []
        for i in range(K):
            neighbours.append(distances[i][0])
        output_vals = [n[-1] for n in neighbours]
        prediction = max(set(output_vals), key=output_vals.count)
        predictions.append(prediction)
    # Calculate the accuracy of the prediction (no. accurate predictions / total predictions)
    accurate_pred = 0 
    pred_count = len(predictions)
    actual = X_test[:,-1]
    for i in range(pred_count):
        if predictions[i] == actual[i]:
            accurate_pred += 1
    accuracy = (accurate_pred/pred_count) * 100.00
    return accuracy

# This is an example the main of KNN with train-and-test + Euclidean
def knnMain(filename,percentTrain,k):
 
    # Data load
    X = loadData(filename)
    # Normalization
    X_norm = dataNorm(X)
    # Data split: train-and-test
    X_split = splitTT(X_norm,percentTrain)
    # KNN: Euclidean
    accuracy = knn(X_split[0],X_split[1],k)
    
    return accuracy
```
{% endraw %}

<br>

### Accuracy
The following accuracy is calculated using the percentage of accurate predictions. Values are rounded up to 3 decimal places. 
- The highest and lowest accuracy for train-and-test split are 27.614% for 70:30 split where k-neighbour=20 and 18.861% for 50:50 split where k-neighbour=1.
- The highest and lowest accuracy for k-fold cross validation split are 25.659% for k-fold = 15 where k-neighbour=20 and 18.861% for k-fold=1 where k-neighbour=1.

|Accuracy|Train-and-Test| | |Cross-Validation| | |
|--------|--------------|-|-|----------------|-|-|
||0.7-0.3|0.6-0.4|0.5-0.5|5-fold|10-fold|15-fold|
|K=1|19.393%|19.270%|18.861%|19.641%|19.895%|19.976%|
|K=5|25.858%|24.536%|22.882%|23.401%|22.410%|23.285%|
|K=10|24.741%|25.613%|25.227%|24.048%|23.916%|24.580%|
|K=15|26.257%|26.272%|26.663%|25.102%|24.731%|24.724%|
|K=20|27.614%|27.169%|26.472%|25.269%|25.162%|25.659%|

<br>

### Run Time 
The computational time is tabulated using the `timeit` library. Values are rounded up to 3 decimal places. 

|Computational Time|Train-and-Test| | |Cross-Validation| | |
|--------|--------------|-|-|----------------|-|-|
||0.7-0.3|0.6-0.4|0.5-0.5|5-fold|10-fold|15-fold|
|K=1|11.969 seconds|13.483 seconds|14.147 seconds|45.429 seconds|50.753 seconds|52.492 seconds|
|K=5|12.136 seconds|13.474 seconds|14.070 seconds|45.299 seconds|50.434 seconds|52.282 seconds|
|K=10|11.931 seconds|13.479 seconds|13.972 seconds|45.307 seconds|50.532 seconds|52.689 seconds|
|K=15|11.906 seconds|13.605 seconds|13.977 seconds|45.840 seconds|50.737 seconds|52.855 seconds
|K=20|11.936 seconds|13.662 seconds|13.992 seconds|45.423 seconds|50.601 seconds|52.021 seconds|