# OpenWeatherMap Current Weather API Documentation

## Overview

This repository contains technical documentation for the **Current Weather** endpoint of the OpenWeatherMap API.

The project demonstrates practical API documentation and testing using **Markdown, OpenAPI 3.0.3, Postman, Swagger Editor, Git, and GitHub**.

## Project Objectives

- Document the Current Weather API endpoint
- Create an API reference using Markdown
- Test API requests using Postman
- Create and validate an OpenAPI 3.0.3 specification
- Document positive and negative API test scenarios

## Technologies Used

- OpenWeatherMap API
- OpenAPI 3.0.3
- Swagger Editor
- Postman
- Markdown
- Git & GitHub

## Repository Structure

- `docs/` – Getting Started, Authentication, and API Reference documentation
- `openapi/` – OpenAPI specification
- `postman/` – Postman collection
- `examples/` – Sample requests and responses
- `images/` – Screenshots and diagrams

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

