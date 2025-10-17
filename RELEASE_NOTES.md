# 🆕 Doublet QC Helper v1.0.0 — Initial Release (October 17, 2025)

**Author:** Kiran Vinod Paul  
**License:** MIT

## Features
- Direct 10x input (`filtered_feature_bc_matrix`)
- Automatic expected doublet rate estimation from Cell Ranger metrics
- QC filtering (genes, UMIs, mito%, top UMI quantile)
- Scrublet-based doublet scoring
- Optional plotting of QC histograms
- Compatible with CentOS HPC environments (no compiling)
- Example dataset included

## Known Limitations
- Designed for 10x Chromium data (single-cell RNA-seq)
- Experimental doublet detection (hashing, MULTI-seq) not included
- Small toy datasets may require adjusting `--pca-comps`

## Citation
If you use this tool, please cite:
```
Paul KV (2025). Doublet QC Helper (Scrublet-based) for 10x scRNA-seq. v1.0.0.
https://github.com/<yourusername>/doublet-qc-helper
```
