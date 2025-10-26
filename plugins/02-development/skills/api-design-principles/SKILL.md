---
name: api-design-principles
description: RESTful API design principles including resource naming, HTTP methods, status codes, pagination, filtering, versioning, and error handling. Use when designing or reviewing APIs.
---

# API Design Principles

## When to Use This Skill
- Designing new REST APIs
- Reviewing API implementations
- Refactoring existing APIs
- Creating API documentation

## Core Principles

1. **Consistency**: Uniform patterns throughout
2. **Simplicity**: Intuitive and easy to use
3. **Flexibility**: Support evolution and extension
4. **Security**: Secure by default

## RESTful Resource Naming

### Use Nouns, Not Verbs
✅ `GET /api/orders`
❌ `GET /api/getAllOrders`

### Use Plural Names
✅ `GET /api/users`
❌ `GET /api/user`

### Hierarchical Relationships
✅ `GET /api/users/123/orders`
❌ `GET /api/getUserOrders?userId=123`

## HTTP Methods

- **GET**: Retrieve (safe, idempotent)
- **POST**: Create
- **PUT**: Replace (idempotent)
- **PATCH**: Partial update (idempotent)
- **DELETE**: Remove (idempotent)

## Status Codes Quick Reference

### Success (2xx)
- **200 OK**: Successful GET/PUT/PATCH/DELETE
- **201 Created**: Successful POST
- **204 No Content**: Success with no response body

### Client Errors (4xx)
- **400 Bad Request**: Invalid input
- **401 Unauthorized**: Not authenticated
- **403 Forbidden**: Not authorized
- **404 Not Found**: Resource doesn't exist
- **409 Conflict**: State conflict
- **422 Unprocessable**: Validation errors
- **429 Too Many Requests**: Rate limit

### Server Errors (5xx)
- **500 Internal Server Error**: Generic error
- **503 Service Unavailable**: Temporary down

## Query Parameters

### Filtering
`GET /api/products?category=electronics&status=active`

### Sorting
`GET /api/products?sort=price_asc`
`GET /api/products?sort=-created_at` (descending)

### Pagination
```
# Offset-based
GET /api/products?offset=40&limit=20

# Page-based
GET /api/products?page=3&per_page=20

# Cursor-based (best for large datasets)
GET /api/products?cursor=xyz&limit=20
```

### Field Selection
`GET /api/users?fields=id,name,email`

## Versioning

### URL Versioning (Recommended)
```
GET /api/v1/users
GET /api/v2/users
```

### Header Versioning
```
GET /api/users
Accept: application/vnd.myapi.v1+json
```

## Response Format

### Success Response
```json
{
  "data": {
    "id": "123",
    "type": "user",
    "attributes": {...}
  },
  "meta": {
    "timestamp": "2024-01-15T10:00:00Z"
  }
}
```

### Collection Response
```json
{
  "data": [...],
  "meta": {
    "total": 100,
    "page": 1
  },
  "links": {
    "next": "/api/users?page=2"
  }
}
```

### Error Response
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "details": [
      {
        "field": "email",
        "message": "Invalid format"
      }
    ]
  }
}
```

## Best Practices Checklist

### DO:
- ✅ Use nouns for resources
- ✅ Use HTTP methods correctly
- ✅ Return appropriate status codes
- ✅ Version from day one
- ✅ Implement pagination
- ✅ Provide filtering/sorting
- ✅ Use HTTPS everywhere
- ✅ Validate all inputs
- ✅ Implement rate limiting
- ✅ Document thoroughly

### DON'T:
- ❌ Use verbs in endpoints
- ❌ Return 200 for errors
- ❌ Break backwards compatibility
- ❌ Expose implementation details
- ❌ Return sensitive data
- ❌ Allow unlimited requests
- ❌ Trust client input

## Quick Decision Guide

**Need to retrieve data?** → GET
**Creating new resource?** → POST
**Full replacement?** → PUT
**Partial update?** → PATCH
**Removing resource?** → DELETE

**Success creating?** → 201 Created
**Invalid input?** → 400 Bad Request
**Not authorized?** → 403 Forbidden
**Not found?** → 404 Not Found
**Rate limited?** → 429 Too Many Requests
