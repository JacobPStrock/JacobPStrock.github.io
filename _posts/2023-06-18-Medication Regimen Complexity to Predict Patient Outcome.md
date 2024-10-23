---
usemathjax:
    true
header: 
    teaser: /assets/images/Post_Images/nonproportional_hazards.jpeg
---

![Sensitivity and specificity](/assets/images/Post_Images/MedicationRegimenComplexity/jcm_sensitivity_specificity_mortality.png)

Medication Regimen Complexity (MRC) may not be a term familiar to those outside of the medical field, yet in clinical circles, it plays an integral role in assessing a patient's prescribed medications. MRC is a comprehensive evaluation that extends beyond merely tallying the number of medications. It delves into the specifics of each medication: the type, dosing frequency, and potential interactions. This deeper dive provides a holistic view of a patient's health status and treatment trajectory. However, there is uncertainty as to the optimal metric, which translates to uncertainy in using these metrics for clinical decisions. It's within this critical aspect of healthcare that I applied predictive classification models, aiming to unveil the predictive potential of MRC and its variants in determining patient outcomes.

Working alongside the clinical research experts Todd Brothers PhD, PharmD, and Mohammad Al-Mamun PhD, during my time at the Northeast Big Data and Innovation Hub, I used predictive models to evaluate the efficacy of two widely utilized MRC indices. Through these predictive analysis and other statistical comparisons, we explored the data to find the most effective metrics for predicting patient outcomes.

In this new project, I'll show the power of bringing modeling techniques in healthcare analytics, for the application in MRC metrics. Although the sensitive nature of our data restricts me from sharing specifics or the precise analysis code, I will provide a thorough rundown of our methodological approach, the intriguing findings it yields, and the implications for future patient care.
<object data="/assets/supplementaryfiles/JCM_MRCI_2022.pdf" width="1000" height="1000" type='application/pdf'></object>


## Objective:

The objective of this study is to apply advanced statistical modeling techniques to assess and compare the predictive power of two commonly used Medication Regimen Complexity (MRC) indices for patient outcomes: MRCI & MRC-ICU.


## Data:

This study recieved all proper ethical approval (see publication details), and used deidentified, retrospective data.

The retrospective cohort study at Roger William Medical Center, Providence, Rhode Island, included 317 adult patients admitted to the intensive care unit (ICU) between 1 February 2020 and 30 August 2020. It included detailed information on patient demographics, laboratory measurements, vitals, medications, and outcome including time on mechanical ventilation, length of stay in the ICU and mortality.

![Cohort Descriptive](/assets/images/Post_Images/MedicationRegimenComplexity/jcm_table1.png)

## Data Processing:

MRCI and MRC-ICU were calculated according to the established criteria. We established cutoff values for both MRC scores based on their distribution within 24 hours of ICU admission. Since there are no standardized cutoff values specifically for critically ill patients, we selected the median values as our cutoff points. The "high" MRCI scoring cohort was defined as having scores greater than 63, while the "high" MRC-ICU cohort was defined as having scores greater than 6. We examined three clinical outcomes: mortality, length of stay (LOS), and the need for mechanical ventilation (MV) in the ICU. To assess LOS, we created a binary variable where LOS was labeled as 0 if it was less than 48 hours and 1 if it exceeded 48 hours. The need for MV was determined using a binary variable after 48 hours of ICU admission, with 0 indicating no mechanical ventilation and 1 indicating the use of mechanical ventilation. Hemodynamic instability was defined by the presence of hypotension (systolic blood pressure < 100 mmHg), mean arterial pressure below 65 mmHg, or abnormal heart rate (arrhythmia or heart rate below 60 bpm or above 100 bpm).

Descriptive statistics were employed to summarize the study population, presenting continuous variables as means and interquartile ranges (IQRs), and categorical variables as frequencies and proportions. Student's t-test, chi-squared (χ²) test, or Fisher's exact test were used to compare clinical characteristics between survivor and non-survivor cohorts, as well as low- and high-MRC-scoring groups. Physiological and clinical characteristics were examined among the survivor and non-survivor cohorts, and severity scores (SAPS II, APACHE II, and CCI) were incorporated

## Analysis & Results:

To identify the predictors of clinical outcomes (mortality, length of stay [LOS], and need for mechanical ventilation [MV]), four multivariable logistic regression models were employed. These models included a combination of severity scores (APACHE II and SAPS II), Medication Regimen Complexity Index (MRCI), Medication Regimen Complexity in Intensive Care Unit (MRC-ICU), demographic variables, Charlson comorbidity index (CCI), and drug classes. Model I consisted of demographics, APACHE II, SAPS II, CCI, and 15 drug classes. Model II included demographics, MRCI at 24 hours and 48 hours, CCI, and drug classes. Model III incorporated demographics, MRC-ICU at 24 hours and 48 hours, CCI, and drug classes. Model IV encompassed all variables (refer to Table S3 for details). For the LOS models, MRCI and MRC-ICU values at 48 hours were excluded as the binary values were based on a 48-hour threshold after ICU admission. Significant predictors (p < 0.05) were selected using a stepwise forward selection method. 

