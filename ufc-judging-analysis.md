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

&nbsp;
&nbsp;


### Individual Judge Biases
I then used the binomial GLM model created to identify individual judge biases. The following graph shows the results of this analysis, where the coeficcient ratios for each judge show the relative importance of each variable used.
![Image](/assets/images/judges.png)
We can see the differences in how inmdividual judges score fights here. Judges with higher coeficcient ratios for the blue poinmts are more grappler friendly (ex: Eric Colon). Derek Cleary seems to prefer grapplers who are very active on the ground with reversals and submissions, whereas grapplers with the ability to take down their opponent and control them should do well on Sal D'Amato's scorecards Chris Lee seem to favor strikes landed to the head, whereas Junichiro Kamijo heavily favors strikes to the leg. Michael Bell values events with fight ending potential (knockdowns & submission attempts) very highly.




I then used the binomial GLM model created to identify individual judge biases. In order to do this, two models were created for each judge. The first model (judge model) used only this judges scorecards, while the other model (nonjudge model) used only scorecards from other judges. The judge model coeficcients were then divided by the non-judge model coeficcients, and these coeficcient ratios show the relative importance of the variables for each judge. The following graoh shows these coeficcient ratios for 6 of the top judges:
