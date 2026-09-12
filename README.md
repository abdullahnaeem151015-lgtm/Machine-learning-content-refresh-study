## Identifying Content Refresh Opportunities Using Low CTR and High Impressions ##

This repository contains my capstone research project completed during the FlyRank ML Internship.

The project investigates a practical search-performance problem:

Can content with high visibility but comparatively weak click-through rate be identified and prioritized for review using a transparent rule and machine-learning models?

The goal was not to automatically decide that a page must be refreshed. Instead, the project builds a decision-support workflow that helps narrow a large content portfolio into a smaller, ranked set of pages that deserve human review first.

📄 [**Read the full research paper**](https://docs.google.com/document/d/19cTni1b_PkbfI8svMO3i6keGDtMc6eAa52-nBYIjfp8/edit?usp=sharing)

The paper covers:

research question and problem framing,
data preparation and leakage prevention,
baseline refresh-candidate rule,
Logistic Regression, Decision Tree, and Random Forest models,
time-aware train/test validation,
permutation importance,
error analysis,
comparison of the original CTR rule with a position-aware alternative,
ranked content-refresh recommendations.

**Project Summary**

The baseline identifies potential refresh-review candidates using two conditions:

relatively high search impressions, and
relatively low click-through rate (CTR).

These conditions create a practical proxy label for content that may deserve review.

Machine-learning models were then trained using other content-performance signals while excluding the variables directly used to construct the target label with permutation importance to understand "what does model mostly lean on" and error analysis to understand "where model is mostly giving wrong predictions".

The final workflow follows this structure:

Problem framing
      ↓
Data preparation
      ↓
Baseline rule
      ↓
Feature selection and leakage checks
      ↓
Model training
      ↓
Time-aware validation
      ↓
Model interpretation
      ↓
Rule comparison
      ↓
Ranked refresh-review queue

**Dataset**

The analysis uses pseudonymized search and engagement data provided through the FlyRank ML Internship environment.

The modeling experiment used a 30% stratified sample of approximately 3.5 million observations.

The study period covered:

Training: June 1–24, 2026
Testing: June 25–30, 2026

The split was deliberately time-aware so the models were trained on earlier observations and evaluated on later observations.

No private client names, URLs, or search queries are included in the paper or repository.

**Models Evaluated**

Three supervised classification models were compared for following purposes:

Logistic Regression as	Simple linear benchmark
Decision Tree as	Interpretable non-linear model
Random Forest	Ensemble model for more complex patterns

Evaluation included:

Accuracy
Precision
Recall
F1 Score
Weighted F1
ROC-AUC

Because the positive class was imbalanced, SMOTE was applied only to the training data.

**Key Findings**

The three models showed different strengths.

Random Forest achieved the strongest ROC-AUC.
Logistic Regression achieved the strongest recall.
Decision Tree performed competitively on several threshold-dependent metrics.
Average ranking position was the strongest feature in the permutation-importance analysis.
Upon Error Analysis to understand where model is mostly giving wrong predictions more False Positives were found.
The original Global CTR Rule performed better than the FlyRank Position-Tier Rule in 12 of 15 model-metric comparisons.
The final output was converted into a ranked review queue so that the highest-priority content could be reviewed first.

These results should be interpreted as decision support, not proof that every flagged page requires a refresh.

**Main Results**

**Baseline Refresh Rule**

The baseline rule identifies observations that combine relatively high impressions with comparatively low CTR.

📊 [View Baseline Rule](https://github.com/abdullahnaeem151015-lgtm/ML-pipeline/blob/main/work/notebooks/Copy_of_w04_baseline_score%20(1).ipynb)

**Model Development and Evaluation**

Contains trained models like Logistic Regression, Decision Tree, Random Forest with time-aware validation, SMOTE, permutation importance, and error analysis.

📊 [View Model Development Notebook](https://github.com/abdullahnaeem151015-lgtm/ML-pipeline/blob/main/work/notebooks/w05_model.ipynb)


**Final Rule Comparison**

The original Global CTR Rule was compared with the position-aware alternative across 15 model-metric combinations that gives following result:

Previous Global CTR Rule: 12 wins
FlyRank Position-Tier Rule: 3 wins

📊 [View validation and rule-audit notebook](https://github.com/abdullahnaeem151015-lgtm/ML-pipeline/blob/main/work/notebooks/Copy_of_w06_validation_audit%20(2).ipynb)

**Ranked Recommendations**

The final signals were converted into a ranked review queue with:

priority scores,
reason codes,
recommended actions.

📊 [View ranked recommendation notebook](https://github.com/abdullahnaeem151015-lgtm/ML-pipeline/blob/main/work/notebooks/Copy_of_w07_action_playbook%20(1).ipynb)

**Research Limitations**

The refresh-candidate target is a proxy, not independently verified ground truth.

A flagged page is therefore treated as:

“worth reviewing”

rather than:

“definitely needs to be refreshed.”

The study also does not claim that refreshing a flagged page will automatically improve CTR, traffic, or rankings.

That would require post-refresh outcome data, controlled experiments, or independently verified human labels.

Evaluation was conducted on a 30% stratified sample using a single time-based holdout period. Model performance has therefore not yet been demonstrated across multiple months, different seasonal conditions, or future data distributions.

**Tech Stack**

-Python
-pandas
-NumPy
-scikit-learn
-imbalanced-learn / SMOTE
-Matplotlib
-Seaborn
-Jupyter / Google Colab
-GitHub

**Internship Context**

This project was completed as part of the FlyRank ML Internship.

FlyRank provided:

the internship project framework,
access to pseudonymized search-performance data,
the technical starter repository,
the capstone workflow.

The analysis, model development, validation, rule comparison, and research paper were completed as part of my internship capstone.

Data usage follows the repository's DATA_USE.md requirements.

**Author:** Abdullah Naeem

BS Computer Science Student,

Aspiring Machine Learning Engineer / Data Scientist,

[**LINKEDIN**](https://www.linkedin.com/in/abdullah-naeem-736103325/)
