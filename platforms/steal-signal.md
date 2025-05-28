---
layout: page
title: MLB Steal Probability Engine
---

<!-- Wrapper container to center everything -->
<div style="text-align: center; margin-bottom: 24px;">

  <p style="margin-bottom: 12px; font-weight: bold;">Skip to:</p>

  <div style="display: inline-flex; gap: 12px; flex-wrap: wrap; justify-content: center;">
    <a href="#model" style="...">Solen Bases Model</a>
    <a href="#deployment" style="...">Live Deployment</a>
  </div>

</div>



<!-- Stolen Bases Model -->
<h2 id="model">Steal Probability Model:</h2>
A generalized linear regression model is used to predicty stolen base success probability. This model utilizes the following variables to account for the specific players in the interraction:

##### Baserunner
Smoothed stolen base percentages are used to account for the baserunner. These smoothed percentages are scaled closer to league average the 
less attempts a player has, meaning a baserunner with just one past attempt that was succesful would have a much closer percentage to league average than 100%.
This methodology takes past suvves unto account while not overreavting to small sample sizes.

##### Opposing Catcher
For the opposing catcher poptime to second base is utilized. This is the amount of time in seconds that it takes a catcher to throw the ball to second base 
after catching it. The same smoothed past percentage methodology used for runners was also tried, but the poptime data ended up being much more statistically significant.

##### Opposing Pitcher
The same methodology used for baserunners was also used for pitcchers. Opposing steal percentages were scaled in the same way so that pitcher with 
fewer attempts against them will have a smoothed steal percentage closer to league average.

### Model Summary
Runner smoothed percent and catcher poptime have lower p-values, indicating they are slightly more important in the model than the pitcher smoothed percentages. The exact same smoothing methodology was used for past runner 
and pitcher percentages so these coeficcients can be compared directly. A coeficcient just above 1.5 for runners and around 1 for pitchers indicates that the model values past runner 
behavior about 50% more than pitcher tendencies when predicting steal outcomes.


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
