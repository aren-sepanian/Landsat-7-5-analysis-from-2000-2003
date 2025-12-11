# Landsat-7-5-analysis-from-2000-2003
Surface temperature analysis for San Andrés Island (2000–2003) using Landsat 7 and Landsat 5 thermal data. Includes preprocessing, Celsius conversion, seasonal comparisons, visualization maps, and summary statistics.

Note: The data files used in the analysis couldn't be uploaded due to size, but are all available on: https://earthexplorer.usgs.gov/

Using coordinates: 
1. Lat: 12.6100, Lon: -81.7400
2. Lat: 12.6100, Lon: -81.6800
3. Lat: 12.4800, Lon: -81.6800
4. Lat: 12.4800, Lon: -81.7400

Dates: 2000-01-01 to 2003-12-01

Methodology:

1. Loading Scenes
   - Converting TIF Files using rasterio, then conversion to float32 values and the nan (not a number) values are removed.

2. Scale Factors
   - Applying the USGS formula
   - Kelvin = DN * MULT + ADD
   - Celsius = Kelvin - 273.15
  
3. Generating Vizualizations
   - Individual maps - Inferno colomap
   - Separated into Jan/Feb to July/Sep
   - Histograms to show the distribution of temperatures
  
4. Min/Max/Mean Values
   - Each scene outputs these values

5. Applying a Linear Regression Test
   - Using Scipy.stats to import
   - Fitting a straight line to the sequence of mean temperatures and measuring if a significant      cool or warm trend exists

6. Applying a Mann-Kendall Test
   - To add to the Linear Regression Test, I applied a non-parametric Mann-Kendall trend test         utilizing the Sen's slope to the mean of the SST. 
