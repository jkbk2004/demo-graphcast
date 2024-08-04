# driver-graphcast for an example prediction.py
## GraphCast prediciton process: Data preparation and main driver level steps required to fetch predictions.
1. Fetching the input data: Graphcast uses the current weather data and the data from 6 hours ago to make predictions 6 hours into the future. Graphcast can fetch preditions for 10 days with a 6 hour time window.
2. Creating the targets.
3. Creating the forcing data.
4. Processing and formatting the data into a suitable format.
5. Bringing them all together and making predictions.
## Inputs
Climate Data Store (CDS) Application Program Interface (API): cdsapi python library, https://cds.climate.copernicus.eu/api-how-to


