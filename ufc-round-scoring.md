---
layout: page
title: UFC Judging Analysis
---
The goal of this project was to idenity the factors most relevant in UFC judging. Additionally, I wanted to identify individual bias and identify the specific criteria that is important to individual judges. A binomial GLM model as well as a decision tree & random forest model were created in order to do this.

## Project Highlights:

### Binomial GLM Model
This model utilizes differences in fighter statistics to model the winner of a round. Differences between the two fighters for the following statistics were used:
- **head**: significant strikes landed to the head
- **body**: significant strikes landed to the body
- **leg**: significant strikes landed to the leg
- **nonsig**: non-significant strikes landed to any part of the body
- **kd**: knockdowns landed
- **td**: takedowns landed
- **rev**: reversals
- **ctrl**: control time (minutes)
- **sub**: submission attempts

The following output shows the log odds ratio for each of the predictors:
![Image](/assets/images/log_odds.png){: width="250" ; style="float: left"}

You can see that the model has identified the head as the most important target to the judges. The model also backs up the fact that knockdowns are very impactful to winning rounds. Takedowns and reversals are valued essentially the same, and will improve the log odds of winning a round by about as much as 50 seconds of control time. A submission attempt is valued more than twice as highly as a reversal or takedown.

<br style="clear:both" />

### Decision Tree & Random Forest Model:
In addition to the binomial GLM model created, a decision tree and random forest were created to judge rounds. Most of the variables are the same here, but instead of the significant strikes being broken down by target (head, body legs), they are broken down by where the striking occured (distance, ground or clinch). This data will allow the decision trees to identify different types of fights, such as a round where one fighter dominated on the ground but lost on the feet. The main decision tree is shown below:
![Image](/assets/images/tree.png)
You can see that this tree has multiple splits based on who won the distance striking as well as the grappling (through ground striking and control time). While this overfits the data, you can see how this approach makes sense for scoring. A random forest model using the same predictors was also created, and the following output shows the results of this:
![Image](/assets/images/varimp_plot.png)
Just like in the decision tree significant distance strikes, control time, and significant ground strikes are the most important predictors. Significant clinch strikes do not have much of an impact, and the mean decrease gini is actually higher for non-significant strikes. Takedowns are not overly important due to most grappling splits occuring on control time and ground striking. Submission attempts, knockdowns, and reversals all occur infrequently so the random forest was unable to capture the importance of these.



[Full Paper](https://oconnellryan.github.io/assets/Analysis-of-UFC-Judging-Criteria.pdf)
