# task-2-api-testing

CODTECH Internship Task 2: API Testing with Postman - RESTful API testing for authentication and data retrieval

## Project Overview

This project demonstrates API testing using **Postman** for testing RESTful APIs. The task covers testing various API endpoints for authentication, data retrieval, and CRUD operations.

## Test Target: JSONPlaceholder API

**Base URL**: `https://jsonplaceholder.typicode.com/`

JSONPlaceholder is a free online REST API that you can use whenever you need some fake data. It's perfect for learning and testing API automation without needing to set up a backend.

## API Endpoints Used

### User Authentication & Data
- `GET /users` - Retrieve all users
- `GET /users/{id}` - Retrieve specific user
- `POST /users` - Create new user
- `PUT /users/{id}` - Update user
- `DELETE /users/{id}` - Delete user

### Posts Management
- `GET /posts` - Retrieve all posts
- `GET /posts/{id}` - Retrieve specific post
- `GET /posts/{id}/comments` - Retrieve post comments

### Comments Management
- `GET /comments` - Retrieve all comments
- `POST /comments` - Add comment

## Test Scenarios

### Scenario 1: User Management
- Retrieve list of all users
- Fetch specific user by ID
- Create new user
- Update existing user
- Delete user

### Scenario 2: Posts & Comments
- Retrieve all posts
- Get post with associated comments
- Create new post
- Add comment to post

### Scenario 3: Data Validation
- Verify response status codes (200, 201, 404)
- Validate JSON response structure
- Check data types and required fields
- Validate response time

## Running Tests in Postman

### Step 1: Import Collection
1. Open Postman
2. Click "Import" button
3. Select `PostmanCollection.json` from this repository
4. Collection will be imported with all test requests

### Step 2: Set Environment
1. Click "Environments" on left sidebar
2. Import `Environment.postman_environment.json`
3. Select the environment before running tests

### Step 3: Run Collection
1. Click on collection name
2. Click "Run" button
3. Tests will execute sequentially
4. View results in the run summary

## Key Features

- Automated API endpoint testing
- Request/response validation
- Variable usage for dynamic data
- Pre-request scripts for data preparation
- Test assertions for response validation
- Comprehensive test documentation

## Technologies Used

- **Postman**: API testing and automation platform
- **JSONPlaceholder**: Free mock REST API
- **JSON**: Data format for requests/responses

## Test Results

See `TestResults.md` for detailed test execution results and metrics.

## Documentation

Refer to `API-Documentation.md` for detailed API endpoint specifications and usage examples.

## Setup Instructions

1. Download and install [Postman](https://www.postman.com/downloads/)
2. Clone this repository
3. Open Postman and import the collection
4. Run tests against JSONPlaceholder API
5. Review test results and reports

## API Response Examples

### Get User (200 OK)
```json
{
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret",
  "email": "Sincere@april.biz",
  "address": {
    "street": "Kulas Light",
    "suite": "Apt. 556",
    "city": "Gwenborough"
  }
}
```

### Create Post (201 Created)
```json
{
  "title": "Test Post",
  "body": "This is a test post",
  "userId": 1,
  "id": 101
}
```

## Best Practices

- Use environment variables for base URL and credentials
- Add assertions to validate responses
- Organize requests into logical folders
- Use pre-request scripts for data preparation
- Document test scenarios clearly
- Maintain separate environments (dev, test, prod)

## Status

✅ API collection created and tested
✅ Test scenarios documented
✅ Environment configuration added
✅ Ready for demonstration

## Author

CODTECH Internship - Software Testing

## License

MIT License
