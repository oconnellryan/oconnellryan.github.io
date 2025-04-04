---
layout: page
---
This project identified some of the factors most relevant to UFC pay per view sales, as well as identified random effects for how much each fighter contributed to Pay-Per-View Sales based on card placement. 

### Result highlights:
The tool below uses my final model to estimate the predicted PPV buys for a custom UFC card: &nbsp;<br>

<div style="width: 100%; display: flex; justify-content: center;">
  <div style="transform: scale(0.8); transform-origin: top left; overflow: hidden; width: fit-content;">
    <iframe 
      src="https://ryanoconnell.shinyapps.io/ppv_app/"
      width="768" 
      height="670" 
      style="border: none;">
    </iframe>
  </div>
</div>

##### Some of the key factors that lead to increased Pay-Per-View Sales were:
 - Higher quality fighters (calculated by performance ratings) across the entire card was correlated with an increased Buyrate.
 - Finishing opponents: each finish was found to increase a main event fighter's draw power by about 7,000 buys.
 - Title fight wins & losses were also found to be impactful for both main event & non-main event fighters.
   - Title fight wins for any fighter on the card lead to a higher buyrate on average (ranging from about 3,000 increased buys for main event fighters to 400 increased buys for lower on the card).
   - Title fight losses were highly impactful, especially for main event fighters. A loss in a title fight reduces a main fighter's predicted draw power by about 25,000 buys.






People decide whether to buy a UFC card based almost entirely on the quality of the main event. Champions with high fighting output sell more cards. Specifically, this means they do the folowing in their fights:
 - Land a high amount of strikes per minute
 - Knock down their opponents
 - Gain control time of their opponent

Aside from these fighting attributes of the champion, the following also lead to more pay per view sales:
 - More title defenses for a champion
 - A challenger who has won title fights before
 - Three title fights stakced on a card (cards with 2 did not see much of an increase)

Fans are more likely to buy cards with main events in these weight classes:
 - Lightweight
 - Welterweight
 - Women's Bantamweight

A light heavyweight main event has lead to the worst pay per view sales

[Read Full Paper](https://oconnellryan.github.io/assets/ufc_ppv_modeling.pdf) &nbsp;<br>


