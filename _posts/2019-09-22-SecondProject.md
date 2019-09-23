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

  * Number of reviews
  * Number of pages
  * Average rating
  * category
  * ISBN

In addition to **the number of ratings** which is the thing that i am trying to predict based on these features.
{: style="text-align: justify"}


#### Step 2: Data Cleaning and Exploratory Data Analysis (**EDA**)

In the cleaning stage, some books were removed because some of their features did not make any sense. For example, books that have zero number of pages or have significantly high number of pages like over 1500 pages were removed.
{: style="text-align: justify"}

After cleaning the data, EDA was done to get initial insights on the data. To elaborate, take a look at the following heatmap:
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/pro2_heatmap.png)



#### Step 3: Models Creation


#### Step 4: Models Training and Validation


#### Step 5: Final Model Testing



### Results


### Final Thoughts and Recommendations
