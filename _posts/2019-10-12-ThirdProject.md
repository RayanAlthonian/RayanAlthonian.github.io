---
layout: post
title: Metis Data Science Bootcamp - Project 3
---
In the fifth week of the bootcamp, we were given the instructions for the third project. In this project, the students were asked to create a classification model that classifies labels based on certain features. For instance, if the data of different crimes is provided, one can train a model to classify the different types of crimes based on, for example, the neighborhood name, time and date. This post will illustrate my approach to tackle this particular problem.
{: style="text-align: justify"}

### Introduction
One of the most important pre-processing steps in some of image processing applications, like face detection and gesture recognition, is skin segmentation. Skin segmentation is challenging due to many areas of concern like the changing light intensity. My goal in this project is to take the different values of RGB colors of different pixels and classify them as skin pixels or non skin pixels.
{: style="text-align: justify"}

### Methodology
The approach that i have followed is summarized in the following figure:
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro3_pic1.png)

These steps will be discussed in detail in the following subsections.
{: style="text-align: justify"}

#### Step 1: Data Collecting
The dataset, [skin segmentation dataset](https://archive.ics.uci.edu/ml/datasets/skin+segmentation), was taken from UCI repository. This dataset includes the RGB values of pixels that were taken from face pictures of people of different ages, ethnic groups and genders. Each pixel is labeled as as either a skin pixel or non-skin pixel.
{: style="text-align: justify"}
#### Step 2: Data Cleaning
In this step, null, Nan values and outliers were handled.
{: style="text-align: justify"}

#### Step 3: Exploratory Data Analysis (**EDA**)
The pair plot for the different features is shown below.
![Image test]({{ site.url }}/images/pro3_pic2.png)

Clearly, there is an overlap between the features but it is partial overlapping which means we can continue with the same features without worrying about removing any feature. Also, note that since we just have 3 features which are the values of the RGB colors, we can not remove any of them even if we have a complete overlapping between the features. Additionally, the scatter plots show that nonlinear model must be used.
{: style="text-align: justify"}
Now, let's have a look at the histograms of the skin pixels and non-skin pixels.

Skin Pixels histograms:   
<p align="center">
<img src="/images/skinhist.png">
</p>

Non-Skin Pixels histograms:  

<p align="center">
<img src="/images/noskinhist.png">
</p>


One interesting thing to notice in the histogram of the red color is that we can clearly say that any red value below 100 will be classified as a non-skin pixel. This tells us on initial thought that red color will be the most important feature in the classification model. The following figure illustrates the previously mentioned observation in a better way than the histogram.
{: style="text-align: justify"}

<p align="center">
<img src="/images/redskin.png">
</p>

Another interesting observation is that the number of skin pixels and non-skin pixels is different, so we have two options:

<ul style="padding-left:20px">

    <li>Oversampling</li>
    <li>Undersampling</li>

</ul>

<p align="center">
<img src="/images/sam.png">
</p>

The dataset is not large, so oversampling is a better option. The oversampling is done using [SMOTE](https://imbalanced-learn.readthedocs.io/en/stable/generated/imblearn.over_sampling.SMOTE.html).  


#### Step 4: Modeling

Before creating any model, the data were split into training and test sets. Now, there are three things that must be noted before talking about the baseline model and the rest of the models. The first thing is that the train set is over-sampled, then the score of it is determined in all the models. The second thing is that when we do cross validation, we have to over-sample the 60 % train set and validate on the remaining 20% for each fold. The last thing is that the best possible hyper-parameters were chosen using cross validation that was applied using pipe-lining. The following figure illustrates how the typical cross validation is done.  
{: style="text-align: justify"}
<p align="center">
<img src="/images/cv.gif">
</p>

<ul style="padding-left:20px">

    <li><b>The Baseline Model: Logistic Regression Model</b> </li>
Logisitc regression model was chosen as the baseline model because it typically performs well in binary classification problems. The parameters for the model were as follows:
{: style="text-align: justify"}

<ul style="padding-left:20px">

    <li>solver= 'saga'</li>
    <li>penalty='elasticnet'</li>
    <li>l1_ratio=0.1</li>
    <li>C=100</li>
    <li>max_iter=1000</li>


</ul>

A summary of the results is shown below:

<table style="width:100%">
 <tr>
   <th>Training F1-score </th>
   <th>Cross-Validation F1-Score</th>
 </tr>
 <tr>
   <td>0.94</td>
   <td>0.939 </td>
 </tr>
</table>
<p style="text-align: justify">
The last thing to note about this model is the coefficients. A simple of bar chart of the coefficients is shown below:
</p>

<p align="center">
<img src="/images/logistic_feature.png">
</p>
 
Well, this is strange. We expected red to have the highest impact on the model, but it did not.

    <li><b>The Second Model: Decision Trees Model </b> </li>



    <li><b>The Final Model: Random Forest </b></li>



</ul>






















#### Step 5: Final Model Testing

### Final Thoughts
