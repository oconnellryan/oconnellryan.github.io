---
layout: page
---
This project identified some of the factors most relevant to UFC pay per view sales, as well as identified random effects for how much each fighter contributed to Pay-Per-View Sales based on card placement. 

### Result highlights:
The tool below uses my final model to estimate the predicted PPV buys for a custom UFC card: &nbsp;<br>

<div style="display: flex; justify-content: center;">
  <div style="width: 614px; height: 536px; overflow: hidden;">
    <iframe 
      src="https://ryanoconnell.shinyapps.io/ppv_app/"
      style="border: none; transform: scale(0.8); transform-origin: top left; width: 768px; height: 670px;">
    </iframe>
  </div>
</div>



##### Some of the key factors that lead to increased Pay-Per-View Sales were:
 - Higher quality fighters (calculated by performance ratings) across the entire card was correlated with an increased Buyrate.
 - Finishing opponents: each finish was found to increase a main event fighter's draw power by about 7,000 buys.
 - Title fight wins & losses were also found to be impactful for both main event & non-main event fighters.
   - Title fight wins for any fighter on the card lead to a higher buyrate on average (ranging from about 3,000 increased buys for main event fighters to 400 increased buys for lower on the card).
   - Title fight losses were highly impactful, especially for main event fighters. A loss in a title fight reduces a main fighter's predicted draw power by about 25,000 buys.
  

### Full Variable Analysis

#### Fighter Strength
Obviously, one would suspect that having better fighters on a card leads to higher Pay-Pey-View sales. To capture fighter strength, I will utilize the Fighter Performance Ratings (FPR) formula I have created which I explain in detail here. The following graph shows the relationship between the combined FPR of the main event fighters and the PPV Buyrate:
![Image](/assets/nba/opps.png) &nbsp;<br>
As expected, there’s a clear positive relationship: higher-rated main event fighters tend to drive more PPV buys.


[Read Full Paper](https://oconnellryan.github.io/assets/ufc_ppv_modeling.pdf) &nbsp;<br>


