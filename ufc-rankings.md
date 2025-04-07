---
layout: page
title: ""
---

### Why This Formula?

The UFC rankings are a key part of the sport’s ecosystem, but as with any system influenced by human voting they can be shaped by perception and promotional dynamics. To offer an alternative lens, I created an objective rankings model that evaluates fighters purely on results and quantifies fighter stock in a consistent, data-driven way.

### Explore The Rankings:
Use the interactive tool below to browse my updated rankings. These are updated automatically after each event and reflect results, opponent strength, and recent activity — not media perception.

<iframe 
  src="https://ryanoconnell.shinyapps.io/rankings/"
  width="50%" 
  height="550" 
  style="border:none;">
</iframe>


### My Rankings Formula Explained:

This formula was originally designed based off of ELO skill ratings used in chess. After each game, a player’s rating goes up or down depending on the opponent’s rating. Beating a higher-rated player than you gives a bigger ELO boost, while losing to a player rated lower than you causes a bigger drop. 

I started by applying the classic ELO rating system to UFC fights, which provided a solid foundation. From there, I modified the formula to account for factors that reflect the quality of a victory (such as early finishes and title fights) and added a decay function to account for inactivity. Once the final structure was in place I ran a grid search to tune key parameters like rating sensitivity and decay rate, optimizing the model's prediction accuracy.

### Post-Fight Adjustment Formula:
The formula I have created goes through all UFC Fights since UFC 17 in chronological order, and adjusts both fighters' ratings after each fight. For a fighter's first fight in the UFC, they are given a default rating of 300. For each fight in the data, the model calculates the expected win probability using the following formulas for the winner and loser: &nbsp;<br>

&nbsp;&nbsp;&nbsp;&nbsp;*WinProb<sub>W</sub> = 1 / (1 + 10 <sup>(Rating<sub>L</sub> - Rating<sub>W</sub>) / 370</sup>)* &nbsp;<br>
&nbsp;&nbsp;&nbsp;&nbsp;*WinProb<sub>L</sub> = 1 / (1 + 10 <sup>(Rating<sub>W</sub> - Rating<sub>L</sub>) / 370</sup>)* &nbsp;<br>
&nbsp;<br>

The expected win probabilities are then used in these formulas to calculate the new fighter ratings: &nbsp;<br>
&nbsp;<br>
&nbsp;&nbsp;&nbsp;&nbsp;*NewRating<sub>W</sub> = Rating<sub>W</sub> + 170 × Title × Method × (1 - WinProb<sub>W</sub>) × (1 + <sup>Rating<sub>L</sub></sup>&frasl;<sub>40000</sub>)* &nbsp;<br>
&nbsp;&nbsp;&nbsp;&nbsp;*NewRating<sub>L</sub> = Rating<sub>L</sub> - 170 × Method × (-1 + WinProb<sub>L</sub>) × (1 - <sup>Rating<sub>W</sub></sup>&frasl;<sub>40000</sub>)* &nbsp;<br>


To account for the added significance of title fights, the variable Title applies a 5% bonus to the winner’s rating change after title wins.

The Method variable adjusts the rating impact based on how the fight was won or lost. A first-round finish sets Method = 1.5, giving a 50% boost to the rating change, while a standard three-round decision results in Method = 1.0. For split decisions, Method = 0.9 to reflect the uncertainty of the outcome.

The *(1 - WinProb)* part of the formula is the ELO system explained earlier, so it will scale the changes in ratings based on differences in pre-fight ratings (larger changes for bigger rating gaps).

The final part of the formula (1 - <sup>Rating<sub>W</sub></sup>&frasl;<sub>40000</sub>) gives bigger boosts for beating strong opponents and smaller penalties for losing to them. It doesn't look at the rating difference, but instead scales by the opponent's overall strength. So beating an elite fighter means more than beating someone average, and losing to a top fighter hurts less because of this part.

### Rating Decay:
While the formula above does a good job of capturing fighter merit, it does not account for long periods of inactivity. To address this, a decay function was added to penalize inactivity and gradually remove inactive fighters from the rankings.

Rating decay begins 270 days (approximately 9 months) after a fighter’s most recent bout. At that point, their rating is reduced by 3%. Once on the decay clock, a fighter's rating continues to decrease by an additional 3% every 90 days of further inactivity. The decay clock is fully reset whenever the fighter competes again, regardless of outcome.

### Future Implementations:

While this model provides a strong foundation for ranking fighters, there are still several areas I plan to improve. The next addition I’m exploring is incorporating weight class adjustments.

The main challenge is that changing weight classes isn’t always a disadvantage; fighters may move up or down and still perform at a high level. Because of this, I’m considering applying weight class adjustments only in rare cases, such as champion vs. champion matchups, where the implications of weight differences are most significant.

On a larger scale, one of the model’s current limitations is the lack of ratings for a fighter’s UFC debut due to data limitations. However, I’m currently working on scraping fight records from before a fighter’s UFC career. With this expanded dataset, the model could not only provide more accurate debut ratings but also potentially scale beyond the UFC, allowing for a more comprehensive global ranking system.



