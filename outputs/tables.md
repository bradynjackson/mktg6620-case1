# Evaluate outputs (choice: trees)

Source: outputs/*.csv from the evaluate run. Values rounded to 3 decimals.

## test_metrics.csv

| method | n | auc | contact_n | top20_churn_rate | top20_mean_prediction | mean_prediction | observed_churn_rate |
|---|---|---|---|---|---|---|---|
| contract | 1409 | 0.737 | 281 | 0.399 | 0.428 | 0.269 | 0.265 |
| logistic | 1409 | 0.847 | 281 | 0.694 | 0.640 | 0.273 | 0.265 |
| trees | 1409 | 0.850 | 281 | 0.694 | 0.648 | 0.270 | 0.265 |

## intervals.csv

| comparison | estimate | low | high | crosses_zero |
|---|---|---|---|---|
| contract | 0.737 | 0.716 | 0.756 | No |
| logistic | 0.847 | 0.825 | 0.870 | No |
| trees | 0.850 | 0.828 | 0.873 | No |
| logistic minus contract | 0.110 | 0.093 | 0.129 | No |
| trees minus contract | 0.112 | 0.096 | 0.131 | No |
| trees minus logistic | 0.002 | -0.005 | 0.010 | Yes |

## probability_groups.csv

| group | n | mean_prediction | observed_churn_rate |
|---|---|---|---|
| 0.0 to 0.2 exclusive | 724 | 0.080 | 0.072 |
| 0.2 to 0.4 exclusive | 272 | 0.298 | 0.254 |
| 0.4 to 0.6 exclusive | 236 | 0.496 | 0.521 |
| 0.6 to 0.8 exclusive | 142 | 0.677 | 0.690 |
| 0.8 to 1.0 inclusive | 35 | 0.834 | 0.914 |

## scenarios.csv

| method | historical_list_churn_rate | assumed_save_rate | net_per_1000_contacts | break_even_save_rate |
|---|---|---|---|---|
| contract | 0.399 | 0.100 | -3569.395 | 0.236 |
| contract | 0.399 | 0.150 | -2254.093 | 0.236 |
| contract | 0.399 | 0.200 | -938.790 | 0.236 |
| logistic | 0.694 | 0.100 | -1619.929 | 0.135 |
| logistic | 0.694 | 0.150 | 670.107 | 0.135 |
| logistic | 0.694 | 0.200 | 2960.142 | 0.135 |
| trees | 0.694 | 0.100 | -1619.929 | 0.135 |
| trees | 0.694 | 0.150 | 670.107 | 0.135 |
| trees | 0.694 | 0.200 | 2960.142 | 0.135 |
