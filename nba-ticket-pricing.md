---
layout: page
title: ""
---
## NBA Ticket Pricing Analysis

As my capstone project for the NBA Future Analytics Stars Program, I developed a predictive model for Chase Center ticket prices.  Using two seasons of Golden State Warriors ticket sales data (provided by the NBA) along with additional external game data, I identified key factors influencing ticket demand and pricing. My project was selected as a finalist in the program’s capstone competition.


## Result Highlights
Beyond seat location, several external factors significantly increased ticket prices:
- Better & big market opponents (playing the Lakers raised courside ticket prices by over $1,000)
- Availability of Steph Curry (his absence decreased average lower bowl ticket prices by about $15)
- Weekend games & earlier game times (both factors raised lower bowl ticket prices about $40)
- Purchasing further out from the game (gameday ticket prices dropped around $50 on average)


The following graphics showcase the predicted ticket prices for each seat in an individual game: &nbsp;<br>

**General Seating:** (Most expensive tickets are red) &nbsp;<br>
<img src="/assets/nba/arena_heatmap.png" alt="Image" width="700"/>  &nbsp;<br>

**Courtside:** (size of seat is predicted price) &nbsp;<br>
<img src="/assets/nba/cs_size_graph.png" alt="Image" width="700"/>  &nbsp;<br>

&nbsp;<br>

## Exploratory Analysis
### External Game Factors
**Opponent:** &nbsp;<br>
Playing big market teams and opponents that win more both lead to higher average ticket prices: &nbsp;<br>
<img src="/assets/nba/opps.png" alt="Image" width="600"/>

&nbsp;<br>

**Weekday:** &nbsp;<br>
Saturday games have the highest prices on average, but there are no other clear trends here: &nbsp;<br>
<img src="/assets/nba/weekdays.png" alt="Image" width="600"/>

&nbsp;<br>

**Star Player Impact:** &nbsp;<br>
Steph Curry missed 15 games in 2022, and the average ticket prices dropped when he was out: &nbsp;<br>
<img src="/assets/nba/curry_22_graph.png" alt="Image" width="600"/>
<img src="/assets/nba/curry_22.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

He did not miss as many games in 2023, but again these games had lower prices: &nbsp;<br>
<img src="/assets/nba/curry_23_graph.png" alt="Image" width="600"/> 
<img src="/assets/nba/curry_23.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>


&nbsp;<br>

**Gametime:** &nbsp;<br>
Most games were played at 7:00 local time. 25 games were played earlier (almost all at 5:30), and the earlier games had lower average ticket prices: &nbsp;<br>
<img src="/assets/nba/new_times.png" alt="Image" width="230" style="horizontal-align: center;"/> &nbsp;<br>


&nbsp;<br>

**Time of Purchase:** &nbsp;<br>
Tickets are more expensive when purchased further out from games. There was a sharp decrease in the price of gameday tickets: &nbsp;<br>
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/days_before_graph.png" alt="Graph" width="600"/>
  
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 10px;">
    <span>Categories:</span>
    <img src="/assets/nba/new_days.png" alt="Image" width="130"/>
  </div>
</div>


&nbsp;<br>

### Stadium Areas
The following sections were deduced with the data provided: &nbsp;<br>
<img src="/assets/nba/new_group.png" alt="Image" width="600"/> 
<img src="/assets/nba/new_group_avgs.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

**Bowl:** &nbsp;<br>
The bowl of the arena was broken down into further sections based on location and club access: &nbsp;<br>
<img src="/assets/nba/new_sections.png" alt="Image" width="600"/> 
<img src="/assets/nba/new_sec_avgs.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

**Courtside & Floor:** &nbsp;<br>
The floor was split up by side of the court: &nbsp;<br>
<img src="/assets/nba/cs_areas_map.png" alt="Image" width="600"/> 
<img src="/assets/nba/curry_23.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

&nbsp;<br>

### Seat Features
**Row:** &nbsp;<br>
As expected, the average ticket price decreases as you go back in rows: &nbsp;<br>
<img src="/assets/nba/row_avgs_graph.png" alt="Image" width="600"/> &nbsp;<br>
This is especially true in the lower bowl: &nbsp;<br>
<img src="/assets/nba/lb_rows_graph.png" alt="Image" width="600"/> &nbsp;<br>
The row trend is not as strong in the upper bowl: &nbsp;<br>
<img src="/assets/nba/ub_rows.png" alt="Image" width="600"/> &nbsp;<br>

**Front Row Views (FRV):** &nbsp;<br>
Many non-row 1 seats overhang tunnels or entrances and have no seats in front of them. I labeled these seats as front row views (Example below of seats overhanging the player tunnel): &nbsp;<br>
<img src="/assets/nba/frv.jpg" alt="Image" width="600"/> &nbsp;<br>

