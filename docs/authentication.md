# Authentication

## Overview

The OpenWeatherMap Current Weather API uses **API key authentication** to authorize API requests. Every request must include a valid API key.

Pass the API key using the `appid` query parameter.

Example:

`appid=API_KEY`

> **Note:** Never expose your actual API key in public repositories. Always use `API_KEY` as a placeholder in documentation and code samples.

---

## Example Request

The following example shows how to authenticate a request using an API key.

```http
GET https://api.openweathermap.org/data/2.5/weather?q=London&units=metric&appid=API_KEY
```

---

## Authentication Errors

If the API key is missing, invalid, or inactive, the API returns an authentication error.

| Status Code | Description |
| ------------ | ----------- |
| `401 Unauthorized` | Missing, invalid, or inactive API key. |

### Example Error Response

```json
{
  "cod": 401,
  "message": "Invalid API key."
}
```

---

## Security Best Practices

Follow these best practices when working with API keys:

- Never commit your API key to a public Git repository.
- Store API keys securely using environment variables or a secret management solution.
- Replace your actual API key with `API_KEY` in documentation and code examples.
- Regenerate your API key immediately if it is accidentally exposed.

For a step-by-step introduction to making your first API request, see the [Getting Started](getting-started.md) guide.

---