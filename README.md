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
- Null Hypothesis: The treatment "gate_40" has no relationship with the metric "retention_7"
- Alternative Hypothesis: "gate_40" treatment does have a relationship with the "retention_7" metric

- True-Positive (Power) - Cases where we assume gate_40 treatment does effect retention_7, and this assumption is correct
- True-Negative (Confidence) - Cases where we assume gate_40 treatment has no effect on retention_7, and this assumption is correct
- False-Positive (Type I Error) - Cases where we assume gate_40 treatment does effect retention_7, but this assumption is incorrect
- False-Negative (Type II Error) - Cases where we assume gate_40 treatment does not effect retention_7, but this assumption is incorrect

### Day-7 Retention:
Checking the 7-Day Retention for each treatment group (using groupbys):

![Fig  1, Groupby D7 Retention](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/5107d235-508f-4bd7-bd35-cb80032692bd)

We can see that the figures seem relatively close, but looking more closely at the differences:

![Fig 2, Retention by Treatment Group](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/59b15a1f-6b4f-49e2-960d-7502989b0fe1)

There is only about 0.8% difference in Day-7 Retention between the control group (gate_30) and the treatment group (gate_40), but at scale this could become longer term retention (higher Day-30 for example), more engagement, and more ad revenue.

So we know that we are seeing a slight difference in retention at this point, but how confident can we be in the result?
- Firstly we can view the histograms visaully, telling us how well the data conforms to a normal curve distribution and allowing us to compare visualizations of the two groups.
- Second, we can calculate the confidence level of the test
- Third, we can see the corresponding P-values that allow a certain confodence level in the test


### Bootstrapping 7-Day Retention (visual confirmation of diff)

Iterating over 1000 instances for distributions of each treatment group, I was able to plot and see a visual difference in "gate_30" and "gate_40" versions:

![Fig 3, Bootstrap Distributions Retention](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/9a80df14-a9ab-4ec9-9399-3ba14dccdd57)

There seems to be minimal overlap, but I wanted to get some test metrics to help quantify the significance of the difference. 

### Running Tests and Getting P-value:
Since the target metric I am interested in (7-Day Retention) is a discrete binomial (only True/False, 1 or 0), that narrows my test options to either Fisher's Exact Test or the Chi-Square Test. Because the number of samples is high and I am not used to using Fisher's Exact Test for samples > 100, I will choose the Chi-Square Test.

Luckily we already have the 2x2 Contingency Table values from the groupby I pulled earlier:

![Fig  1, Groupby D7 Retention](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/1311800b-d7c2-48b0-9b41-5ab833cd10bb)

And we can just input those values into the 2x2 for the test:

![Fig 4, Chi2 pvalue ](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/24427e16-c358-4b1e-9351-a9d093fa8500)

## Results:
A p-value of 0.1 is well under the 5% threshold that is typically used. This lends to a very low probability that the null hypothesis is true. Looks like it is a significant difference and we should stick with the Gate 30 Campaign (ads at level 30).

![Fig 5, Result](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/0526ba41-bce1-4791-9273-14be9886c5a6)

## Final Thoughts:
Other aspects we could analyze:
- 1-Day Retention
- Influence of 1-Day Retention on 7-Day Retention
- Influence of Sum of Game Rounds on 7-Day Retention

- Ideally we could dig deeper and find out 30-Day Retention, which is not included in this data set, but can be done internally at Tactile Games.

