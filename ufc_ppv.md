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


