# README – Rainfall Scenario Forcing Library

## Overview

This folder contains rainfall forcing files used for debris-flow simulations.
The scenarios are based on:

* observed rainfall structure (Marcela event),
* precipitation return levels from the Hydrological Atlas of Switzerland (HADES),
* and systematic scaling of rainfall intensity to represent potential climate-driven changes.

All scenarios have a **duration of 6 hours**, consistent with the observed event.

---

## File naming convention

Each file follows the format:

```
rain_D6h_RPXXX_PYYYY_ZZZ.csv
```

Where:

* `DXh` → duration (3,6 hours)
* `RPXXX` → return period in years (e.g., 2, 30, 100, 200)
* `PYYYY` → probability level of HADES return level

  * `P0500` → median estimate (probability = 0.5)
  * `P0975` → upper confidence bound (probability = 0.975)
* `ZZZ` → scenario type

  * `BASE` → baseline scenario
  * `S105` → +5% intensity
  * `S110` → +10% intensity
  * `S112` → +12% intensity
  * `S120` → +20% intensity
  * `S130` → +30% intensity

---

## Scenario design

### Baseline scenarios

* Derived from **area-averaged HADES precipitation totals**
* Use the **observed rainfall temporal structure**
* Represent present-day extreme precipitation conditions

Two probability levels are provided:

* **P0500 (main scenarios):** median estimate (best estimate)
* **P0975 (sensitivity scenarios):** upper bound (uncertainty range)

---

### Scaled scenarios

For each baseline scenario, rainfall intensity is uniformly increased by:

* +5%, +10%, +12%, +20%, +30%

These represent **climate-informed sensitivity scenarios**, consistent with projected increases in extreme precipitation in Switzerland.

The temporal structure and duration remain unchanged.

---

## File contents

Each `.csv` file contains:

### Primary forcing variables

* `time_s` → time in seconds
* `rate_mps` → rainfall rate in m/s

These columns are directly usable as model input.

---

### Additional diagnostic variables (if included)

* `rate_mmh` → rainfall intensity in mm/h
* `depth_mm` → rainfall depth per time step
* `t_mid_h` → time in hours

These are provided for analysis and verification.

---

## Summary table

**File:** `scenario_summary_table.csv`

This file provides a summary of all scenarios, including:

* duration (hours)
* probability level
* return period (years)
* scaling factor
* total rainfall (mm)
* peak intensity (mm/h)
* mean intensity (mm/h)

This table is the best starting point for comparing scenarios.

---

## Interpretation notes

* The **P0500 scenarios** represent the main, most realistic forcing conditions.
* The **P0975 scenarios** represent upper-bound conditions and should be interpreted as uncertainty/sensitivity cases.
* The scaling factors do not represent exact climate projections, but rather **plausible increases in precipitation intensity** based on MeteoSwiss climate scenarios (CH2018/CH2025).

---

## Recommended usage

* Use **P0500 baseline + scaled scenarios** as the main experiment set.
* Use **P0975 scenarios** to assess sensitivity to extreme precipitation uncertainty.
* Compare scaled scenarios against their corresponding baseline to evaluate changes in hazard response.

---

## Contact

For questions regarding scenario construction or file usage, please contact:

* Edgar Dolores-Tesillos / https://edgardotes.github.io *

