# Credit Risk Classification Analysis

This README describes the performance differences between train_test_split and RandomOverSampler. Loan data is used in this comparison, with loans grouped into 'healthy' and 'high risk' categories. The dataset contains nearly 20,000 rows, with 3% falling into the 'high risk' group.

- Accuracy
    - Using the train_test_split method, a 95% accuracy is reached.
    - RandomOverSampler improves on this, going over 99% accuracy.
- Precision
    - Healthy loan predictions hit an astounding 100% precision with train_test_split. High risk loans, however, drop to 85%. I believe this can be attributed to the imbalance between the number of supporting data points. With 18,765 healthy loans, the model has plenty of samples to train on. There are 30x fewer high risk loans in this dataset to train on, which is clearly a detriment to the training algorithm.
    - The RandomOverSampler method shows wonderful precision scores on both fronts, with both healthy and high risk loans at 99%. The goal of over-sampling is to make up for the difference in sample sizes in datasets ([source](https://imbalanced-learn.org/stable/over_sampling.html)) which can be seen with the increase to 75,036 samples for each loan category. The 14% increase in precision for high risk loan predictions is a great example of over-sampling's benefits.
- Recall
    - train_test_split accurately predicts 99% of loans it describes as healthy. 91% of its high risk predictions were accurate, meaning 56 of 619 high risk predictions were inaccurate.
    - Similarly to the precision scores, RandomOverSampler kicks both recall scores to 99%. Around 0.5% of the model's predictions were inaccurate in this case.

Random over-sampling improves almost all prediction scores when compared to the train_test_split method. Using this loan data example, over-sampling is the clear favorite. With major financial decisions on the line, there is no reason to use a prediction method that labels high risk loans inaccurately as frequently as train_test_split does.