# Data Folder

This folder contains the data artifacts used throughout the project pipeline. Each subfolder represents one stage in the workflow, where the output of one stage becomes the input of the next.

## Folder Structure

`00_mimic_data/`
Contains the structured MIMIC-IV Demo data after preprocessing.
Main output: `unified_table.csv`, an admission-level table with one row per hospital admission.

`01_profiles/`
Contains deterministic clinical profiles generated from the unified table.
Main files:

* `clean_factual_profiles.jsonl`
* `clean_symptom_profiles.jsonl`

`02_clinical_notes/`
Contains synthetic clinical notes generated from the structured profiles using LLM-based text generation.

`02_clinical_notes/ollama/`
Contains the final locally generated clinical notes used for model training and evaluation.
Main file:

* `clinical_notes.jsonl` — the full deliverable corpus.
* `smoke_test_note.json` / `smoke_test_batch.json` — small sanity-check outputs from early pipeline debugging (single note / small batch), kept for reference only. They are not part of the training corpus and are not consumed by any downstream notebook.

`02_clinical_notes/openai/`
Intentionally empty. See the note on `notebooks/02_synthetic_corpus_pipeline_openai.ipynb` in the main `README.md` — this notebook served as methodological validation for the note-writing prompt, not as a maintained second corpus.

`03_notes_splits/`
Contains the train, validation, and test splits created for model development and evaluation.
Main files:

* `train.jsonl`
* `validation.jsonl`
* `test.jsonl`

## Raw MIMIC-IV Demo Data

The original file `mimic-iv-clinical-database-demo-2.2.zip` is not included in this repository.

To reproduce the pipeline, download the MIMIC-IV Clinical Database Demo v2.2 from PhysioNet ([physionet.org/content/mimic-iv-demo/2.2](https://physionet.org/content/mimic-iv-demo/2.2/)) and place it under:

`data/00_mimic_data/mimic-iv-clinical-database-demo-2.2.zip`

Then run the notebooks in order, starting from:

`notebooks/00_import_and_arrange_mimic.ipynb`
