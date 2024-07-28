# Customer Satisfaction Analysis

## Description

In this project, we aim to identify the characteristics of unhappy customers based on survey features. The primary metric of interest is the recall of class zero ("Unhappy").

## Dataset

The dataset contains samples with 6 distinct features and a label indicating 'Happy' (1) or 'Unhappy' (0). Using this data, we performed a benchmark analysis of various classifiers to identify the top three models for further analysis. 

## Benchmark Analysis

After tuning the base models to find the best hyperparameters, we achieved the following recall values for class zero on the test dataset:

- **Tuned Bernoulli NB:** 0.83
- **LGBMC:** 0.75
- **Tuned Random Forest:** 0.67

The Tuned Bernoulli NB emerged as the best base model for predicting on the original 6-feature test dataset. These three base models were retained as inputs for the ensemble models.

## Stacking Ensemble Methods

We selected the three top classifiers suitable for stacking ensemble methods. Each classifier used the three best base models as inputs, achieving the following recall values for class zero on the test dataset:

- **Nearest Centroid**: 0.83
- **Decision Tree**: 0.75
- **Extra Tree**: 0.75

The Nearest Centroid Stacking meta-model proved to be the best stacking ensemble classifier among the top three.

## Voting Ensemble Methods

We evaluated two voting ensemble methods: Hard Voting and Soft Voting. The Hard Voting meta-model achieved a recall of class zero greater than 0.99, while the Soft Voting meta-model had a recall of 0.92 for class zero. The Hard Voting meta-model demonstrated superior performance among the voting approaches.

## Feature Selection

Using Recursive Feature Elimination, we identified the two most important features to retain in the prediction model:
- **X1:** "My order was delivered on time"
- **X5:** "I am satisfied with my courier"

These features reflect an underlying construct related to customer satisfaction with the delivery service.

## Model Performance

With the reduced feature set, the Bernoulli NB base model achieved a recall for class zero greater than 0.99 on the test dataset. Similarly, both the Nearest Centroid Stacking meta-model and the Hard Voting meta-model achieved a recall for class zero greater than 0.99. However, both models had a recall of 0.64 for class one ("Happy customers"), meaning 36% of true class one customers were misclassified as class zero.

## Recommendations

1. **Increase Dataset Size:** To further analyze and validate the outstanding results of both the Hard Voting and Nearest Centroid meta-models on the two-feature dataset, we recommend increasing the size of the subset of data. This would enhance the representation of unhappy customers (class zero) in the test dataset (a minimum of 30 samples is recommended) while maintaining the same train-test ratio (0.8 to 0.2). After this increase, refit and re-evaluate the models to gain additional insights on the patterns of unhappy customers.

2. **Focus on Key Features:** As identified through Recursive Feature Elimination, the final ensemble model can perform exceptionally by focusing on two features:
   - X1: "My order was delivered on time"
   - X5: "I am satisfied with my courier"

   Both features are part of a construct related to customer satisfaction with the delivery service. Benchmarking the company's delivery partners and ensuring standardized quality assurance processes are crucial to maintaining high customer satisfaction.

3. **Simplify Future Surveys:** Future surveys can reduce the number of questions, keeping only those related to X1 and X5. This would save time and effort for respondents, making the survey easier and faster to complete. Additionally, it would enhance the efficiency of future analyses on larger sample volumes.

4. **Include a 'Courier' Feature:** Including a 'Courier' feature in the dataset could allow us to predict which business partners provide good service levels and customer satisfaction, and which ones need improvement.

5. **Investigate Root Causes:** As both final meta-models accurately identify almost all unhappy customers, research on the root causes of low satisfaction (e.g., focus groups or qualitative techniques) should be conducted. This research can focus on the two most important features.

6. **Follow-Up with Happy Customers:** Although the recall for class one is 0.64, a quick follow-up with happy customers to ask about their experiences might foster brand loyalty.

## Conclusions

1. The two most important features in the dataset are:
   - X1: "My order was delivered on time"
   - X5: "I am satisfied with my courier"

   This implies that accurate predictions can be made by focusing on customer satisfaction with the delivery service.

2. Two ensemble models (Nearest Centroid Stacking and Hard Voting) show outstanding results when predicting with only these two features, ensuring the detection of truly unhappy customers. However, this might be related to specific feature-value distributions for class zero customers in the test dataset.

3. For further analysis, increasing the subset size is recommended to ensure that class zero samples are well represented.

4. There is an opportunity to investigate the performance of the company's delivery partners. This can be approached by reaching out to unhappy customers for research purposes and by conducting an internal comparison between service suppliers.

5. Including a 'Courier' column in subsequent datasets is recommended to enable trend analysis by business partner.

Last update: 2024.07.27

Prepared by: Japhet Hernández-Vaquero

For: Apziva Residency Program