&nbsp;<br>

**Wheelchair Access (WCA) Areas:** &nbsp;<br>
There are WCA (wheelchair access) areas in the arena. These seats are located in the back of sections in the lower bowl: &nbsp;<br>
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/lb_wca_graph.png" alt="Graph" width="560"/>
  
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 10px;">
    <span>View from seat:</span>
    <img src="/assets/nba/wca_lb_view.jpg" alt="Image" width="180"/>
  </div>
</div> &nbsp;<br>

The WCA sections in the upper bowl are located in front of or in the middle of sections: &nbsp;<br>
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/ub_wca_map.png" alt="Graph" width="560"/>
  
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 10px;">
    <span>View from seat:</span>
    <img src="/assets/nba/wca_ub_view.jpg" alt="Image" width="180"/>
  </div>
</div>


&nbsp;<br>

**Graphs of New Rows Created:** &nbsp;<br>
The lower bowl front row view seats have a premium while the WCA seats are not very expensive: &nbsp;<br>
<img src="/assets/nba/lb_rows_graph2.png" alt="Image" width="600"/>  &nbsp;<br>
The upper bowl front row view seats have similar prices to row 1 seats. The WCA seats have the highest average prices in the upper bowl: &nbsp;<br>
<img src="/assets/nba/ub_rows2.png" alt="Image" width="600"/> 

&nbsp;<br>

## Final Models:
Three models were created to model the ticket prices for entire stadium based on the areas broken down earlier. Many of the predictors were the same for each model, but each model was adjusted for the factors relevant in its area.
### Lower Bowl Model:
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/lb_model.png" alt="Image" width="400" style="margin-right: 20px;"/>

  <div>
    <ul style="margin: 0; padding-left: 20px;">
      <li>Sideline club tickets are much more expensive, while general 100 tickets are slightly more expensive than the Pepsi club</li>
      <li>Tickets closer to the center of the court are much more expensive</li>
      <li>Tickets prices drop around $6 every row you go back</li>
      <li>Row 1 tickets are predicted $100 more espensive than  the seat directly behind them</li>
      <li>Front row view seats (not row 1) are predicted $50 more than the seat directly behind them</li>
      <li>Wheelchair areas are the cheapest seats in the lower bowl</li>
    </ul>
  </div>
</div>

&nbsp;<br>

The following graph shows predicted lower bowl prices for a specific game:
<img src="/assets/images/lb_heatmap.png" alt="Image" width="700"/> 

&nbsp;<br>

### Upper Bowl Model:
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/ub_model.png" alt="Image" width="400" style="margin-right: 20px;"/>

  <div>
    <ul style="margin: 0; padding-left: 20px;">
      <li>Upper behind seats are cheaper than upper bowl and upper premium</li>
      <li>Predicted prices decrease as you go closer to the corners of the arena</li>
      <li>Ticket prices drop around $2 every row you go back</li>
      <li>Row 1 seats are predicted to be roughly $11 more than the seat directly behind them</li>
      <li>Front row view seats (not row 1) are predicted $15 more than the seat directly behind them</li>
      <li>Unlike the lower bowl, wheelchair access sections contain the most expensive upper bowl seats</li>
    </ul>
  </div>
</div>

&nbsp;<br>

The following graph shows predicted upper bowl prices while holding external factors constant:
<img src="/assets/nba/ub_heatmap.png" alt="Image" width="700"/> 


### Courtside Model:
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/cs_model.png" alt="Image" width="400" style="margin-right: 20px;"/>

  <div>
    <ul style="margin: 0; padding-left: 20px;">
      <li>True front row seats are predicted to be worth roughly $1800 more than the seat directly behind them</li>
      <li>Predicted prices drop around $600 when going from row BB (true row 2) to A1 (the section behind)</li>
      <li>Tickets in the middle are more expensive (unless sitting behind the baskets)</li>
    </ul>
  </div>
</div>

&nbsp;<br>

Courtside graph (size of seat is predicted price):
<img src="/assets/nba/cs_size_graph.png" alt="Image" width="700"/> 

### Other Model Takeaways:
All three models back up the earlier findings regarding external game factors:
- Better & bigger market opponents lead to higher prices
- Prices are higher in games where Steph Curry plays
- Friday & Saturday games are the most expensive
- Games before 7:30 are more expensive
- Tickets get cheaper as the event approaches

&nbsp;<br>
## Materials:
[Full Write Up](https://oconnellryan.github.io/assets/fas-capstone.pdf) &nbsp;<br>
[Code (R Markdown)](https://oconnellryan.github.io/assets/nba/nba_ticket_pricing.Rmd) &nbsp;<br>






