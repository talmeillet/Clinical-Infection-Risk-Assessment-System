# Clinical Infection Risk Assessment System

## Project Motivation

In the healthcare sector, vast amounts of unstructured clinical data—such as admission summaries, physician notes, and shift reports—contain critical clinical cues indicating patient risk. Currently, manual analysis of these texts is slow, inconsistent, and highly dependent on human expertise. This project aims to automate the detection of patients at high risk for **Nosocomial Infections** using natural language processing. By analyzing unstructured clinical narratives, our system assists medical staff in early identification, patient prioritization, and clinical decision support.

## Visual Abstract

*[כאן כדאי להוסיף תרשים או איור של זרימת העבודה: מ-MIMIC-IV דרך ה-Scaffold-and-Augment ועד לסיווג הסופי]*

## Datasets

We utilized the **MIMIC-IV Clinical Database Demo (v2.2)**. Since the demo lacked free-text notes, we implemented a sophisticated **Scaffold-and-Augment** pipeline to generate high-fidelity, realistic synthetic clinical summaries that map objective clinical data to subjective patient reports.

## Methodology: The Scaffold-and-Augment Pipeline

Our architecture separates deterministic clinical logic from generative text creation to ensure consistency and prevent clinical hallucinations:

* **Phase A: Fact Profile Generation**: Mapping rows from the `unified_table.csv` into hierarchical JSON structures (demographics, labs, procedures, etc.). This expanded our 275 original admissions into ~950 factual profiles.
* **Phase B: Symptom Enrichment**: Augmenting profiles with subjective symptoms (e.g., pain, chills) based on official clinical guidelines (CDC, IDSA, StatPearls). We generated ~1,900 enriched profiles, ensuring a balanced distribution of severity levels and infection categories.
* **Phase C: Quality Assurance**: Rigorous validation to ensure label consistency and prevent **label-leakage** (ensuring no clinical labels appear in the synthetic text).
* **Phase D: LLM Synthesis**: Using local LLMs (via Ollama) to convert verified clinical facts into natural-sounding narratives. This approach provides:
* **Control**: Every clinical decision is traceable.
* **Diversity**: Variance is driven by factual profiles rather than just stylistic LLM output.
* **Accuracy**: Prevention of impossible clinical scenarios (e.g., verbal reports from intubated patients).


## Input/Output Example

* **Input**: Clinical note fragment regarding a 67-year-old male with elevated WBC, invasive monitoring, and documented weakness.
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
