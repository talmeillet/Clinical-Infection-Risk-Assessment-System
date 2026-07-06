# Data folder

Each subfolder is one stage of the pipeline, in order. Outputs of one stage
are the inputs of the next.

Here it is in English, as plain text instead of a table:

**`00_mimic_data/`** - produced by `notebooks/00_import_and_arrange_mimic.ipynb`. Contains the raw MIMIC-IV demo zip (not committed — see below) plus `unified_table.csv`, one row per admission.

**`01_profiles/`** - produced by `notebooks/01_create_synthetic_profiles.ipynb`. Contains the deterministic clinical profiles: `clean_factual_profiles.jsonl` (stage A-B) and `clean_symptom_profiles.jsonl` (stage C-D, validated).

**`02_clinical_notes/openai/`** - produced by `notebooks/02_synthetic_corpus_pipeline_openai.ipynb`. Contains GPT-4o-mini generated notes — methodological validation run.

**`02_clinical_notes/ollama/`** - produced by `notebooks/03_synthetic_corpus_pipeline_ollama.ipynb`. Contains Llama 3.1:8b generated notes, rebalanced — **the project deliverable**.

**`03_notes_splits/`** - produced by `notebooks/04_split_and_models.ipynb`. Contains `train.jsonl`, `validation.jsonl`, and `synthetic_test.jsonl`.

Want me to update `data/README.md` in the zip I put together earlier to use this format instead of the table?

## Getting the raw MIMIC-IV data

`mimic-iv-clinical-database-demo-2.2.zip` is excluded from version control
(16 MB+, and PhysioNet data-use terms). Download it from
[physionet.org/content/mimic-iv-demo/2.2](https://physionet.org/content/mimic-iv-demo/2.2/)
and place it at `data/00_mimic_data/mimic-iv-clinical-database-demo-2.2.zip`
before running notebook `00`.
