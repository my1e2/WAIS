# The Shrinking of the West Antarctic Ice Sheet

**A geospatial climate modeling study investigating the susceptibility of the West Antarctic Ice Sheet to rising global temperatures and its implications for global sea-level rise.**

---

## Overview

This research was conducted as part of the **FIRE (First-Year Innovation and Research Experience)** program at the University of Maryland, College Park, within the **Climate Computing** stream (September 2022 – December 2023). The project investigates how rising global temperatures, driven largely by increasing CO2 emissions, are contributing to the destabilization of the West Antarctic Ice Sheet (WAIS) — the largest ice mass on Earth and one of the most significant variables in long-term sea-level rise projections.

Using a combination of high-performance computing, global climate models, and multi-variable geospatial analysis, this study examines surface temperature, sea ice concentration, snow depth, wind patterns, and Antarctic mass anomalies to identify correlations that explain the ice sheet's ongoing shrinkage and help project its future behavior.

Findings were synthesized into a co-authored research paper and presented at an academic summit via poster board.

---

## Research Question

How are surface temperature, sea ice concentration, snow depth, wind patterns, and Antarctic ice mass interrelated over the West Antarctic Ice Sheet — and what do these correlations reveal about the ice sheet's stability and its future contribution to global sea-level rise?

---

## Key Findings

- Summer temperatures across the WAIS were measurably higher during 2005–2015 relative to 2022, and this period of elevated temperature directly correlates with a sustained decline in Antarctic mass anomalies (Figure 2 vs. Figure 4).
- The unusually lower and more stable 2022 temperatures are potentially attributable to reduced atmospheric CO2 during the COVID-19 lockdowns of 2020–2021, representing a short-term stabilization signal in ice mass beginning around 2021.
- Wind direction patterns derived from sea level pressure analysis (Figure 1) are consistent with sea ice concentration distributions observed in Figure 3: sea-facing winds from the south push warmer air into the WAIS boundary, reducing sea ice concentration in the south, while outflowing winds toward the north preserve greater sea ice concentration in that region.
- Colder surface temperatures at the WAIS edges (Figure 1) correspond spatially with elevated sea ice concentration (Figure 3) and greater average snow depth (Figure 5), confirming the interdependence of these variables.
- Quantifying true WAIS stability is inherently limited — major structural changes in the ice sheet operate on timescales of approximately 10,000 years (Oppenheimer, 1998), making short-term model output a partial but necessary window into longer-term dynamics.

---

## Figures & Results

### Figure 1 — WRF Surface Temperature, Sea Level Pressure & Wind (April 1, 2017)
A WRF-ARW model output generated via the Cheyenne supercomputer, visualizing surface temperature (°F), sea level pressure (hPa), and wind barbs (knots) over the WAIS and surrounding ocean on 2017-04-01. The domain was set using corner coordinates 55°W 77°S, 55°W 62°30'S, 105°W 62°30'S, and 105°W 77°S, with physics settings tuned for polar conditions. Higher sea level pressure south of the WAIS and lower pressure to the north drives onshore winds from the south (warmer, marine air) and offshore winds to the north (colder, continental air), directly influencing where sea ice forms and melts along the ice sheet boundary.

**Tool:** WRF-ARW via Cheyenne | **Time range:** 2017-04-01 00:00 to 18:00 UTC

---

### Figure 2 — Average WAIS Temperatures: 2005–2015 vs. 2022 (Line Plot)
A comparative line graph (Matplotlib) plotting monthly average surface temperatures for two periods: the 2005–2015 baseline (blue) and 2022 (red). The 2005–2015 curve shows relatively stable values ranging from approximately -14°F to -16°F. The 2022 curve traces a wider arc, dipping lower in winter months and remaining consistently below the baseline average through summer — a potentially significant deviation linked to reduced CO2 output during pandemic-era lockdowns.

**Tool:** Python (Matplotlib) | **Data source:** CESM2.1 / NCAR

---

### Figure 3 — Sea Ice Concentration: South Pole (Polar Stereographic Plot)
A polar stereographic circular plot (Matplotlib + Cartopy) depicting the spatial distribution of sea ice concentration across the South Pole region. A rainbow color gradient maps concentration percentages, with the South Polar Stereographic projection and land mass overlays providing geographic context. High concentration (red/orange) is visible to the north of the WAIS boundary, consistent with the cold outflowing winds identified in Figure 1. Reduced concentration (blue/purple) in the southern sea zones aligns with warmer marine air advecting onshore from the south.

**Tool:** Python (Matplotlib, Cartopy) | **Data source:** CESM2.1

---

### Figure 4 — Antarctic Mass Anomalies, 2002–2023 (Line Graph)
A time-series line graph (Matplotlib) charting annual Antarctic mass anomalies in gigatonnes derived from NASA's GRACE satellite data. Starting near 0 Gt in 2002, mass anomalies decline steadily to approximately -2,298 Gt by 2023, with a visible negative acceleration during the 2005–2015 period of elevated temperatures. A notable inflection begins around 2021, where the downward trend slows and briefly reverses — correlating with the temperature stabilization observed in Figure 2 and suggesting a short-term mass recovery during the post-lockdown CO2 reduction window.

**Tool:** Python (Matplotlib) | **Data source:** NASA GRACE satellite

---

### Figure 5 — Average Snow Depth Across Antarctic Grid Cells (Polar Stereographic Plot)
A polar stereographic circular plot (Matplotlib + Cartopy) showing the distribution of average snow depth (meters) across the Antarctic domain. Snow accumulation is highest along the coastal perimeter of the WAIS — particularly in areas corresponding to colder surface temperatures and higher sea ice concentration in Figures 1 and 3 — and lowest in areas exposed to marine wind intrusion. The spatial coherence between snow depth, temperature, and sea ice concentration reinforces the multi-variable correlations central to the study's conclusions.

