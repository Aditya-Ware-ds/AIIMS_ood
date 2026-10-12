# AIIMS prostate MRI - prepared dataset (for course use only)

Research use only. Do not copy this data outside the approved environment. Do not try to identify patients.

## Contents
- images/<code>/t2.nii.gz, adc.nii.gz, dwi_highb.nii.gz
  All three are on the SAME voxel grid (the T2 grid), so voxel (i, j, k) is the same place in all of them.
- masks/<code>/lesion.nii.gz, normal.nii.gz, zones.nii.gz (train and val patients only)
  lesion: lesion region(s); normal: small sample regions of normal tissue (not the whole gland);
  zones: PZ = 1, TZ = 2 (covers only some slices). Mask values are labels, 0 = background.
- split.csv: code -> train / val / test (test labels are hidden)
- labels_dev.csv: patient labels for train and val (label 1 = lesion present, PI-RADS 3-5; 0 = PI-RADS 1-2)
- slice_labels_dev.csv: labelled slices for train/val (slice_index is 0-based along the third array axis)

## Important notes
- DWI: the high-b-value image. Frame confirmed as b=1500 by AIIMS: False.
- Only some slices are labelled. Unlabelled slices are NOT necessarily normal.
- Images are raw intensities (not normalised). Normalise as your model expects.
- Never use the patient code, file names or file sizes as model input.

## What to submit for the test patients
1. patient_scores.csv with columns: code, score (higher = more likely lesion present)
2. slice_scores.csv with columns: code, slice_index, score (score ALL slices of each test patient)

CSV vs mask slice-number check (instructor info): {'no_csv_row': 61, '0-based': 36}
