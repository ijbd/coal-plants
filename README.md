# EASIUR Python Integration Module
Python module for assessing health damages associated with generator emissions.

Code by ijbd

## Updates
2/12/2021
> Gathered data for emissions, generator location, and marginal social costs. 

2/15/2021
> Fixed EASIUR processing script. Updated data source descriptions.

## Use



## Data Sources

**Sample data is already included**, but the descriptions of each dataset, and the steps taken to get them, are outlined below.

### EASIUR:
>"The Estimating Air pollution Social Impact Using Regression (EASIUR) model is an easy-to-use tool estimating the social cost (or public health cost) of emissions in the United States. The EASIUR model was derived using regression on a large dataset created by CAMx, a state-of-the-art chemical transport model. The EASIUR closely reproduce the social costs of emissions predicted by full CAMx simulations but without the high computational costs." 

To get EASIUR Data:
1. Run `getEasiurLocs.py` from the `data/easiur_msc` directory. This script will pull the locations of every power plant in the United States and compile them in a CSV file. It does not include generators with no latitude/longitude locations, and it fixes a latitude typo for plant #62242 in New York. This file is used in conjuction with the EASIUR Online Data Access Tool.
2. Go to the [EASIUR Online Tool](https://barney.ce.cmu.edu/~jinhyok/easiur/online/) [1,2], and use the batch conversion tool by uploading the file generated by `getEasiurLocs.py`. Each line of the output file contains a location and the corresponding Marginal Social Cost of 4 pollutants
3. Move the output file back to `data/easiur_msc`, then run the `processEasiur.py`.

### EIA Annual Emissions
This [dataset](https://www.eia.gov/electricity/data/emissions/) [3] provides *annual* unit-level generation and emissions (CO2, NOx, and SO2). 

### EIA-860 
>"The survey Form EIA-860 collects generator-level specific information about existing and planned generators and associated environmental equipment at electric power plants with 1 megawatt or greater of combined nameplate capacity. Summary level data can be found in the Electric Power Annual."

Available [here](https://www.eia.gov/electricity/data/eia860/) [4].

## Citations

[1] Jinhyok Heo, Peter J. Adams, H. Gao. (2016) "Reduced-form modeling of public health impacts of inorganic PM2.5 and precursor emissions", Atmospheric Environment, 137, 80—89,. doi:10.1016/j.atmosenv.2016.04.026

[2] Jinhyok Heo, Peter J. Adams, H. Gao. (2016) "Public Health Costs of Primary PM2.5 and Inorganic PM2.5 Precursor Emissions in the United States", Environmental Science & Technology, 50 (11), 6061—6070. doi:10.1021/acs.est.5b06125

[3] Energy Information Agency (2019) "Emissions by Plant and Region" 

[4]  Energy Information Administration, Form EIA-930 User Guide Known Issues (2020).550
