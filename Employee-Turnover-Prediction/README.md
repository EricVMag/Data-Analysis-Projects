# Employee Turnover Prediction

A machine-learning case study analyzing employee turnover and building a
classifier to identify employees at elevated risk of leaving.

## Project context

This project was completed as the capstone for the **Google Advanced
Data Analytics Professional Certificate on Coursera**. The fictional
Salifort Motors business scenario, dataset, and original notebook
framework were provided through the course.

The **data cleaning decisions, exploratory analysis, visualizations,
model development and tuning, validation strategy, model selection,
evaluation, interpretation, and business recommendations** in the
accompanying notebook reflect my work.

## Business problem

The HR department wants to better understand employee turnover and
identify patterns that could inform retention efforts. The analytical
objective is to predict whether an employee will leave the company based
on information available to HR.

This is a **binary classification** problem:

-   `0` --- employee stayed
-   `1` --- employee left

## Dataset

The course-provided dataset contains approximately 15,000 employee
records and includes variables related to:

-   employee satisfaction
-   performance evaluation
-   number of projects
-   average monthly hours
-   tenure
-   workplace accidents
-   promotions
-   department
-   salary level
-   employee turnover

### Dataset availability

The original dataset was supplied within the Coursera course environment
and is no longer available to me, so it is **not included in this
repository**. The notebook retains its executed outputs so that the
analysis, visualizations, and model results can still be reviewed.

## Analytical approach

The project follows an end-to-end analytics workflow:

1.  **Data cleaning** --- standardized column names, checked missing
    values and duplicates, and examined outliers.
2.  **Exploratory data analysis** --- investigated how satisfaction,
    workload, evaluation scores, tenure, salary, department, promotions,
    and workplace accidents relate to turnover.
3.  **Feature preparation** --- one-hot encoded categorical variables
    and created stratified training, validation, and test sets.
4.  **Model development** --- trained and tuned Random Forest and
    XGBoost classifiers using cross-validation.
5.  **Model selection** --- compared the models on validation data and
    selected the champion model based primarily on recall.
6.  **Final evaluation** --- evaluated the selected XGBoost model on the
    held-out test set and examined its confusion matrix and feature
    importance.
7.  **Business interpretation** --- translated model results into
    retention-oriented recommendations and identified limitations and
    next steps.

## Key findings

Exploratory analysis showed several notable patterns:

-   Lower satisfaction was strongly associated with turnover.
-   Evaluation score, project count, and monthly hours showed nonlinear
    relationships with turnover.
-   Employees who left were concentrated in the **3--6 year tenure
    range**.
-   Promotions were uncommon, but promoted employees were overwhelmingly
    represented among those who stayed.
-   Turnover varied across departments and salary levels.
-   Salary was associated with turnover, although workload,
    satisfaction, and evaluation variables provided stronger predictive
    signals in the final model.

These relationships are **associations rather than causal effects**.

## Model comparison

Both models were tuned using cross-validation, with **recall** used as
the primary selection metric because the business case places greater
cost on failing to identify an employee who ultimately leaves.

  ------------------------------------------------------------------------------------
  Model         Dataset               Precision       Recall           F1     Accuracy
  ------------- ------------------ ------------ ------------ ------------ ------------
  Random Forest Cross-validation          0.971        0.905        0.936        0.980

  XGBoost       Cross-validation          0.960        0.914        0.936        0.979

  Random Forest Validation                0.971        0.912        0.940        0.981

  XGBoost       Validation                0.963    **0.917**        0.940        0.980

  **XGBoost**   **Test**              **0.953**    **0.927**    **0.940**    **0.980**
  ------------------------------------------------------------------------------------

XGBoost was selected as the champion model because it achieved the
higher validation recall while maintaining strong precision and F1
performance.

## Business recommendations

The results suggest that HR should pay particular attention to broad
patterns in:

-   employee satisfaction
-   unusually high or low workloads
-   extreme project loads
-   employees in the 3--6 year tenure range

Model predictions should be used as a **decision-support tool**, not as
the basis for adverse employment decisions. Follow-up research would be
needed to determine which factors are causal and which interventions
would actually improve retention.

## Limitations and next steps

The original dataset is no longer available, so the published notebook
cannot currently be rerun from raw data. Executed outputs are retained
for review.

Potential extensions include:

-   adding a logistic-regression baseline for interpretability
-   expanding the hyperparameter search
-   tuning the classification threshold based on the business cost of
    false positives and false negatives
-   using additional model-explanation methods
-   testing whether the identified turnover patterns remain stable over
    time
-   evaluating retention interventions prospectively

## Tools

Python · pandas · NumPy · Matplotlib · Seaborn · scikit-learn · XGBoost
· Jupyter Notebook

## Files

-   `employee_turnover_prediction.ipynb` --- complete analysis,
    modeling, and evaluation notebook
-   `executive_summary.pdf` --- one-page stakeholder summary

## Author note

This repository is intended as a portfolio presentation of analytical
work completed within a course-provided case study. The project origin
is disclosed to distinguish the supplied scenario and data from the
analysis and modeling work performed as part of the capstone.
