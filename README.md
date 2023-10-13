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
Checking the 7-Day Retention for each treatment group (using groupbys):

![image](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/f3066377-c25c-486d-865a-b68a70432cd8)

We can see that the figures seem relatively close, but looking more closely at the differences:

![image](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/0623d763-bc9a-4561-98e5-6bf1ba140585)

There is only about 0.8% difference in Day-7 Retention between the control group (gate_30) and the treatment group (gate_40), but at scale this could become longer term retention (higher Day-30 for example), more engagement, and more ad revenue.

So we know that we are seeing a slight difference in retention at this point, but how confident can we be in the result?
- Firstly we can view the histograms visaully, telling us how well the data conforms to a normal curve distribution and allowing us to compare visualizations of the two groups.
- Second, we can calculate the confidence level of the test
- Third, we can see the corresponding P-values that allow a certain confodence level in the test


### Bootstrapping 7-Day Retention (visual confirmation of diff)

![image](https://github.com/BenJLopez/Cookie-Cats-Mobile-Game-AB-Testing/assets/86575100/21733feb-e145-47d2-8bde-9264e691f913)


(down to confidence level 95%? 99%?)
### Confidence Level Tests:

## Results:


## Final Thoughts:
