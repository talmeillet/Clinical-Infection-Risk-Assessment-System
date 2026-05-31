# Post-Op-Infection-Prediction-NLP
## Motivation
Surgical Site Infections (SSI) are among the important postoperative complications and may lead to prolonged hospitalization, readmission, additional treatment, and increased healthcare burden. Discharge summaries often contain rich clinical information that may indicate elevated SSI risk, including surgical details, comorbidities, laboratory values, antibiotic treatment, postoperative course, and wound status. However, this information is usually written as unstructured free text, making it difficult to use directly for automated risk assessment. Since real labeled discharge summaries are difficult to access due to privacy and ethical constraints, this project investigates whether LLM-generated synthetic clinical notes can be used to train and evaluate text classification models for SSI risk prediction.

## Problem Definition
We define the task as binary text classification. 
* Input: A synthetic free-text postoperative discharge summary.
* Output: A binary label predicting the patient's status: High SSI Risk or Low SSI Risk.

Given a synthetic free-text postoperative discharge summary, the model predicts whether the patient is at High SSI Risk or Low SSI Risk. The synthetic summaries will be generated using an attributed generation approach, where each example is conditioned on sampled medical and stylistic attributes such as surgery type, urgency, wound class, comorbidities, laboratory values, antibiotic prophylaxis, postoperative course, and clinical writing style. Labels will be assigned according to explicit literature-based risk rules rather than free-form LLM judgment. The trained classifiers will be compared against zero-shot and few-shot LLM baselines using clinically relevant metrics, especially recall for the high-risk class.



תקציר ויזואלי
בסיסי הנתונים בהם השתמשתן
שיטות ליצירת דאטה סינתטי (ואוגמנטציה)
דוגמאות לקלט ולפלט, 
מודלים ותהליכי העבודה, 
פרמטרים ותהליך האימון, 
מדדי ההערכה (Metrics), 
התוצאות, 
תיאור מבנה הריפוזיטורי (התיקיות)  
שמות חברות הצוות
.
