---
layout: page
title: NBA Ticket Pricing
---
In this project I created a predictive model of NBA ticket prices. 2 seasosns of Warriors ticket sales data as well as external game data including opponents and injuries were used for this analysis.


## Result Highlights
The following graphic showcases the predicted ticket prices for each seat in an individual game:
![Image](/assets/nba/arena_heatmap.png)

&nbsp;<br>

## Exploratory Analysis
### External Game Factors
**Opponent:** &nbsp;<br>
Opponents Matter. Playing big market teams and a higher opponent winning percentage both lead to higher average ticket prices:
![Image](/assets/nba/opps.png)

&nbsp;<br>

**Weekday:** &nbsp;<br>
Saturday games have the highest prices on average:
![Image](/assets/nba/weekdays.png)

&nbsp;<br>

**Star Players:** &nbsp;<br>
Steph Curry missed 15 games in 2022, and we can see the average ticket prices dropped quickly in the periods he missed games due to injury:
![Image](/assets/nba/curry_22_graph.png)
![Image](/assets/nba/curry_22.png){: width="200" }

He did not miss as many games in 2023, but again these games had lower prices:
![Image](/assets/nba/curry_23_graph.png)
![Image](/assets/nba/curry_23.png){: width="200" }

&nbsp;<br>

**Gametime:** &nbsp;<br>
Most games were played at 7:00 local time. 25 games were played earlier, with 21 of these being played at 5:30. The earlier games had lower prices on average: &nbsp;<br>
![Image](/assets/nba/new_times.png){: width="200" }

&nbsp;<br>

**Time of Purchase:** &nbsp;<br>
Tickets are more expensive when purchased further out from games. There is a sharp drop off in the price of gameday tickets:
![Image](/assets/nba/days_before_graph.png)
Days purchased before game were split into the following categories for modeling:
![Image](/assets/nba/new_days.png){: width="200" }

&nbsp;<br>

### Stadium Areas
The following sections were deduced with the data provided:
![Image](/assets/nba/new_group.png)
![Image](/assets/nba/new_group_avgs.png){: width="200" }

**Bowl:** &nbsp;<br>
The bowl of the arena was broken down into further sections based on location and club access:
![Image](/assets/nba/new_sections.png)
![Image](/assets/nba/new_sec_avgs.png){: width="200" }

**Courtside & Floor:** &nbsp;<br>
The floor was split up by side:
![Image](/assets/nba/cs_areas_map.png)
![Image](/assets/nba/cs_avgs.png){: width="150" }

### Seat Features
**Row:** &nbsp;<br>
The average ticket price decreases as you go back in rows:
![Image](/assets/nba/row_avgs_graph.png)
This is especially true in the lower bowl:
![Image](/assets/nba/lb_rows_graph.png)
![Image](/assets/nba/ub_rows.png)

**Front Row Views (FRV):** &nbsp;<br>
Many non-row 1 seats overhang tunnels or entrances and have no seats in front of them. These seats were labeled as front row views (Example below of seats overhanging the player tunnel):
![Image](/assets/nba/frv.jpg)

&nbsp;<br>

**Wheelchair Access (WCA) Areas:** &nbsp;<br>
There are WCA (wheelchair access) areas in the arena. These seats are located in the back of sections in the lower bowl: &nbsp;<br>
![Image](/assets/nba/lb_wca_map.png){: width="525" ; style="float: left" }
View from seat: ![Image](/assets/nba/wca_lb_view.jpg){: width="200" } 
<br style="clear:both" />
The WCA sections in the upper bowl are located in front of or in the middle of sections: &nbsp;<br>
![Image](/assets/nba/ub_wca_map.png){: width="500" ; style="float: left" } 
View from seat: ![Image](/assets/nba/wca_ub_view.jpg){: width="200" }


&nbsp;<br>

**Graphs of New Rows Created:** &nbsp;<br>
The front row view seats appear to have a premium while the WCA seats are not very expensive in the lower bowl:
![Image](/assets/nba/lb_rows_graph2.png)
The front row view seats have an average price around the same as row 1 seats in the upper bowl. The upper bowl WCA seats have the highest average prices in the upper bowl:
![Image](/assets/nba/ub_rows2.png)

&nbsp;<br>

## Modeling
### Lower Bowl:
The following model predicts ticket prices for seats in the lower bowl:
![Image](/assets/nba/lb_model.png)
The model backs up the earlier findings regarding external game factors:
- Better & large market opponents lead to higher prices
- Prices are higher in games where Curry plays
- Friday & Saturday games are the most expensive
- Tickets get cheaper as an event approaches

&nbsp;<br>

The following graph shows predicted lower bowl prices while holding external factors constant:
![Image](/assets/nba/lb_heatmap.png)

Specific to lower bowl:
- Sideline club tickets are much more expensive, while general 100 tickets are slightly more expensive than the Pepsi club
- Tickets closer to the center of the court are much more expensive
- Tickets prices drop around $6 when you go back a row
- Row 1 tickets are predicted $100 more espensive than  the seat behind them
- Front row view seats are predicted $50 more than the seat behind them
- Wheelchair areas are the cheapest seats in the lower bowl

### Upper Bowl:
A seperate model was created for the upper bowl:
![Image](/assets/nba/ub_model.png)
The following graph shows predicted upper bowl prices while holding external factors constant:
![Image](/assets/nba/ub_heatmap.png)

Findings specific to upper bowl:
- Upper behind seats are cheaper than upper bowl and upper premium
- Predicted prices decrease as you go closer to the corners
- Ticket prices drop around $2 when you go back a row
- Row 1 seats are predicted to be roughly $11 more than the seat behind them
- Front row view seats are predicted $15 more than the seat behind them
- Wheelchair access sections are the most expensive upper bowl seats

### Courtside:

Finally, a courtside model was created:
![Image](/assets/nba/cs_model.png)
Courtside graph (size of seat is predicted price):
![Image](/assets/nba/cs_size_graph.png)
Key takeaways:
- True front row seats are predicted to be worth roughly $1800 more than the seat behind them
- Predicted prices drop around $600 when going from row BB (true row 2) to A1 (the section behind)
- Tickets in the middle are more expensive when not sitting behind the basket


## Materials:
[Full Write Up](https://oconnellryan.github.io/assets/nba/ryan_oconnell-fas_capstone.pdf) &nbsp;<br>
[Full Code (R Markdown)](https://oconnellryan.github.io/assets/nba/nba_ticket_pricing.Rmd) &nbsp;<br>
The data for this project cannot be shared






