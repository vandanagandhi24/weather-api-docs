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
appid=YOUR_API_KEY
```

> **Note:** Never expose your actual API key in public repositories. Always use `YOUR_API_KEY` as a placeholder in documentation.

---

## First API Request

**HTTP Method:** `GET`

**Endpoint:** `/data/2.5/weather`

### Example Request

```http
GET https://api.openweathermap.org/data/2.5/weather?q=Delhi&units=metric&appid=YOUR_API_KEY
```

---

## Query Parameters

| Parameter | Required | Description | Example |
|-----------|----------|-------------|---------|
| `q` | Yes* | Name of the city for which weather information is required. | `Delhi` |
| `units` | No | Specifies the unit system for temperature values. | `metric` |
| `appid` | Yes | API key used to authenticate the request. | `YOUR_API_KEY` |

---

## Expected Response

If the request is successful, the API returns:

- **Status Code:** `200 OK`
- **Response Format:** `application/json`

### Example Response

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
        "temp": 34.09,
        "feels_like": 39.65,
        "temp_min": 34.09,
        "temp_max": 34.09,
        "pressure": 1002,
        "humidity": 53,
        "sea_level": 1002,
        "grnd_level": 977
    },
    "visibility": 10000,
    "wind": {
        "speed": 2.63,
        "deg": 98,
        "gust": 1.67
    },
    "clouds": {
        "all": 100
    },
    "dt": 1785827879,
    "sys": {
        "country": "IN",
        "sunrise": 1785802437,
        "sunset": 1785850831
    },
    "timezone": 19800,
    "id": 1273294,
    "name": "Delhi",
    "cod": 200
}
```
