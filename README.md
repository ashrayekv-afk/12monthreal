# NKPI bilateral calculator — 8.6.0

A rebuilt **Topographic NKPI outlook · 12 months** appears in the baseline dropdown. It predicts a shared pattern across six corneal measurements, then recalculates the original baseline NKPI with age held constant. Both eyes have a current → 12-month score, quarterly line, and the two largest modeled contributors to the score movement.

This is a **dataset-fitted experimental scenario**, not a validated progression forecast or probability. More intuitive behavior is not evidence of greater clinical accuracy.

## Deploy

1. Use Windows **Extract All** on **NKPI_v860_Extract.zip**.
2. Upload the extracted contents to the existing GitHub repository, preserving folders and replacing same-name files. The ZIP contains 99 files. Keep deployment secrets private.
3. Streamlit main file: **kcn_dual_calculator_app.py**. Reboot after upload, then refresh the browser.
4. Calculate a **Single visit**, then open **Topographic NKPI outlook · 12 months** beneath the NKPI results. The footer should show **8.6.0-topographic-outlook**.

Local: `pip install -r requirements.txt` then `streamlit run kcn_dual_calculator_app.py`.

## What changed

- The model fits actual signed changes in ARC, PRC, thinnest pachymetry, BAD-D, ARTmax and Kmax from 232 eligible paired eyes / 130 patients. A shared factor couples the six estimates.
- Baseline NKPI, younger age, greater steepness and thinness inform the size of modeled structural change. Nonnegative directions are explicit research assumptions; there is no score floor, artificial percentage uplift, or room-to-100 multiplier.
- Age informs topographic change but stays fixed when future measurements are scored. Merely getting one year older cannot lower the displayed trajectory.
- A low current NKPI does not trigger growth because it has more headroom. The learned activity approaches zero at very low NKPI. It does not estimate the probability of remaining stable.
- Top two drivers show projected measurement changes and their exact contributions to NKPI movement. The expandable six-measurement audit accounts for the entire movement.
- Current and projected scores, two eye lines, full 0–100 and magnified-change views, and exact quarterly values are retained. Projections are dashed and labelled experimental.

## How the evidence is used

The dataset fits the change magnitudes. Published natural-history studies support age and steepness directions. The user's clinic observations motivate the nondecreasing NKPI/activity constraint. No individual clinic outcome records were supplied, so reported detection rates and treatment decisions were not converted into 12-month probabilities or fabricated training cases. Thinness and the shared nonnegative structural pattern are additional candidate assumptions.

The frozen NKPI classifier includes correlated inputs with opposing coefficients. Consequently, structural worsening and score increase are not interchangeable; score offsets remain visible rather than forcing an upward endpoint.

## Internal accuracy

Repeated nested patient-grouped assessment, conditional on the frozen NKPI formula, included 45 eyes / 25 patients with 9–15-month follow-up:

| Fixed-age score metric | New model | Unchanged measurements |
|---|---:|---:|
| RMSE, NKPI points | 3.92 | 3.93 |
| MAE, NKPI points | 1.92 | 1.96 |

A meaningful accuracy advantage has **not** been established. Near-year Kmax MAE was 2.10 D versus 2.07 D for unchanged measurements; the new model is not uniformly better. The frozen score was developed on overlapping records, treatment timing and quality need further audit, and only one eligible development eye had baseline NKPI ≥65. The dataset cannot support confident high-score individual forecasts.

Original NKPI models, extraction and observed-change evidence are preserved. Existing quality-advisory scoring remains. The historical probability calculation is audit-only and was not refitted; it is not displayed as a forecast percentage.

After extraction, open **docs/BASELINE_OUTLOOK_PREVIEW.html** for the working offline synthetic example. See **docs/BASELINE_OUTLOOK.md** for formulas, evidence and results, and **docs/TEST_REPORT.md** for engineering checks. No private patient records are included.
