# Wind & hail impact forecasts provided on WCR Sandbox

See WCR Sandbox for [wind](https://data.iac.ethz.ch/WCR_sandbox/WiSchaWa/index.html?date=01/03/2018&lead=2) and [hail](https://data.iac.ethz.ch/WCR_sandbox/HaSchaWa_V2/)

## Hazard preparation and imapact computation

**data input.** ICON forecast (1km and 2km resolutions) for wind speed and hail size over Switzerland. Data are in netcdf format. We currently receive MCH forecast data via a data
pipeline over CSCS, but the impact forecasts are planned to be coupled directly to MCH open government data (already available for wind speed, not yet for hail size). Forecast data
will be continuous and do not need to be preprocessed. Data are received several times per day (different init times) and span lead times up to 45h. 

**impact computation.** The hazard intensity matrix is converted to an impact matrix in the standard CLIMADA sytle compuation, using calibrated impact functions and Swiss exposure
layers like the number of buildings per 1km grid cell.

## Different forecast products

**aggregated impact-based forecasts**. After the standard CLIMADA impact calucation per centroid, the impacts are spatially aggregated to specific regions (e.g., nationally or per
canton). E.g., 11 spatially-explicit impact forecast members are aggregated to 11 national impact forecast members (i.e., 11 numbers for the estimated number of
damaged buildings per canton). The spatially-aggregated impact forecasts are then plotted depending on the aggregation (histogram, confidence intervals, density functions, pie charts).

## Other products that might rely on HazardForecast object before impact compuation

**impact-oriented warnings**. Warnings levels based on how many members surpass vulnerability-informed hazard-intenstity thresholds. This does not require the CLIMADA impact computation
(no exposure information needed). Warning levels per centroid (e.g. on 1km grid) are aggragated (usually using max()) to Swiss warning regions.



