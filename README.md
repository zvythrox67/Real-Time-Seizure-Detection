# Seizure Detection Under Wearable Constraints

## Overview
This project tests how well a seizure detection algorithm works when limited to the constraints of a wearable device instead of a hospital EEG machine.

## Dataset
CHB-MIT Scalp EEG Database (PhysioNet) — 23-channel EEG from patient chb01, sampled at 256 Hz. Seven files contained seizures; eight did not.

## Method
- Sliced EEG into 2-second windows
- Labelled each window as seizure or non-seizure
- Extracted 5 simple features per window
- Trained a Random Forest classifier
- Tested under 4 conditions: full clinical, reduced channels, added noise, downsampled

## Results

| Condition | Accuracy | Sensitivity |
|---|---|---|
| Clinical (23 ch) | 80% | 78% |
| Reduced (4 ch) | 72% | 70% |
| Noisy (4 ch) | 65% | 60% |
| Downsampled (64 Hz) | 58% | 52% |

**Key finding:** Accuracy dropped 22 percentage points from clinical to wearable conditions.

![Wearable degradation chart]
<img width="561" height="332" alt="image" src="https://github.com/user-attachments/assets/de9ef2e0-453a-4a38-9615-1cc9d88a93bd" />

*Figure 1: Seizure detection accuracy and sensitivity under four conditions, showing progressive degradation from clinical to wearable settings.*


## Files
- `chb01_*.edf` — raw EEG recordings
- `eeg_windows.csv` — labelled dataset
- `eeg_balanced.csv` — balanced dataset
- `figure1_wearable_degradation.png` — results chart

## Tools
Python 3, NumPy, Pandas, Matplotlib, MNE, Scikit-learn. Runs in Google Colab.

## References
[1] Shoeb, A. and Guttag, J. "Application of Machine Learning to Epileptic Seizure Detection." ICML, 2010.

[2] Goldberger, A. et al. "PhysioBank, PhysioToolkit, and PhysioNet." *Circulation* 101, no. 23 (2000): e215–e220.

[3] Pedregosa, F. et al. "Scikit-learn: Machine Learning in Python." *Journal of Machine Learning Research* 12 (2011): 2825–2830.
