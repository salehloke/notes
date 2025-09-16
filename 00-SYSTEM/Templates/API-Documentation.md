---
created: {{date}}
updated: {{date}}
status: draft
area: Work
tags: [work, api, documentation, reference]
module: {{MODULE}}
service: {{SERVICE_NAME}}
---

# API Documentation – {{title}}

## Service Overview
- **Base URL**: `{{BASE_URL}}`
- **Service**: {{SERVICE_NAME}}
- **Module**: {{MODULE}}
- **Authentication**: JWT Bearer Token / API Key
- **Version**: v{{VERSION}}

## Authentication
```http
Authorization: Bearer <jwt_token>
# OR
Authorization: Key <api_key>
```

## Endpoints

### Endpoint Name
```http
{{METHOD}} {{ENDPOINT_PATH}}
Content-Type: application/json
Authorization: Bearer <token>
```

#### Request
```json
{
  "field1": "value",
  "field2": 123
}
```

#### Response (Success - 200)
```json
{
  "data": {
    "id": "12345",
    "result": "success"
  },
  "message": "Operation completed successfully"
}
```

#### Response (Error - 400/500)
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": []
  }
}
```

#### Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| field1 | string | Yes | Description of field1 |
| field2 | number | No | Description of field2 |

#### Usage Example
```bash
curl -X {{METHOD}} \
  "{{BASE_URL}}{{ENDPOINT_PATH}}" \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"field1": "value", "field2": 123}'
```

## Data Models

### ModelName
```typescript
interface ModelName {
  id: string;
  name: string;
  createdAt: Date;
  updatedAt: Date;
}
```

## Error Codes
| Code | HTTP Status | Description |
|------|-------------|-------------|
| VALIDATION_ERROR | 400 | Input validation failed |
| UNAUTHORIZED | 401 | Invalid or missing authentication |
| FORBIDDEN | 403 | Insufficient permissions |
| NOT_FOUND | 404 | Resource not found |
| INTERNAL_ERROR | 500 | Server internal error |

## Rate Limits
- **Rate**: 100 requests per minute per API key
- **Burst**: 10 requests per second

## Related APIs
- [[API Name 1]]
- [[API Name 2]]

## Related Work
- [[Ticket Reference]]
- [[Project Reference]]

## Notes
- Additional implementation notes
- Known issues or limitations
- Performance considerations

---
*Last updated: {{date}}*
*Environment: Local/SIT/UAT/PRD*