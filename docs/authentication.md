# Authentication

## Overview

The OpenWeatherMap Current Weather API uses **API Key Authentication** to authorize API requests. Every request must include a valid API key.

Pass the API key using the `appid` query parameter.

Example:

`appid=YOUR_API_KEY`

> **Note:** Never expose your actual API key in public repositories. Always use `YOUR_API_KEY` as a placeholder in documentation and code samples.

---

## Example Request

The following example shows how to authenticate a request using an API key.

```http
GET https://api.openweathermap.org/data/2.5/weather?q=Delhi&units=metric&appid=YOUR_API_KEY
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
  "message": "Invalid API key. Please see https://openweathermap.org/faq#error401 for more info."
}
```

---

## Security Best Practices

Follow these best practices when working with API keys:

- Never commit your API key to a public Git repository.
- Store API keys securely using environment variables or a secret management solution.
- Replace your actual API key with `YOUR_API_KEY` in documentation and code examples.
- Regenerate your API key immediately if it is accidentally exposed.

---