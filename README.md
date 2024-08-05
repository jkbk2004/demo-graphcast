# An example prediction.py to fetch prediction with GraphCast_small - ERA5 1979-2015 - resolution 1.0
## GraphCast prediciton process: Data preparation and main driver level steps required to fetch predictions.
1. Fetching the input data: Graphcast uses the current weather data and the data from 6 hours ago to make predictions 6 hours into the future. Graphcast can fetch preditions for 10 days with a 6 hour time window.
2. Creating the targets.
3. Creating the forcing data.
4. Processing and formatting the data into a suitable format.
5. Bringing them all together and making predictions.
## Inputs
Climate Data Store (CDS) Application Program Interface (API): cdsapi python library, authentication instruction at https://cds.climate.copernicus.eu/api-how-to
1. Getting the single-level values: e.g. total_precipitation_6hr for timestamps ranging from 2024–01–01 00:00 to 12:00.
2. Getting the pressure-level values: pressure-level values for the two input timestamps.
3. Merging the single and pressure values: an inner-merge operation on the basis of time, latitude and longitude.
4. Integrating year and day progress: year_progress_sin, year_progress_cos, day_progress_sin and day_progress_cos.
5. Other steps include renaming columns and variables.
## Prediction targets
11 prediction fields:
1. u_component_of_wind,
2. v_component_of_wind,
3. geopotential,
4. specific_humidity,
5. temperature,
6. vertical_velocity,
7. 10m_u_component_of_wind,
8. 10m_v_component_of_wind,
9. 2m_temperature,
10. mean_sea_level_pressure,
11. total_precipitation.
## Forcings
Forcings for every coordinate and prediction timestamp are:
1. total_incident_solar_radiation,
2. year_progress_sin,
3. year_progress_cos,
4. day_progress_sin,
4. day_progress_cos.
## Post-processing the inputs, targets and forcings
Parsing through each data variable and removing unneeded indices to make sure each data variable is assigned to its right coordinates.
1. Converting to right form of xarray.
## Predictions using Graphcast
This step requires the model weights and normalization statistics files. The files to be downloaded are:
1. stats/diffs_stddev_by_level.nc,
2. stats/stddev_by_level.nc,
3. stats/mean_by_level.nc and
4. params/GraphCast_small — ERA5 1979–2015 — resolution 1.0 — pressure levels 13 — mesh 2to5 — precipitation input and output.npz.

Note that the relative paths of the aforementioned files in the prediction.py is depicted below.
```
    .
    ├── prediction.py
    ├── model
        ├── params
            ├── GraphCast_small - ERA5 1979-2015 - resolution 1.0 - pressure levels 13 - mesh 2to5 - precipitation input and output.npz
        ├── stats
            ├── diffs_stddev_by_level.nc
            ├── mean_by_level.nc
            ├── stddev_by_level.nc
```





