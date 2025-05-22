---
layout: page
title: Live UFC Analytics Platform (KO Trends)
---

**Skip to:**
<div style="display: flex; gap: 12px; flex-wrap: wrap; margin-bottom: 24px;">
  <a href="#live-scoring" style="...">Live Scoring</a>
  <a href="#judging" style="...">Judging Analysis</a>
  <a href="#rankings" style="...">Fighter Ratings</a>
</div>


<!-- Live Scoring -->
<h2 id="live-scoring">Live Scoring Model:</h2>
See how real-time stats fuel live score predictions and win probability visuals through a streamlined modeling process.
### Live Data Collection:

A Python script scrapes ESPN Fightcenter at the end of each round. The script collects:
- Total strikes landed
- Significant strikes (broken up by target)
- Control time
- Takedowns
- Submission attempts &nbsp;<br>

Below is an example of what the ESPN stat feed looks like at the end of a round:
<img src="/assets/ufc/fightcenter_ex.png" alt="Image" width="570"/> &nbsp;<br>
Stat differences are calculated from the red corner’s perspective and used to estimate round win probabilities. For the round above (Błachowicz was red), the differences are: &nbsp;<br>
- 2 Significant Head Strikes (5 - 3)
- 0 Significant Body Strikes (1 - 1)
- 2 Significat Leg Strikes (11 - 9) &nbsp;<br>

No other stats were recorded, so the model only used the differences in head & leg strikes here.

### The Model:

To eliminate bias, fighters were first randomly assigned to either column in the dataset. For each round, the difference in fight statistics between the two fighters was calculated.

The response variable was structured as a four-level factor representing possible round outcomes:
- 10-8 for Fighter 1
- 10-9 for Fighter 1
- 10-9 for Fighter 2
- 10-8 for Fighter 2

This setup allows the model to capture both the direction and the margin of victory in each round.

The model itself is an ordered logistic regression (ordered GLM). It takes the stat differences as input and returns the predicted probability of each of the four outcomes. &nbsp;<br>
&nbsp;<br>
The following graph shows the coeficcient (or value) for each statistic: 
<img src="/assets/ufc/new_coefs.png" alt="Image" width="700"/> &nbsp;<br>
The model result is a set of four probabilities representing the likelihood of a 10-9 or 10-8 round for either fighter. The total win probability for each fighter is also calculated as the sum of both.

### Scoring Output:

Utilizing the predicted probabilities, the python script can tweet the predicted winner and score of each round. Depending on the 10-8 probabilities, there are the different scoring messages: &nbsp;<br>

**Standard 10-9 (10-8 probability less than 25%):**
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 2 Scoring Model Prediction:<br><br>10-9 Carlos Ulberg <br>📊61% Win Probability<a href="https://twitter.com/hashtag/UFCLondon?src=hash&amp;ref_src=twsrc%5Etfw">#UFCLondon</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1903576651151077422?ref_src=twsrc%5Etfw">March 22, 2025</a></blockquote>


**10-8 Warning (10-8 probability between 25% and 50%):**
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 2 Scoring Model Prediction:<br><br>10-9 Justin Gaethje <br>⚠️ Possible 10-8 Round (26% Probability)<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFC313?src=hash&amp;ref_src=twsrc%5Etfw">#UFC313</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1898600263918780614?ref_src=twsrc%5Etfw">March 9, 2025</a></blockquote> 
</div>

**10-8 Round (10-8 probability greater than 50%):**
<div style="transform: scale(1); transform-origin: top left; width: fit-content;">
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Round 1 Scoring Model Prediction:<br><br>10-8 Rhys McKee<br>🚨 Model predicted a 91% chance of a 10-8<a href="https://twitter.com/hashtag/UFC?src=hash&amp;ref_src=twsrc%5Etfw">#UFC</a> <a href="https://twitter.com/hashtag/UFCVegas105?src=hash&amp;ref_src=twsrc%5Etfw">#UFCVegas105</a></p>&mdash; KO Trends (@KOTrends) <a href="https://twitter.com/KOTrends/status/1908675378459091215?ref_src=twsrc%5Etfw">April 6, 2025</a></blockquote> 
</div>

### Live Win Probability Graphs:

Using additional code to scrape ESPN Fightcenter during rounds, I can collect live data whenever it updates. This live data refreshes about every 10 seconds, and using the same model framework discussed above I can predict the win probability for each fighter at any point during the round.

**Win probability graph Example:** &nbsp;<br>
<img src="/assets/ufc/round2.png" alt="Image" width="700"/>

&nbsp;<br>

<!-- Rankings Formula -->
<h2 id="rankings">Fighter Performance Ratings:</h2>
<p>Rankings model, performance scores, and career trajectory charts.</p>
<img src="/assets/ufc/rankings.png" style="width: 300px; border-radius: 8px;">

<!-- Judging Analysis -->
<h2 id="judging">Judging Report Cards:</h2>
<p>SGPS, judge bias visuals, and split round breakdowns.</p>
<img src="/assets/ufc/judging_viz.png" style="width: 300px; border-radius: 8px;">

