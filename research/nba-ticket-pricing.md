---
layout: page
title: NBA Ticket Pricing Analysis
---

## Result Highlights
Beyond seat location, several external factors significantly increased ticket prices:
- Better & big market opponents (playing the Lakers raised courside ticket prices by over $1,000)
- Availability of Steph Curry (his absence decreased average lower bowl ticket prices by about $15)
- Weekend games & earlier game times (both factors raised lower bowl ticket prices about $40)
- Purchasing further out from the game (gameday ticket prices dropped around $50 on average)

**The following graphics showcase the predicted ticket prices for each seat in an individual game:** &nbsp;<br>

**General Seating:** (Most expensive tickets are red) &nbsp;<br>
<img src="/assets/nba/arena_heatmap.png" alt="Image" width="700"/>  &nbsp;<br>

**Courtside:** (size of seat is predicted price) &nbsp;<br>
<img src="/assets/nba/cs_size_graph.png" alt="Image" width="700"/>  &nbsp;<br>

&nbsp;<br>

## Exploratory Analysis
### External Game Factors
**Opponent:** &nbsp;<br>
Games against high-winning-percentage or big market teams tend to have higher average ticket prices: &nbsp;<br>
<img src="/assets/nba/opps.png" alt="Image" width="700"/>

&nbsp;<br>

**Weekday:** &nbsp;<br>
Ticket prices are highest on weekends (especially Saturdays) and lowest on Mondays and Wednesdays: &nbsp;<br>
<img src="/assets/nba/weekdays.png" alt="Image" width="700"/>

&nbsp;<br>

**Star Player Impact:** &nbsp;<br>
Average ticket prices dropped during the 15 games Steph Curry missed in 2022: &nbsp;<br>
<img src="/assets/nba/curry_22_graph.png" alt="Image" width="600"/>
<img src="/assets/nba/curry_22.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

Curry missed just 5 games in 2023, but those games again saw lower ticket prices: &nbsp;<br>
<img src="/assets/nba/curry_23_graph.png" alt="Image" width="600"/> 
<img src="/assets/nba/curry_23.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>


&nbsp;<br>

**Gametime:** &nbsp;<br>
Most games started at 7:00, but the 25 earlier games (21 at 5:30) saw lower average ticket prices: &nbsp;<br>
<img src="/assets/nba/new_times.png" alt="Image" width="230" style="horizontal-align: center;"/> &nbsp;<br>


&nbsp;<br>

**Time of Purchase:** &nbsp;<br>
Tickets bought further in advance were more expensive, with prices dropping sharply on gameday: &nbsp;<br>
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
I assigned the following sections within the arena based on seat location and club access: &nbsp;<br>
<img src="/assets/nba/new_sections.png" alt="Image" width="600"/> 
<img src="/assets/nba/new_sec_avgs.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

**Courtside & Floor:** &nbsp;<br>
I further split up the floor by side of the court: &nbsp;<br>
<img src="/assets/nba/cs_areas_map.png" alt="Image" width="600"/> 
<img src="/assets/nba/floor_avgs.png" alt="Image" width="130" style="vertical-align: center;"/> &nbsp;<br>

&nbsp;<br>

### Seat Features
**Row:** &nbsp;<br>
Average ticket prices decrease as seat rows get farther from the court: &nbsp;<br>
<img src="/assets/nba/row_avgs_graph.png" alt="Image" width="700"/> &nbsp;<br>
This trend is especially strong in the lower bowl: &nbsp;<br>
<img src="/assets/nba/lb_rows_graph.png" alt="Image" width="700"/> &nbsp;<br>
In the upper bowl, row number has less impact on ticket price: &nbsp;<br>
<img src="/assets/nba/ub_rows.png" alt="Image" width="700"/> &nbsp;<br>

**Front Row Views (FRV):** &nbsp;<br>
Many non–row 1 seats are positioned above tunnels or entrances with no seats in front. I labeled these as “front row view” seats (example below: seats overhanging the player tunnel): &nbsp;<br>
<img src="/assets/nba/frv.jpg" alt="Image" width="600"/> &nbsp;<br>

&nbsp;<br>

**Wheelchair Access (WCA) Areas:** &nbsp;<br>
In the lower bowl, wheelchair-accessible (WCA) seating is specifically located at the back of sections: &nbsp;<br>
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/lb_wca_graph.png" alt="Graph" width="560"/>
  
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 10px;">
    <span>View from seat:</span>
    <img src="/assets/nba/wca_lb_view.jpg" alt="Image" width="180"/>
  </div>
</div> &nbsp;<br>

In the upper bowl, wheelchair-accessible (WCA) seating is located near the front or middle of sections: &nbsp;<br>
<div style="display: flex; align-items: center;">
  <img src="/assets/nba/ub_wca_map.png" alt="Graph" width="560"/>
  
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 10px;">
    <span>View from seat:</span>
    <img src="/assets/nba/wca_ub_view.jpg" alt="Image" width="180"/>
  </div>
</div>


&nbsp;<br>

**Price Graphs With New Rows Created:** &nbsp;<br>
The lower bowl front row view seats have a premium while the WCA seats are not very expensive: &nbsp;<br>
<img src="/assets/nba/lb_rows_graph2.png" alt="Image" width="700"/>  &nbsp;<br>
In the upper bowl, front row view seats are priced similarly to row 1 seats, while WCA sections have the highest average ticket prices.: &nbsp;<br>
<img src="/assets/nba/ub_rows2.png" alt="Image" width="700"/> 

&nbsp;<br>

## Final Models:
Three models were created to model the ticket prices for entire stadium based on the areas defined earlier. Many of the predictors were the same for each model, but each model was adjusted for the factors relevant in its area.
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






