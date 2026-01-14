# API Reference

This document provides a detailed reference for the Example Platform REST API.

The API is designed to be predictable, resource-oriented, and easy to integrate with.

## Base URL

All API requests must be sent to the following base URL:

```
https://api.example.com/v1
```

## Authentication

The API uses API key–based authentication.

Each request must include an `Authorization` header with a valid bearer token.

### Header format

```
Authorization: Bearer <API_KEY>
```

Requests without valid authentication will return `401 Unauthorized`.

## Content Type

All requests and responses use JSON.

### Required header

```
Content-Type: application/json
```


## HTTP Status Codes

The API uses standard HTTP status codes to indicate the success or failure of requests.

| Status Code | Meaning |
|------------|---------|
| 200 | Request succeeded |
| 201 | Resource created |
| 400 | Bad request |
| 401 | Unauthorized |
| 404 | Resource not found |
| 500 | Internal server error |

## Endpoints

### GET /users

Retrieve a list of users.

#### Request

```
GET /users
```

#### Query Parameters

| Name | Type | Description |
|-----|------|-------------|
| limit | integer | Number of users to return |
| page | integer | Page number |

#### Example Request

```bash
curl -X GET "https://api.example.com/v1/users?limit=10&page=1" \
  -H "Authorization: Bearer <API_KEY>"
```

#### Example Response – 200 OK

```json
{
  "users": [
    {
      "id": "123",
      "email": "user@example.com",
      "status": "active"
    }
  ]
}
```

### GET /users/{id}

Retrieve a single user by ID.

#### Request

```
GET /users/{id}
```

#### Path Parameters

| Name | Type | Description |
|-----|------|-------------|
| id | string | User identifier |

#### Example Request

```bash
curl -X GET "https://api.example.com/v1/users/123" \
  -H "Authorization: Bearer <API_KEY>"
```

#### Example Response – 200 OK

```json
{
  "id": "123",
  "email": "user@example.com",
  "status": "active"
}
```

### POST /users

Create a new user.

#### Request

```
POST /users
```

#### Request Body

```json
{
  "email": "user@example.com",
  "password": "securePassword"
}
```

#### Example Request

```bash
curl -X POST "https://api.example.com/v1/users" \
  -H "Authorization: Bearer <API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "securePassword"
  }'
```

#### Example Response – 201 Created

```json
{
  "id": "123",
  "status": "created"
}
```

## Error Responses

When an error occurs, the API returns a JSON response with details.

### Error Response Format

```json
{
  "error": {
    "code": 400,
    "message": "Invalid request"
  }
}
```

### Common Errors

| Code | Message | Description |
|-----|---------|-------------|
| 400 | Invalid request | Request validation failed |
| 401 | Unauthorized | Missing or invalid API key |
| 404 | Not found | Resource does not exist |
| 500 | Internal error | Unexpected server error |

## Rate Limiting

To ensure fair usage, the API enforces rate limits.

- 100 requests per minute per API key
- Exceeding the limit returns `429 Too Many Requests`

## Versioning

The API is versioned using the URL.

Example:

```
https://api.example.com/v1
```

Breaking changes will be introduced in new major versions.

## Related Documentation

- Getting Started Guide
- Installation & Configuration Guide
- Release Notes
