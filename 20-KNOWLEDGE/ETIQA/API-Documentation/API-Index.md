---
created: 2025-01-15
updated: 2025-01-15
status: active
area: Work
tags: [work, api, documentation, index, reference]
module: ALL
---

# API Documentation Index

## Quick Access
- [[#Backend APIs]] - NestJS microservices
- [[#Frontend APIs]] - Client-side service layers  
- [[#Third-Party APIs]] - External integrations
- [[#Development Tools]] - Testing and utilities

## Backend APIs

### Core Services
- [[Portal-Enjoy-Rewards-API]] - Enjoy rewards management
- [[Auth-Service-API]] - Authentication and authorization
- [[Smile-Service-API]] - Main customer services
- [[Tracker-Service-API]] - Analytics and tracking
- [[Wellness-Service-API]] - Wellness features
- [[Broker-Service-API]] - Broker management

### API Patterns
```typescript
// Standard response format
interface ApiResponse<T> {
  data: T;
  message?: string;
  meta?: {
    pagination?: PaginationInfo;
    timestamp: string;
  };
}

// Error response format  
interface ApiError {
  error: {
    code: string;
    message: string;
    details?: any[];
  };
}
```

### Authentication
All backend APIs use JWT Bearer token authentication:
```http
Authorization: Bearer <jwt_token>
```

## Frontend APIs

### Service Layers
- [[Portal-Customer-API]] - Customer portal services
- [[BackOffice-Admin-API]] - Admin interface services
- [[Micro-Site-APIs]] - Micro-site service integrations

### Common Patterns
```typescript
// Axios service configuration
const basePath = "/api/v5/endpoint";

// Error handling pattern
try {
  const response = await axios.get(endpoint);
  return response.data;
} catch (error) {
  if (axios.isAxiosError(error)) {
    return error.response?.data;
  }
  throw error;
}
```

## Third-Party APIs

### External Integrations
- [[WOGI-Provider-API]] - Voucher provider integration
- [[External-Services-API]] - Other third-party services

## Development Environment

### Base URLs by Environment
| Environment | Base URL | Port |
|-------------|----------|------|
| Local | `http://localhost:10100` | 10100 |
| SIT | `https://sit-api.domain.com` | 443 |
| UAT | `https://uat-api.domain.com` | 443 |
| Production | `https://api.domain.com` | 443 |

### Common Headers
```http
Content-Type: application/json
Authorization: Bearer <token>
X-API-Version: v5
```

## Testing & Utilities

### API Testing Tools
- **Postman Collections** - Available in `docs/postman/`
- **curl Examples** - Included in each API documentation
- **Swagger/OpenAPI** - Available at `/api/docs` endpoints

### Development Workflow
1. **Local Development**
   ```bash
   # Start backend services
   cd smile-aio/backend
   npm run dev:all
   
   # Backend APIs available at:
   # http://localhost:10100/api/*
   ```

2. **API Documentation Updates**
   - Update relevant API markdown file
   - Test endpoints in Postman
   - Update this index if new APIs added
   - Link related work tickets

## Quick Reference

### HTTP Status Codes
| Code | Meaning | Usage |
|------|---------|-------|
| 200 | OK | Successful GET, PUT, PATCH |
| 201 | Created | Successful POST |
| 204 | No Content | Successful DELETE |
| 400 | Bad Request | Validation errors |
| 401 | Unauthorized | Missing/invalid token |
| 403 | Forbidden | Insufficient permissions |
| 404 | Not Found | Resource not found |
| 500 | Internal Server Error | Server errors |

### Common Query Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| page | number | Page number (1-based) |
| limit | number | Items per page (default: 20) |
| sort | string | Sort field and direction |
| search | string | Search query |
| filter | string | Filter criteria |

## Dataview Queries

### All API Documentation
```dataview
TABLE WITHOUT ID
link(file.link, file.name) as "API",
module as "Module",
service as "Service",
status as "Status"
FROM "20-KNOWLEDGE/ETIQA/API-Documentation"
WHERE tags contains "api"
SORT module, service
```

### APIs by Module
```dataview
TABLE WITHOUT ID
link(file.link, file.name) as "API",
service as "Service", 
status as "Status"
FROM "20-KNOWLEDGE/ETIQA/API-Documentation"
WHERE tags contains "api" AND module = "ENJOY"
SORT service
```

## Related Work
- [[Enjoy-Rewards-System-Architecture]] - System overview
- [[Developer Work Organization System]] - Work management
- [[Task {ENJOY} ES-3813- To Fix Enjoy Rewards GE Tracker]] - Current work

## Maintenance

### Regular Updates
- [ ] Review API changes monthly
- [ ] Update authentication patterns as needed
- [ ] Add new endpoints when implemented
- [ ] Archive deprecated APIs

### Documentation Standards
- Use the [[API-Documentation]] template for new APIs
- Include real examples and curl commands
- Link related tickets and architecture docs
- Update status tags when APIs change

---
*Maintained by: Development Team*
*Last review: 2025-01-15*