# Annotate-OOI2021

[![DOI](https://zenodo.org/badge/1062015413.svg)](https://doi.org/10.5281/zenodo.17462951)

## What this repository does

This repository contains code and a small notebook to assist with annotating fin whale call detections from the  [2021 OOI RCA dataset](https://oceanobservatories.org/pi-instrument/rapid-a-community-test-of-distributed-acoustic-sensing-on-the-ocean-observatories-initiative-regional-cabled-array/) .

The core scripts are:

- `annotate.py`: a minimal script to run annotation workflows from the command line.
- `annotate.ipynb`: an interactive Jupyter notebook to  perform annotation using [hvPlot](https://hvplot.holoviz.org/en/docs/latest/index.html)

- `annotate.md`: a example markdown file showing potential outputs for the annotation tool.

## Intended inputs and outputs

- Inputs: processed DAS files in ``netCDF`` format (not included in this repo — see "Data availability" below).
- Outputs: annotation files in CSV format (timestamps, labels, annotator id, etc.), suitable for evaluating automated associations and perform localization.

Note: the repository provides utilities and examples but does not include the full datasets used in our experiments (these are too large for a Git repository).

## Usage

Open the notebook to run interactive annotation and visualization:

```bash
jupyter lab annotate.ipynb
```

## Data availability

The input data used with these scripts is too large to store in this Git repository. We plan to publish a curated dataset that enables reproducing our experiments and using this code as part of the DCLDE 2027 workshop. When that dataset is released it will include download and access instructions; this README will be updated with the dataset DOI and link at that time.

If you need access earlier for collaboration or review, please contact the maintainers (see below).

## Contributing

Contributions are welcome. Please open an issue to discuss larger changes before submitting a pull request. Small fixes and docs updates can be submitted directly.

## License

This repository is licensed under the GNU General Public License v3.0 (GPL-3.0). See the `LICENSE` file in the repository root for the full text and details about redistribution and modification under this license.

## Contact

If you have questions about the code or the forthcoming dataset, contact: qgoestch (maintainer) — please open an issue.

## Cite

If you use these tools or the forthcoming dataset in publications or workshops (e.g., DCLDE 2027), please cite the dataset and code according to the DOI and citation information that will be published alongside the dataset.


## Dependency management

This repository is a small Python project. Two supported ways to create an environment and install the dependencies are shown below. The project provides a modern `pyproject.toml` (Poetry format) and a `requirements.txt` fallback.

1) Poetry (recommended)

 - Install Poetry (https://python-poetry.org) and then run in the repository root:

```bash
poetry install
poetry shell        # optional: spawn a shell within the venv
```

Poetry will create an isolated virtual environment and install the dependencies listed in `pyproject.toml`. To run the notebook or script from the active environment, use `poetry run jupyter lab` or `poetry run python annotate.py`.

2) pip (fallback)

If you prefer a plain virtual environment with pip, create a venv and install from `requirements.txt`:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Notes
- The repository does not pin exact versions in `pyproject.toml`; Poetry will resolve a compatible set. If you need fully pinned reproducible installs, run `poetry lock` and commit the generated `poetry.lock`, or export a pinned `requirements.txt` with `poetry export -f requirements.txt --output requirements.txt --without-hashes`.
- The minimal expected runtime dependencies include: numpy, pandas, xarray, holoviews, hvplot, panel, bokeh, and scipy. See `pyproject.toml` for the canonical list used by Poetry.

