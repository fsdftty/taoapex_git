# TaoApex API Documentation

The [TaoApex](https://taoapex.com/) API allows developers to integrate [PromptHub](https://taoapex.com/en/products/prompt/) functionality into their applications.

> **Note:** API access is available on PromptHub Pro and above plans.

## Authentication

All API requests require authentication using an API key.

```bash
curl https://api.taoapex.com/v1/prompts \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Getting Your API Key

1. Log in to [https://taoapex.com/](https://taoapex.com/)
2. Go to Settings > API
3. Click "Generate API Key"
4. Copy and store your key securely

## Base URL

```
https://api.taoapex.com/v1
```

## Endpoints

### List Prompts

Get all prompts in your library.

```
GET /prompts
```

**Query Parameters:**
| Parameter | Type | Description |
|-----------|------|-------------|
| `page` | integer | Page number (default: 1) |
| `limit` | integer | Items per page (default: 20, max: 100) |
| `folder` | string | Filter by folder ID |
| `tags` | string | Filter by tags (comma-separated) |
| `search` | string | Full-text search |

**Response:**
```json
{
  "data": [
    {
      "id": "prompt_123",
      "title": "Blog Post Generator",
      "content": "Write a blog post about {{topic}}...",
      "tags": ["content", "blog"],
      "folder_id": "folder_456",
      "created_at": "2024-01-15T10:30:00Z",
      "updated_at": "2024-01-15T10:30:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 150
  }
}
```

### Get Single Prompt

```
GET /prompts/:id
```

### Create Prompt

```
POST /prompts
```

**Request Body:**
```json
{
  "title": "My New Prompt",
  "content": "Write a {{length}} article about {{topic}}",
  "tags": ["writing", "article"],
  "folder_id": "folder_456"
}
```

### Update Prompt

```
PUT /prompts/:id
```

### Delete Prompt

```
DELETE /prompts/:id
```

### List Folders

```
GET /folders
```

### Create Folder

```
POST /folders
```

**Request Body:**
```json
{
  "name": "Work Projects",
  "parent_id": null
}
```

## Rate Limits

| Plan | Requests/minute |
|------|----------------|
| Pro | 60 |
| Team | 120 |
| Enterprise | Custom |

## Error Codes

| Code | Description |
|------|-------------|
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid API key |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error |

## SDKs & Libraries

Coming soon:
- JavaScript/TypeScript SDK
- Python SDK
- Go SDK

## Webhooks

Webhook support is available on Team and Enterprise plans. Configure webhooks to receive notifications when:
- Prompts are created, updated, or deleted
- Team members make changes
- Usage thresholds are reached

## Support

For API support, please contact:
- **Email:** api-support@taoapex.com
- **GitHub:** [Create an Issue](https://github.com/taoapex/taoapex/issues)

---

[Back to Documentation](./README.md) | [PromptHub Guide](./prompthub.md) | [Try PromptHub](https://taoapex.com/en/products/prompt/) | [TaoApex Home](https://taoapex.com/)
