### Introduction

To improve the participation rates of the SAT in a particular state, a study of data for the SAT and ACT tests from the years 2017 and 2018 was carried out. The data studied includes the participation rates, the average final or composite scores for both tests, as well as scores for each subject/component broken down at state-level across the United States of America.

___

### Overview

#### Obtaining Dataframe for study
The relevant python libraries and data were imported into the jupyter notebook file to start. Data was cleaned and merged to form a "final" dataframe. The below data dictionary gives a quick summary of this dataframe.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|Name of State|
|act_201X_participation|float|ACT|Participation within the State in year 201X|
|act_201X_english|float|ACT|English Score for the State in year 201X|
|act_201X_math|float|ACT|Math Score for the State in year 201X|
|act_201X_reading|float|ACT|Reading Score for the State in year 201X|
|act_201X_science|float|ACT|Science Score for the State in year 201X|
|act_201X_composite|float|ACT|Composite Score for the State in year 201X|
|sat_201X_participation|float|SAT|Participation within the State in year 201X|
|sat_201X_readingwriting|int|SAT|Evidence-based Reading and Writing Score for the State in year 201X|
|sat_201X_math|int|SAT|Math Score for the State in year 201X|
|sat_201X_total|int|SAT|Total Score for the State in year 201X|

___

#### Trend investigation

Trend investigation revealed that Colorado's ACT participation dropped from 100% to 30% between 2017 and 2018 while it's SAT participation increased from 11% to 100%. 
A similar observation was made for Illinois whose ACT participation dropped from 93% to 43% between 2017 and 2018 while it's SAT participation increased from 9% to 99%.

___

#### Data Visualization

A heatmaps as well as several histograms, scatterplots and boxplots were plotted which revealed the following: 

Studying participations generally reveal 3 groups:
1) Full or almost full participation
2) Moderately high participation
3) Low participation

Studying scores generally reveal 2 groups:
1) Lower scoring states which generally have higher participation rates
2) Higher scoring states which generally have lower participation rates
This was confirmed using hypothesis testing subsequently as well.

Studying scores also reveal that there is little correlation between scoring between the ACT an SAT, even for similar subjects. Therefore, states that do well in the SAT may or may not do well in the ACT.

___

#### Additional research, conclusions and recommendations

Minnesota is the "smartest" state. 
The swings in Colorado and Illinois from ACT to SAT were down to state initiatives.
It was recommended to lobby the local authorities in Kentucky to take up the SAT.
It was also recommended to further the study by looking at the number of colleges/scholarships that require the SAT for admission or consideration.