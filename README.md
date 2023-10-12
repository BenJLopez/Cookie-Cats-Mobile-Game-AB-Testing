# Cookie-Cats-Mobile-Game-AB-Testing

## Problem Statement:
Cookie Cats is a "Match 3" style Mobile Game that was released by Tactile Games in 2016 and is still active on popular mobile platforms (Android, iPhone). The dataset for this project was originally provided as a DataCamp project, for the purpose of studying the effects of different marketing campaigns on player retention. The developer set up a controlled test with two groups of users:
- One group received a timed marketing/ad campaign message at level 30 in Cookie Cats, referred to as "gate_30"
- The second group received the campaign message at level 40, referred to as "gate_40"

I will work through the provide data set to analyze the effects of the AB Test on Day-1 and Day-7 Retention Metrics, attribute hypothesis testing definitions to this test, and find confidence level in the experiment.

## Data Description:

A .csv file with 5 columns was provided with complete values (no nulls)


user_id = random numerical value unique to each user
version = either "gate_30" or "gate_40" campaign treatment as mentioned above
sum_gamerounds = number of game rounds played by user within 14 days of install
retention_1 = App opened/played again 1 day after install date
retention_7 = App opened/played again 7 days after install date

## Analysis:
### Hypothesis Test Definitions:
Considering "gate_30" as the standard control version, and "gate_40" as the test treatment:
Null Hypothesis: The treatment "gate_40" has no relationship with the metric "retention_7"
Alternative Hypothesis: "gate_40" treatment does have a relationship with the "retention_7" metric

True-Positive (Power) - Cases where we assume gate_40 treatment does effect retention_7, and this assumption is correct
True-Negative (Confidence) - Cases where we assume gate_40 treatment has no effect on retention_7, and this assumption is correct
False-Positive (Type I Error) - Cases where we assume gate_40 treatment does effect retention_7, but this assumption is incorrect
False-Negative (Type II Error) - Cases where we assume gate_40 treatment does not effect retention_7, but this assumption is incorrect

### Day-7 Retention:
groupbys
histograms (visual confirmation of diff)
(down to confidence level 95%? 99%?)
### Confidence Level Tests:

## Results:


## Final Thoughts:
