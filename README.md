# Trip Planner

A single-page web app that helps you plan a trip. Enter where you are leaving from and where you want to go, and it shows the distance, the current weather, and a 7-day forecast for your destination.

Built with plain HTML, CSS and JavaScript. No frameworks, no build step, no API keys.

## Features

- **Distance:** straight-line distance between two places in kilometres and miles
- **Travel time estimates:** approximate flight time, and approximate road time for trips under 2,500 km
- **Current weather:** temperature, conditions, wind speed and humidity at the destination
- **7-day forecast:** daily high and low, conditions and chance of rain
- **Travel date:** pick a date in the next 7 days and that day is highlighted in the forecast
- **Packing hints:** simple suggestions based on the forecast (hot, cold, rain)
- **Use my location:** fill in the starting point from your browser's location
- **Responsive and theme-aware:** works on phones and follows your light or dark mode setting

## Getting started

1. Download `trip-planner.html`.
2. Open it in any modern browser (double-click the file).
3. Make sure you are online, because the app fetches live data.

That's it. There is nothing to install.

## How to use

1. Type your starting city in **Leaving from** (it defaults to Delhi), or click **Use my current location**.
2. Type your destination in **Going to**, for example `Paris`, `Tokyo` or `Dubai`.
3. Optionally choose a **Travel date**.
4. Click **Plan my trip**.

## How it works

| Step | What happens | Used |
| --- | --- | --- |
| 1 | City names are converted to latitude and longitude | [Open-Meteo Geocoding API](https://open-meteo.com/en/docs/geocoding-api) |
| 2 | Weather and forecast for the destination are fetched | [Open-Meteo Forecast API](https://open-meteo.com/en/docs) |
| 3 | Distance is calculated in the browser | Haversine formula (`distanceKm` function) |
| 4 | Results are drawn into the page | DOM manipulation |

### The Haversine formula

The Haversine formula calculates the shortest distance between two points on a sphere using their latitudes and longitudes. The app uses an Earth radius of 6,371 km.

## Project structure

```
trip-planner.html   # the whole app: markup, styles and script
README.md
```

## Limitations

- The distance is a **straight line**, not a driving or flight route. Actual road distances will be longer.
- Flight and road times are **rough estimates** (flights assume about 800 km/h plus 30 minutes, roads assume about 60 km/h on a route 30% longer than the straight line).
- If several places share a name, the app uses the first match from the geocoding service.
- The forecast covers 7 days only.
- It needs an internet connection.
- "Use my current location" needs your permission, and some browsers only allow it on `https://` pages or `localhost` rather than a file opened from disk. If it does not work, type your city instead.

## Possible improvements

- Show the route on an interactive map
- Real road distance and time using a routing API
- Currency converter for the destination
- Save favourite destinations in `localStorage`
- Let the user choose between Celsius and Fahrenheit

## Credits

Weather and place data provided by [Open-Meteo](https://open-meteo.com/), which is free for non-commercial use.
