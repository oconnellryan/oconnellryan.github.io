---
layout: page
title: NBA Ticket Pricing
---
In this project I created a predictive model of NBA ticket prices. 2 seasosns of Warriors ticket sales data as well as external game data including opponents and injuries were used for this analysis.


## Result Highlights
The following graphic showcases the predicted ticket prices for each seat in an individual game:
![Image](/assets/images/arena_map.png)

### Exploratory Analysis
**External Game Factors:** &nbsp;<br>
Opponents Matter. Playing big market teams and a higher opponent winning percentage both lead to higher average ticket prices:
![Image](/assets/images/opps.jpeg)

&nbsp;<br>

Steph Curry missed 15 games in 2022, and we can see the average ticket prices dropped quickly in the periods he missed games due to injury:
![Image](/assets/images/curry_graph.jpeg)
![Image](/assets/images/curry_22.jpeg){: width="200" }

&nbsp;<br>

Almost all of the games before 7:00 were at 5:30. These earlier games had higher average ticket prices:
![Image](/assets/images/times.jpeg){: width="200" }

&nbsp;<br>

Tickets are more expensive when purchased further out from games. There is a sharp drop off in the price of gameday tickets:
![Image](/assets/images/days_out.jpg)

&nbsp;<br>

**Stadium Areas:** &nbsp;<br>
The bowl of the arena was broken down into the following sections based on location and club access:
![Image](/assets/images/sections.jpeg)
![Image](/assets/images/sec_prices.jpg){: width="200" }



The floor was split up by side:
![Image](/assets/images/floor.jpg)
![Image](/assets/images/floor_avgs.jpg){: width="200" }

**Seat Features:** &nbsp;<br>
The average ticket price decreases as you go back in rows:
![Image](/assets/images/lb_rows.jpg)
![Image](/assets/images/ub_rows.jpg)

There are WCA (wheelchair access) areas in the arena. These seats are located in the back of sections in the lower bowl: &nbsp;<br>
![Image](/assets/images/wca_lb_graph.jpg){: width="=500" ; style="float" } View from seat: ![Image](/assets/images/wca_lb_view.jpg){: width="200" }
The WCA sections in the upper bowl are located in front of or in the middle of sections:
![Image](/assets/images/wca_ub_graph.jpg){: width="=500" ; style="float" } View from seat: ![Image](/assets/images/wca_ub_view.jpg){: width="200" }



