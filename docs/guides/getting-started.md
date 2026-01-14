# Getting Started

This guide helps you get up and running with the Example Platform as quickly as possible.

It is intended for developers and technical users who want to integrate with the platform or evaluate its functionality.

## Prerequisites

Before you begin, make sure you have:

- Basic understanding of REST APIs
- An HTTP client (for example: curl or Postman)
- A valid API key
- Internet access

## Step 1: Obtain an API Key

To authenticate with the platform, you need an API key.

1. Log in to the developer portal.
2. Navigate to **Settings → API Keys**.
3. Generate a new API key.
4. Store the key securely.

> ⚠️ Important  
> Keep your API key private. Do not expose it in public repositories or client-side code.

## Step 2: Make Your First API Request

Once you have your API key, you can make your first request.

### Example request

```bash
curl -X GET "https://api.example.com/v1/users" \
  -H "Authorization: Bearer <API_KEY>"
```

### Example response

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

If you receive a `200 OK` response, your integration is working correctly.

## Step 3: Create a Resource

To create a new user, send a POST request to the `/users` endpoint.

### Example request

```bash
curl -X POST "https://api.example.com/v1/users" \
  -H "Authorization: Bearer <API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "securePassword"
  }'
```

### Successful response

```json
{
  "id": "123",
  "status": "created"
}
```

## Step 4: Handle Errors

The API uses standard HTTP status codes to indicate success or failure.

| Status Code | Description |
|------------|-------------|
| 400 | Invalid request |
| 401 | Unauthorized |
| 404 | Resource not found |
| 500 | Internal server error |

Always validate responses and handle errors gracefully in your application.

## Next Steps

Now that you have completed the basic setup, you can:

- Review the full API Reference
- Explore available endpoints and request limits
- Implement retry logic and error handling
- Configure advanced settings

## Need Help?

If you have issues:

- Verify that your API key is valid
- Check request headers and payloads
- Review error messages returned by the API

For detailed endpoint descriptions, see the full API reference.
