# Notebooks

Run in order — each notebook consumes the previous one's output from `../data/`.

1. **`00_import_and_arrange_mimic.ipynb`** — Builds `unified_table.csv`, one
   row per hospital admission, from the MIMIC-IV demo `hosp` + `icu` modules.
2. **`01_create_synthetic_profiles.ipynb`** — Turns each admission into a
   structured, de-identified clinical profile (fully rule/template based, no
   LLM) that later feeds the note-writer.
3. **`02_synthetic_corpus_pipeline_openai.ipynb`** — Generates clinical notes
   with GPT-4o-mini. Serves as methodological validation, not the deliverable.
4. **`03_synthetic_corpus_pipeline_ollama.ipynb`** — Generates clinical notes
   with Llama 3.1:8b (local, via Ollama), reusing the same profiles and
   prompt design as notebook 02. This corpus, after rebalancing, is the
   project deliverable.
5. **`04_split_and_models.ipynb`** — EDA on the synthetic corpus, train /
   validation / test split, and classifier training for infection-concern
   prediction.

## Note on cached model weights

`transformers`/`torch` model downloads are
cached locally when notebook 04 runs. That cache is intentionally excluded
from version control (see `../.gitignore`) — it's re-downloaded automatically
on first run, no manual step needed.
