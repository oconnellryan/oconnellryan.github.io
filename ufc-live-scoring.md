---
layout: page
title: Live UFC Scoring Model
---
Using an ordered GLM model with the data available on ESPN Fightcenter, I have created a model that predicts the score of UFC rounds live.
&nbsp;<br>
The predictors used in this model are significant strikes landed (broken up by the head, body & legs), non-significant strikes, knockdowns, control time, takedowns, and submission attempts. The differences of these statistics (red corner - blue corner) are used to predict the winner of the round, as well as their odds of winning the round 10-8. More details on this model & the specific coeficcients are available here.
<img src="/assets/ufc/fightcenter_ex.png" alt="Image" width="500"/>
&nbsp;<br>