Feature selection was performed using an L1 penalization technique called LASSO, which minimizes the influence of multicollinearity. The demographic variables considered were age, sex, height, weight, body mass index (BMI), and race. Odds ratios (OR) were calculated for each outcome of interest. All analyses were conducted using R software, specifically Version 4.0.0 (R Project for Statistical Computing), and implemented packages such as glm, glmnet, and ggplot2.

![Patient Classification](/assets/images/Post_Images/MedicationRegimenComplexity/jcm_violinplot.png)

The MRC scores, both MRCI (Medication Regimen Complexity Index) and MRC-ICU (Medication Regimen Complexity in Intensive Care Unit), showed significant associations with critical outcomes like mortality, length of ICU stay (LOS), and the need for mechanical ventilation (MV). This was similar to APACHE II and SAPS II scores, which are designed to predict mortality risk and the severity of disease.

To evaluate the prediction ability of MRC scores for mortality, LOS, and the need for MV, seven logistic classifier models were constructed without any variable selection. Correlation analysis was performed using the Pearson correlation coefficient, and the SAPS II severity score was chosen due to its high correlation with the APACHE II classification system (see Figure S1). The best-fit models were selected based on the best Akaike information criterion (AIC) measurement during cross-validation, employing an interactive process. All predictor variables were included in each prediction model setup to explicitly explore their individual roles. Model performance was assessed using the area under the receiver operating characteristic (ROC) curve (AUC), with an AUC of at least 0.7 considered acceptable. The models underwent a "leave-one-out" cross-validation method with 10,000 repetitions, and the AUC was selected as the overall performance measure. Sensitivity and specificity analyses were conducted for each of the three outcomes. Additionally, variable importance rankings were recorded for each clinical outcome in the prediction models.

![ROC](/assets/images/Post_Images/MedicationRegimenComplexity/jcm_sensitivity_specificity.png)


The ROC analysis revealed that models incorporating Medication Regimen Complexity (MRC) scores alongside traditional severity scores like APACHE II and SAPS II demonstrated comparable or slightly superior predictive power, as evidenced by AUC values. These findings highlight the added value of MRC scores in enhancing model accuracy not only for mortality but also for predicting the length of ICU stay and the necessity for mechanical ventilation, suggesting that MRC scores capture additional patient risk factors not fully accounted for by physiological and clinical measures alone.

![Table 3](/assets/images/Post_Images/MedicationRegimenComplexity/jcm_table3.png)

* Both Medication Regimen Complexity Index (MRCI) and Medication Regimen Complexity in Intensive Care Unit (MRC-ICU) scores were significantly associated with clinical outcomes, including mortality, length of stay (LOS), and the need for mechanical ventilation (MV).
* Higher MRC scores were linked to hemodynamic instability and higher severity scores, such as APACHE II and SAPS II.
* Survivors had significantly lower MRCI, MRC-ICU, APACHE II, and SAPS II scores compared to non-survivors.
* The addition of MRC-ICU and SAPS II scores improved the prediction accuracy of clinical outcomes.
* Hispanic ethnicity was identified as an important variable in predicting mortality, LOS, and the need for MV.
* The use of vasopressors, pulmonary agents, paralytic agents, and psychiatric medications significantly influenced clinical outcomes.
* The study findings suggest that MRC scores can be valuable in identifying high-risk patients and optimizing clinical management.
* Logistic regression models and logistic classifier models demonstrated the predictive capabilities of MRC scores for patient outcomes.
* The L1 penalization technique (LASSO) was used for variable selection, minimizing multicollinearity and improving prediction accuracy.
* The study highlights the importance of incorporating MRC scores into standardized severity index scoring tools to enhance the prediction of critical care outcomes.

## Conclusions:

1. Medication Regimen Complexity (MRC) scores, including MRCI and MRC-ICU, are significantly associated with clinical outcomes, such as mortality, length of stay (LOS), and the need for mechanical ventilation (MV). These scores provide valuable insights into a patient's health status and treatment course.

2. Higher MRC scores are linked to hemodynamic instability, higher severity scores, and poorer clinical outcomes. Monitoring and managing medication regimens based on MRC scores can help identify patients at higher risk and optimize their care.

3. Incorporating MRC scores, along with severity-of-illness scores like APACHE II and SAPS II, improves the accuracy of predicting clinical outcomes. This integration can enhance clinical decision-making and resource allocation in critical care settings.

4. The use of specific medications, such as vasopressors, pulmonary agents, paralytic agents, and psychiatric medications, significantly influences patient outcomes. Understanding the impact of these medications can guide medication selection and management strategies to improve patient outcomes.

5. The inclusion of MRC scores and medication-related factors in predictive models and statistical analysis provides valuable insights for clinicians and researchers. These models can assist in identifying high-risk patients, optimizing medication regimens, and improving patient-centered care.

6. The study emphasizes the need for standardized MRC scoring and the integration of MRC scores into clinical decision support tools. By incorporating MRC scores into electronic health records and clinical workflows, healthcare professionals can receive alerts and recommendations for medication review and safer patient care.

7. Future research should focus on validating the findings using larger patient cohorts and diverse populations. Additionally, exploring the role of MRC scores in specific high-acuity diseases and evaluating the impact of interventions based on MRC assessments would further enhance our understanding of medication regimen complexity and patient outcomes in critical care settings.