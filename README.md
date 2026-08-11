# Employee Turnover Predictive Analytics

**Using predictive analytics to turn workforce data into actionable retention decisions**

## Project Overview

Employee turnover creates both financial and operational challenges for organizations. This project examined how predictive analytics could be used to identify employees at elevated risk of voluntary turnover before they leave, allowing an organization to focus retention resources where they may have the greatest impact.

Using an assigned simulated HR dataset containing **9,999 employee records**, I independently developed and evaluated multiple machine learning approaches for predicting turnover. The project moved beyond model performance alone by considering classification thresholds, intervention costs, expected retention outcomes, and the practical consequences of false-positive predictions.

The ultimate goal was not simply to build the most accurate model, but to determine how workforce data could support more informed and proactive business decisions.

## Business Question

The project addressed two related questions:

1. **Can employee turnover risk be predicted accurately using available workforce data?**
2. **How should model predictions be translated into practical retention decisions?**

A useful turnover model must do more than correctly classify employees. False positives can lead an organization to spend resources intervening with employees who were not likely to leave, while false negatives represent employees whose turnover risk may go unaddressed.

The analysis therefore evaluated model performance alongside the financial and operational consequences of using those predictions.

## Analytical Approach

The project followed an end-to-end predictive analytics workflow designed to preserve data integrity and provide an unbiased evaluation of model performance.

The process included:

- Data import, cleaning, and quality assessment
- Exploratory data analysis
- Stratified training and testing split
- Feature selection using Boruta
- Ten-fold stratified cross-validation
- Development of multiple preprocessing strategies to address class imbalance
- Hyperparameter tuning
- Comparison of four machine learning model families
- Evaluation using multiple classification metrics
- Held-out test-set validation
- Classification threshold optimization
- Cost-benefit analysis
- Translation of technical findings into business recommendations

All preprocessing and feature-selection decisions were performed using the training data to protect the integrity of the held-out test set and reduce the risk of information leakage.

## Models Evaluated

Four classification approaches were developed and compared:

- Penalized Logistic Regression
- Random Forest
- XGBoost
- Support Vector Machine

Candidate workflows were evaluated using multiple measures rather than relying on a single performance statistic, including:

- Youden's J-Index
- ROC AUC
- Precision-Recall AUC
- Sensitivity
- Specificity
- Confusion matrices
- Held-out test performance

Multiple class-imbalance strategies were also evaluated, including no sampling, upsampling, downsampling, SMOTE, ADASYN, and class weighting where supported.

## Model Selection

Tree-based models substantially outperformed the alternative approaches.

During cross-validation, XGBoost produced the highest J-Index among the strongest workflows, with Random Forest performing nearly identically. Rather than automatically selecting the model with the single highest cross-validation statistic, additional performance measures and held-out test results were considered.

**Random Forest was ultimately selected as the recommended model** because it maintained excellent predictive performance while producing fewer false-positive predictions.

That distinction mattered from a business perspective. Every employee incorrectly identified as a likely leaver could receive an unnecessary retention intervention, consuming organizational resources without producing the intended benefit.

The model-selection decision therefore balanced statistical performance with operational value.

## Threshold Optimization

The analysis also examined whether the traditional **50% classification threshold** was appropriate for identifying turnover risk.

The Random Forest model achieved its strongest statistical balance at a threshold of approximately **43–44%**, demonstrating that the default cutoff was not necessarily the most useful decision point.

The analysis then went one step further by comparing classification thresholds using the financial assumptions provided for the project.

This allowed the final recommendation to answer a more practical question:

> **At what level of predicted turnover risk does intervention create the greatest expected organizational value?**

## Business Impact

The assignment assumed:

- **$100,000 cost** for an employee departure
- **$5,000 cost** for each targeted retention intervention
- **50% probability** that an intervention successfully prevents turnover

Under these assumptions, using the optimized approach produced an estimated:

- **$30.7 million in net savings**
- **703 employees receiving targeted retention interventions**
- **343 employees expected to remain with the organization because of successful interventions**
- **17 unnecessary interventions**

These estimates are based on the simulated dataset and assignment assumptions and should not be interpreted as actual organizational financial outcomes.

