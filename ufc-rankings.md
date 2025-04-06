---
layout: page
title: ""
---

### Why these rankings?

The official UFC rankings are often influenced more by promotion than performance. Voted on by an unkown media panel they can reflect hype, star power, and marketing priorities over merit. Fighters with UFC favor often receive fast-track opportunities, while others are stalled despite consistent wins. This is why an I have created an unbiased ranking formula that ranks fighters based on merit.


### Explore the Rankings
Use the interactive tool below to browse my updated rankings. These are updated automatically after each event and reflect results, opponent strength, and recent activity — not media perception.

<iframe 
  src="https://ryanoconnell.shinyapps.io/rankings/"
  width="50%" 
  height="550" 
  style="border:none;">
</iframe>


### My Rankings Formula Explained

This formula was originally designed based off of ELO skill ratings used in chess. After each game, a player’s rating goes up or down depending on the opponent’s rating. Beating a higher-rated player than you gives a bigger ELO boost, while losing to a player rated lower than you causes a bigger drop. 

I started by applying the classic Elo rating system to UFC fights, which provided a solid foundation. From there, I modified the formula to account for factors that reflect the quality of a victory (such as early finishes and title fights) and added a decay function to account for inactivity. Once the final structure was in place, I ran a grid search to tune key parameters—like rating sensitivity and decay rate — optimizing the model's prediction accuracy. Here’s exactly how the final formula works:

#### Post-Fight Adjustment Formula
The formula I have created goes through all UFC Fights since UFC 17 in chronological order, and adjusts both fighters' ratings after each fight. For a fighter's first fight in the UFC, they are given a default rating of 300. For each fight in the data, the model calculates the expected win probability using the following formula (for the winner): &nbsp;<br>

&nbsp;&nbsp;&nbsp;&nbsp;*P<sub>L</sub> = 1 / (1 + 10 ** ((R<sub>L</sub> - winner_rating) / 370))* &nbsp;<br>
&nbsp;<br>

The expected win probability of the winner is then used in these formulas to calculate the new ratings: &nbsp;<br>
&nbsp;&nbsp;&nbsp;&nbsp;*winner_new_rating = winner_rating + k * t * m * (1 - expected_win_prob)*(1 + loser_rating/40000)* &nbsp;<br>
&nbsp;&nbsp;&nbsp;&nbsp;*loser_new_rating = loser_rating - k * m * (-1 + expected_win_prob)*(1 - winner_rating/40000)* &nbsp;<br>

k is a constant that is the same for every fight (170). To also give some additional merit to title fights, the variable t was included that gives the winner a 5% ratings boost in a title fight. t was not included for the loser formula.

The variable m adjusts for the method of victory. It scales from a round 1 finish being 1.5 (so a 50% boost to the ratings increase) to being equal to 1 for a three round decision win. For split decicions, m is set to 0.9, as to not give the winning fighter the same boost as when all three judges had them winning.

The (1 - expected_win_prob) part of the formula is the ELO system explained above, so it will scale the changes in ratings based on differences in pre-fight ratings (larger changes for bigger rating gaps).

The final part of the formula - (1 + loser_rating/40000) - gives the winner a larger boost for taking out a highly rated opponent. Unlike the ELO part which is looking at rating differences, this part of the formula would give higher ratings boost to an 800 rated fighter who just defeated another 800 rated fighter than a 300 rated fighter who defeated another 300 rated fighter. The opposite is true for losers; losses to highly rated opponents will be weighted less than losses to low rated opponents.

#### Rating Decay
While the formula above does a good job of capturing fighter merit, they do not account for long periods of inactivity. In order to punish inactivity and remove previous fighters from the rankings, I added a decay function to the rankings model. 

Rating decay does not begin until 270 days since a fighter has fought (about 9 months). When it has been exactly 270 days since a their last fight, a fighter's rating is decreased 3%. Additionally, they are now placed on the decay clock which will decrease their rating another 3% after each 90 days of subsequent inactivity. The only way this decay clock resets is when a fighter participates in a fight (win or lose).


### Future Implementations

While this model does a good job of ranking fighters, there are still some ways I would like to improve it. The next addition I am working on is controlling for weight classes. The difficulty here is that changing weight classes is not always a disadvantage, so I am thinking about only including this for champion vs champion fights (although these are very rare).

On a larger scale, it would be nice to have better ratings for a fighters first UFC fight. This limitation is currently due to data, but I am working on scraping fighter's previous fights before they entered the UFC. With more data, I could potentially expand this model well outside of the UFC which would also give more accurate ratings for fighter's UFC debuts.



