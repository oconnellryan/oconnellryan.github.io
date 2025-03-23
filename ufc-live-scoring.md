---
layout: page
title: Live UFC Scoring Model
---
Using an ordered GLM model with the data available on ESPN Fightcenter, I have created a model that predicts the score of UFC rounds live. &nbsp;<br>
&nbsp;<br>
The predictors used in this model are significant strikes landed (broken up by the head, body & legs), non-significant strikes, knockdowns, control time, takedowns, and submission attempts. The differences of these statistics (red corner - blue corner) are used to predict the winner of the round, as well as their odds of winning the round 10-8. More details on this model & the specific coeficcients are available here. &nbsp;<br>
<img src="/assets/ufc/fightcenter_ex.png" alt="Image" width="650"/> &nbsp;<br>
&nbsp;<br>
So for the round pictured above, the difference in significant head strikes is 2 in favor of Jan Blachowicz, and the difference in significant leg strikes is also 2 for Blachowicz. All of the other differences are zero as the body strikes are the same, and there are no other stats recorded. With these stats, the model predicted Jan had a 63% chance of winning round 1. &nbsp;<br>

&nbsp;<br>

### Live Win Probability Graphs

Utilizing a script that scrapes the ESPN fightcenter data every time it updates (about every 10 seconds during rounds), I can create a graph of the real-time win probability at any point duuring the round. Here is an example of one of these: &nbsp;<br>
<img src="/assets/ufc/win_prob_graph.png" alt="Image" width="800"/>
