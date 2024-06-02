---
layout: page
title: UFC Judging Analysis
---
The goal of this project was to idenity the factors most relevant in UFC judging. Additionally, I wanted to identify individual bias and identify the specific criteria that is important to individual judges. A binomial GLM model as well as a decision tree & random forest model were created in order to do this.

### Binomial GLM Model
This model utilizes differences in fighter statistics to model the winner of a round. Differences between the two fighters for the following statistics were used:
- **head**: significant strikes landed to the head
- **body:** significant strikes landed to the body
- leg: significant strikes landed to the leg
- nonsig: non-significant strikes landed to any part of the body
- kd: knockdowns landed
- td: takedowns landed
- rev: reversals
- ctrl: control time (minutes)
- sub: submission attempts

The following output shows the log odds ratio for each of the predictors:
![Display Name](/assets/images/log_dds.png)

You can see that the model has identified the head as the most important target to the judges. 
