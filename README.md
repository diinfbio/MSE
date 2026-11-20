# Multisign Encoding (MSE): Experimental Data and Statistical Results

This repository accompanies the manuscript **“Multisign Encoding for Categorical Variables: An Algebraic Representation for Distance-Based Learning”**, prepared for *Information Sciences*.

It provides the benchmark datasets in ARFF format, the experimental evaluation metrics, and statistical summaries supporting the manuscript's tables and findings.

## Study overview

- **16 binary-classification benchmark datasets** in their original ARFF file format.
- **18 categorical-encoding approaches:** six MSE formulations and 12 comparison methods.
- **11 experimental seeds (1–11)** and **stratified 20-fold cross-validation**.
- **k-nearest neighbors (k = 5)** with method-specific distance measures.
- **Primary outcome:** macro-F1; supplementary metrics include accuracy and AUROC.
- **Statistical inference:** paired dataset-level comparisons, Friedman, Wilcoxon signed-rank tests, and equivalence testing (TOST), with Holm adjustments.

## Repository contents

| Location | Description |
| --- | --- |
| `datasets/*.arff` | The 16 benchmark datasets, using the original ARFF filenames listed below. |
| `data/seed_level_metrics_16_datasets.csv` | Macro-F1, accuracy, and AUROC metrics for each dataset, method, and seed (3,168 records). Each score summarizes 20 cross-validation folds. |
| `data/dataset_encoding_summary_16_datasets.csv` | Dataset-by-method averages, standard deviations across seeds, and macro-F1 ranks. |
| `data/dimensionality_vs_baselines_16_datasets.csv` | Coordinate-count comparisons for MSE and reference encodings. |
| `statistics/average_ranks_16_datasets.csv` | Mean macro-F1 and average rank for the 18 encoding methods. |
| `statistics/friedman_macro_f1_16_datasets.csv` | Friedman omnibus test results. |
| `statistics/seven_paired_comparisons_16_datasets.csv` | Seven paired method comparisons, Wilcoxon and TOST p-values, Holm adjustments, and 90% TOST confidence intervals. |
| `statistics/dimensionality_summary_16_datasets.csv` | Average encoded coordinate counts and relative reduction. |
| `metadata/dataset_mapping.csv` | Dataset filenames, manuscript labels, row counts, and original attribute counts. |
| `metadata/encoder_name_mapping.csv` | Encoding method identifiers and display labels. |
| `SHA256SUMS.txt` | SHA-256 checksums for repository files. |

## Benchmark datasets

The `dataset` field in the CSV files matches the exact filename stem of the corresponding ARFF file in `datasets/`.

| ARFF file | Manuscript dataset label |
| --- | --- |
| `adult.arff` | adult |
| `Australian.arff` | Australian |
| `bank-marketing.arff` | bank-marketing |
| `compass.arff` | compass |
| `credit-approval.arff` | credit-approval |
| `credit-g.arff` | credit-g |
| `cylinder-bands.arff` | cylinder-bands |
| `dresses-sales.arff` | dresses-sales |
| `Insurance.arff` | Insurance |
| `jungle_chess_2pcs_endgame_elephant_elephant.arff` | jungle-chess-2pcs-endgame-elephant-elephant |
| `KDD.arff` | KDD |
| `kdd_internet_usage.arff` | kdd-internet-usage |
| `molecular-biology_promoters.arff` | molecular-biology-promoters |
| `national-longitudinal-survey-binary.arff` | national-longitudinal-survey-binary |
| `sick.arff` | sick |
| `thoracic_surgery.arff` | thoracic-surgery |

The source repositories and bibliographic references for these public datasets are identified in the manuscript. Please credit the original dataset providers when reusing their data.

## Statistical summaries

For each dataset and method, macro-F1 is averaged across the 20 folds within a seed and then across the 11 seeds. Dataset-level averages are used for paired statistical comparisons and method ranks.

- **Friedman test:** compares 18 methods across 16 datasets.
- **Wilcoxon signed-rank tests:** two-sided asymptotic tests with continuity correction; Holm adjustment across the seven specified paired comparisons.
- **TOST equivalence tests:** paired t-based two one-sided tests with an equivalence margin of ±0.01 macro-F1 and 15 degrees of freedom; Holm adjustment across the seven TOST p-values.
- **Dimensionality:** coordinate counts and relative reductions are summarized separately from predictive metrics.

Representative results (rounded to manuscript precision):

| Measure | Value |
| --- | ---: |
| Average rank: Ordinal | 5.750 |
| Average rank: One-Hot | 6.781 |
| Average rank: fixed MSE | 7.156 |
| Friedman χ²(17) | 36.562 |
| Friedman p-value | 0.003856 |
| Mean paired macro-F1 difference: fixed MSE − One-Hot | −0.002644 |
| Holm-adjusted TOST p-value: fixed MSE vs. One-Hot | 0.00330 |
| Mean coordinate-count reduction: MSE vs. One-Hot | 84.1% |

## Using the data

1. Open the ARFF files under `datasets/` with an ARFF-compatible reader.
2. Join experimental results to benchmark datasets using the `dataset` field and the ARFF filename stem.
3. Use the seed-level CSV for descriptive aggregation and the statistics CSV files for the reported comparisons.
4. Use `metadata/encoder_name_mapping.csv` to interpret method identifiers.

## Citation

When using the experimental results, cite **“Multisign Encoding for Categorical Variables: An Algebraic Representation for Distance-Based Learning”** (Aliaga-Rojas and Inostroza-Ponta). Cite the original dataset sources for any benchmark data reused from `datasets/`. Repository publication details may be added after archival release.
