## MODULE TWO FINAL PROJECT: HYPOTHESIS TESTING, STATISTICAL ANALYSIS

by Alex Shropshire, Connor Anderson, Kevin Velasco

For our module two final project, we were tasked to demonstrate our ability to gather real-world information and use our knowledge of statistically analysis and hypothesis testing to gain an analytical understanding in a meaningful way. We selected the European Soccer Dataset (https://www.kaggle.com/hugomathien/soccer) to use for our project. We have angled ourselves as an analytics team, with the goal to help improve club management, players development/player selection, formation tactics, team attributes, and transfer market. 

THE DATA

The data is sourced within an SQL database. We created an entity relationship diagram of the data structure and found that the dataset had two subsets:  tables that contained real-life match data and leagues across the European continent and fictional statistics of players and teams from the soccer video game FIFA. 

Video game player attributes and player info was disconnected from real-world tables. This was unfortunate because we want to focus on real-world matches, so that eliminated those tables for use. Rather than use SQL to join the tables together, we split our hypothesis tests into separate jupyter and maintained the original tables as pandas dataframes. Then, in each test, we performed the appropriate joins between tables of interest to stitch together the necessary data required for analysis. 

METHODOLOGY
For the following tests, we first state our our null & alternative hypothesis, and then perform the necessary data exploration, data cleaning, feature engineering, and data organization. And then we calculate the effect size (quantifying the difference between two groups) to help us determine the appropriate sample size. The powers of each hypothesis varies, but we maintain an alpha of 0.05 throughout each test. This alpha, or the significance level (α) is the probability of making the wrong decision when the null hypothesis is true. We wanted to keep this consistent, a standard while performing out various t-tests and the p-values generated from them. 

When testing for the differences between two groups, we can imagine two separate situations. In one, there is no real difference between the two groups. In the other situation, the mean difference between the two groups is not zero. For our purposes, we chose to run t-tests rather than z-tests. Why you might ask? Well for one, we determined to denote the entire dataset as a sample of the population of all soccer leagues. Without knowing all the top-flight leagues information, the population standard deviation is unknown, we can only use the t-test in this situation. 




### HYPOTHESIS #1 ###
Is there a statistical difference in the odds of winning a game when a team is playing in front of their home crowd? This was the only required hypothesis for this dataset.  By keeping our scope on the dataset as whole, no joins were required in this analysis, as the match table was the sole table of interest. Our H0 (Null Hypothesis): there is no statistically significant difference in the odds of winning a game when a team is at playing at home vs. when a team is playing away, 
HA (Alternative Hypothesis): there is a statistically significant difference in the odds of winning a game when a team is playing at home vs. when a team is playing away. To aid with our analysis, we engineered new features creating Booleans for when the home team won and the away team won, with 1’s being indicative of wins. Calculating the Cohen’s d between the means of the home win rate and the away win rate as ~0.359, we then use this to find the ideal sample size. With a power of .95 and an alpha of .05, we determined that we needed a sample size of 202. 

We then use the boostrap method to generate arrays of 50 means of randomly selected samples between the home wins and the away wins. Bootstrapping allows assigning measures of accuracy (defined in terms of bias, variance, confidence intervals, prediction error or some other such measure) to sample estimates. This technique allows estimation of the sampling distribution of almost any statistic using random sampling methods. This ensures our data for the 2-sample T-test is randomly collected, independent, and approximately normally distributed. Calculating the t-statistic, with a value of ~27.92, we were first alarmed that it was incorrect. But, after calculating the difference between the home win rate (~0.459) and the away win rate (~0.287) to be ~0.171, it seemed to fit the numbers. With a final p-value of 3.89e-50, we have the evidence within our sampling to confidently reject the null hypothesis, and accept the alternative that a difference between the two means exists. 

HYPOTHESIS #2



HYPOTHESIS #3

HYPOTHESIS #4
