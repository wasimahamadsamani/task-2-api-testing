# API Testing Guide for Postman

## Overview
This document provides a comprehensive guide for testing the RESTful APIs using Postman. The test suite covers authentication, data retrieval, and error handling scenarios.

## Prerequisites
- Postman (v11.0 or higher)
- Active API credentials
- Network connectivity to api.example.com
- Valid Bearer token

## Getting Started

### Step 1: Import Collection
1. Open Postman
2. Click on Import
3. Select `PostmanCollection.json` from this repository
4. The collection will contain all API requests

### Step 2: Set Up Environment
1. Import `Environment.postman_environment.json`
2. Configure the following variables:
   - `base_url`: https://api.example.com/v1
   - `auth_token`: Your bearer token
   - `username`: Your test username
   - `password`: Your test password

### Step 3: Configure Settings
1. Load `config.json` for test configuration
2. Review timeout and retry settings
3. Adjust logging preferences

## Running Tests

### Manual Testing
1. Select individual requests from collection
2. Click "Send" to execute
3. Review response status and data

### Automated Testing
1. Right-click on collection
2. Select "Run collection"
3. Configure test parameters
4. Monitor execution progress

## Test Categories

### Authentication Tests
- Login with valid credentials
- Login with invalid credentials
- Token validation
- Token refresh

### Data Retrieval Tests
- Get all users (paginated)
- Get user by ID
- Get user profile
- Filter users by role

### Error Handling Tests
- 400 Bad Request (invalid data)
- 401 Unauthorized (invalid token)
- 403 Forbidden (insufficient permissions)
- 404 Not Found (non-existent resource)

## Expected Results

### Success Criteria
- All authentication tests return 200 or 401
- All data retrieval tests return 200
- Response time < 1000ms
- Valid JSON responses

### Performance Benchmarks
- Authentication endpoint: <200ms
- Data retrieval: <500ms
- Batch operations: <2000ms

## Debugging

### Common Issues

**Issue**: 401 Unauthorized
- **Solution**: Verify token is valid and not expired
- **Check**: auth_token variable in environment

**Issue**: 404 Not Found
- **Solution**: Verify endpoint path is correct
- **Check**: base_url and endpoint variables

**Issue**: Timeout
- **Solution**: Check network connectivity
- **Check**: Increase timeout in config.json

### Logging
Enable verbose logging in config.json:
```json
"logging": {
  "enabled": true,
  "level": "debug"
}
```

## Test Reports

After running tests:
1. Check test results summary
2. Review TestResults.md for detailed results
3. Export test report as HTML
4. Share results with team

## Best Practices

1. **Always clean up**: Delete test data after testing
2. **Use environment variables**: Never hardcode credentials
3. **Document edge cases**: Note unusual behavior
4. **Version control**: Keep test collection updated
5. **Regular execution**: Run tests before deployment

## API Endpoints Reference

See `API-Documentation.md` for complete endpoint documentation

## Troubleshooting

### Pre-flight Checks
- [ ] API server is running
- [ ] Network is accessible
- [ ] Authentication token is valid
- [ ] Environment variables are set
- [ ] Collection is imported

### Test Execution Issues
- [ ] Check browser console for errors
- [ ] Verify request headers
- [ ] Validate request body format
- [ ] Check response headers
- [ ] Review server logs

## Support
For issues or questions, contact the API team or refer to API-Documentation.md
