---
layout: page
title: UFC Judging Analysis
---
The goal of this project was to identify the importance of relevant factors of UFC Judging and identify how individual judges value these factors differently. This began as my Senior Thesis project that was completed in May 2024 at Syracuse University, and I have since improved upon the methods as well as added to it.

## Project Walkthrough:

### Data & Methodology
Round by round scorecard data was scraped from mmadecisions.com. The fight data used for this project was scraped from ufcstats.com. 

The fight data included significant strikes landed with two different breakdowns. The first breakdown, which I will refer to as the target data, is broken down by whether the strike was landed to the head, body or legs. The second significant strike breakdown is by whether they were landed at distance, in the clinch or on the ground, so I will call this the positional breakdown. Aside from significant strikes landed, the fight data also included knockdowns, non-significant strikes landed, control time, takedowns landed, reversals and submission attempts.

In order to remove the red vs. blue corner effect, I randomly assigned each fighter's data to one of two sets of columns. After fighters were randomly assigned for each round, I calculated the difference between each of the statistics mentioned above between the two fighters. The differences of these statistics will then be used to predict the win probability of fighter 1 in the models. 

### Binomial GLM Models
The main GLM model utilized the target data as this seemed to be the more valuable breakdown as well as the stronger model. Here are the results after running this model
![Image](/assets/ufc/target_model.png)


The following output shows the log odds ratio for each of the predictors:
![Image](/assets/images/log_odds.png)

You can see that the model has identified the head as the most important target to the judges. The model also backs up the fact that knockdowns are very impactful to winning rounds. Takedowns and reversals are valued essentially the same, and will improve the log odds of winning a round by about as much as 50 seconds of control time. A submission attempt is valued more than twice as highly as a reversal or takedown.

<br style="clear:both" />

### Individual Judge Biases
I then used the binomial GLM model created to identify individual judge biases. The following graph shows the results of this analysis, where the coeficcient ratios for each judge show the relative importance of each variable used.
![Image](/assets/images/judges.png)
We can see the differences in how individual judges score fights here. Judges with higher coeficcient ratios for the blue points are more grappler friendly (ex: Eric Colon). Derek Cleary seems to prefer grapplers who are very active on the ground with reversals and submissions, whereas grapplers with the ability to take down their opponent and control them should do well on Sal D'Amato's scorecards Chris Lee seem to favor strikes landed to the head, whereas Junichiro Kamijo heavily favors strikes to the leg. Michael Bell values events with fight ending potential (knockdowns & submission attempts) very highly.

### Decision Tree & Random Forest Model:
In addition to the binomial GLM model created, a decision tree and random forest were created to judge rounds. Most of the variables are the same here, but instead of the significant strikes being broken down by target (head, body legs), they are broken down by where the striking occured (distance, ground or clinch). This data will allow the decision trees to identify different types of fights, such as a round where one fighter dominated on the ground but lost on the feet. The main decision tree is shown below:
![Image](/assets/images/tree.png)
You can see that this tree has multiple splits based on who won the distance striking as well as the grappling (through ground striking and control time). While this overfits the data, you can see how this approach makes sense for scoring. A random forest model using the same predictors was also created, and the following output shows the results of this:
![Image](/assets/images/varimp_plot.png)
Just like in the decision tree significant distance strikes, control time, and significant ground strikes are the most important predictors. Significant clinch strikes do not have much of an impact, and the mean decrease gini is actually higher for non-significant strikes. Takedowns are not overly important due to most grappling splits occuring on control time and ground striking. Submission attempts, knockdowns, and reversals all occur infrequently so the random forest was unable to capture the importance of these.



[Full Paper](https://oconnellryan.github.io/assets/Analysis-of-UFC-Judging-Criteria.pdf)
