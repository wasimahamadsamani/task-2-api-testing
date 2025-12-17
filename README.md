# task-2-api-testing

CODTECH Internship Task 2: API Testing with Postman - RESTful API testing for authentication and data retrieval

## 🎬 Live Demo

**[View Interactive Demo](https://htmlpreview.github.io/?https://github.com/wasimahamadsamani/task-2-api-testing/blob/main/API-DEMO.html)**

## Project Overview

This project demonstrates API testing using Postman for testing RESTful APIs. The task covers testing various API endpoints for authentication, data retrieval, and CRUD operations.

## Test Target: JSONPlaceholder API

**Base URL:** `https://jsonplaceholder.typicode.com/`

JSONPlaceholder is a free online REST API that you can use whenever you need some fake data. It's perfect for learning and testing API automation without needing to set up a backend.

## API Endpoints Used

### User Authentication & Data
- `GET /users` – Retrieve all users
- `GET /users/{id}` – Retrieve specific user
- `POST /users` – Create new user
- `PUT /users/{id}` – Update user
- `DELETE /users/{id}` – Delete user

### Posts Management
- `GET /posts` – Retrieve all posts
- `GET /posts/{id}` – Retrieve specific post
- `GET /posts/{id}/comments` – Retrieve post comments
- `POST /posts` – Create new post
- `PUT /posts/{id}` – Update post
- `DELETE /posts/{id}` – Delete post

### Comments Management
- `GET /comments` – Retrieve all comments
- `GET /comments/{id}` – Retrieve specific comment
- `GET /posts/{id}/comments` – Retrieve comments for post

## Test Scenarios

### Scenario 1: Get All Users
- Send GET request to `/users`
- Verify status code 200
- Validate response contains user array
- Validate required fields (id, name, email, etc.)

### Scenario 2: Get Specific User
- Send GET request to `/users/1`
- Verify status code 200
- Validate response structure
- Confirm user ID matches request

### Scenario 3: Create New Post
- Send POST request with title, body, userId
- Verify status code 201 (Created)
- Validate response includes generated ID
- Confirm data returned matches sent data

### Scenario 4: Update Existing Post
- Send PUT request with updated data
- Verify status code 200
- Validate updated fields in response

### Scenario 5: Delete Resource
- Send DELETE request
- Verify status code 200/204
- Confirm deletion via subsequent GET request

### Scenario 6: Error Handling
- Test non-existent endpoints (404)
- Test invalid data (400)
- Verify appropriate error responses

## Postman Collection

Collection includes pre-configured requests with:
- Proper headers
- Request bodies
- Response validations
- Environment variables
- Pre-request scripts
- Test assertions

## Running Tests

### Using Postman
1. Import collection and environment
2. Configure variables
3. Run collection runner
4. Review test results

### Using Newman (CLI)
```bash
newman run collection.json -e environment.json --reporters cli,json
```

## Test Coverage

- ✅ GET requests (fetch data)
- ✅ POST requests (create data)
- ✅ PUT requests (update data)
- ✅ DELETE requests (remove data)
- ✅ Response validation
- ✅ Status code verification
- ✅ JSON schema validation
- ✅ Error handling
- ✅ Authentication testing
- ✅ Data consistency checks

## Key Testing Concepts

### 1. Request Methods
- GET - Retrieve resources
- POST - Create new resources
- PUT - Update existing resources
- DELETE - Remove resources

### 2. Status Codes
- 200 OK - Successful request
- 201 Created - Resource created
- 204 No Content - Successful deletion
- 400 Bad Request - Invalid data
- 401 Unauthorized - Missing auth
- 404 Not Found - Resource not found
- 500 Server Error

### 3. Response Validation
- Status code checks
- JSON structure validation
- Data type verification
- Required field presence
- Value range validation

### 4. Test Assertions
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response has required fields", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('id');
    pm.expect(jsonData).to.have.property('title');
});
```

## Best Practices

1. Organize requests in folders
2. Use environment variables for URLs and data
3. Write clear, descriptive test names
4. Include pre-request and test scripts
5. Document expected responses
6. Test error scenarios
7. Validate response times
8. Use assertions for validations
9. Maintain test data consistency
10. Generate readable reports

## Tools & Technologies

- Postman - API testing platform
- Newman - Postman CLI runner
- JSONPlaceholder - Mock API server
- JavaScript - Pre-request and test scripts

## Test Results

All tests pass with:
- Response time: < 500ms
- Status code validation: ✅
- Response structure validation: ✅
- Data integrity checks: ✅

## Troubleshooting

**Connection timeout:**
- Check internet connectivity
- Verify API endpoint is accessible
- Check proxy settings

**Status 404:**
- Verify correct endpoint URL
- Check resource ID exists
- Confirm base URL configuration

**Invalid JSON:**
- Verify Content-Type header
- Check request body format
- Validate JSON syntax

## Status

✅ API Collection Configured
✅ Test Cases Documented
✅ Validations Implemented
✅ Reports Generated

## License

MIT License
