---
layout: post
title: Metis Data Science Bootcamp - Project 2
---

In the beginning of the second week of the bootcamp, we were given a project, that is due the last day in the third week, which is about scraping the web and then creating a linear regression model that would predict something based on some features that might be relevant to the prediction. For instance, you can predict the return on investment (**ROI**) of certain movie based on the fact that you know the number of ratings, reviews, run-time, etc. This post will illustrate my approach to tackle this particular problem.
{: style="text-align: justify"}

### Introduction

Let's say that you are a publisher or a writer who is eager to know whether people are going to be really engaged with your book or not. Now this is an interesting issue!
{: style="text-align: justify"}

**How can we provide such a client with this particular desire ?**

Well, we can rely on books related websites like [goodreads](https://www.goodreads.com) which is a massive social media network for book enthusiasts in which they can review, share, create lists, etc. The data from this website can be scraped, then we can manipulate them using python to get some insights and build models that can predict the engagement. The following sections will illustrate my approach in this project.
{: style="text-align: justify"}

### Methodology

The approach that i have followed is summarized in the following figure:
{: style="text-align: justify"}

![Image test]({{ site.url }}/images/data_j.png)

These steps will be discussed in detail in the following subsections.
{: style="text-align: justify"}

#### Step 1: Web Scraping

In this step, Selenium and BeautifulSoup were used to extract data from [goodreads](https://www.goodreads.com). Data of 5000 books from 5 main genres were chosen which are Art, Business, Fiction, Science and Self-help. Selenium was used only to login to the website since the lists of books were hidden for guests. BeautifulSoup was used to extract the following features from each book:
{: style="text-align: justify"}

<ul style="padding-left:20px">

    <li>Number of reviews</li>
    <li>Number of pages</li>
    <li>Average rating</li>
    <li>Category</li>
    <li>ISBN</li>

</ul>

In addition to **the number of ratings** which is the thing that i am trying to predict based on these features.
{: style="text-align: justify"}


#### Step 2: Data Cleaning and Exploratory Data Analysis (**EDA**)

In the cleaning stage, some books were removed because some of their features did not make any sense. For example, books that have zero number of pages or have significantly high number of pages like over 1500 pages were removed.
{: style="text-align: justify"}

After cleaning the data, EDA was done to get initial insights on the data. To elaborate, take a look at the following heatmap:
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro2_heatmap.png)

We can clearly see from the heatmap that overall we have low multi-colinearity so we do not need to worry about perfect colinearity. Also, the map tells us that number of reviews and fiction will probably have the highest effect on the model.
{: style="text-align: justify"}

Now, we can also get more insights from the pair plot below:
{: style="text-align: justify"}
Loading history...
Saturday, September 28th
￼￼
![Image test]({{ site.url }}/images/pro2_pairplot.png)

This pair plot shows that the number of reviews have almost linear relationship with the number of ratings which means that it is of a great value to any model that we are going to create. Also, the histogram of number of ratings and number of reviews tells us that most likely we need to apply some kind of transformation like logarithmic transformation or power transformation.
{: style="text-align: justify"}

#### Step 3: Models Creation

In this stage, a set of models were created based on the observations that were seen from EDA. Some models involved some kind of variable transformation, others involved interaction terms and others just used some of the parameters without any transformation or interaction parameters. Also, it should be noted that any feature that has a p-value > 0.05 were removed from the model. Now, only three models of all the models that were created will be discussed in the following subsection.
{: style="text-align: justify"}
#### Step 4: Models Training and Validation

* **The First Model (Baseline Model)**

In this model, only the numerical data were considered without any additional modifications.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro2_model1.png)

R-squared= 0.648, cross-validation score= 0.639. The R-squared is not bad. However, the residual is absolutely horrible.  
{: style="text-align: justify"}

* **The Second Model**

In this model, the number of reviews were only included. In addition to applying logarithmic transformation on both the number of reviews and the number of ratings.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro2_model2.png)
R-squared= 0.879, cross-validation score= 0.878. The residual plot is better than the previous one. However, the Q-Q plot is not so great.
{: style="text-align: justify"}

* **The Final Model**

Like the previous model, logarithmic transformation was applied, but also the rest of features were included except Philosophy.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro2_model3.png)

R-squared= 0.889, cross-validation score= 0.888. The residual plot is better than the previous one and the Q-Q plot is also better.
{: style="text-align: justify"}

#### Step 5: Final Model Testing and Results

The cross validation result for the final model is 0.888 and the testing result is 0.875, so R-squared and the residual plot shows that we have a fairly excellent model. However, when we look at the condition number from the stats table shown below, it turns out that we were tricked by over-fitting.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro2_stats_table2.png)

Now, that's quite an issue. **How can we solve it ?**

Well, thanks to regularization which can help us in avoiding over-fitting by providing a model that is somehow between the complex model and simple model.   
{: style="text-align: justify"}

### Final Thoughts and Recommendations

In essence, a few modifications on the model are needed to make it perform in a better way. Firstly, and most importantly, regularization must be used to solve the issue of over-fitting. Furthermore, ISBN can be used to get an extremely significant feature like the price of the book which will certainly enhance the prediction of the model. Lastly, gathering additional data will also enhance the accuracy of the prediction.
{: style="text-align: justify"}
