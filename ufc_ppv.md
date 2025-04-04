---
layout: page
---
This project identified some of the factors most relevant to UFC pay per view sales, as well as identified random effects for how much each fighter contributed to Pay-Per-View Sales based on card placement. 

## Result highlights:
The tool below allows you to build a custom UFC card and uses my model to predict the Pay-Per-View Sales: &nbsp;<br>

<div style="display: flex; justify-content: center;">
  <div style="width: 614px; height: 536px; overflow: hidden;">
    <iframe 
      src="https://ryanoconnell.shinyapps.io/ppv_app/"
      style="border: none; transform: scale(0.8); transform-origin: top left; width: 768px; height: 670px;">
    </iframe>
  </div>
</div>



#### Some of the key factors that lead to increased Pay-Per-View Sales were:
 - Higher quality fighters (calculated by performance ratings) across the entire card was correlated with an increased Buyrate.
 - Finishing opponents: each finish was found to increase a main event fighter's draw power by about 7,000 buys.
 - Title fight wins & losses were also found to be impactful for both main event & non-main event fighters.
   - Title fight wins for any fighter on the card lead to a higher buyrate on average (ranging from about 3,000 increased buys for main event fighters to 400 increased buys for lower on the card).
   - Title fight losses were highly impactful, especially for main event fighters. A loss in a title fight reduces a main fighter's predicted draw power by about 25,000 buys.
  

## Full Variable Analysis

#### Fighter Strength
Obviously, one would suspect that having better fighters on a card leads to higher Pay-Pey-View sales. To capture fighter strength, I will utilize the Fighter Performance Ratings (FPR) formula I have created which I explain in detail here. The following graph shows the relationship between the combined FPR of the main event fighters and the PPV Buyrate: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/main_fpr_buyrate.png" alt="Image" width="600"/>
</p>
As expected, there’s a clear positive relationship: higher-rated main event fighters tend to drive more PPV buys.

This raises a follow up question of how much the strength of the rest of the card matters? The following graph examines this by showcasing the total FPR of all non-main event fighters and the PPV Buyrate: &nbsp;<br>
<p style="text-align: center;">
  <img src="/assets/ufc/rest_fpr_buyrate.png" alt="Image" width="600"/>
</p>
Interestingly, this relationship appears even stronger. This suggests that fans may evaluate the full card, not just the main event, when deciding whether to purchase a PPV.

#### Previous Title Fight Results
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


[Read Full Paper](https://oconnellryan.github.io/assets/ufc_ppv_modeling.pdf) &nbsp;<br>


