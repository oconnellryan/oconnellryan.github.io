---
layout: page
title: MLB Steal Probability Engine
---

<!-- Wrapper container to center everything -->
<div style="text-align: center; margin-bottom: 24px;">

  <p style="margin-bottom: 12px; font-weight: bold;">Skip to:</p>

  <div style="display: inline-flex; gap: 12px; flex-wrap: wrap; justify-content: center;">
    <a href="#model" style="...">Solen Bases Model</a>
    <a> | </a>
    <a href="#deployment" style="...">Live Deployment</a>
  </div>

</div>



<!-- Stolen Bases Model -->
<h2 id="model">Steal Probability Model:</h2>
A generalized linear regression model I built is used to predict stolen base success probability. This model utilizes the following variables to account for the specific players in the interraction:

##### Baserunner
Smoothed stolen base percentages are used to account for the baserunner (smoothed percentages are scaled closer to league average the 
less attempts a player has). This methodology takes past success unto account while not overreacting to small sample sizes.

##### Catcher
For the opposing catcher poptime to second base is utilized (the amount of time in seconds that it takes a catcher to throw the ball to second base). This data was more predictive for catchers than past smoothed percentages.

##### Pitcher
Smoothed past steal percentages were also used for pitchers (success of baserunners against the pitcher).

### Model Summary
The model utilizes these three variabkes to predict the success probability of stolen base attempts. Some key attrbiutes of the model are:
- The baserunner and catcher have more of an impact than the pitcher.
- The model weighted runner data approximately 1.5 times more heavily than pitcher data.


<!-- Live Deployment -->
<h2 id="deployment">Live Deployment:</h2>
The live engine was built using python. The script leverages the MLB API to collect the result and names of the players involved in steal attempt as they happen live during games. Player names are then used to look up 
smoothed percentages and poptime data which is fed to the model resulting in a prediction.

### Tweet Output:
  <!-- Tweet Embed -->
  <div style="flex: 1; min-width: 400px;">
    <div style="transform: scale(1); transform-origin: top left; width: fit-content;">
      <blockquote class="twitter-tweet">
        <p lang="en" dir="ltr">
          George Springer Stole 2B ✅<br><br>
          🟢 Good Matchup<br>
          84% Successful Steal Chance<br><br>
          Player Steal Grades:<br>
          🏃 George Springer: 61st/302<br>
          ⚾ Randy Vásquez: 106th/401<br>
          🧤 Elias Díaz: 12th/61
        </p>
        &mdash; Steal Decisions Live (@StealSignal) 
        <a href="https://twitter.com/StealSignal/status/1925342409459745182?ref_src=twsrc%5Etfw">May 22, 2025</a>
      </blockquote>
    </div>
    <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
  </div>
  
Live tweets produced by this engine contain the following data:
- Result (succesful steal or caught stealing)
- Model grade and predicted steal probability
- Player steal grades

Model grades are simply broken into good, okay, or bad matchups based on predicted probabilities. Player steal grades are where each specific player ranks within their position based on smoothed percentages or poptime.
