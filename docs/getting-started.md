# Getting Started

## Overview

The OpenWeatherMap Current Weather API provides real-time weather information for a specified location. Developers can retrieve weather details such as temperature, humidity, wind speed, atmospheric pressure, and weather conditions by sending HTTP requests to the API.

This guide explains the prerequisites, authentication method, base URL, and how to make your first API request.

---

## Prerequisites

Before using the API, ensure you have the following:

- An active **OpenWeatherMap** account.
- A valid **API key**.
- An API client such as **Postman** to test API requests.
- A basic understanding of **HTTP requests** and **JSON** responses.

---

## Base URL

`https://api.openweathermap.org`

---

## Authentication

The OpenWeatherMap API uses **API Key Authentication**.

Include your API key in the `appid` query parameter with every request.

**Example**

```text
appid=API_KEY
```

> **Note:** Never expose your actual API key in public repositories. Always use `API_KEY` as a placeholder in documentation.

For more information, see the [Authentication](authentication.md) guide.
---

## First API Request

**HTTP Method:** `GET`

**Endpoint:** `/data/2.5/weather`

### Example Request

```http
GET https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=API_KEY
```

---

## Query Parameters

| Parameter | Required | Description | Example |
|-----------|----------|-------------|---------|
| `q` | Yes | Name of the city for which weather information is required. | `London` |
| `units` | No | Specifies the unit system for temperature values. | `metric` |
| `appid` | Yes | API key used to authenticate the request. | `API_KEY` |

---

## Expected Response

If the request is successful, the API returns:

- **Status Code:** `200 OK`
- **Response Format:** `application/json`

### Example Response

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
---

## Next Steps

- See the [Authentication](authentication.md) guide for details about API key authentication.
- See the [API Reference](api-reference.md) for endpoint parameters, response fields, and error responses.
- See the [API Testing](../testing.md) documentation for Postman test scenarios and results.