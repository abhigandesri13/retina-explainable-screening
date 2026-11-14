# RetinaExplain AI

**An Explainable Deep Learning System for Diabetic Retinopathy Screening**

An educational and research-oriented computer vision project to classify diabetic retinopathy (DR) severity from retinal fundus images, provide visual explanations, and serve reproducible inference through an API.

> **Medical-use limitation:** This project is not a clinically validated diagnostic device. Its predictions must not be used to make medical decisions.

## Objectives

- Build a reproducible five-class DR image-classification pipeline.
- Assess image quality and document preprocessing.
- Compare transfer-learning architectures using leakage-aware evaluation.
- Evaluate macro F1, balanced accuracy, class-wise sensitivity/specificity, quadratic weighted kappa, and calibration—not accuracy alone.
- Generate Grad-CAM visualizations and investigate their limitations.
- Track experiments and model artifacts.
- Package inference behind an API and containerize the application.

## DR severity classes

| Grade | Label |
|---:|---|
| 0 | No DR |
| 1 | Mild |
| 2 | Moderate |
| 3 | Severe |
| 4 | Proliferative DR |

Verify this mapping against dataset metadata before training.

## Planned stack

Python, PyTorch, torchvision, timm, OpenCV, Albumentations, scikit-learn, MLflow, Optuna, Grad-CAM, FastAPI, pytest, Docker, GitHub Actions. Kaggle Notebooks are the primary development and free-GPU environment. Tools will be introduced only when needed.

## Initial dataset candidate

[Diabetic Retinopathy 224x224 Gaussian Filtered — Kaggle](https://www.kaggle.com/datasets/sovitrath/diabetic-retinopathy-224x224-gaussian-filtered)

Selection remains provisional until provenance, license, directory structure, label mapping, class counts, duplicates and split metadata are audited. Do not commit dataset images or credentials.

Potential external-validation candidate: [IDRiD](https://idrid.grand-challenge.org/Data/). Access terms, label compatibility and possible overlap must be checked before use.

## Reproducibility and data integrity

- Keep the test set untouched during model selection and threshold tuning.
- Prefer patient-level splits when reliable patient identifiers exist.
- If patient identifiers are unavailable, document the limitation and use defensible grouping and duplicate checks.
- Record random seeds, package versions, data manifests, split definitions and experiment configurations.
- Never report metrics that have not been produced by an actual run.

## Repository layout

```text
configs/                 Data, model and training configuration
notebooks/               Exploration and experiment notebooks
src/data/                Dataset loading and preprocessing
src/models/              Model construction
src/training/            Training loops and optimization
src/evaluation/          Metrics and evaluation
src/explainability/      Grad-CAM and related methods
src/inference/           Prediction pipeline
api/                     FastAPI application
tests/                   Automated tests
scripts/                 Reproducible utilities
reports/                 Analysis and evaluation reports
artifacts/               Local model artifacts (not committed)
```

## Development status

- [x] Existing TensorFlow/Keras notebook reviewed as a baseline artifact.
- [x] New GitHub repository created.
- [ ] Phase 2: environment and repository configuration
- [ ] Phase 3: dataset audit and engineering
- [ ] Phase 4: PyTorch model experiments
- [ ] Phase 5: model evaluation
- [ ] Phase 6: explainability
- [ ] Phase 7: experiment and model management
- [ ] Phase 8: API and user interface
- [ ] Phase 9: containerization and deployment
- [ ] Phase 10: portfolio documentation and release

## Responsible reporting

Report class-wise performance and uncertainty. Discuss false negatives, false positives, calibration, dataset bias, distribution shift and external validation. A heatmap is not proof of clinical reasoning or lesion detection.

## License

Choose a repository code license only after reviewing dataset terms and intended code licensing. Dataset contents remain subject to their original terms.
