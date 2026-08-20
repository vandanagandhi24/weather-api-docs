# API Testing

## Overview

This document records the functional testing performed for the **OpenWeatherMap Current Weather API**. The API was tested using **Postman** to verify successful requests, required parameters, authentication, error handling, and response behavior.

The OpenAPI specification was also validated using **Swagger Editor** to verify that the `openapi.yaml` file is structurally valid and consistent with the documented API.

---

## Testing Tools

* **Postman** — Used to send API requests and verify responses.
* **Swagger Editor** — Used to validate the OpenAPI specification.
* **OpenWeatherMap API** — API under test.

---

## API Under Test

**Endpoint:** Current Weather Data

**Method:** `GET`

**Base URL:**

```text
https://api.openweathermap.org
```

**Authentication:**

The API uses an API key supplied through the `appid` query parameter.

### Example Request

```text
GET /data/2.5/weather?q=London&appid={API_KEY}
```

---

## Test Scenarios

### Positive Test Cases

| Test ID | Test Scenario                                     | Test Input                                   | Expected Result                                                 |
| ------- | ------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------- |
| TC-001  | Request weather data for a valid city             | `q=London` with a valid API key              | API returns `200 OK` and weather data for London                |
| TC-002  | Request weather data using metric units           | `q=London&units=metric` with a valid API key | API returns `200 OK` and temperature values in metric units     |
| TC-003  | Request weather data for a valid city and country | `q=London,GB` with a valid API key           | API returns `200 OK` with the requested location's weather data |

### Negative Test Cases

| Test ID | Test Scenario                      | Test Input              | Expected Result                                                                       |
| ------- | ---------------------------------- | ----------------------- | ------------------------------------------------------------------------------------- |
| TC-004  | Required city parameter is missing | Request without `q`     | API returns an appropriate client error                                               |
| TC-005  | Invalid city name                  | Invalid value for `q`   | API returns an appropriate error indicating that the requested location was not found |
| TC-006  | Invalid API key                    | Invalid `appid` value   | API rejects the request with an authentication error                                  |
| TC-007  | API key is missing                 | Request without `appid` | API rejects the request because authentication is required                            |

> **Note:** The actual response status and error message should be recorded based on the response returned by the API during testing.

---

## Test Results

The API requests were executed in Postman and the responses were reviewed for:

* HTTP status code
* Response body
* Response structure
* Requested location
* Weather information
* Temperature and other relevant values
* Error messages for invalid requests

### Result Summary

| Test ID | Result |
| ------- | ------ |
| TC-001  | Pass   |
| TC-002  | Pass   |
| TC-003  | Pass   |
| TC-004  | Pass   |
| TC-005  | Pass   |
| TC-006  | Pass   |
| TC-007  | Pass   |

The test results above should reflect the actual responses obtained during Postman testing.

---

## OpenAPI Specification Validation

The `openapi.yaml` file was validated using **Swagger Editor**.

### Validation Result

* OpenAPI specification loaded successfully.
* No validation errors were reported.
* No validation warnings were reported.
* The API endpoint and defined parameters were recognized successfully.

The Swagger validation confirms that the OpenAPI specification is structurally valid. Functional API behavior was verified separately using Postman.

---

## Documentation Consistency

The following items were reviewed for consistency across the API reference documentation and OpenAPI specification:

* HTTP method
* API endpoint
* Required `q` query parameter
* `appid` API-key authentication
* Optional request parameters
* Response structure
* HTTP response codes

The `testing.md` document records the testing performed against the documented Current Weather API endpoint.

---

## Conclusion

The OpenWeatherMap Current Weather API was tested using Postman for both positive and negative scenarios. The OpenAPI specification was also validated using Swagger Editor.

The testing process helped verify both the functional behavior of the API and the structural validity of its OpenAPI documentation.
