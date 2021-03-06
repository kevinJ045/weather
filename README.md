Weather.js
==========

[![Build Status](https://secure.travis-ci.org/noazark/weather.svg?branch=master)](https://travis-ci.org/noazark/weather)
[![npm](https://img.shields.io/npm/v/weather.js.svg)](https://www.npmjs.com/package/weather.js)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/noazark/weather/master/LICENSE)


## About

There really should be a conclusive JavaScript weather library.
Weather.js fetches data from [OpenWeatherMap](http://openweathermap.org/) (no affiliation).
Since other providers format their output differently, currently this is
the only source provider.

Weather.js is still in early development so expect changes and please
contribute! Among the features I hope to incorporate:

-   historical weather information
-   API key usage (but there is a beta version!)
-   more data sources
-   more conversions!


## Install

Weather.js works in the browser and node.js. Take your pick. For the
browser, [download the most recent version on GitHub][Weather.js]. For use in
node, just install using NPM.

```
npm install -g weather.js
```

## Usage

At the moment you can access the current weather conditions and the
forecast for any city. By default it will use the closest match as
returned by Open Weather Map.

```javascript
// API Key methods
var apiKey = '12345';
Weather.setApiKey( apiKey );
var tempApiKey = Weather.getApiKey();

var cityId = '4393217';

// Get current Weather for a given city
Weather.getCurrent( 'Kansas City', function( current ) {
    console.log(
        [ 'Currently:', current.temperature(), 'and', current.conditions() ].join( ' ' );
    );
} );

// Get current Weather for a given city using the city id
Weather.getCurrentByCityId( cityId, function( current ) {
    console.log(
        [ 'Currently:', current.temperature(), 'and', current.conditions() ].join( ' ' );
    );
} );

// Get the forecast for a given city
Weather.getForecast( 'Kansas City', function( forecast ) {
    console.log( 'Forecast High in Kelvin: ' + forecast.high() );
    console.log( 'Forecast High in Fahrenheit' + Weather.kelvinToFahrenheit( forecast.high() ) );
    console.log( 'Forecast High in Celsius' + Weather.kelvinToCelsius( forecast.high() ) );
} );

// Get the forecast for a given city using the city id
Weather.getForecastByCityId( cityId, function( forecast ) {
    console.log( 'Forecast High in Kelvin: ' + forecast.high() );
    console.log( 'Forecast High in Fahrenheit' + Weather.kelvinToFahrenheit( forecast.high() ) );
    console.log( 'Forecast High in Celsius' + Weather.kelvinToCelsius( forecast.high() ) );
} );

// Get the forecast for a given city using the latitude and longitude
var lat = 39.100,
    long = -94.579;
Weather.getForecastByLatLong( lat, long, function( forecast ) {
    console.log( 'Forecast High in Kelvin: ' + forecast.high() );
    console.log( 'Forecast High in Fahrenheit' + Weather.kelvinToFahrenheit( forecast.high() ) );
    console.log( 'Forecast High in Celsius' + Weather.kelvinToCelsius( forecast.high() ) );
} );
```

[openweathermap.org]: http://openweathermap.org
[Weather.js]: http://github.com/noazark/weather
