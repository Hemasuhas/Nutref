# API Documentation

## Authentication

### Overview
The API uses token-based authentication. Users can obtain an authentication token through login or registration endpoints.

### Obtaining an Authentication Token
1. **Login**: Use `/api/auth/login` with valid credentials to receive a token.
2. **Register**: Use `/api/auth/register` to create a new user account and receive a token upon successful registration.

## Endpoints

### Auth
- **POST** `/api/auth/login`
  - **Description**: Log in a user and return an authentication token.
  - **Request Body**:
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```
  - **Response**:
    ```json
    {
      "token": "string"
    }
    ```

- **POST** `/api/auth/register`
  - **Description**: Register a new user.
  - **Request Body**:
    ```json
    {
      "username": "string",
      "email": "string",
      "password": "string"
    }
    ```
  - **Response**:
    ```json
    {
      "token": "string"
    }
    ```

### User Profile
- **GET** `/api/user/profile`
  - **Description**: Retrieve the authenticated user's profile information.
  - **Response**:
    ```json
    {
      "username": "string",
      "email": "string",
      "profileData": { ... }
    }
    ```

### Nutrition Tracking
- **POST** `/api/nutrition/add`
  - **Description**: Add a nutrition entry for the user.
  - **Request Body**:
    ```json
    {
      "foodItem": "string",
      "calories": "integer",
      "date": "string"
    }
    ```
  - **Response**:
    ```json
    {
      "status": "success"
    }
    ```

- **GET** `/api/nutrition/get`
  - **Description**: Retrieve nutrition entries for the user.
  - **Parameters**:  `date` (optional) to filter by dates.
  - **Response**:
    ```json
    [{
      "foodItem": "string",
      "calories": "integer",
      "date": "string"
    }, ...]
    ```

### Recommendations
- **GET** `/api/recommendations/get`
  - **Description**: Get nutrition recommendations based on user profile.
  - **Response**:
    ```json
    {
      "recommendations": ["string", ...]
    }
    ```

## Error Responses
- **400 Bad Request**: The request was invalid or cannot be served. 
- **401 Unauthorized**: Authentication credentials were missing or incorrect. 
- **404 Not Found**: The requested resource was not found. 
- **500 Internal Server Error**: An error occurred on the server side.

---

This documentation provides a comprehensive guide to using the API effectively. Please refer to this document while integrating and utilizing the API.