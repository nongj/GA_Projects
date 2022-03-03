# Executive Summary

***

A study on the relationship between income levels (measured by GDP) and SAT scores/participation rates between 2017 to 2019 across US states. 

## Background

Over the past decade, an escalating level of dissent regarding the Scholastic Assessment Test (SAT) is observed on multiple media platforms in the US ([*Forbes*](https://www.forbes.com/sites/susanadams/2020/09/30/the-forbes-investigation-how-the-sat-failed-america/?sh=21d7cb4253b5), [*NY Times*](https://www.nytimes.com/2020/05/23/us/SAT-ACT-abolish-debate-california.html#:~:text=Critics%20of%20the%20tests%20cite,white%20and%20Asian%2DAmerican%20students.&text=Critics%20also%20say%20the%20tests,private%20coaching%20and%20test%20prep.), [*Washington Post*](https://www.washingtonpost.com/education/2019/03/19/is-it-finally-time-get-rid-sat-act-college-admissions-tests/)), criticizing the widely-taken college admission test as biased towards the affluent and conversely, prejudiced against individuals from a lower socio-economic background. 


## Problem Statement

Representing the College Board's legal team, prepare a defense against these allegations and strive towards reshaping the negative perceptions associated with the SAT model. The targetted audiance is the mass media as well as the general US population. The statement should be corroborated by statistical evidence derived from 2017-2019 data on SAT scores and participation rate at the state scale. If the evidence suggest otherwise, propose recommendations to alleviate income inequity resultant of the SAT model. 


## Method(ology)

By consolidating SAT scores/participation rates at the state scale between 2017 to 2019, aggregated/averaged values for SAT scores/participation rates are derived. These values are then measured against the total nominal GDP (2020) as a index of income levels, with the objective of identifying statistical relationships between socio-economic status and SAT performance. 


## Data Dictionary

The data dictionary is inserted below for ease of reference: \

|Feature|Type|Dataset|Date|Description|
|---|---|---|---|---|
|**state**|*string*|states_coordinates.csv|2021|Name of US state| 
|**usps_code**|*string*|states_coordinates.csv|2021|US State code based on United States Postal Service convention|
|**longitude**|*float*|states_coordinates.csv|2021|Geographic coordinate taken from east or west of the prime meridian|
|**latitude**|*float*|states_coordinates.csv|2021|Geographic coordinate taken from north south of the equater|
|**pop_2020**|*integer*|population_size_us_states_2000.csv|2020|Total population size per state in 2020|
|**total_gdp_2020**|*integer*|GDP_us_states_2000.csv|2020|Aggregate gross domestic product at current prices per state in 2020, without factoring in inflation adjustments|
|**num_high_school_grad_2017**|*integer*|SAT Suite Results: 2017|2017|Number of high school graduates per state in 2017|
|**num_sat_taker_2017**|*integer*|SAT Suite Results: 2017|2017|Number of SAT takers per state in 2017|
|**pr_2017**|*float*|sat_2017.csv|2017|Percentage of high school graduates taking SAT per state in 2017. Derived by dividing number of SAT takers for a state in 2017 over the number of high school graduates in the same state in the same year.|
|**ebrw_2017**|*integer*|sat_2017.csv|2017|Average score for the SAT Evidence-based Reading and Writing section per state in 2017. The range of possible scores is between 200 to 800 points.|
|**math_2017**|*integer*|sat_2017.csv|2017|Average score for the SAT Math section per state in 2017. The range of possible scores is between 200 to 800 points.|
|**total_2017**|*integer*|sat_2017.csv|2017|The total average score for the SAT per state in 2017. The range of possible scores is between 400 to 1600 points.|
|**num_high_school_grad_2018**|*integer*|SAT Suite Results: 2018|2018|Number of high school graduates per state in 2018|
|**num_sat_taker_2018**|*integer*|SAT Suite Results: 2018|2018|Number of SAT takers per state in 2018|
|**pr_2018**|*float*|sat_2018.csv|2018|Percentage of high school graduates taking SAT per state in 2018. Derived by dividing number of SAT takers for a state in 2018 over the number of high school graduates in the same state in the same year.|
|**ebrw_2018**|*integer*|sat_2018.csv|2018|Average score for the SAT Evidence-based Reading and Writing section per state in 2018. The range of possible scores is between 200 to 800 points.|
|**math_2018**|*integer*|sat_2018.csv|2018|Average score for the SAT Math section per state in 2018. The range of possible scores is between 200 to 800 points.|
|**total_2018**|*integer*|sat_2018.csv|2018|The total average score for the SAT per state in 2018. The range of possible scores is between 400 to 1600 points.|
|**num_high_school_grad_2019**|*integer*|SAT Suite Results: 2019|2019|Number of high school graduates per state in 2019|
|**num_sat_taker_2019**|*integer*|SAT Suite Results: 2019|2019|Number of SAT takers per state in 2019|
|**pr_2019**|*float*|sat_2019.csv|2019|Percentage of high school graduates taking SAT per state in 2019. Derived by dividing number of SAT takers for a state in 2019 over the number of high school graduates in the same state in the same year.|
|**ebrw_2019**|*integer*|sat_2019.csv|2019|Average score for the SAT Evidence-based Reading and Writing section per state in 2019. The range of possible scores is between 200 to 800 points.|
|**math_2019**|*integer*|sat_2019.csv|2019|Average score for the SAT Math section per state in 2019. The range of possible scores is between 200 to 800 points.|
|**total_2019**|*integer*|sat_2019.csv|2019|The total average score for the SAT per state in 2019. The range of possible scores is between 400 to 1600 points.|
|**num_high_school_grad_avg**|*integer*|SAT Suite Results|2017 to 2019|The total average number of high school graduates per state from 2017 to 2019. Derived by summing the number of high school graduates per state in the stated period divided by 3.|
|**num_sat_taker_avg**|*integer*|SAT Suite Results|2017 to 2019|The total average number of SAT takers per state from 2017 to 2019. Derived by summing the number of SAT takers per state in the stated period divided by 3.|
|**part_rate_avg**|*float*|SAT Suite Results|2017 to 2019|Percentage of high school graduates taking SAT per state between 2017 to 2019. Derived by dividing the total average number of SAT takers for a state from 2017 to 2019 over the total average number of high school graduates in the same state within the same period.|
|**ebrw_avg**|*integer*|sat_2017.csv, sat_2018.csv, sat_2019.csv|2017 to 2019|The total average score for SAT Evidence-based Reading and Writing section per state in from 2017 to 2019. The range of possible scores is between 200 to 800 points. Derived by summing the average SAT EBRW score per state in the stated period divided by 3.|
|**math_avg**|*integer*|sat_2017.csv, sat_2018.csv, sat_2019.csv|2017 to 2019|The total average score for SAT Math section per state in from 2017 to 2019. The range of possible scores is between 200 to 800 points. Derived by summing the average SAT Math score per state in the stated period divided by 3.|
|**total_avg**|*integer*|sat_2017.csv, sat_2018.csv, sat_2019.csv|2017 to 2019|The total average score for the SAT per state between 2017 to 2019. The range of possible scores is between 400 to 1600 points. Derived by adding the total average score for SAT Math section and total average score for SAT EBRW section for the same state.|

## Summary of Analysis

### SAT Score vs Participation Rate

![score_vs_pr](score_vs_pr.png)

Before addressing the problem statement, it is first imperative to understand the relationship between SAT scores and participation rates. From the correlation matrix, the correlation coefficient (= -0.85) indicates a strong negative linear correlation between SAT scores and participation rates. For states with lower participation rates, the individuals sitting for the SATs mostly constitute the academically inclined minority of the eligible population who are pursuing a college degree, and by extension, account for the higher SAT scores. In contrast, for states with (close to) full participation rates, the more even range of SAT scores may be attributed to the higher scores being 'diluted' by the lower scores by virtue of having an all-encompassing population. Equally important to note, participation rates are heavily contingent on state policies

Just to get a sensing, by adopting a minimum average participation rate of 50% as a baseline to ensure at least half of the eligible population take the SATs, there are no states in this category with a total average SAT score above the mean of 1123. Again maintaining the minimum participation rate of 50%, there are only 3 states (i.e. Massachusetts, Vermont, Virginia) with total average SAT scores above the median of 1098, which equates to 6% of all states. 

### Relationship Between GDP and Total Average SAT Score
![gdp_vs_score](gdp_vs_score.png)

By performing a regression analysis, the r-value of -0.27 indicates that there is no discernible correlation between total GDP and total average SAT score. Visually, the absence of a correlation between both factors is illustrated through the random unordered distribution of datapoints coupled with the significant vertical distance between most datapoints and the best-fit line. 

### SAT Score vs Participation Rate
![gdp_vs_pr](gdp_vs_pr.png)

Likewise, the r-value of 0.27 shows that there is no discrenible correlation between total GDP and average participation rate. This is graphically reflected in the scatterplot above too.  

### Spatial Distribution of Total Average SAT Scores Across States
![score_map](score_map.png)

For good measure, the map above exhibits the spatial distribution of total average SAT scores across states. Intriguingly, states that excel in SATs are geographically concentrated about the mid-west and mid-south regions, which are mostly landlocked. Traditionally, coastal states experience higher/faster economic growth due to a greater volume of trade and commerce. Future research may explore this trend while factoring in the significant deviations in participation rates across the respective states. 

## Conclusion and Recommendations

Contrary to media allegations, the study shows there is no linear correlation between socio-economic status (measured by GDP) and SAT scores. In fact, the marginal negative correlation coefficient for total GDP and total average SAT score even alludes to individuals with lower income possibly performing better at SATs, although it remains a speculation at best. Nonetheless, the primary conclusion of the analysis is that the SAT model does not favor the rich over the poor, at least from a statistical viewpoint. The College Board may consider dedicating more effort and resources to convey the study findings in a bid to counteract the negative perceptions of the SAT model developed in the past decade. In a similar vein, the College Board may also undertake additional measures and offer greater incentives for states with lower participation rates. As participation rates are largely determined by state prevailing state policies, the College Board should focus on fostering collaborations with state governments to enhance participation rates. 
