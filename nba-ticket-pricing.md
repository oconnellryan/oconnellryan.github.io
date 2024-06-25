---
layout: page
title: NBA Ticket Pricing
---
In this project I created a predictive model of NBA ticket prices. 2 seasosns of Warriors ticket sales data as well as external game data including opponents and injuries were used for this analysis.


## Result Highlights
The following graphic showcases the predicted ticket prices for each seat in an individual game:
![Image](/assets/nba/arena_heatmap.png)

### Exploratory Analysis
**External Game Factors:** &nbsp;<br>
Opponents Matter. Playing big market teams and a higher opponent winning percentage both lead to higher average ticket prices:
![Image](/assets/nba/opps.png)

&nbsp;<br>

Saturday games have the highest prices on average:
![Image](/assets/nba/weekdays.png)

&nbsp;<br>

Steph Curry missed 15 games in 2022, and we can see the average ticket prices dropped quickly in the periods he missed games due to injury:
![Image](/assets/nba/curry_22_graph.png)
![Image](/assets/images/curry_22.png){: width="200" }
He did not miss as many games in 2023, but again these games had lower prices:
![Image](/assets/nba/curry_23_graph.png)
![Image](/assets/nba/curry_23.png){: width="200" }

&nbsp;<br>

Most games were played at 7:00 local time. 25 games were played earlier, with 21 of these being played at 5:30. The earlier games had lower prices on average:
![Image](/assets/nba/times.jpeg){: width="200" }

&nbsp;<br>

Tickets are more expensive when purchased further out from games. There is a sharp drop off in the price of gameday tickets:
![Image](/assets/nba/days_before_graph.png)
Days purchased before game were split into the following categories for modeling:
![Image](/assets/nba/new_days.png)

&nbsp;<br>

**Stadium Areas:** &nbsp;<br>
The following categories were created with the data provided:
![Image](/assets/nba/new_group.png)
![Image](/assets/nba/new_group_avgs.png){: width="200" }

The bowl of the arena was broken down into further sections based on location and club access:
![Image](/assets/nba/new_sections.png)
![Image](/assets/nba/new_sec_avgs.png){: width="200" }



The floor was split up by side:
![Image](/assets/nba/cs_areas_map.png)
![Image](/assets/nba/cs_avgs.png){: width="150" }

**Seat Features:** &nbsp;<br>
The average ticket price decreases as you go back in rows:
![Image](/assets/nba/row_avgs_graph.png)
This is especially true in the lower bowl:
![Image](/assets/nba/lb_rows_graph.png)
![Image](/assets/nba/ub_rows_graph.png)


Many non-row 1 seats overhang tunnels or entrances and have no seats in front of them. These seats were labeled as front row views (Example below of seats overhanging the player tunnel):
![Image](/assets/images/frv.jpg)

&nbsp;<br>

There are WCA (wheelchair access) areas in the arena. These seats are located in the back of sections in the lower bowl: &nbsp;<br>
![Image](/assets/nba/lb_wca_map.png){: width="525" ; style="float: left" }
View from seat: ![Image](/assets/images/wca_lb_view.jpg){: width="200" } 
<br style="clear:both" />
The WCA sections in the upper bowl are located in front of or in the middle of sections: &nbsp;<br>
![Image](/assets/nba/ub_wca_map){: width="500" ; style="float: left" } 
View from seat: ![Image](/assets/images/wca_ub_view.jpg){: width="200" }


&nbsp;<br>

The front row view seats appear to have a premium while the WCA seats are not very expensive in the lower bowl:
![Image](/assets/nba/lb_rows_graph2.png)
The front row view seats have an average price around the same as row 1 seats in the upper bowl. The upper bowl WCA seats have the highest average prices in the upper bowl:
![Image](/assets/nba/ub_rows_graph2.png)

### Modeling

