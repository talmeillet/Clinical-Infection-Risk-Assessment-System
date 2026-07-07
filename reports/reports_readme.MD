## Reports Folder

All figures and tables here are generated automatically by the notebooks — nothing in this folder is hand-edited. Regenerating them just means re-running the relevant notebook.

### EDA
- `eda_mimic.png` — from `notebooks/00_import_and_arrange_mimic.ipynb`. Overview of the MIMIC-IV cohort before any synthetic text is generated (label balance, infection categories, vitals, age/gender).
- `eda_synthetic_notes.png` — from `notebooks/04_split_and_models.ipynb`. Overview of the synthetic note corpus itself, before splitting (label balance, infection source, note length, symptom severity).

### Training
- `training_curve_pubmedbert.png`, `training_curve_gpt2.png` — training/validation loss per epoch for each model, with the best (lowest-loss) epoch marked.

### Test-set evaluation
- `confusion_matrix_pubmedbert_test.png`, `confusion_matrix_gpt2_test.png` — LOW/HIGH confusion matrix on the held-out, patient-disjoint test split.
- `infection_type_accuracy_pubmedbert_test.png`, `infection_type_accuracy_gpt2_test.png` — % of test-set notes correctly classified, broken down by infection type (ground truth).
- `infection_type_predicted_label_pubmedbert_test.png`, `infection_type_predicted_label_gpt2_test.png` — how many test notes of each infection type the model actually predicted as LOW vs. HIGH (the model's-eye view, as opposed to the ground-truth breakdown above).
- `infection_type_performance_pubmedbert_test.csv`, `infection_type_performance_gpt2_test.csv` — the numbers behind the two charts above, per infection type.

### Summary
- `model_comparison_final.csv` — recall/precision/F1 (HIGH class) and ROC-AUC for both models, on both the validation and test splits. The headline comparison table; see the main `README.md` Results section for the interpretation.
