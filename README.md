# MLF-SC: Incorporating Multi-Layer Features to Sparse Coding for Unsupervised Anomaly Detection

[![Actions Status](https://github.com/LeapMind/MLF-SC/workflows/MLF-SC/badge.svg)](https://github.com/LeapMind/MLF-SC/actions)
[![Maintainability](https://api.codeclimate.com/v1/badges/88983fffd83c373f5808/maintainability)](https://codeclimate.com/github/LeapMind/MLF-SC/maintainability)

MLF-SC (Multi-Layer Feature Sparse Coding) is an anomaly detection method that incorporates multi-scale features to sparse coding.
This is a PyTorch implementation for [MVTec](https://www.mvtec.com/company/research/datasets/mvtec-ad/) datasets (Carpet, Grid, Leather, Tile, Wood, ...).

## Output visualization of MVTec dataset (Grid, Hazelnut, and Bottle)
![001-447078](https://user-images.githubusercontent.com/46925310/79984100-a641e380-84e3-11ea-8acb-c2822d879ab7.png)
![010-390276](https://user-images.githubusercontent.com/46925310/79984083-a215c600-84e3-11ea-8788-aa59538e93c7.png)
![018-341679](https://user-images.githubusercontent.com/46925310/79984095-a510b680-84e3-11ea-86d8-d603b00289aa.png)

## Quick Start
```
git clone git@github.com:LeapMind/MLF-SC.git
pip3 install -r requirements.txt
python3 main.py train cfg/sample_config.yml
python3 main.py test cfg/sample_config.yml
```

## Download Dataset
```
wget ftp://guest:GU.205dldo@ftp.softronics.ch/mvtec_anomaly_detection/mvtec_anomaly_detection.tar.xz
tar -xvf mvtec_anomaly_detection.tar.xz 
```

## Usage
You can train and test for each texture dataset.

### Set dataset path to `config.yml`
Set `root` in `config.yml` to texture dataset path (like `path/to/mvtec_anomaly_detection/carpet/`).  

### Train
```
$ python3 main.py train cfg/config.yml
```

### Test and Visualize Output
```
$ python3 main.py test cfg/config.yml
```

## Contribution

Anomaly detection performance for the texture categories of the MVTec AD dataset. For each cell in the R1 / R2 columns, the ratio of correctly classified samples of normal R1 and that of anomalous images R2 are shown with R1 / R2 notation.  The maximum averages (R1 + R2) / 2 are marked with boldface. The performance for the non-sparse-coding-based methods are cited from Table 2 of (Bergmann et al., 2019). The AUROC columns show only sparse coding and MLF-SC.

|   | R1 / R2 |  |  |  |  |  |  | AUROC |  |
| :---: | :---: | --- | --- | --- | --- | --- | --- | :---: | --- |
|  Category | AE (SSIM) | AE (L2) | AnoGAN | CNN<br/>Feature Dictionary | Texture<br/>Inspection | Sparse<br/>Coding | MLF-SC<br/>(Proposed) | Sparse<br/>Coding | MLF-SC<br/>(Proposed) |
|  Carpet | 0.43 / 0.90 | 0.57 / 0.42 | 0.82 / 0.16 | 0.89 / 0.36 | 0.57 / 0.61 | 0.43 / 0.79 | **1.00 / 0.98** | 0.58 | **0.99** |
|  Grid | 0.38 / 1.00 | 0.57 / 0.98 | 0.90 / 0.12 | 0.57 / 0.33 | 1.00 / 0.05 | 0.76 / 0.72 | **1.00 / 0.88** | 0.89 | **0.97** |
|  Leather | 0.00 / 0.92 | 0.06 / 0.82 | 0.91 / 0.12 | 0.63 / 0.71 | 0.00 / 0.99 | 0.84 / 0.96 | **0.97 / 0.97** | 0.95 | **0.99** |
|  Tile | 1.00 / 0.04 | 1.00 / 0.54 | 0.97 / 0.05 | 0.97 / 0.44 | 1.00 / 0.43 | 0.94 / 0.60 | **0.94 / 0.76** | 0.86 | **0.92** |
|  Wood | 0.84 / 0.82 | 1.00 / 0.47 | 0.89 / 0.47 | 0.79 / 0.88 | 0.42 / 1.00 | 0.84 / 0.60 | **0.95 / 0.98** | 0.97 | **0.99** |
|  Average | 0.53 / 0.74 | 0.64 / 0.65 | 0.90 / 0.18 | 0.77 / 0.54 | 0.60 / 0.62 | 0.７６ / 0.81 | **0.97 / 0.91** | 0.85 | **0.97** |

## License
Non-commercial, research purposes only

## License of dependent libraries
See `LICENSE` directory.
