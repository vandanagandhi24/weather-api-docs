# API Reference

## Overview

The `/data/2.5/weather` endpoint retrieves the current weather information for a specified location.

Use this endpoint to obtain weather details such as temperature, humidity, atmospheric pressure, wind speed, cloud coverage, and weather conditions in JSON format.

## Endpoint Information

| Property | Value |
|----------|-------|
| HTTP Method | `GET` |
| Base URL | `https://api.openweathermap.org` |
| Endpoint | `/data/2.5/weather` |
| Response Format | `application/json` |
| Authentication | API key passed through the `appid` query parameter |

## Request URL

```http
GET https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=API_KEY
```

## Query Parameters

| Parameter | Type | Required | Description |
|----------|-------|----------|-------------|
| `q` | string | Yes | Name of the city for which weather information is requested |
| `units` | string | No | Specifies the unit system. Supported values are listed below. Defaults to `standard` if omitted. |
| `appid` | string | Yes | API key used to authenticate the request. |

### Temperature Units

| Value | Units |
|-------|-------|
| `standard` | Kelvin |
| `metric` | Celsius |
| `imperial` | Fahrenheit |

## Example Request

The following example retrieves the current weather information for London in metric units.


```http
GET https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=API_KEY
```
The following example retrieves the current weather information for London in Fahrenheit.

```http
GET https://api.openweathermap.org/data/2.5/weather?q=London&units=imperial&appid=API_KEY
```

> **Note:** Replace `API_KEY` with your actual OpenWeatherMap API key.

## Example Response

The following example shows a successful response returned by the Current Weather endpoint.

```json
{
    "coord": {
        "lon": -0.1257,
        "lat": 51.5085
    },
    "weather": [
        {
            "id": 802,
            "main": "Clouds",
            "description": "scattered clouds",
            "icon": "03d"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 17.07,
        "feels_like": 16.66,
        "temp_min": 15.57,
        "temp_max": 18.26,
        "pressure": 1021,
        "humidity": 70,
        "sea_level": 1021,
        "grnd_level": 1017
    },
    "visibility": 10000,
    "wind": {
        "speed": 3.09,
        "deg": 70
    },
    "clouds": {
        "all": 40
    },
    "dt": 1787559272,
    "sys": {
        "type": 2,
        "id": 2075535,
        "country": "GB",
        "sunrise": 1787547613,
        "sunset": 1787598363
    },
    "timezone": 3600,
    "id": 2643743,
    "name": "London",
    "cod": 200
}
```

## Response Fields

The following table describes the most commonly used fields returned in the response.

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `coord.lon` | number | Longitude of the requested location. | `-0.1257` |
| `coord.lat` | number | Latitude of the requested location. | `51.5085` |
| `weather.id` | integer | Weather condition identifier. | `802` |
| `weather.main` | string | Primary weather condition. | `Clouds` |
| `weather.description` | string | Detailed description of the weather condition. | `scattered clouds` |
| `weather.icon` | string | Weather icon identifier. | `03d` |
| `base` | string | Internal parameter used by the API. | `stations` |
| `main.temp` | number | Current temperature. | `17.07` |
| `main.feels_like` | number | Perceived temperature based on weather conditions. | `16.66` |
| `main.temp_min` | number | Minimum temperature observed for the location. | `15.57` |
| `main.temp_max` | number | Maximum temperature observed for the location. | `18.26` |
| `main.pressure` | integer | Atmospheric pressure. | `1021` |
| `main.humidity` | integer | Relative humidity percentage. | `70` |
| `main.sea_level` | integer | Atmospheric pressure at sea level. | `1021` |
| `main.grnd_level` | integer | Atmospheric pressure at ground level. | `1017` |
| `visibility` | integer | Visibility distance in meters. | `10000` |
| `wind.speed` | number | Wind speed. | `3.09` |
| `wind.deg` | integer | Wind direction in degrees. | `70` |
| `clouds.all` | integer | Cloudiness percentage. | `40` |
| `dt` | integer | Time of data calculation (Unix timestamp). | `1787559272` |
| `sys.type` | integer | Internal system type identifier. | `2` |
| `sys.id` | integer | Internal system identifier. | `2075535` |
| `sys.country` | string | Country code. | `GB` |
| `sys.sunrise` | integer | Sunrise time (Unix timestamp). | `1787547613` |
| `sys.sunset` | integer | Sunset time (Unix timestamp). | `1787598363` |
| `timezone` | integer | Shift from UTC in seconds. | `3600` |
| `id` | integer | Unique city identifier. | `2643743` |
| `name` | string | Name of the requested location. | `London` |
| `cod` | integer | Response status code returned by the API. | `200` |

## Error Responses

The API returns standard HTTP status codes to indicate the success or failure of a request.

| Status Code | Description |
|-------------|-------------|
| `400 Bad Request` | Invalid or missing request parameters. |
| `401 Unauthorized` | Missing or invalid API key. |
| `404 Not Found` | Requested location was not found. |

### 400 Bad Request

This response is returned when the required `q` parameter is missing.

```json
{
    "cod": "400",
    "message": "Nothing to geocode"
}
```

### 401 Unauthorized

This response is returned when the API key is missing or invalid.

```json
{
    "cod": 401,
    "message": "Invalid API key."
}
```

### 404 Not Found

This response is returned when the specified city or location cannot be found.

```json
{
    "cod": "404",
    "message": "city not found"
}
```

## Status Codes

| Status Code | Description |
|-------------|-------------|
| `200 OK` | The request was processed successfully. |
| `400 Bad Request` | The request contains invalid or missing parameters. |
| `401 Unauthorized` | Authentication failed because the API key is missing or invalid. |
| `404 Not Found` | The specified location could not be found. |