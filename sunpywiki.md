# SUNTANS Python Wiki

## Downloading Data from Online
The SUNTANS python library supports functionality for downloading and converting data from the internet to automatically be used with SUNTANS. Access to stream gauge data from USGS, time series observations from the US-IOOS server, NOAA/NWS weather observations, and the NARR weather model are all supported.

The data downloading functionality is in the DataDownloStream ad directory. 

#### USGS Stream Gauge Data
Downloading stream gauge data is as simple as specifying a list of USGS station IDs, a start date, and an end date. Then the call ```getUSGSnwis(stationids, starttime, endtime, ncfile)``` will automatically load a database that can be automatically incorporated into a SUNTANS model.

An example script:
```python
#INPUT VARIABLES
stationids = ['08066500',
              '08078000',
              '08067500',
              '08076000',
              '08075000',
              '08074500',
              '08076500',
              '08073600',
              '08075770']

starttime = '2000-01-01'
endtime = '2012-01-01'

mydirectory = os.path.dirname(os.path.realpath(__file__))
ncfile = mydirectory + 'USGS_Rivers_20002012.nc'

usgs.getUSGSnwis(stationids, starttime, endtime, ncfile)
```

#### NARR Weather Model Data
Joe cannot currently get the NARR functionality to work.

#### NOAA IOOS Data
NOAA IOOS Data measurements within a specified box can be taken from the internet, with a specified Lat/Long cooridinate boundaries and a time frame.

```python
from datetime import datetime
import netcdfio
from getNOAAIOOSopendap import extractIOOS

startt = "201001"
endt = "201002"
latlon = [-95.60, -93.7, 28.8, 30]
varlist = ['waterlevel', 'conductivity', 'watertemp', 'airtemp',
           'airpressure', 'windspeed', 'winddirn']
ncfile = mydirectory + 'USIOOS_OceanObs_20102011.nc'
shpfile = mydirectory + 'USIOOS_OceanObs_20102011.shp'

# Extract the data
data = extractIOOS(varlist, startt, endt, latlon)

# Write to a netcdf file
globalatts = {'title': 'US-IOOS oceanographic observation data',
              'history': 'Created on ' + datetime.ctime(datetime.now()),
              'source': 'http://opendap.co-ops.nos.noaa.gov/dods/IOOS/'}

datetime.ctime
netcdfio.writePointData2Netcdf(ncfile, data, globalatts)

# Write the metadata to a shapefile
netcdfio.pointNC2shp(ncfile, shpfile)
```


