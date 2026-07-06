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

* `clinical_notes.jsonl`

`03_notes_splits/`
Contains the train, validation, and synthetic test splits created for model development and evaluation.
Main files:

* `train.jsonl`
* `validation.jsonl`
* `synthetic_test.jsonl`

## Raw MIMIC-IV Demo Data

The original file `mimic-iv-clinical-database-demo-2.2.zip` is not included in this repository.

To reproduce the pipeline, download the MIMIC-IV Clinical Database Demo v2.2 from PhysioNet ([physionet.org/content/mimic-iv-demo/2.2](https://physionet.org/content/mimic-iv-demo/2.2/)) and place it under:

`data/00_mimic_data/mimic-iv-clinical-database-demo-2.2.zip`

Then run the notebooks in order, starting from:

`notebooks/00_import_and_arrange_mimic.ipynb`
