# Update to 8.6.0 — topographic outlook

1. Download `NKPI_v860_Extract.zip` and use **Extract All** in Windows.
2. Upload the extracted files and folders to the current GitHub repository, replacing same-name files. Do not upload the ZIP itself or overwrite private deployment secrets.
3. Keep Streamlit's main file `kcn_dual_calculator_app.py` and reboot the app.
4. Refresh the browser. The footer must show **8.6.0-topographic-outlook**.
5. Calculate verified **Single visit** inputs and open **Topographic NKPI outlook · 12 months**. Each eye displays current and 12-month NKPI, point change, and two topographic drivers. The chart is inside the dropdown.
6. Test **Magnify change**, the exact-score table and the six-measurement audit. Editing an input clears that eye's old line until recalculation.

The original NKPI score formula, source extraction and longitudinal evidence are unchanged. The baseline trajectory is newly fitted and rescored at fixed age. It remains an experimental scenario with no demonstrated meaningful improvement over unchanged measurements.

Standard DEFLATE ZIP: 99 files, no encryption and no ZIP64 requirement. No private patient dataset, report images or credentials are included. The inactive historical `research/evaluate_trajectory.py` is retired; remove an old repository copy if desired. The retained aggregate feasibility report is historical, not the new model's evaluation.
