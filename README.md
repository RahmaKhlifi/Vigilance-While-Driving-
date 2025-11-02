# Vigilance-While-Driving-

Tools and notebooks for analyzing vigilance / PSG (polysomnography) segments and visualizing results.

## Table of contents

- Overview
- Features
- Repository structure
- Installation
- Usage
  - Run the Jupyter notebook
  - Command-line examples
- Example: visualize a PSG segment
- Data
- Notebooks & scripts
- Development
- Contributing
- License
- Contact
- Acknowledgements

---

## Overview

VigilanceProject contains code and notebooks to load, process, and visualize physiological recordings (e.g., PSG) and associated metadata. The primary analysis and visualization are contained in the Jupyter notebook `vigilanceproject.ipynb`.

## Features

- Load PSG data and hypnograms
- Preprocess signals (filtering, resampling, artifact handling)
- Epoch extraction and segment visualization
- Hypnogram overlay and annotation
- Export figures (PNG/HTML) for reports

## Repository structure

Adjust this tree to match the actual files and folders in your repository.

.
├── README.md         
├── vigilanceproject.ipynb # main notebook
├── src/
│   ├── data_utils.py
│   ├── preprocess.py
│   ├── visualize.py
│   └── models.py
├── data/
│   ├── raw/                   # raw data (not tracked)
│   └── processed/

## Installation

requirements:

- jupyterlab
- notebook
- numpy
- pandas
- scipy
- mne
- matplotlib
- scikit-learn
- seaborn
- tqdm
- pyyaml

## Usage

### Run the Jupyter notebook

1. Activate your environment (see Installation).
2. Start Jupyter:

```powershell
jupyter lab    # or jupyter notebook
```

3. Open `vigilanceproject (1).ipynb` and run the cells.

### Command-line script examples

(If your repo includes scripts in `src/`, run e.g.)

```powershell
python src/visualize.py --input data/raw/sub-01.edf --start 0 --duration 120
```


## Example — visualize a PSG segment

If your code provides a function like:

```python
def visualize_psg_segment(patient_row, start=0.0, duration=120.0, channels=None, interactive=True, save_png=None, scale='auto'):
    ...
```

You can call it in the notebook or a Python script:

```python
from src.visualize import visualize_psg_segment

patient_row = {
    'patient_id': 'sub-01',
    'psg_path': 'data/raw/sub-01.edf',
    'hypnogram_path': 'data/processed/sub-01_hypnogram.csv'
}

visualize_psg_segment(
    patient_row,
    start=60.0,
    duration=180.0,
    channels=['C3-A2', 'O1-A2'],
    interactive=False,
    save_png='figs/sub-01_seg1.png'
)
```

## Data

Raw data (PSG/EDF files) are expected under `data/raw/`. Do not commit private patient data or PHI.

Processed files (filtered, resampled, CSV metadata) go to `data/processed/`.

Example structure:

```
data/
  raw/
    sub-01.edf
    sub-02.edf
  processed/
    sub-01_hypnogram.csv
    sub-02_hypnogram.csv
```


## Notebooks & scripts

- `vigilanceproject (1).ipynb` — main analysis and visualization notebook.
- `src/visualize.py` — helpers for plotting and exporting figure assets.
- `src/preprocess.py` — filtering, resampling, and artifact removal routines.

## Development

Run unit tests:

```powershell
pytest -q
```

Lint and formatting:

```powershell
black .
flake8
```

## Contributing

Contributions welcome! Please:

1. Fork the repo
2. Create a branch (git checkout -b feature/your-feature)
3. Add tests where appropriate
4. Open a pull request describing your changes

Please follow the code style used in the repository (PEP8 / Black).

## License

This project is released under the MIT License. See `LICENSE` for details.

Replace with the appropriate license if different.

## Contact

Maintainer: <!-- TODO: add your name and email or GitHub handle -->

GitHub: @RahmaKhlifi

## Acknowledgements

Thank you to dataset providers, contributors, mentors, and libraries (e.g., MNE-Python, PhysioNet).
