# OpenWeatherMap Current Weather API Documentation

## Overview

This repository contains API documentation for the **Current Weather** endpoint of the OpenWeatherMap API. It demonstrates API documentation best practices using Markdown, OpenAPI 3.1, Postman, Git, and GitHub.

## Project Objectives

- Document the Current Weather endpoint
- Test API requests using Postman
- Write API reference documentation
- Create an OpenAPI 3.1 specification
- Generate interactive documentation using Swagger UI and Redoc
- Publish the documentation using GitHub Pages

## Technologies Used

- OpenWeatherMap API
- OpenAPI 3.1
- Swagger Editor
- Postman
- Markdown
- Git & GitHub
- GitHub Pages

## Repository Structure

- `docs/` – API documentation pages
- `openapi/` – OpenAPI specification

## Understanding the API Response

The Current Weather API returns weather information for the requested location.

The following fields provide key weather details:

| Field | Description |
|---|---|
| `name` | Name of the requested city. |
| `main.temp` | Current temperature. |
| `main.humidity` | Humidity percentage. |
| `weather[0].description` | Description of the current weather conditions. |
| `wind.speed` | Wind speed. |

**Note:** The temperature and wind speed units depend on the `units` parameter. If no unit is specified, the API uses its default units.
- `postman/` – Postman collection
- `examples/` – Sample requests and responses
- `images/` – Screenshots and diagrams
