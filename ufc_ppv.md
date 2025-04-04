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


[Read Full Paper](https://oconnellryan.github.io/assets/ufc_ppv_modeling.pdf) &nbsp;<br>


