---
layout: page
title: ""
---
## NBA Ticket Pricing Analysis

As my capstone project for the NBA Future Analytics Stars Program, I developed a predictive model for Chase Center ticket prices.  Using two seasons of Golden State Warriors ticket sales data (provided by the NBA) along with additional external game data, I identified key factors influencing ticket demand and pricing. My project was selected as a finalist in the program’s capstone competition.


## Result Highlights
The following graphic showcases the predicted ticket prices for each seat in an individual game scaling from lowest (red) to the highest prices tickets (green):
![Image](/assets/nba/arena_heatmap.png)

&nbsp;<br>

## Exploratory Analysis
### External Game Factors
**Opponent:** &nbsp;<br>
Opponents Matter. Playing big market teams and a higher opponent winning percentage both lead to higher average ticket prices:
![Image](/assets/nba/opps.png)

&nbsp;<br>

**Weekday:** &nbsp;<br>
Saturday games have the highest prices on average. However, there is not an overly clear trend regarding weekends:
![Image](/assets/nba/weekdays.png)

&nbsp;<br>

**Star Players:** &nbsp;<br>
Steph Curry missed 15 games in 2022, and we can see the average ticket prices dropped quickly in the periods he missed games due to injury:
![Image](/assets/nba/curry_22_graph.png)
<img src="/assets/nba/curry_22.png" alt="Image" width="200"/> &nbsp;<br>

He did not miss as many games in 2023, but again these games had lower prices:
![Image](/assets/nba/curry_23_graph.png)
<img src="/assets/nba/curry_23.png" alt="Image" width="200"/> &nbsp;<br>

&nbsp;<br>

**Gametime:** &nbsp;<br>
Most games were played at 7:00 local time. 25 games were played earlier (21 of the 25 earlier games were played at 5:30). The earlier games had lower prices on average: &nbsp;<br>
<img src="/assets/nba/new_times.png" alt="Image" width="200"/> &nbsp;<br>


&nbsp;<br>

**Time of Purchase:** &nbsp;<br>
Tickets are more expensive when purchased further out from games. There is a sharp drop off in the price of gameday tickets: &nbsp;<br>
![Image](/assets/nba/days_before_graph.png)
Days purchased before game were split into the following categories for modeling: &nbsp;<br>
<img src="/assets/nba/new_days.png" alt="Image" width="200"/> &nbsp;<br>

&nbsp;<br>

### Stadium Areas
The following sections were deduced with the data provided: &nbsp;<br>
![Image](/assets/nba/new_group.png)
<img src="/assets/nba/new_group_avgs.png" alt="Image" width="200"/> &nbsp;<br>

**Bowl:** &nbsp;<br>
The bowl of the arena was broken down into further sections based on location and club access: &nbsp;<br>
<img src="/assets/nba/new_sections.png" alt="Image" width="560"/> 
<img src="/assets/nba/new_sec_avgs.png" alt="Image" width="160"/> &nbsp;<br>

**Courtside & Floor:** &nbsp;<br>
The floor was split up by side: &nbsp;<br>
![Image](/assets/nba/cs_areas_map.png)
<img src="/assets/nba/curry_23.png" alt="Image" width="200"/> &nbsp;<br>

### Seat Features
**Row:** &nbsp;<br>
As expected, the average ticket price decreases as you go back in rows: &nbsp;<br>
![Image](/assets/nba/row_avgs_graph.png)
This is especially true in the lower bowl:
![Image](/assets/nba/lb_rows_graph.png)
The trend is not as strong in the upper bowl:
![Image](/assets/nba/ub_rows.png)

**Front Row Views (FRV):** &nbsp;<br>
Many non-row 1 seats overhang tunnels or entrances and have no seats in front of them. These seats were labeled as front row views (Example below of seats overhanging the player tunnel): &nbsp;<br>
![Image](/assets/nba/frv.jpg)

&nbsp;<br>

**Wheelchair Access (WCA) Areas:** &nbsp;<br>
There are WCA (wheelchair access) areas in the arena. These seats are located in the back of sections in the lower bowl: &nbsp;<br>
&nbsp;<br>
<img src="/assets/nba/lb_wca_graph.png" alt="Image" width="800"/> &nbsp;<br>
View from seat: &nbsp;<br>
<img src="/assets/nba/wca_lb_view.jpg" alt="Image" width="200"/> &nbsp;<br>
<br style="clear:both" />
The WCA sections in the upper bowl are located in front of or in the middle of sections: &nbsp;<br>
<img src="/assets/nba/ub_wca_map.png" alt="Image" width="500"/> &nbsp;<br>
View from seat: 
<img src="/assets/nba/wca_ub_view.jpg" alt="Image" width="200"/> &nbsp;<br>


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
- Better & big market opponents lead to higher prices
- Prices are higher in games where Steph Curry plays
- Friday & Saturday games are the most expensive
- Tickets get cheaper as an event approaches

&nbsp;<br>

The following graph shows predicted lower bowl prices for a specific game:
![Image](/assets/images/lb_heatmap.png)

Findings specific to lower bowl:
- Sideline club tickets are much more expensive, while general 100 tickets are slightly more expensive than the Pepsi club
- Tickets closer to the center of the court are much more expensive
- Tickets prices drop around $6 every row you go back
- Row 1 tickets are predicted $100 more espensive than  the seat directly behind them
- Front row view seats (not row 1) are predicted $50 more than the seat directly behind them
- Wheelchair areas are the cheapest seats in the lower bowl

### Upper Bowl:
A seperate model was created for the upper bowl:
![Image](/assets/nba/ub_model.png)
The following graph shows predicted upper bowl prices while holding external factors constant:
![Image](/assets/nba/ub_heatmap.png)

Findings specific to upper bowl:
- Upper behind seats are cheaper than upper bowl and upper premium
- Predicted prices decrease as you go closer to the corners of the arena
- Ticket prices drop around $2 every row you go back
- Row 1 seats are predicted to be roughly $11 more than the seat directly behind them
- Front row view seats (not row 1) are predicted $15 more than the seat directly behind them
- Unlike the lower bowl, wheelchair access sections contain the most expensive upper bowl seats

### Courtside:

Finally, a courtside model was created:
![Image](/assets/nba/cs_model.png)
Courtside graph (size of seat is predicted price):
![Image](/assets/nba/cs_size_graph.png)
Key takeaways:
- True front row seats are predicted to be worth roughly $1800 more than the seat directly behind them
- Predicted prices drop around $600 when going from row BB (true row 2) to A1 (the section behind)
- Tickets in the middle are more expensive (unless sitting behind the baskets)


## Materials:
[Full Write Up](https://oconnellryan.github.io/assets/fas-capstone.pdf) &nbsp;<br>
[Code (R Markdown)](https://oconnellryan.github.io/assets/nba/nba_ticket_pricing.Rmd) &nbsp;<br>






