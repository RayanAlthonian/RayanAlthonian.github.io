---
layout: post
title: Metis Data Science Bootcamp Project 1
---

In the first week of the bootcamp, Metis intstructors teach basic data science libraries like Numpy, Matplotlib, Pandas and Seaborn.
{: style="text-align: justify"}
The first project is about doing exploratory data analysis (EDA) on NYC subway data to provide a specific client with their needs which is done by using the tools that were taught in the first week of the bootcamp.
{: style="text-align: justify"}
The client is an NGO called women tech, women yes (WTWY) which aims to empower women in the technology sector. The client wants to invite people to a gala, that is meant to support women in tech, in the beginning of summer, so they asked us to determine the best possible times, days and stations in which their street team is more likely to signup the maximum amount of people and hence invite them to the gala.
{: style="text-align: justify"}
### Our Approach in Analyzing the Data

We have followed certain steps in analyzing the data. Firstly, we have determined the analysis period which is 5 weeks prior to the beginning of June since June is the first month in summer. Secondly, we have extracted the data from [MTA webiste](http://web.mta.info/nyct/subway/). Thirdly, we have then cleaned the data by omitting outliers and negative values of the counting of the flow of people through the turnstiles. Lastly, we created visuals and deduced insights from them and then, we provided the client with the best possible times, stations and days.
{: style="text-align: justify"}
### The Visuals and the Corresponding Insights

The first visual that we have obtained is the one that shows the best days for the whole analysis period.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/fig1.png)

We notice from the figure that Thursday, Wednesday and Friday are the top three days
in terms of the average daily inflows and outflows, so we can say on initial thought that these three days are more likely to bring more people to the gala. Also, we notice that the inflows and outflows are not equal that is because some of the exits
do not have turnstiles which means that the number of people leaving will not be counted in these cases.
 {: style="text-align: justify"}

 The second figure shows the top five stations in terms of volume for the whole analysis period.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/fig2.png)

The last figure shows the average daily volume for each day with respect to the time.
{: style="text-align: justify"}
![Image test]({{ site.url }}/images/fig3.png)

we notice here that there is one issue, on Friday between 5 to 7 am a sudden spike occurs. This garbage data is due to the inaccuracy in cleaning the data.
{: style="text-align: justify"}

### Final Thoughts

I think the first project is relatively easy, but it might be challenging for those
who do not have to prior exposure to pandas. Overall, it was an interesting project
and experience to test out what we have learned in the first week.
{: style="text-align: justify"}
