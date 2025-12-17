# API Documentation

## Base URL
```
https://api.example.com/v1
```

## Authentication

### Bearer Token Authentication
All endpoints require a Bearer token in the Authorization header.

```
Authorization: Bearer {access_token}
```

### Obtaining Access Token
**Endpoint:** POST /auth/login

**Request:**
```json
{
  "username": "user@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

## API Endpoints

### 1. Get All Users
**Method:** GET  
**Endpoint:** `/users`  
**Authentication:** Required  

**Query Parameters:**
- `page` (optional, default: 1) - Page number
- `limit` (optional, default: 10) - Results per page
- `role` (optional) - Filter by user role

**Response:**
```json
{
  "data": [
    {
      "id": 1,
      "username": "john_doe",
      "email": "john@example.com",
      "role": "admin",
      "created_at": "2024-01-15T10:30:00Z"
    }
  ],
  "pagination": {
    "current_page": 1,
    "total_pages": 5,
    "total_items": 50
  }
}
```

### 2. Get User by ID
**Method:** GET  
**Endpoint:** `/users/{id}`  
**Authentication:** Required  

**Path Parameters:**
- `id` - User ID

**Response:**
```json
{
  "id": 1,
  "username": "john_doe",
  "email": "john@example.com",
  "role": "admin",
  "profile": {
    "first_name": "John",
    "last_name": "Doe",
    "avatar_url": "https://example.com/avatar.jpg"
  },
  "created_at": "2024-01-15T10:30:00Z"
}
```

### 3. Create User
**Method:** POST  
**Endpoint:** `/users`  
**Authentication:** Required (admin only)  

**Request Body:**
```json
{
  "username": "new_user",
  "email": "newuser@example.com",
  "password": "secure_password",
  "role": "user"
}
```

**Response (201 Created):**
```json
{
  "id": 51,
  "username": "new_user",
  "email": "newuser@example.com",
  "role": "user",
  "created_at": "2024-01-15T11:45:00Z"
}
```

### 4. Update User
**Method:** PUT  
**Endpoint:** `/users/{id}`  
**Authentication:** Required  

**Request Body:**
```json
{
  "email": "newemail@example.com",
  "role": "moderator"
}
```

**Response (200 OK):**
```json
{
  "id": 1,
  "username": "john_doe",
  "email": "newemail@example.com",
  "role": "moderator",
  "updated_at": "2024-01-15T12:00:00Z"
}
```

### 5. Delete User
**Method:** DELETE  
**Endpoint:** `/users/{id}`  
**Authentication:** Required (admin only)  

**Response (204 No Content)**

### 6. Get User Profile
**Method:** GET  
**Endpoint:** `/profile`  
**Authentication:** Required  

**Response:**
```json
{
  "id": 1,
  "username": "john_doe",
  "email": "john@example.com",
  "profile": {
    "first_name": "John",
    "last_name": "Doe",
    "phone": "+1234567890",
    "bio": "Software Developer"
  }
}
```

## Error Handling

### Standard Error Response
```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "Invalid request parameters",
    "details": {
      "field": "email",
      "reason": "Invalid email format"
    }
  }
}
```

## HTTP Status Codes
- `200 OK` - Successful GET/PUT request
- `201 Created` - Successful POST request
- `204 No Content` - Successful DELETE request
- `400 Bad Request` - Invalid parameters
- `401 Unauthorized` - Missing or invalid token
- `403 Forbidden` - Insufficient permissions
- `404 Not Found` - Resource not found
- `500 Internal Server Error` - Server error

## Rate Limiting
API requests are rate-limited to 1000 requests per hour per API key.
Remaining requests are available in response header: `X-RateLimit-Remaining`
