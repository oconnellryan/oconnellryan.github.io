---
layout: page
title: UFC Rankings Formula
---

#### Why These Rankings?

The official UFC rankings are often influenced more by promotion than performance. Voted on by an unkown media panel they can reflect hype, star power, and marketing priorities over merit. Fighters with UFC favor often receive fast-track opportunities, while others are stalled despite consistent wins. This is why an I have created an unbiased ranking formula that ranks fighters based on merit.


#### The Rankings Formula

This formula was originally designed based off of ELO ratings used in chess. In chess, the Elo system assigns each player a rating that reflects their skill level. After each game, a player’s rating goes up or down depending on the opponent’s rating and the match outcome—beating a higher-rated player gives a bigger boost, while losing to a lower-rated player causes a bigger drop.

The fighter rankings I have created work very similary. The formula goes through all UFC Fights since UFC 17 in chronological order, and adjusts both fighter ratings after each fight. If a fighter has not fought in the UFC, they are given a default rating (). For each fight in the data, the model calculates the expected win probability using the following formula (for the winner): &nbsp;<br>
     expected_win_prob = 1 / (1 + 10 ** ((loser_rating - winner_rating) / s)) &nbsp;<br>
&nbsp;<br>

The expected win probability of the winner is then used in this formula to calculate the new rating of the winner: &nbsp;<br>
     winner_new_rating = winner_rating + k * m * t * (1 - expected_win_prob)*(1 + loser_rating/40000) &nbsp;<br>
     loser_new_rating = loser_rating + k * m * (0 - expected_loser*(1 - winner_rating/40000)) &nbsp;<br>
  &nbsp;<br>

The final part of the formula - (1 + loser_rating/40000) - gives the winner a larger boost for taking out a highly rated opponent. So  this part of the formula would give higher ratings boost to am 800 rated fighter who just defeated another 800 rated fighter than a 300 rated fighter who defeated another 300 rated fighter. k is a constant the same for every fight.

There are two more variables in the new fighter ratings formula: t and m. t stands for title fight, and simply gives the winner rating boost a 5% increase if it is a tile fight (t is not present in the loser ratings adjustment formula).

The variable m adjusts for the method of victory. It scales from a round 1 finish being 1.5 (so a 50% boost to the ratings increase) to 1 for a 3 round decision win. For split decicions, this is set to 0.9, as to not give the winning fighter the same boost as when all three judges had them winning.

