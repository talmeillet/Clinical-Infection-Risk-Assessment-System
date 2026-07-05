# Clinical Infection Risk Assessment System

## Project Motivation

In the healthcare sector, vast amounts of unstructured clinical data—such as admission summaries, physician notes, and shift reports—contain critical clinical cues indicating patient risk. Currently, manual analysis of these texts is slow, inconsistent, and highly dependent on human expertise. This project aims to automate the detection of patients at high risk for **Nosocomial Infections** using natural language processing. By analyzing unstructured clinical narratives, our system assists medical staff in early identification, patient prioritization, and clinical decision support.

## Visual Abstract

<img width="650" height="300" alt="image" src="https://github.com/user-attachments/assets/53880f00-c8e0-4d0e-be92-686dbd2864b4" />

## Datasets

We utilized the **MIMIC-IV Clinical Database Demo (v2.2)**. Since the demo lacked free-text notes, we implemented a sophisticated **Scaffold-and-Augment** pipeline to generate high-fidelity, realistic synthetic clinical summaries that map objective clinical data to subjective patient reports.


זה נשמע מצוין ומסודר מאוד. הנה ניסוח מקצועי ומובנה שתוכלי להעתיק ל-README שלך. הוא שומר על הסדר הלוגי שביקשת ומדגיש את המקצועיות הטכנית והרפואית של הפרויקט.

---

### Project Methodology: The Pipeline from MIMIC-IV to Synthetic Clinical Notes

Our project follows a rigorous, multi-stage pipeline designed to generate realistic clinical narratives while ensuring data integrity and clinical accuracy.

1. **Data Acquisition (MIMIC-IV Demo):** We utilized the **MIMIC-IV Clinical Database Demo v2.2**. This dataset provided the foundational structured records (Hosp & ICU modules) required to build our clinical foundation.
2. **Unified Table Construction:** We synthesized a `unified_table.csv` at the admission-level (one row per `hadm_id`). We carefully selected clinical columns such as demographics, lab results, and procedures, while applying **Anti-Leakage protocols** (generalizing antibiotic names and diagnosis titles) to ensure the model focuses on clinical context rather than explicit labels.
3. **Fact Profile Generation (Scaffold):** Using a Scaffold-and-Augment methodology, we transformed each row from the unified table into multiple, diverse factual profiles in JSON format. Each profile focuses on different clinical aspects (e.g., admission review, lab results, or procedural support), ensuring a rich variety of clinical facts while maintaining the veracity of the original data.
4. **Symptom Enrichment & Augmentation:** To mirror real-world subjective reporting, we integrated a symptom knowledge base derived from official clinical guidelines (CDC, IDSA, NHSN). We augmented the profiles by injecting subjective symptoms tailored to specific infection categories (e.g., respiratory symptoms for pneumonia, urinary symptoms for UTI). This ensures clinical consistency—patients are never assigned contradictory symptoms.
5. **LLM-Based Narrative Synthesis:** We employed local LLMs (via **Ollama**) to convert these structured JSON profiles into natural-sounding clinical narratives. By providing only pre-verified facts, we prevent clinical hallucinations and ensure that the generative model acts as a writer, not an originator of clinical facts.
6. **EDA & Model Training & Evaluation:** We performed Exploratory Data Analysis (EDA) on the generated corpus and proceeded to train and evaluate the downstream infection classification models, validating our results against the ground-truth infection categories.


## Input/Output Example

* **Input**: "A 79-year-old male presented as an urgent transfer from another hospital. He has been experiencing chills, loss of appetite, malaise, and rapid heart rate since admission. During a week-long stay, he underwent percutaneous abdominal drainage and parenteral nutrition. His white blood cell count is 12.6 with 82.9% neutrophils."
* **Output**: `High Infection Concern`


## Repository Structure

```text
├── Data/               # Raw and processed JSON/CSV files
├── Notebook/               # Python scripts and Jupyter notebooks
├── Results/            # Experimental results (CSV/JSON)
├── Slides/             # Project presentation (PPT/PDF)
├── Visuals/            # Visual abstract and result figures
└── README.md

```

## Team Members
- Tal Meillet
- Hodaya Yasayev Klenter
---

### מה חסר להשלמת ה-README?

כדי להפוך אותו ל"מושלם", נצטרך להוסיף את החלקים הבאים ברגע שתסיימי אותם:

1. **Models and Pipelines**: פירוט טכני של המודל שאימנת (איזה LLM שימש כקלאסיפייר? איזה ארכיטקטורה של מודל סיווג?).
2. **Training Process**: פרמטרים של האימון.
3. **Metrics & Results**: טבלאות וגרפים (כשתסיימי את שלב 6).

**איך זה נראה לך עד כה? תרצי שאוסיף דגש מסוים על שלב ספציפי בתהליך העבודה שלך?**
