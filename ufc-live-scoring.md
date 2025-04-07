---
layout: page
title: ""
---

## Result Highlights:
This model utilizes fight statistics to predict win probabilities of UFC rounds live. This model can be used to graph the live win probability, and the scoring bot tweets predicted scores at the end of rounds:
<img src="/assets/ufc/win_prob_graph.png" alt="Image" width="700"/>
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 2 Scoring Model Prediction:<br><br>10-9 Carlos Ulberg <br>📊61% Win Probability<a href="https://twitter.com/hashtag/UFCLondon?src=hash&amp;ref_src=twsrc%5Etfw">#UFCLondon</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1903576651151077422?ref_src=twsrc%5Etfw">March 22, 2025</a></blockquote> &nbsp;<br>

## Live Data Collection:

The data for this model is scraped from ESPN Fightcenter at the end of rounds using Python. This data includes knockdowns, total strikes landed, significant strikes (also broken down by the head, body & legs), control time, takedowns & submission attempts. Here is an example fo what this data looks like at the end of a round: &nbsp;<br>
<img src="/assets/ufc/fightcenter_ex.png" alt="Image" width="500"/> &nbsp;<br>
The difference between both fighters for each statistic is calculated, and these differences are utilized in the model to calculate the probability of each fighters winning the round. &nbsp;<br>

### The Model:

To eliminate bias, fighters were first randomly assigned to either column in the dataset. For each round, the difference in fight statistics between the two fighters was calculated.

The response variable is structured as a four-level factor representing possible round outcomes:
- 10-8 for Fighter 1
- 10-9 for Fighter 1
- 10-9 for Fighter 2
- 10-8 for Fighter 2

This setup allows the model to capture both the direction and the margin of victory in each round.

The model itself is an ordered logistic regression (ordered GLM). It takes the stat differences as input and returns the predicted probability of each of the four outcomes. The result is a set of four probabilities representing the likelihood of a 10-9 or 10-8 round for either fighter. The total win probability for each fighter is also calculated as their 10-9 win probability plus their 10-8 win probability.

### Scoring Output:

Utilizing the predicted probabilities, the python script can tweet the predicted winner and score of each round. If the predicted 10-8 win probability is less than 25%, the predicted score is 10-9 with the followning tweet output:
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 1 Scoring Model Prediction:<br><br>10-9 Jan Blachowicz <br>📊63% Win Probability<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFCLondon?src=hash&amp;ref_src=twsrc%5Etfw">#UFCLondon</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1903575061862175163?ref_src=twsrc%5Etfw">March 22, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>
If the predicted 10-8 probability is greater than 25% but lower than 50%, the predicted score is still 10-9 but the tweet will contain the 10-8 probaility instead of win probability:
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 2 Scoring Model Prediction:<br><br>10-9 Justin Gaethje <br>⚠️ Possible 10-8 Round (26% Probability)<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFC313?src=hash&amp;ref_src=twsrc%5Etfw">#UFC313</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1898600263918780614?ref_src=twsrc%5Etfw">March 9, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>
Finally, if the predicted 10-8 probability is greater than 50% the model will predict a 10-8 win and output the 10-8 probability:
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 1 Scoring Model Prediction:<br><br>10-8 Rhys McKee<br>🚨 Model predicted a 91% chance of a 10-8<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFCVegas105?src=hash&amp;ref_src=twsrc%5Etfw">#UFCVegas105</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1908675378459091215?ref_src=twsrc%5Etfw">April 6, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</div>

&nbsp;<br>

### Live Win Probability Graphs:

Using additional code to scrape ESPN Fightcenter during rounds, I can collect live data whenever it updates. This live data refreshes about every 10 seconds, and using the same model framework discussed above I can predict the win probability for each fighter at any point during the round.

The following graph showcases the predicted round win probability throughout round 1 of Jan Blachowicz vs Carlos Ulberg:
<img src="/assets/ufc/win_prob_graph.png" alt="Image" width="700"/>

&nbsp;<br>
**Want to see this in action?**&nbsp;<br>
I post live scores and visuals during UFC events on X (Twitter) [@KOTrends](https://twitter.com/KOTrends)
