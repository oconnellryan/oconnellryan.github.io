---
layout: page
title: Analysis of UFC Judging Criteria
---

My Senior Thesis (completed in May 2024 at Syracuse University) analyzed which factors influence UFC judging and how individual judges value them differently. Since then, I’ve expanded the work into a full [Live UFC Analytics Platform](../platforms/ko-trends.md), which powers real-time judging insights and analysis for fans.

# Senior Thesis Highlights:

#### Data & Methodology:
I wrote R scripts to scrape scorecard data from [MMAdecisions.com](https://mmadecisions.com/) and fight statistics from [UFCStats.com](http://ufcstats.com/statistics/events/completed).

The fight statistics included significant strikes landed with two different breakdowns: &nbsp;<br>

<div style="display: flex; justify-content: flex-start; gap: 60px;">

  <div>
    <span>Target Breakdown:</span>
    <ul>
      <li>Significant head strikes</li>
      <li>Significant body strikes</li>
      <li>Significant leg strikes</li>
    </ul>
  </div>

  <div>
    <span>Positional Breakdown:</span>
    <ul>
      <li>Significant strikes at distance</li>
      <li>Significant clinch strikes</li>
      <li>Significant ground strikes</li>
    </ul>
  </div>

</div>

Aside from significant strikes landed, the fight data also included:
- knockdowns landed
- non-significant strikes landed and attempted
- takedowns landed and attempted
- control time
- reversals
- submission attempts &nbsp;<br>

To remove red vs. blue corner bias, I randomly assigned each fighter's data to one of two sets of columns. I then calculated the difference between each of the statistics mentioned above for the two fighters.

#### Binomial GLM Models:
Two models were built for each striking breakdown, using the majority scorecard winner as the response variable.
<div style="display: flex; gap: 40px;">

  <div style="text-align: center;">
    <div style="font-weight: bold; margin-bottom: 6px;">Target Model:</div>
    <img src="/assets/ufc/target_model.png" alt="Target Model" width="365"/>
  </div>

  <div style="text-align: center;">
    <div style="font-weight: bold; margin-bottom: 6px;">Position Model:</div>
    <img src="/assets/ufc/position_model.png" alt="Position Model" width="365"/>
  </div>

</div>
**Some key takeaways from the models:**
- The target model has identified the head as the most important target to the judges
- Both models show knockdowns are extremely impactful to winning round
- Takedowns and reversals are valued very similarly in both models
- The value of a takedown/reversal is around the same as 50 seconds of control time
- Submission attempts are valued around twice as much as a takedown/reversal

<br style="clear:both" />

#### Individual Judge Biases:
After building the GLM models, I used them to identify individual judges' scoring tendencies by subsetting the data for each judge. I repeated this process for each of the judge data subsets:
 1. Rounds where the two judges not being examined had different scores were dropped
 2. Two new winner variables were created for each round:
    - Winner<sub>j</sub> indicates who the selected judge had winning the round, and
    - Winner<sub>nj</sub> is the winner selected by the other two judges
 3. These new variables were used to create two models for each judge:
    - The judge model was fitted using the Winner<sub>j</sub> variable
    - The non-judge model fitted using the Winner<sub>nj</sub> variable
 5. A Wald test was used to assess whether the coefficient differences between the two models were significant
 6. A graph was created to compare the coeficcients. &nbsp;<br>
 
*This Process was also repeated using both the target & position model to examine all variables*

Here is an example of the target output graphs for one of the judges (Derek Cleary):
<img src="/assets/ufc/cleary_target_graph.png" alt="Image" width="700"/> &nbsp;<br>
This output shows us the following about Derek Cleary:
- He values significant head strikes lower than other judges
- He also values significant body strikes lower than other judges
- He also seems to value submission attempts a bit high

We can also examine the alternative graph for the position models: 
<img src="/assets/ufc/cleary_position_graph.png" alt="Image" width="700"/> &nbsp;<br>
In this graph, the only statistically significant difference that can be seen is in significant distance strikes.


#### Decision Tree & Random Forest Models:
In addition to the binomial GLM model created, a decision tree and random forest were created to judge rounds. Most of the variables are the same here, but instead of the significant strikes being broken down by target (head, body legs), they are broken down by where the striking occured (distance, ground or clinch). This data will allow the decision trees to identify different types of fights, such as a round where one fighter dominated on the ground but lost on the feet. The main decision tree is shown below:
![Image](/assets/images/tree.png)
You can see that this tree has multiple splits based on who won the distance striking as well as the grappling (through ground striking and control time). While this overfits the data, you can see how this approach makes sense for scoring. A random forest model using the same predictors was also created, and the following output shows the results of this:
![Image](/assets/images/varimp_plot.png)
Just like in the decision tree significant distance strikes, control time, and significant ground strikes are the most important predictors. Significant clinch strikes do not have much of an impact, and the mean decrease gini is actually higher for non-significant strikes. Takedowns are not overly important due to most grappling splits occuring on control time and ground striking. Submission attempts, knockdowns, and reversals all occur infrequently so the random forest was unable to capture the importance of these.

&nbsp;<br>

**Read my thesis:** [*Analysis of UFC Judging Criteria*](https://oconnellryan.github.io/assets/Analysis-of-UFC-Judging-Criteria.pdf) (Spring 2024)
