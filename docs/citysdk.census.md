# Global





* * *

### parseToVariable(aliasOrVariable) 

Checks to see if a string is in the aliases dictionary and returns the appropriate variable if so.e.g. "income" will return "DP03_0064PE"If the string is not in the alias dictionary, it will return the same string back. This is useful for parsinguser input. (Either a user requests a variable in the alias dictionary OR a specific variable)

**Parameters**

**aliasOrVariable**: `string`, A string to parse into a variable string.

**Returns**: `string`, Variable string


### latLngToFIPS(lat, lng, callback) 

Converts co-ordinates to Census FIPS via the Geocoder API

**Parameters**

**lat**: `float`, Latitude

**lng**: `float`, Longitude

**callback**: `function`, Callback function



### acsSummaryRequest(request, callback) 

Makes a request to the ACS5 Summary API. Should be used via APIRequest and not on its own, typically

**Parameters**

**request**: `object`, JSON request (see APIRequest)

**callback**: `function`, Makes a request to the ACS5 Summary API. Should be used via APIRequest and not on its own, typically



### APIRequest(request, callback) 

Processes a data request by looking at a JSON requestJSON Requests should include:"year" - Year of the request. See acs5years object for available years. Defaults to 2013 if not specified."lat" - Latitude of the requested location (either specified as x, lat, or latitude) NORTH"lng" - Longitude of the requested location (either specified as y, lng, or longitude) EAST"sublevel" - Defaults to "false". If set to "true", it will return the group of sublevels from the specified level."level" - Level of the request. Options are: blockGroup, tract, county, state, us. Will default to blockGroup."variables" - Array of variables either by alias or specific nameexampleRequest = {      "year": "2013",      "lat": 38.9047,      "lng": -77.0164,      "level": "blockGroup"      "variables": [          "income"      ]  };  exampleResponse = {      "year": "2013",      "lat": 38.9047,      "lng": -77.0164,      "level": "blockGroup",      "state": "11",      "county": "001",      "tract": "004701",      "blockGroup": "2",      "data": {          "income": 33210      }  };  A response where you set sublevel to "true" will have an array in the data field instead of an object.  Another example request:  {     "state": "NY",     "level": "state",     "variables": [         "income",         "population"     ]

**Parameters**

**request**: `object`, The JSON object of the request

**callback**: `function`, A callback, which accepts a response parameter



### GEORequest(request, callback) 

Get a city's geography by name, as well as requested variables. Currently supported locations:Asheville, NCAustin, TXBoston, MAChicago, ILFargo, NDMontgomery County, MD (Using the co-ordinates for Gaithersburg, MD)NYC, NYPortland, ORSan Francisco, CASeattle, WAWashington, DCExample request:{     "level": "place",     "lat": 30.2500,     "lng": -97.7500,     "variables": [         "income",         "population"     ]}level - The level data should be request for from the ACS5 (if any variables specified)geolevel - The level geographies should be split. Options are: blockGroup, place, tract. *For Montgomery County, MD, there is no "place" tag but instead "county"lat/lng - Coordinatesvariables - Optional variables to acquire from the ACS5 based uponThe response will be geoJSON of the requested city, with variable results attached as properties.

**Parameters**

**request**: `object`, The JSON request

**callback**: `function`, The callback to take the response, which is geoJSON




* * *










