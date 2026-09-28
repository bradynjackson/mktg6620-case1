# Results

## Q2 — Data checks and separation
### Data and cleaning
The data has 7,043 rows and 21 columns with 5,174 No and 1,869 Yes. 
There are 11 blank TotalCharges. The 11 blanks were filled with 0. All 
11 are customers with tenure 0, no rows were removed. Filling in with 
0 makes sense because with tenure 0, that means they are new customers 
so we wont have data for them. After cleaning, none of the seven inputs 
has a missing value.  The three numeric inputs were standardized and the 
four categorical inputs all became 0/1 columns. Churn is recorded to 1 
(yes) or 0 (No). There doesn't seem to be any alarming outliers. It did a 
1.5 * IQR fence and no values fell above or below that. 
### Partitions
We did three partitions. 60% goes to training and 40% is split evenly into 
validation and test. We saw that the train rows came out to 4,225, 
validation and test both came out to 1,409. There was no overlap, and the 
fitting used training rows only. Each partition is about the same churn rate 
at 26.5%. The test rows never influence the fitting so the evaluation is honest. 

## Q3 — Uncertainty and value
### AUC and top-20% list
For contract, we got an AUC of .737, logistic AUC was .847, and AUC for 
trees was .850. We see that logistic and trees AUC were the highest and trees 
beat logistic by .0025. Our top 20 churn rate also followed the same patterns 
with logistic and trees higher than contract (.399) with logistic at .694 
and trees at .694. The 69.4% applies to both logistic and trees. Top 20 mean prediction also followed the same trend with contract at 
.428, logistic at .640, and trees at .648. The top 20 churn rate is 69.4% 
compared to the overall of 26.5%
### Intervals
Our contract estimate was .737, logistic was .847, and trees was .850. Our 
range for contract was (.716, .756), logistic was (.825, .870), and trees was 
(.828, .873). The change in AUC vs. contract for logistic was (+0.110) and 
trees was (+0.112), and neither interval crosses zero. We saw that trees - 
logistic interval crossed zero (-0.005 to 0.010). The two "vs. contract" 
intervals don't cross zero. Both models are scored on the same re sampled rows 
each time.  
### Probability check (trees)
We see that as the groups increase towards 1, our n in each group decreases. 
Our top group in n = 35. The prediction for that was .834 and the observed was 
.914, which was under predicted. The last bin also differs the most. Next 
closest would be group 0.2 to 0.4 with prediction at .298 and observed at .254, 
which was over predicted.  Overall predicted was 27% and observed was 26.5%. The 
Top 20 list predicted was 64.8% and observed was 69.4%.
### Value scenarios
The three net values for trees: -$1,620, +$670, and +$2,960. Break even is 
13.5%. S changes the recommendation. The result goes from a loss to a profit 
between 10% and 15%. To work it out to see if it check out, I'll pick .15. 
Our math is as follows 1000 * (0.69395 * 0.15 * 66 - 6.20) and that comes to 
$670. That matches the trees 15% row. Break even would be 13.5%. The break 
even (13.5%) falls inside the 10-20% range we tested, and the data can't tell 
the real save rate. 

## Q4 — Choice and comparison
### Validation choice (recoded Sept 27, 10:24 pm)
Trees has the highest validation AUC. Our output gives us AUC's of 
trees 0.846, logistic 0.838 and contact 0.743. Both logistic and trees 
rank better than contract by about 0.10 AUC. Trees vs. logistic has a 
difference of .007 AUC. That is a very close difference for AUC where 
on the top-20% list, trees had the highest churn rate at 65.1%
### Comparison table
| Method | Final-test AUC | ΔAUC vs. contract | 95% interval | Carry forward? | Reason |
|---|---|---|---|---|---|
| Contract rule | 0.737 | — | 0.716 to 0.756 (AUC) | No | The other two models beat contract |
| Logistic regression | 0.847 | +0.110 | 0.093 to 0.129 | Yes | Model had a churn of 69.4% |
| Boosted trees | 0.850 | +0.112 | 0.096 to 0.131 | Yes | Performed the best overall |
Carry it forward would mean a pilot candidate.
### What would change my recommendation
My recommendation would change if the pilot showed a real save rate below 13.5%. 
I would also look at if contract or offer costs were higher than assumed. . 