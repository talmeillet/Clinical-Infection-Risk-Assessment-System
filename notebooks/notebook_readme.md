# Notebooks

Run in order - each notebook consumes the previous one's output from `../data/`.

1. **`00_import_and_arrange_mimic.ipynb`** - Builds `unified_table.csv`, one row per hospital admission, from the MIMIC-IV demo `hosp` + `icu` modules.
2. **`01_create_synthetic_profiles.ipynb`** - Turns each admission into structured, de-identified clinical profiles.
   This stage performs rule-based profile augmentation by creating multiple factual views of each admission (e.g., laboratory-focused, procedure-focused, treatment-focused, and balanced clinical profiles), while preserving the original patient facts.  
   These profiles are later used as controlled inputs for LLM-based clinical note generation.
3. **`02_synthetic_corpus_pipeline_openai.ipynb`** - Generates synthetic clinical notes using GPT-4o-mini.  
   This notebook was used as a methodological validation stage for testing the synthetic generation pipeline, prompt structure, factual consistency rules, and quality-control checks.
   The original OpenAI-generated outputs were preserved for comparison. Re-running this notebook requires a valid OpenAI API key with available quota, and outputs may differ from the original generation.  
   The final project corpus was generated locally using Ollama (Notebook 03).
4. **`03_synthetic_corpus_pipeline_ollama.ipynb`** - Generates the final synthetic clinical note corpus using Llama 3.1:8B locally through Ollama.
   This notebook uses the same factual profiles and overall generation methodology validated in Notebook 02, with prompt adaptations and additional quality-control refinements designed for the local model behavior.
   The generation process includes checks for diagnosis leakage, unsupported clinical statements, repetitive templates, and factual consistency before creating the final deliverable dataset.
5. **`04_split_and_models.ipynb`** - Performs exploratory data analysis,patient-level train / validation / test splitting, and infection-concern classification. Establishes a zero-shot baseline using the same base LLM (Llama 3.1:8b via Ollama) that generated the notes - prompted directly, with no task-specific training - to measure how much fine-tuning actually adds over just asking the model.
Two fine-tuned classifiers, PubMedBERT and GPT-2, are then trained and evaluated against that baseline.
During experimentation, different synthetic augmentation settings were evaluated. Initial experiments with larger augmentation produced more generated notes per admission but introduced higher similarity between samples.
The final dataset uses a reduced augmentation strategy (3 generated notes per admission), improving the balance between dataset size, diversity, and model performance.

## Note on cached model weights

`transformers`/`torch` model downloads are
cached locally when notebook 04 runs. That cache is intentionally excluded
from version control (see `../.gitignore`) - it's re-downloaded automatically
on first run, no manual step needed.