The analysis demonstrates how predictive analytics can help organizations allocate limited retention resources more strategically rather than applying costly interventions broadly across the workforce.

## Workforce Insights

The modeling process identified several workplace factors that consistently contributed useful information when predicting turnover, including:

- Employee satisfaction
- Number of projects
- Employee tenure
- Performance evaluation
- Average monthly working hours

The findings suggested that retention efforts should consider employees' day-to-day work experiences, workload, and key tenure milestones alongside traditional factors such as compensation.

Importantly, these variables represent **predictive associations rather than evidence of causation**. A model can identify patterns that help an organization determine where to look, but additional organizational investigation is necessary before concluding why employees are leaving.

## From Analytics to Action

The recommended model was intended to function as a **decision-support tool rather than a replacement for managerial judgment**.

Employees identified as having elevated turnover risk could be prioritized for proactive support such as:

- Stay interviews
- Career-development conversations
- Workload discussions
- Mentoring
- Individualized manager support

Model outputs provide a starting point for better questions and more targeted action. Managers and HR professionals would still need to understand the employee's experience before determining whether an intervention is appropriate.

## Communicating to Different Audiences

An additional requirement of the project was translating the same analysis for two different audiences.

A **technical colleague summary** documented the modeling workflow, evaluation process, model-selection rationale, and recommendations for continued monitoring and model maintenance.

A separate **manager-facing executive summary** translated those findings into business language focused on retention decisions, financial implications, and recommended actions.

This reinforced an important part of applied People Analytics: strong analysis creates value only when the findings can be communicated in a way that supports decision-making.

## My Role

This was an **independent graduate analytics project** completed as part of my Advanced Analytics coursework in Industrial-Organizational Psychology.

I completed the full analytical workflow, including:

- Preparing and exploring the employee dataset
- Protecting the train/test structure throughout the analysis
- Conducting feature selection
- Developing and tuning candidate modeling workflows
- Comparing model performance
- Evaluating results on held-out data
- Selecting the final model
- Optimizing classification thresholds
- Conducting the financial cost-benefit analysis
- Interpreting workforce predictors
- Developing technical and manager-facing recommendations
- Documenting the complete analysis in R and Quarto

## Reflection

This project represented a significant step forward in my analytics capabilities.

I entered the course with relatively limited experience in R. The assignments leading up to this project required substantial practice troubleshooting code, understanding how modeling workflows fit together, and learning how seemingly small decisions can affect the integrity of an analysis.

By the time I reached the final project, I had put in the repetitions necessary to independently work through a much larger predictive modeling workflow. The project also reinforced the importance of planning analytical work carefully; some model-tuning processes required significant computational time, making thoughtful sequencing and validation especially important.

What I value most about the project is not simply that I built a machine learning model. I developed a much stronger understanding of **why the analytical decisions matter, how to interpret model results, and how to translate those results into a business recommendation.**

With real organizational data, I would begin with significantly more organizational discovery. Workforce data cannot be separated from the people and systems that created it. I would want to understand relevant organizational history, workforce practices, employee experiences, and the broader business environment before interpreting predictive patterns or recommending interventions.

Predictive analytics can identify where an organization should look. Understanding **why** a pattern exists requires context.

## Portfolio Materials

This repository contains a selected portfolio example from a larger graduate analytics project using an **assigned, simulated HR dataset**. It is intended to demonstrate the application of R, predictive modeling, model evaluation, analytical reasoning, and business translation within a People Analytics context.

### View the Project

📄 [**Employee Turnover Analytics Portfolio Sample (PDF)**](employee-turnover-analytics-sample.pdf)

💻 [**Full Quarto Analysis & R Code**](FinalProject.KJ.qmd)

The **portfolio sample** provides a concise, business-facing overview of the project, analytical approach, key findings, and recommendations.

The **Quarto analysis** provides the underlying technical workflow, including data preparation, feature selection, model development and comparison, validation, threshold optimization, and cost-benefit analysis.

> **Note:** The dataset used for this project was an assigned, simulated HR dataset. Financial estimates reflect assumptions provided as part of the graduate assignment and do not represent actual organizational outcomes.

