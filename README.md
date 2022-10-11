# Alphabet-Soup-Charity-Funding

## Overview

In this project, I built a deep learning binary classifier to help Alphabet Soup Charity decide whether an applicant is a good candidate for funding or not.

![intrp.jpg](intro.jpg)

The data provided by the charit contains historical dataon roughly 34K applicant who received funding and whether they were successful or not. Using this data, I trained the deep learning classifier.
<ol>
<li>  Preprocess the data so that we can use it to train our model </li>
<li> Build, Compile and Fit our Deep Learning model </li>
<li> Finetune our model by dropping noisy features and modifying model architecture</li>
</ol>

To evaluate the model, I used Accuracy Score, as well as Adam optimizer for the optimization.

## Results

First, I preprocessed the data, then I finetuned the model using different settings for the network.

### Preprocessing
<ol>

<li> The EIN and NAME columns have been dropped  </li>
<li> The columns with more than 10 unique values have been grouped together  </li>
<li> The categorical variables have been encoded using one-hot encoding </li>
<li> The preprocessed data is split into features and target arrays  </li>
<li> The preprocessed data is split into training and testing datasets  </li>
<li> The numerical values have been standardized using the StandardScaler() module </li>
</ol>

<br>

**Note: All these trials are compiled using binary cross entropy as a loss function, and Adam optimizer**
### Trial 0

Trained a model with these settings:
![initial.png](initial.png)
Activation is Relu per all layers and Sigmoid at the output layer. The model is trained for 20 epochs.

That model achieved 65 % test accuracy. I modifeied the model architecture to  increase the performance.

### Trial 1

I trained the same model using same architecture, but we dropped the noisy features. I determined these noisy features using the correlation between the features and the target variable. I found out that **STATUS** and **ASK_AMT** are noisy and dropped them. The model performance is increased to ~ 66 %

### Trial 2

To increase the model performance, I added a hidden layer. 
![trial2.png](trial2.png)
The performance is increased to become 72%



### Trial 3
In this trial we changed the number of units per each layer.
![trial3.png](trial3.png)
That didn't improve performance.  It was only 65% accurate. 

### Trial 4

Using the following architecture, and `tanh` as an activation for the output layer,I conducted the fourth trial. 
![trial4.png](trial4.png)

It only achieved 62% accuracy.

### Trial 5

I used the following architecture, but `sigmoid` activation per all layers.
![trial5.png](trial5.png)

It achieved 69% test accuracy

###  Trial 6
Since trial 5 architecture achieved the best results so far, I trained the model using the same architecture but for a longer amount of time by increasing the number of epochs to 50 instead of 20.
![trial6.png](trial6.png)
The performance didn't improve as expected and it only achieved 65%.



## Summary

Despite the large capacity of neural networks of machine learning models, feature engineering could leads to better results. I explored the effect of changing the number of layers, units per layers, activation of output layer, activations of hidden layers and number of epochs on the performance of the netwrok. The best results achieved so far is the one obtained at trial 2, which is ~ 72 % test accuracy.
