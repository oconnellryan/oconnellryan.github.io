---
layout: page
---

### Live Data

The data for this model is scraped from ESPN Fightcenter at the end of rounds using Python. This data includes knockdowns, total strikes landed, significant strikes (also broken down by the head, body & legs), control time, takedowns & submission attempts. Here is an example fo what this data looks like at the end of a round: &nbsp;<br>
<img src="/assets/ufc/fightcenter_ex.png" alt="Image" width="650"/> &nbsp;<br>
The difference between both fighters for each statistic is calculated, and these differences are utilized in the model to calculate the probability of each fighters winning the round. &nbsp;<br>

### The Model

To eliminate bias, fighters were first randomly assigned to either column in the dataset. For each round, the difference in fight statistics between the two fighters was calculated.

The response variable is structured as a four-level factor representing possible round outcomes:
- 10-8 for Fighter 1
- 10-9 for Fighter 1
- 10-9 for Fighter 2
- 10-8 for Fighter 2

This setup allows the model to capture both the direction and the margin of victory in each round.

The model itself is an ordered logistic regression (ordered GLM). It takes the stat differences as input and returns the predicted probability of each of the four outcomes. The result is a set of four probabilities representing the likelihood of a 10-9 or 10-8 round for either fighter. The total win probability for each fighter is also calculated as their 10-9 win probability plus their 10-8 win probability.

### Scoring Output

Utilizing the predicted probabilities, the python script can tweet the predicted winner and score of each round. If the predicted 10-8 win probability is less than 25%, the predicted score is 10-9 with the followning tweet output:
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 1 Scoring Model Prediction:<br><br>10-9 Jan Blachowicz <br>📊63% Win Probability<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFCLondon?src=hash&amp;ref_src=twsrc%5Etfw">#UFCLondon</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1903575061862175163?ref_src=twsrc%5Etfw">March 22, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

If the predicted 10-8 probability is greater than 25% but lower than 50%, the predicted score is still 10-9 but the tweet will contain the 10-8 probaility instead of win probability:
<div style="transform: scale(0.85); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 2 Scoring Model Prediction:<br><br>10-9 Justin Gaethje <br>⚠️ Possible 10-8 Round (26% Probability)<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFC313?src=hash&amp;ref_src=twsrc%5Etfw">#UFC313</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1898600263918780614?ref_src=twsrc%5Etfw">March 9, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

Finally, if the predicted 10-8 probability is greater than 50% the model will predict a 10-8 win and output the 10-8 probability:
<div style="transform: scale(0.85); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 1 Scoring Model Prediction:<br><br>10-8 Rhys McKee<br>🚨 Model predicted a 91% chance of a 10-8<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFCVegas105?src=hash&amp;ref_src=twsrc%5Etfw">#UFCVegas105</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1908675378459091215?ref_src=twsrc%5Etfw">April 6, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

A real-time scoring model that uses live fight stats to predict round-by-round win probability. &nbsp;<br>
&nbsp;<br>
The predictors used in this model are significant strikes landed (broken up by the head, body & legs), non-significant strikes, knockdowns, control time, takedowns, and submission attempts. The differences of these statistics (red corner - blue corner) are used to predict the winner of the round, as well as their odds of winning the round 10-8. More details on this model & the specific coeficcients are available here. &nbsp;<br>
<img src="/assets/ufc/fightcenter_ex.png" alt="Image" width="650"/> &nbsp;<br>
&nbsp;<br>
So for the round pictured above, the difference in significant head strikes is 2 in favor of Jan Blachowicz, and the difference in significant leg strikes is also 2 for Blachowicz. All of the other differences are zero as the body strikes are the same, and there are no other stats recorded. With these stats, the model predicted Jan had a 63% chance of winning round 1. &nbsp;<br>

&nbsp;<br>

### Live Win Probability Graphs

Utilizing a script that scrapes the ESPN fightcenter data every time it updates (about every 10 seconds during rounds), I can create a graph of the real-time win probability at any point duuring the round. Here is an example of one of these: &nbsp;<br>
<img src="/assets/ufc/win_prob_graph.png" alt="Image" width="800"/>

&nbsp;<br>
**Want to see this in action?**&nbsp;<br>
I post live scores and visuals during UFC events on X (Twitter) [@KOTrends](https://twitter.com/KOTrends)