**Tool:** Python (Matplotlib, Cartopy) | **Data source:** CESM2.1

---

## Methods & Tools

### Climate Models
- **CESM2.1 (Community Earth System Model):** Global climate model run with the T1850G compset and a spatial resolution of 2° x 2° (f_19_g17_gl4). The T1850G compset was selected for its high-resolution functionality and compatibility with the Community Sea Ice Model (CSIM). Simulated variables include Ice Sheet Surface Temperature and Sea Ice Concentration across latitudes -90° to 90° and longitudes -55° to 55°.
- **WRF (Weather Research & Forecasting Model):** Regional atmospheric model used to generate output for Surface Temperature, Sea Level Pressure, and Wind. Configuration required targeted edits to the `&time`, `&domain`, and `&physics` namelists with polar-specific physics parameterizations.

### Computing Infrastructure
- **Cheyenne Supercomputer (NCAR/CISL):** High-performance computing system used to execute all CESM2.1 and WRF simulations. Raw model output data was sourced from NCAR servers.

### Data Processing & Visualization
- **Python:** Primary analytical and visualization tool
- **Matplotlib:** Line plots, time-series graphs, color-mapped geospatial outputs
- **Cartopy:** Polar stereographic projections and South Pole regional mapping
- **NASA GRACE Satellite Data:** Antarctic mass anomaly dataset (2002–2023)

---

## Background & Literature Context

The study builds on a substantial body of prior work:

- **Modeling foundations:** Ferrari et al. (2020) on boundary forcing and model resolution; Pattyn et al. (2017) on advances in numerical ice-sheet modeling; Pollard & DeConto (2009) on multi-million-year WAIS growth/collapse cycles.
- **Observational data:** Rignot et al. (2008) on satellite-derived Antarctic mass loss; Shepherd, Wingham & Rignot (2004) on warm ocean erosion of the WAIS.
- **Internal ice dynamics:** Alley & Whillans (1991) on simultaneous thinning and thickening driven by internal processes; Budd, Jenssen & Smith (1984) on three-dimensional time-dependent ice sheet modeling.
- **Long-term stability & sea-level risk:** Oppenheimer (1998) on global warming and WAIS stability; Alley et al. (2015) on ocean-ice interactions and threshold behavior; Hughes (1981) on the structural vulnerabilities of the WAIS underbelly.

---

## Conclusions

The results establish a coherent, multi-variable picture of WAIS dynamics. Elevated summer temperatures between 2005 and 2015 correlated directly with accelerating ice mass loss. The anomalous temperature dip and mass stabilization observed around 2021–2022 aligns with the reduction in global CO2 emissions during COVID-19 lockdowns, offering a rare natural experiment in the link between emissions, temperature, and ice sheet behavior. Wind-driven sea ice asymmetry, confirmed across Figures 1, 3, and 5, further illustrates how atmospheric circulation patterns mediate the WAIS boundary conditions. Together, these correlations provide a foundation for more refined predictive modeling of sea-level rise under future emissions scenarios.

---

## Future Work

- Continue tracking CO2 emission effects on WAIS temperature and mass anomalies through the post-lockdown period
- Monitor how the studied variables evolve over the next decade relative to the baselines established here
- Compare outputs against prior model predictions to validate and calibrate result confidence
- Determine whether a specific post-lockdown trend persists in the variable data, strengthening or qualifying the CO2–temperature–ice mass conclusion

---

## Authors

R. De Vera, C. Makkar, B. Newman, M. Sartor
University of Maryland, College Park, MD — FIRE Program, Climate Computing Stream

---

## Acknowledgements

High-performance computing support provided by the Cheyenne supercomputer (doi:10.5065/D6RX99HX), NCAR's Computational and Information Systems Laboratory, sponsored by the National Science Foundation.

---

## References

Alley, R. B., Anandakrishnan, S., Christianson, K. et al. (2015). Oceanic Forcing of Ice-Sheet Retreat: West Antarctica and More. *Annual Reviews*, 43, 207–231.

Alley, R. B., Whillans, I. M. (1991). Changes in the West Antarctic Ice Sheet. *Science*, 254, 959–963.

Budd, W., Jenssen, D., & Smith, I. (1984). A Three-Dimensional Time-Dependent Model of the West Antarctic Ice Sheet. *Annals of Glaciology*, 5, 29–36.

Ferrari, F., Cassola, F., Tuju, P. E. et al. (2020). Impact of Model Resolution and Initial/Boundary Conditions in Forecasting Flood-Causing Precipitations. *Atmosphere*, 11(6):592.

Hughes, T. (1981). The weak underbelly of the West Antarctic ice sheet. *Journal of Glaciology*, 27(97), 518–525.

Oppenheimer, M. (1998). Global warming and the stability of the West Antarctic Ice Sheet. *Nature*, 393, 325–332.

Pattyn, F., Favier, L., Sun, S. et al. (2017). Progress in Numerical Modeling of Antarctic Ice-Sheet Dynamics. *Current Climate Change Reports*, 3, 174–184.

Pollard, D., DeConto, R. (2009). Modelling West Antarctic ice sheet growth and collapse through the past five million years. *Nature*, 458, 329–332.

Rignot, E., Bamber, J., van den Broeke, M. et al. (2008). Recent Antarctic ice mass loss from radar interferometry and regional climate modeling. *Nature Geoscience*, 1, 106–110.

Shepherd, A., Wingham, D., and Rignot, E. (2004). Warm ocean is eroding West Antarctic Ice Sheet. *Geophysical Research Letters*, 31, L23402.
