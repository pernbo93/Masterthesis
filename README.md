# Masterthesis
This is a repository for the data used in the work of my master thesis in meteorology.

Title: Analysis of urban meteorological data. Comparison of local measurements and a numerical
mesoscale model under the aspect of local air quality modeling.

Abstract: This thesis explores the meteorology in an urban area during a winter period and how
well a numerical model is able to represent it. The air quality in the cities is of large
interest to the citizens and policymakers. However, effects of buildings and anthropogenic
activity on the meteorology in the city are complex. Lack of meteorological observations
makes it difficult to create good predictions of the dispersion of tracers and to evaluate the
models used as well. Meteorological modeling with focus on the planetary boundary layer
(PBL) over Bjørvika, Oslo is performed using the Weather Research and Forecasting (WRF)
model combined with the single-layer urban canopy model (SLUCM). The simulated
meteorological parameters are evaluated by comparison with observational measurements
of the temperature at six levels, and the wind speed and the wind direction at two levels in
a tower crain mast in Bjørvika, from January 9 to March 1, 2018. The results show a large
difference of the meteorology between the model and the observations. The wind speeds
are overestimated and the temperatures are underestimated by WRF. Furthermore, the
atmosphere in the model is more stable compared to the observations when comparing
hourly values, indicating that the model parameters will not represent the local dispersion
correctly. However, the summed distribution of the atmospheric stability in WRF was
more similar to the observations, indicating that the parameters from WRF could work
better for dispersion estimations of longer timescales.

Link to the thesis: (Coming soon)

The observations used and description can be fined at:
https://zenodo.org/record/1247012#.W6u2gWgzbIU

All data are raw data and to be usable the temperature needs to be corrected (to be retrieved to the raw value of the temperature):
10m --> -6e-06T + 0.0623
30m --> -0.0072T + 0.1849
50m --> 0.0074T -0.2795
65m --> 0.0037T -0.0429
75m --> 0.0005T + 0.0609
Tcorrected = T - Tcorrection

For the WRF setup see namelist.wps and namelist.input. The measuring period (January 9 to March 1, 2018) was seperated into seven runs.
Because of poor resolution of the Oslo fjord SST, I modified the initialization of the TSK in the d02, d03 and d04 domains. Example of ncl code for the TSK modification:

ncap2 -v -O -s "where(LANDMASK ==0 && LAKEMASK ==0)TSK=276;" wrfinput_d02 tsk_mod.nc
ncks -x -v "TSK" wrfinput_d02 wrfinput_d02_mod.nc
ncks -A -v TSK tsk_mod.nc wrfinput_d02_mod.nc

which set the TSK=276K at the fjord grids.

