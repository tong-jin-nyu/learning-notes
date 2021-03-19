# Analytical

## Time on Facebook Distribution

Created on: 03/09/2021

Modified on: 03/09/2021

## Question 

What do you think the distribution of time spent per day on Facebook looks like? What metrics would you use to describe that distribution?

## Solution

1. User segments

- Lite User
  - Those who occasionally use Facebook to check new feeds and say hello to their friends.
- Regular user
  - Those who use Facebook on a daily basis.
- Power user
  - Those who spend a large amouont of their time on Facebook.

2. Based on user segments, we expect the distribution structure of user's time on Facebook to be multimodel with three peaks: one near the lower end of the distribution, representing the general lite users; one would be clustered around the middle, representing the regular user group; the third one would be at the higher end of the distribution, representing the power user group. 

3. Because the distribution is a tri-model (multilevel model), instead of referring to the mean, we need to use **mode** and **median**, along with quantiles, to describe and measure.

4. The distribution would probably be **right skewed**, meaning that the majority of users are in the lite and regular groups while there exist extreme power users that are at the very right side of the distribution.

5. Finally, we need to check if there exist outliers. We can run an interquartile range (IQR) test to highlight outliers. We can also use a boxplot to visualize outliers. We need to exclude outliers from our analysis because some of them could be bots instead of real users. 

The above hypotheses need to be validated using real data.