# MeLiDos FUSPCEU GLC dataset

This repository contains the Madrid, Spain site data collected by Fundación
Universitaria CEU San Pablo (FUSPCEU) for the MeLiDos field study. It is a GLC
Schema 3.0.2 Data Package derived from the
[original MeLiDos dataset](https://github.com/MeLiDosProject/BaezaEtAl_Dataset_2025).

The package entry point is `datapackage.json`. Core metadata are stored in
`data/`; the 419 participant-level CSV files referenced by
`data/datasets.json` are organized under `data/files/` by sensor,
longitudinal-report, questionnaire, and study-timing resource.

The source dataset is:

> Baeza Moyano, D., Pérez Gutiérrez, M. C., Cantarero García, G., González
> Lezcano, R. A., Melero Tur, S., Zauner, J., & Spitschan, M. (2025).
> *Personal light exposure dataset for Madrid, Spain* (Version 1.0.1)
> [Data set]. https://doi.org/10.5281/zenodo.16834951

The refactoring converts the source repository's processed tabular RData
resources to UTF-8 CSV, separates records by participant, preserves R factor
ordering as numeric value/label metadata, and supplies GLC 3.0.2 metadata.

## Important source-processing notes

- The source correction workbook documents manual sleep-diary corrections to
  dates, AM/PM interpretation, swapped fields, and implausible values. Those
  corrections are already reflected in the processed RData used here.
- S023 chest timestamps were corrected in the source pipeline by shifting them
  25 years, 27 days, 7 hours, and 45 minutes, using the other worn devices as
  temporal references after a battery-depletion timestamp failure.
- S021 chest timestamps were judged unrecoverable by the source pipeline, so
  no S021 chest resource is included.
- S021 and S023 wrist timestamps were shifted forward by four hours in the
  source pipeline.
- The study-date workbook notes additional device-specific limitations,
  including 60-second glasses sampling for S014, early termination of S018
  wrist recording, and invalid collar data for S021 and S022.

## Calibration-date note

The source metadata workbook supplies device delivery dates but no separately
identified calibration dates. These delivery dates are used provisionally as
calibration-date proxies. Serials 3910 and 3082 occur in the deployment records
but are missing from the device inventory; their earliest recorded deployment
dates are used provisionally. All such dates require confirmation against the
actual calibration records.

## Validation

The package is validated against GLC Schema 3.0.2 with validator 0.5.2.
Validation also runs automatically through
`.github/workflows/validate-glc-dataset.yml`.

## License

The dataset is licensed under the Creative Commons Attribution 4.0
International License (CC BY 4.0). See `LICENSE`.
