# Doublet QC Helper — 10x scRNA-seq (Scrublet-based)

**Author:** Kiran Vinod Paul (with AI-assisted development)  
**License:** MIT License  
**Version:** v1.0.0  
**Date:** 2025-10-17  

A lightweight Python utility to **detect and filter doublets** in 10x Genomics single-cell RNA-seq datasets using [Scrublet](https://github.com/AllonKleinLab/scrublet). Includes QC-aware filtering and optional automatic estimation of expected doublet rates from Cell Ranger metrics.

## ✨ Features
- Reads 10x `filtered_feature_bc_matrix` directly
- Automatically estimates expected doublet rate from Cell Ranger `metrics_summary.csv`
- QC filtering by minimum gene/UMI counts, mitochondrial %, and top UMI quantile
- Scrublet-based doublet scoring
- Outputs per-cell doublet calls, QC summary, and optional plots
- Supports HPC setups with wheel-only installs (no compiler needed)

## ⚙️ Installation
```bash
git clone https://github.com/<yourusername>/doublet-qc-helper.git
cd doublet-qc-helper
python3 -m venv env
source env/bin/activate
pip install -r requirements_min_no_plot.txt
pip install --only-binary=:all: --no-deps scanpy==1.10.2
```

## 🚀 Usage
```bash
python doublet_qc_helper.py   --mtx /path/to/filtered_feature_bc_matrix   --metrics /path/to/metrics_summary.csv   --out run1
```

### Optional arguments
- `--no-plots`: disable plot generation (HPC-safe)
- `--expected-rate`: override doublet rate manually
- `--pca-comps`: number of PCA components (auto-limited by data size)
- `--score-quantile`: manual score cutoff (e.g. 94 for top 6% doublets)

## 🧪 Example Data
```bash
python doublet_qc_helper.py   --mtx example_data   --metrics example_data/metrics_summary.csv   --out test_run   --no-plots
```

## 📤 Outputs
- `*_doublet_scores.csv` — per-cell QC and doublet calls  
- `*_QC_summary.txt` — thresholds, doublet rate, summary stats  
- `*_plot_*.png` — optional histograms for QC metrics

## 🧬 Downstream Filtering (Seurat)
```r
singlets <- read.table("run1_singlets.txt", stringsAsFactors = FALSE)$V1
seu <- subset(seu, cells = singlets)
```

## 📄 License
MIT License. See [LICENSE](LICENSE).

## 📢 Citation
- Scrublet: Wolock SL, Lopez R, Klein AM. *Cell Syst.* 2019.
- Scanpy: Wolf FA, Angerer P, Theis FJ. *Genome Biol.* 2018.

If you use this tool, please cite this repository:
```
Paul KV (2025). Doublet QC Helper (Scrublet-based) for 10x scRNA-seq. v1.0.0.
https://github.com/kiranvpaul/Doublet-QC-helper
```
