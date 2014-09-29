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


