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
| Authentication | API Key (`appid`) |

## Request URL

```http
GET https://api.openweathermap.org/data/2.5/weather?q=Delhi&units=metric&appid=YOUR_API_KEY
```

## Query Parameters

| Parameter | Type | Required | Description |
|----------|-------|----------|-------------|
| `q` | String | Yes | Name of the city for which weather information is requested |
| `units` | String | No | Specifies the unit system. Supported values are listed below. Defaults to `standard` if omitted. |
| `appid` | String | Yes | API key used to authenticate the request. |

### Temperature Units

| Value | Units |
|-------|-------|
| `standard` | Kelvin |
| `metric` | Celsius |
| `imperial` | Fahrenheit |

## Example Request

The following example retrieves the current weather information for Delhi in metric units.


```http
GET https://api.openweathermap.org/data/2.5/weather?q=Delhi&units=metric&appid=YOUR_API_KEY
```
The following example retrieves the current weather information for Delhi in Fahrenheit.

```http
GET https://api.openweathermap.org/data/2.5/weather?q=Delhi&units=imperial&appid=YOUR_API_KEY
```

> **Note:** Replace `YOUR_API_KEY` with your actual OpenWeatherMap API key.

## Example Response

The following example shows a successful response returned by the Current Weather endpoint.

```json
{
    "coord": {
        "lon": 77.2167,
        "lat": 28.6667
    },
    "weather": [
        {
            "id": 804,
            "main": "Clouds",
            "description": "overcast clouds",
            "icon": "04d"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 30.59,
        "feels_like": 36.24,
        "temp_min": 30.59,
        "temp_max": 30.59,
        "pressure": 999,
        "humidity": 69,
        "sea_level": 999,
        "grnd_level": 975
    },
    "visibility": 10000,
    "wind": {
        "speed": 3.84,
        "deg": 105,
        "gust": 3.4
    },
    "clouds": {
        "all": 100
    },
    "dt": 1785912974,
    "sys": {
        "country": "IN",
        "sunrise": 1785888871,
        "sunset": 1785937187
    },
    "timezone": 19800,
    "id": 1273294,
    "name": "Delhi",
    "cod": 200
}
```

## Response Fields

The following table describes the most commonly used fields returned in the response.

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `coord.lon` | number | Longitude of the requested location. | `77.2167` |
| `coord.lat` | number | Latitude of the requested location. | `28.6667` |
| `weather.id` | integer | Weather condition identifier. | `804` |
| `weather.main` | string | Primary weather condition. | `Clouds` |
| `weather.description` | string | Detailed description of the weather condition. | `overcast clouds` |
| `weather.icon` | string | Weather icon identifier. | `04d` |
| `base` | string | Internal parameter used by the API. | `stations` |
| `main.temp` | number | Current temperature. | `30.59` |
| `main.feels_like` | number | Perceived temperature based on weather conditions. | `36.24` |
| `main.temp_min` | number | Minimum temperature observed for the location. | `30.59` |
| `main.temp_max` | number | Maximum temperature observed for the location. | `30.59` |
| `main.pressure` | integer | Atmospheric pressure. | `999` |
| `main.humidity` | integer | Relative humidity percentage. | `69` |
| `main.sea_level` | integer | Atmospheric pressure at sea level. | `999` |
| `main.grnd_level` | integer | Atmospheric pressure at ground level. | `975` |
| `visibility` | integer | Visibility distance in meters. | `10000` |
| `wind.speed` | number | Wind speed. | `3.84` |
| `wind.deg` | integer | Wind direction in degrees. | `105` |
| `wind.gust` | number | Wind gust speed. | `3.4` |
| `clouds.all` | integer | Cloudiness percentage. | `100` |
| `dt` | integer | Time of data calculation (Unix timestamp). | `1785912974` |
| `sys.country` | string | Country code. | `IN` |
| `sys.sunrise` | integer | Sunrise time (Unix timestamp). | `1785888871` |
| `sys.sunset` | integer | Sunset time (Unix timestamp). | `1785937187` |
| `timezone` | integer | Shift from UTC in seconds. | `19800` |
| `id` | integer | Unique city identifier. | `1273294` |
| `name` | string | Name of the requested location. | `Delhi` |
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
| `404 Not Found` | The specified location could not be found.|