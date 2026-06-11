# CV-anodic-peak-extraction
Python script for baseline subtraction and anodic peak current extraction from cyclic voltammograms (CV)

Python script for measuring the anodic peak current of CV by linear baseline subtraction.

---

## Method
For each forward (anodic) scan, the script:
1. Fits a straight baseline by least-squares regression to the pre-peak window (default **E = −0.15 to 0 V**), where the current is mainly the non-faradaic background.
2. Extends this baseline under the peak.
3. Measures **ΔI** as the vertical difference between the peak maximum and the extended baseline, evaluated at the peak potential.
4. Reports **R²** of the baseline fit (R² = 1 is a perfect fit; > 0.99 for all scans here).

ΔI is averaged over three consecutive forward scans of the same CV run, and this average is used to calculate Iₙ. The same fit window and procedure are applied to every voltammogram (blank I₀ and analyte I; MIP and NIP), so the baseline is treated identically across all measurements.

---

## Repository Contents

| File | Description |
|------|-------------|
| `main_v2.ipynb` | Main notebook — baseline fit, peak detection, ΔI extraction, and output plot |
| `raw_data.csv` | Raw data |
| `cv_peak_summary.csv` | Output data |
| `cv_oxidation_peaks.png` | Output plot |
| `README.md` | This file |


---

## Usage

1. Clone this repository
2. Place your CV data file (exported from PSTrace) in the same folder as the notebook
3. Open Jupyter Notebook:
```bash
jupyter notebook
```
4. Open `anodic_peak_extraction.ipynb`
5. Edit the parameters in **Cell 2** if your filename, fit window, or scan numbers differ:

```python
DATA_FILE = 'cv_scan.csv'   # CV data exported from PSTrace (potential, current columns)
E_FIT_MIN = -0.15           # lower bound of baseline fit window (V)
E_FIT_MAX =  0.0            # upper bound of baseline fit window (V)
```

6. Run all cells — the output plot (baseline, peak, and measured ΔI) is saved automatically as `.png`

> **Input format:** the script expects CV data exported from PSTrace as a text/CSV file with a potential column (V) and a current column (µA). Adjust the import settings in the notebook if your export layout differs.


---

## Author

Developed by: Vu Bao Chau Nguyen, Ph.D.

Keywords: cyclic voltammetry, baseline subtraction, anodic peak current.
