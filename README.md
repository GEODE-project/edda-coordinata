# EDDA-Coordinata: An Annotated Dataset of Historical Geographic Coordinates

[![DOI](https://img.shields.io/badge/DOI-10.63317%2F5guc63fgjocp-0A7BBB?logo=doi&logoColor=white)](https://doi.org/10.63317/5guc63fgjocp)

Code and data accompanying the paper:

**EDDA-Coordinata: An Annotated Dataset of Historical Geographic Coordinates**  
Ludovic Moncla, Pierre Nugues, Thierry Joliveau, Katherine McDonough  
Proceedings of the Fifteenth Language Resources and Evaluation Conference (LREC 2026)  
DOI: [10.63317/5guc63fgjocp](https://doi.org/10.63317/5guc63fgjocp)  
Pages: 6224-6234  
Paper page: [lrec2026-main-493](https://lrec.elra.info/lrec2026-main-493)  
Preprint: [arXiv:2602.23941](https://arxiv.org/abs/2602.23941)

## Hugging Face Resources

- Dataset: [GEODE/edda-coordinata](https://huggingface.co/datasets/GEODE/edda-coordinata)
- Fine-tuned model: [GEODE/mt5-small-coords-norm](https://huggingface.co/GEODE/mt5-small-coords-norm)
- Demo: [GEODE/edda-coordinates (Space)](https://huggingface.co/spaces/GEODE/edda-coordinates)

## Overview

This repository contains notebooks and annotated resources used to:

1. Explore the EDDA-Coordinata dataset.
2. Measure inter-annotator agreement.
3. Train models for coordinate-bearing entry detection and coordinate extraction and normalization.


The project focuses on extracting and normalizing historical geographic coordinates from early modern encyclopedic texts.

## Repository Structure

```text
.
|-- edda_coordinata.json
|-- requirements.txt
|-- data/
|   |-- annotator1.json
|   `-- annotator2.json
`-- src/
		|-- 01_dataset_exploration.ipynb
		|-- 02_inter_annotator_agreement.ipynb
		|-- 03_train_coordinate_entry_classifier.ipynb
		|-- 04_finetune_mt5_coordinate_normalizer.ipynb
		`-- 05_zero_few_shot_coordinate_extraction.ipynb
```

## Data Files

- `edda_coordinata.json`: Main EDDA-Coordinata dataset (entries, text, extracted coordinates, meridian fields).
- `data/annotator1.json`, `data/annotator2.json`: Annotation files used for agreement analysis.


## Notebooks

- `src/01_dataset_exploration.ipynb`: Exploratory analysis of the EDDA-Coordinata dataset.
- `src/02_inter_annotator_agreement.ipynb`: Inter-annotator agreement computation and reporting.
- `src/03_train_coordinate_entry_classifier.ipynb`: Training/evaluation of a binary classifier for detecting coordinate-bearing entries.
- `src/04_finetune_mt5_coordinate_normalizer.ipynb`: Fine-tuning mT5 for coordinate extraction and normalization.
- `src/05_zero_few_shot_coordinate_extraction.ipynb`: Zero-/few-shot prompting experiments (OpenAI API-based workflow).

## Setup

### 1) Create a virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 2) Install dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

The `requirements.txt` file includes the dependencies used across all notebooks. 
Optional runtime requirements remain environment-specific (for example, a CUDA/MPS-compatible setup for acceleration and an `OPENAI_API_KEY` for prompting experiments).

## Running the Notebooks

Open notebooks from `src/` in Jupyter or VS Code and run cells in order.

1. Dataset exploration `src/01_dataset_exploration.ipynb`.
2. Compute inter-annotator agreement scores `src/02_inter_annotator_agreement.ipynb`.
3. Train models using `src/03_train_coordinate_entry_classifier.ipynb` and `src/04_finetune_mt5_coordinate_normalizer.ipynb`.

### API key for prompting notebook

`src/05_zero_few_shot_coordinate_extraction.ipynb` expects an OpenAI API key via environment variable:

```bash
export OPENAI_API_KEY="your_key_here"
```

or in a local `.env` file:

```env
OPENAI_API_KEY=your_key_here
```



## Citation

If you use this repository or dataset, please cite:

```bibtex
@inproceedings{moncla-etal-2026-edda,
	title={EDDA-Coordinata: An Annotated Dataset of Historical Geographic Coordinates},
	author={Moncla, Ludovic and Nugues, Pierre and Joliveau, Thierry and McDonough, Katherine},
	booktitle={Proceedings of the Fifteenth Language Resources and Evaluation Conference (LREC 2026)},
	pages={6224--6234},
	year={2026},
	publisher={European Language Resources Association (ELRA)},
	doi={10.63317/5guc63fgjocp},
	url={https://lrec.elra.info/lrec2026-main-493}
}
```
