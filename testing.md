# Weather API Testing

## Overview

This document records the functional testing performed on the Weather API using Swagger UI.

The testing covers positive and negative scenarios to verify that the API behaves as documented.

## Test Environment

| Item | Details |
|------|---------|
| API | Weather API |
| Endpoint | `GET /data/2.5/weather` |
| Tool | Swagger UI |
| Response Format | `application/json` |
| Authentication | API Key (`appid`) |

## Test Scenarios

### TC-01: Valid City with Metric Units

**Objective:** Verify that the API returns current weather information for a valid city when metric units are specified.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | `Delhi` |
| `units` | `metric` |
| `appid` | Valid API key |

**Expected Result:**

The API should return a successful response with HTTP status `200 OK` and current weather information for Delhi.

**Actual Result:**

The API returned HTTP status `200 OK` and current weather information for Delhi.

**Status:** PASS

---

### TC-02: Valid City with Imperial Units

**Objective:** Verify that the API returns current weather information when imperial units are specified.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | `Delhi` |
| `units` | `imperial` |
| `appid` | Valid API key |

**Expected Result:**

The API should return HTTP status `200 OK` with weather information using the imperial unit system.

**Actual Result:**

The API returned HTTP status `200 OK` with weather information using the imperial unit system.

**Status:** PASS

---

### TC-03: Valid City with Default Units

**Objective:** Verify that the API successfully processes the request when the optional `units` parameter is omitted.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | `Delhi` |
| `units` | Not provided |
| `appid` | Valid API key |

**Expected Result:**

The API should return HTTP status `200 OK` and use the standard unit system.

**Actual Result:**

The API returned HTTP status `200 OK` and weather information using the standard unit system.

**Status:** PASS

---

### TC-04: Missing Required City Parameter

**Objective:** Verify that the request cannot be submitted when the required `q` parameter is missing.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | Not provided |
| `units` | Not provided |
| `appid` | Valid API key |

**Expected Result:**

The request should be rejected because `q` is a required parameter.

**Actual Result:**

Swagger UI prevented the request from being executed and displayed the validation message:

> For 'q': Required field is not provided.

**Status:** PASS

**Note:** The request was not sent to the API because Swagger UI performed client-side validation.

---

### TC-05: Invalid API Key

**Objective:** Verify that the API rejects a request containing an invalid API key.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | `Delhi` |
| `units` | `metric` |
| `appid` | Invalid API key |

**Expected Result:**

The API should reject the request and return HTTP status `401 Unauthorized`.

**Actual Result:**

The API rejected the request and returned the expected unauthorized response.

**Status:** PASS

---

### TC-06: City Not Found

**Objective:** Verify that the API returns an appropriate error when the requested city does not exist.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | Invalid city name |
| `units` | `metric` |
| `appid` | Valid API key |

**Expected Result:**

The API should return HTTP status `404 Not Found` with an appropriate error message.

**Actual Result:**

The API returned HTTP status `404 Not Found` with the expected city-not-found error message.

**Status:** PASS

---

### TC-07: Invalid Units Value

**Objective:** Verify that an unsupported value cannot be submitted for the `units` parameter.

**Request Parameters:**

| Parameter | Value |
|-----------|-------|
| `q` | `Delhi` |
| `units` | `invalid` |
| `appid` | Valid API key |

**Expected Result:**

The request should not be executed because `invalid` is not an allowed value for the `units` parameter.

**Actual Result:**

Swagger UI did not allow the invalid value to be submitted and prevented the request from being executed.

**Status:** PASS

**Note:** The API itself was not called for this scenario because Swagger UI validated the `units` parameter against the OpenAPI `enum` values.

---

## Test Summary

| Test Case | Scenario | Expected Result | Status |
|-----------|----------|-----------------|--------|
| TC-01 | Valid city + metric | `200 OK` | PASS |
| TC-02 | Valid city + imperial | `200 OK` | PASS |
| TC-03 | Valid city + default units | `200 OK` | PASS |
| TC-04 | Missing `q` | Swagger validation error | PASS |
| TC-05 | Invalid API key | `401 Unauthorized` | PASS |
| TC-06 | City not found | `404 Not Found` | PASS |
| TC-07 | Invalid `units` | Swagger validation error | PASS |

## Conclusion

All seven test scenarios were successfully validated using Swagger UI.

The testing confirmed that the documented request parameters, authentication behavior, response codes, and validation rules are consistent with the observed API behavior.
