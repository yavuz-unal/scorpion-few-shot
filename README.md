# Few-Shot Learning for Sex Classification in Venomous Scorpions

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20796510.svg)](https://doi.org/10.5281/zenodo.20796510)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains the code accompanying the manuscript:

> **Ünal, Y., & Koç, H.** Few-Shot Learning for Sex Classification in Venomous Scorpions: A Framework for Data-Scarce Biological Research. *(Under review at Pattern Analysis and Applications.)*

## Overview

This project implements few-shot learning experiments for sex classification of the scorpion species *Aegeaeobuthus gibbosus* (Brullé, 1832). The framework is designed to address data scarcity in biological domains where specimen collection is constrained by safety, ecological, and logistical factors.

## Dataset

The associated image dataset is archived on Zenodo:

- **DOI**: [10.5281/zenodo.20796510](https://doi.org/10.5281/zenodo.20796510)
- **Composition**: 198 high-resolution images of 99 individuals (50 female, 49 male), each photographed in dorsal and ventral views
- **Format**: JPEG, controlled laboratory conditions

> **Note**: The dataset is currently under embargo pending paper acceptance. A reviewer-only access link is provided in the manuscript submission.

## Quick Start

### 1. Clone this repository

```bash
git clone https://github.com/[USERNAME]/scorpion-few-shot.git
cd scorpion-few-shot
```

### 2. Download and extract the dataset

After publication, download from Zenodo and extract:

```bash
# Place the extracted folder in the repo root
unzip aegeaeobuthus_gibbosus_images.zip
```

The directory structure should look like:

```
scorpion-few-shot/
├── scorp_few_shot.ipynb
├── README.md
├── requirements.txt
└── aegeaeobuthus_gibbosus_dataset/
    ├── female-dorsal/
    ├── female-ventral/
    ├── male-dorsal/
    ├── male-ventral/
    ├── female.txt
    └── male.txt
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the notebook

```bash
jupyter notebook scorp_few_shot.ipynb
```

The notebook can also be run directly in Google Colab (Drive mounting is handled with a try/except for cross-environment compatibility).

## Methodology

The framework uses few-shot learning with the following key design choices:

- **Individual-level splits**: Dorsal and ventral images of the same specimen are always kept together (both in train or both in test) to prevent data leakage. The `female.txt` and `male.txt` pairing files encode these individual associations.
- **K-fold cross-validation**: Person-level k-fold ensures robust evaluation across limited samples.
- **Reproducibility**: All experiments use a fixed random seed (`seed=42`) and deterministic CUDA settings.

## Reproducibility

Reproducibility is a hard requirement for the target journal. To reproduce the reported results:

1. Use Python 3.9 or later
2. Install the exact dependency versions in `requirements.txt`
3. Run all cells in order
4. Use `seed=42` (default in the `seed_everything()` function)

Hardware used in original experiments: NVIDIA GPU with CUDA 11+. CPU execution is possible but significantly slower.

## Repository Structure

```
.
├── scorp_few_shot.ipynb    # Main notebook with all experiments
├── README.md               # This file
├── requirements.txt        # Python dependencies
├── LICENSE                 # MIT license
├── CITATION.cff            # Citation metadata
└── .gitignore              # Git ignore patterns
```

## Citation

If you use this code or dataset, please cite both:

**Paper:**
```bibtex
@article{unal2026fewshot,
  title   = {Few-Shot Learning for Sex Classification in Venomous Scorpions:
             A Framework for Data-Scarce Biological Research},
  author  = {Ünal, Yavuz and Koç, Halil},
  journal = {Pattern Analysis and Applications},
  year    = {2026},
  note    = {Under review}
}
```

**Dataset:**
```bibtex
@dataset{koc2026scorpion,
  title     = {Aegeaeobuthus gibbosus Image Dataset for Few-Shot Sex Classification},
  author    = {Koç, Halil and Ünal, Yavuz},
  year      = {2026},
  publisher = {Zenodo},
  version   = {1.0},
  doi       = {10.5281/zenodo.20796510},
  url       = {https://doi.org/10.5281/zenodo.20796510}
}
```

## License

This code is released under the MIT License. See [LICENSE](LICENSE) for details.

The dataset is released separately under the CC-BY 4.0 license.

## Authors

- **Yavuz Ünal** — Department of Computer Engineering, Sinop University, Turkey
  ORCID: [0000-0002-3007-679X](https://orcid.org/0000-0002-3007-679X)
  Email: yunal@sinop.edu.tr

- **Halil Koç** — Department of Biology, Sinop University, Turkey
  ORCID: [0000-0003-0429-2824](https://orcid.org/0000-0003-0429-2824)
  Email: halilkoc@sinop.edu.tr

## Contact

For questions about the code or experiments, please open a GitHub issue or contact the corresponding author at yunal@sinop.edu.tr.
