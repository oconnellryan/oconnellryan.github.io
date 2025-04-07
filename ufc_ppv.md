---
layout: page
title: ""
---

## UFC Pay-Per-View Sales Analysis:
The goal of this project was to identify key fighter attributes that significantly influence UFC Pay-Per-View (PPV) sales and to quantify the incremental PPV value that each individual fighter contributes to an event. Originally developed as a class paper, the project has since been expanded and refined with improved methodologies including enhanced feature engineering, model selection, and the use of fixed and random effects to separate brand value from fighting style.

### Result highlights:
The tool below allows you to build a custom UFC card and predict the Pay-Per-Views using the model. This model uses a combination of fighter attributes found significant and the individual effects calculated for each fighter: &nbsp;<br>

<div style="display: flex; justify-content: center;">
  <div style="width: 614px; height: 536px; overflow: hidden;">
    <iframe 
      src="https://ryanoconnell.shinyapps.io/ufc_ppv_predictor/"
      style="border: none; transform: scale(0.8); transform-origin: top left; width: 768px; height: 670px;">
    </iframe>
  </div>
</div>

**Some of the key factors that were found to impact Pay-Per-View Sales:**
 - Higher quality fighters across the entire card was correlated with an increased sales.
 - Each finish on a main event fighter's record was found to increase PPV Buy Rate by about 7,000
 - Title fight wins & losses were also found to be impactful:
   - Title fight wins for any fighter on the card lead to a higher Buy Rate on average.
   - Title fight losses were particularly hurtful to main event fighters: Each one reduces predicted draw power by about 25,000 buys.
&nbsp;<br>

### Data & Methodology Overview
Pay-Per-View buy rate data was sourced from Tapology, covering 210 UFC events through UFC 274. The dataset was filtered to include events from UFC 57 (2006) onward, ensuring relevance to the modern UFC era. Within this timeframe, 32 events lacked available PPV data. The model developed in this project is specifically designed to predict PPV buy rates for events within this modern-era range.

Fighter data from UFC Stats provided detailed fight outcomes, title fight indicators, and fight-level statistics. Various fighter metrics were tested, with the most relevant ones included in the model.

A custom formula I created that adjust ratings after each fight based on quality of opponent was also used to capture fighter quality. You can read more about how this formula works [here](https://oconnellryan.github.io/ufc-rankings.html). For this PPV analysis, I utilized a modified version of this FPR formula that does not give fighters boosts for finishes or title fight wins.

### Full Variable Analysis

#### Fighter Strength:
Obviously, one would suspect that having better fighters on a card leads to higher Pay-Pey-View sales. I will use my Fighter Performance Ratings (FPR) to examine this. The following graph shows the relationship between the combined FPR of the main event fighters and the Pay-Per-View Buyrate: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/main_fpr_buyrate.png" alt="Image" width="600" style="display: block; margin: auto;"/>
</p>
As expected, there’s a clear positive relationship: higher-rated main event fighters tend to drive more PPV buys.

This raises a follow up question of how much the strength of the rest of the card matters? The following graph examines this by showcasing the total FPR of all non-main event fighters and the PPV Buyrate: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/rest_fpr_buyrate.png" alt="Image" width="600"/>
</p>
Interestingly, this relationship appears even stronger. This suggests that fans may evaluate the full card, not just the main event, when deciding whether to purchase a Pay-Per-View.

#### Previous Title Fight Results:
**Title Fight Wins:** &nbsp;<br>
Fighters who defend the belt multiple times in a row get the pportunity to build lasting name recognition and fan loyalty. The next graph shows the average PPV Buyrate by the total number of title wins among main event fighters: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/main_title_buyrate.png" alt="Image" width="600"/>
</p>
Main event fighters who have won on the big state multiple times clearly seem to generate more Pay-Per-View sales.

What about the rest of the card? The following graph examines the same relationship for all non-main event fighters: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/rest_title_buyrate.png" alt="Image" width="600"/>
</p>
This relationship is very strong as well, again suggesting that higher level fighters (particularly those who have won titles before) generate more Pay-Per-View buys, even when not placed in the main event. 

**Title Fight Losses:** &nbsp;<br>
If a fighter's value rises after winning a title fight, this raises the question of what happens to fighters ability to generate PPV sales after taking title fight losses. This graph examines the relationship between title fight losses by main event fighters and PPV Buyrate: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/main_title-l_buyrate.png" alt="Image" width="600"/>
</p>
There’s no clear relationship. Title fight losses do not appear to hurt a main event fighter’s ability to sell PPVs, though it’s also possible the effect is obscured by other variables.

Looking at the same relationship for the rest of the main card, we can actually see a positive trend: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/rest_title-l_buyrate.png" alt="Image" width="600"/>
</p>
So losses in title fights do not appear to have a negative impact on non-main event fighters. However, it is important to remember that most of the demand is driven by the main event and if a fighter was fighting for a title they were likely in a main event. So this positive relationship likely does not mean that a fighter's value increases after a title fight loss, but suggests they likely still have relatively high value on the rest of the main card.

#### Finishes:
It is also to be expected that fighters who finish their opponents are likely to sell more pay pey views. The following graph examines this relationship for Main Event fighters by examining the combined number of finishes between the two fighters related to PPV Buyrate: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/main_finish_buyrate.png" alt="Image" width="600"/>
</p>
The graph certainly suggest that fighters who finish their opponents tend to generate higher Pay-Per-View sales.

Let’s check whether this also holds for the rest of the card: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/rest_finish_buyrate.png" alt="Image" width="600"/>
</p>
While not quite as strong as a relationship as the main event fighters, we can again see that the other fighters on the card having more finishes is positively correlated with Buyrate.
&nbsp;<br>

### Final Model Results:
#### Fighter Attributes (Main & Interraction Effects):
The graph below displays the coefficient values for main effects (blue) and interaction effects (red). The blue bars represent the general impact of each fighter attribute on PPV buys, regardless of card placement. The red bars indicate how the importance of these attributes changes specifically for fighters higher on the card (interaction effects).
<p style="text-align: center;">
  <img src="/assets/ufc/coef_graph.png" alt="Image" width="600"/>
</p>
The results align closely with the initial analysis. Fighter quality and having finished past opponents influences PPV buy rates across all card placements. However, past title fight outcomes (both wins and losses) have a much stronger impact on PPV buys for fighters in main-event positions.

&nbsp;<br>

[View Class Research Paper (April 2023)](https://oconnellryan.github.io/assets/ufc_ppv_modeling.pdf) &nbsp;<br>


