# Alphabet-Soup-Charity-Funding

## Overview

In this project, I am working on building a deep learning binary classifier to help Alphabet Soup Charity to decide whether an applicant is a good candidate for funding or not.

![intrp.jpg](images/intro.jpg)

The data provided by the charit contains historical data about ~ 34K applicant who received funds and whether they were successful or not. Employing this data, we train our deep learning classifier. The steps implemented are as follows
<ol>
<li>  Preprocess the data so that we can use it to train our model </li>
<li> Build, Compile and Fit our Deep Learning model </li>
<li> Finetune our model by dropping noisy features and modifying model architecture</li>
</ol>

Moreover, to evaluate the model, we use Accuracy Score, as well as Adam optimizer for the optimization.

In the next section we are discussing the obtained results for each of the conducted experiments


## Results

In this section we discuss the results found during conducting our analysis. As previously mentioned, we first preprocess the data itself, then we finetune the model using different settings for the network.

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

We firstly trained a model with these settings:
![initial.png](images/initial.png)
Activation is Relu per all layers and Sigmoid at the output layer. Moreover, model is trained for 20 epochs.

That model achieved 65 % test accuracy. Afterwards, we modifeied the model architecture to push this performance above.

### Trial 1

We trained the same model using same architecture, but we dropped the noisy features. we determine these noisy features using the correlation between the features and the target variable. We found out that **STATUS** and **ASK_AMT** are noisy and dropped them. Hence, the model performance is increased to ~ 66 %

### Trial 2

To increase the model performance, we added a hidden layer. so the architecture becomes as follows:
![trial2.png](images/trial2.png)
The performance is increased to become 72%



### Trial 3
In this trial we changed the number of units per each layer. So, the architecture becomes as follows
![trial3.png](images/trial3.png)
However, that didn't improve performance as it achieved only 65%

### Trial 4

Using the following architecture, and `tanh` as an activation for the output layer, we conducted our fourth trial. 
![trial4.png](images/trial4.png)

However, we only achieved 62% accuracy.

### Trial 5

We used the following architecture, but `sigmoid` activation per all layers.
![trial5.png](images/trial5.png)

And we achieved 69% test accuracy

###  Trial 6
Since trial 5 architecture achieved the best results so far, we trained a model using the same architecture but for longer time by increasing the number of epochs to 50 instead of 20.
![trial6.png](images/trial6.png)
However, the performance didn't improve as expected and we only achieved 65%.



## Summary

Despite the large capacity of neural networks as machine learning models, feature engineering could leads to better results. In addition, we explored the effect of changing the number of layers, units per layers, activation of output layer, activations of hidden layers and number of epochs on the performance of the netwrok. The best results achieved so far is the one obtained at trial 2, which is ~ 72 % test accuracy.
