# Log Management API

This API provides REST endpoints for logging `info`, `warning`, and `error` messages to a centralized system. Users can send POST requests to the respective endpoints with their API key and log message.

---

## Table of Contents

- [Base URL](#base-url)
- [Authentication](#authentication)
- [Endpoints](#endpoints)
  - [Log Info](#log-info)
  - [Log Warning](#log-warning)
  - [Log Error](#log-error)
- [Request Examples](#request-examples)
- [Response Format](#response-format)
- [Error Handling](#error-handling)

---

## Base URL

```
http://your-flask-server-url
```

---

## Authentication

Each request requires an `apiKey` in the JSON body for authentication. This key identifies the application making the request.

---

## Endpoints

### Log Info
- **URL**: `/logInfo`
- **Method**: `POST`
- **Description**: Logs an informational message.
- **Request Body** (JSON):
  ```json
  {
    "apiKey": "your-api-key",
    "log": "Informational message"
  }
  ```

### Log Warning
- **URL**: `/logWarning`
- **Method**: `POST`
- **Description**: Logs a warning message.
- **Request Body** (JSON):
  ```json
  {
    "apiKey": "your-api-key",
    "log": "Warning message"
  }
  ```

### Log Error
- **URL**: `/logError`
- **Method**: `POST`
- **Description**: Logs an error message.
- **Request Body** (JSON):
  ```json
  {
    "apiKey": "your-api-key",
    "log": "Error message"
  }
  ```

---

## Request Examples

### Log Info Example
```bash
curl -X POST http://your-flask-server-url/logInfo \
-H "Content-Type: application/json" \
-d '{
  "apiKey": "exampleApiKey123",
  "log": "This is an informational message."
}'
```

### Log Warning Example
```bash
curl -X POST http://your-flask-server-url/logWarning \
-H "Content-Type: application/json" \
-d '{
  "apiKey": "exampleApiKey123",
  "log": "This is a warning message."
}'
```

### Log Error Example
```bash
curl -X POST http://your-flask-server-url/logError \
-H "Content-Type: application/json" \
-d '{
  "apiKey": "exampleApiKey123",
  "log": "This is an error message."
}'
```

---

## Response Format

### Success Response
- **Status Code**: `200`
- **Body**:
  ```json
  {
    "success": true
  }
  ```

### Failure Response
- **Status Code**: `200`
- **Body**:
  ```json
  {
    "error": "error description"
  }
  ```

---

## Error Handling

1. **Unauthorized**:
   - If the `apiKey` is invalid or missing, the server will return:
     ```json
     {
       "error": "unauthorized"
     }
     ```

2. **Internal Error**:
   - If the server encounters an issue while processing the log, the response will be:
     ```json
     {
       "error": "internal error"
     }
     ```

3. **Missing Parameters**:
   - If the request body is incomplete or malformed, the response will be:
     ```json
     {
       "error": "unauthorized"
     }
     ```

