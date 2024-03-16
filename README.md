# Dealing-with-a-COUNT-data-in-R-and-Python

![CountFLOWchart](https://user-images.githubusercontent.com/124582074/216988012-a4fbcf69-fe10-4bd9-b342-1019b3d8483d.jpg)

## Introduction
As a simple introduction, let me first explain what a COUNT data is, in such a way that even a farmer can relate with it. Let us assume the country *Germany* want to
study the effect of exchange RATE (to Naira), AGE of applicant, TYPE of visa, GENDER of applicant and applicant's level of EDUCation, on NUMBER of monthly visa applications received. The response of interest here is a COUNT (Number of monthly visa applications). These counts cannot include a negative number, the minimum will be zero. And mathematically, the problem can be expressed as:  

                                     NUMBER = RATE + TYPE + AGE + GENDER + EDUC ---------- (1)  
                                     NUMBER = RATE + TYPE + AGE + GENDER  + (1|EDUC) ----- (2)  
                                     
Model 1 and 2 above represents fixed and mixed effect models respectively. EDUC was used as a fixed/factor effect in equation 1 but used as a random effect in equation 2. *Fixed vs Mixed effect models* is a topic for another day. So back to our topic of interest, NUMBER is the response or dependent variable, every other variable at the right-hand side are called the explanatory or independent variables. Other examples of COUNT data includes: number of times a patient visits the hospital, number of items sold per day in a shop, number of graduates in a school every calender year, number of calls you receive daily, number of new members welcomed on a whatsapp group every month, and so on.

## Which model suits best?
When you have a count response, the possible distributions to fit are the discrete distributions **Poisson** and **Negative binomial**. Although the first option that comes to mind is to fit a poisson distribution, however a poisson distribution assumes that mean and variance of your response variable are equal. This will imply that the values of your response variable vary as expected. But this assumption never or most times never holds in the real world. Scientists came up with solutions to tackle such issue. 

There are 3 possible scenarios: For,

   • **Equidispersion** (when Mean of response = Variance of response) : use the regular Poisson
   
   • **Overdispersion** (when Mean of response < Variance of response): use the Negative Binomial or Quasi-Poisson
   
   • **Underdispersion** (when Mean of response > Variance of response): use the Conway-Maxwell Poisson (COM-Poisson) regression or Generalized Poisson regression.

The solution provided above are most appropriate to use if your count are not inflated by zeros. But when this is the case, there are other methods already provided by to take care of the inflation or disturbances that could arise due to excess of zeros in the counts. 

They include (in addition to the list above): For,

• **Equidispersion** : use the Hurdle or Truncated Poisson, Zero-Inflated Poisson

• **Overdispersion** : use the Hurdle or truncated Negative binomial, Zero-Inflated Negative binomial, COM-Poisson and Generalized Poisson

• **Underdispersion** use the COM-Poisson regression or Generalized Poisson regression.

At the beginning of the note, the flow chart for the topic of discussion clearly explains everything I have written so far pictorially. 
The step-by-step way to carry out the building of all the model in both R and Python can be found in this repository. In the codes, there was no dataset used, but you can always plug in your data and fit any of the models. The idea is to have a guide on what model method is best to use in any particular condition of your COUNT data.

If you have any questions/comments/suggestions you can reach me via email on ikedichi.edward.azuh@biom.uni-freiburg.de
