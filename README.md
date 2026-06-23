# V-DistilBERT: Vocabulary-Expanded DistilBERT for Cross-Site Scripting (XSS) Payload Detection

## Project Summary
This repository accompanies the research proposal *"A Fine-Tuned DistilBERT Architecture with Vocabulary-Expanded Tokenization for Cross-Site Scripting Payload Detection"* (Emmanuel Acquah, KNUST, 2026).

V-DistilBERT engineers DistilBERT (Sanh et al., 2019) via a dual [M]-MODIFY operation: (1) WordPiece tokenizer vocabulary expansion with domain-specific web-security tokens to address sub-word fragmentation of XSS-relevant terminology, and (2) a re-calibrated classification head tuned for the length and structure of short, often-obfuscated HTML/JavaScript payload text. The model is benchmarked against a locked baseline DistilBERT and three classical-ML baselines (XGBoost, SVM, Random Forest) on a public XSS payload corpus, with a post-hoc SHAP explainability layer auditing token-level classification decisions.

The engineering and deployment rationale is grounded in Technology Threat Avoidance Theory (Liang & Xue, 2009) and motivated by Ghana's documented web-application threat landscape, where lightweight, low-compute security NLP tooling is directly relevant to SME and e-government capacity constraints.

## Planned Repository Structure
```
v-distilbert-xss-ghana/
├── README.md
├── requirements.txt
├── data/
│   └── public/                          # Cleaned/split copy of the Shah & Hussain (2024) Kaggle XSS corpus
├── notebooks/
│   ├── 01_baseline_distilbert.ipynb     # Phase 1: locked baseline (never modified after first run)
│   ├── 02_classical_ml_baselines.ipynb  # Phase 1: XGBoost / SVM / Random Forest baselines
│   ├── 03_vdistilbert_engineering.ipynb # Phase 2: V-DistilBERT construction (vocab expansion + head re-calibration)
│   └── 04_evaluation_shap.ipynb         # Phase 3: comparison, Wilcoxon test, SHAP attribution
├── models/
│   └── checkpoints/                     # Mirrored to Kaggle Dataset output (see Section 4D)
└── results/
    └── comparison_tables/
```

## Dataset
- **Source:** Cross-Site Scripting (XSS) Dataset for Deep Learning (Shah & Hussain, 2024), Kaggle.
  https://www.kaggle.com/datasets/syedsaqlainhussain/cross-site-scripting-xss-dataset-for-deep-learning
- **Composition:** 13,686 labelled HTML/JavaScript text samples (7,373 malicious / 6,313 benign).
- **Tier:** Public dataset only (acknowledged MEDIUM tier per the project's marking scheme; no primary/field data collected — see Section 4C/5 of the proposal for the full rationale).

## Status
This repository is created ahead of model training, per the project's Phase 0 (reproducible environment setup). Code will be committed incrementally as each phase (baseline → engineering → evaluation) is completed, per the timeline in Section 10 of the proposal.

## Citation
If you use this repository, please cite the associated research proposal (DOI to be registered via Zenodo upon first stable release).

## License
MIT License (code). Dataset license follows the source dataset's own terms (Shah & Hussain, 2024, Kaggle).
