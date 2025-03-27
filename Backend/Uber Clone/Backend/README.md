# Uber Clone Backend

## Overview
This project is a backend implementation for an Uber Clone application. It handles user registration, authentication, and data management using Node.js, Express, and MongoDB.

## Endpoint Documentation

### POST /users/register

#### Description
This endpoint allows new users to register by providing their details. It validates the input data, hashes the password, creates a new user in the database, generates an authentication token, and returns the token along with user details.

#### Request Body
The request body must be in JSON format and include the following fields:

- **fullname**: An object containing:
  - **firstname**: (string, required) Must be at least 3 characters long.
  - **lastname**: (string, optional) Can be at least 3 characters long.
- **email**: (string, required) Must be a valid email format and unique.
- **password**: (string, required) Must be at least 6 characters long.

#### Example Request
```json
{
  "fullname": {
    "firstname": "John",
    "lastname": "Doe"
  },
  "email": "john.doe@example.com",
  "password": "securepassword"
}
```

#### Responses
- **201 Created**: User successfully registered.
  - Response Body:
    ```json
    {
      "token": "generatedAuthToken",
      "user": {
        "fullname": {
          "firstname": "John",
          "lastname": "Doe"
        },
        "email": "john.doe@example.com"
      }
    }
    ```

- **400 Bad Request**: Validation errors occurred.
  - Response Body:
    ```json
    {
      "errors": [
        {
          "msg": "Error message",
          "param": "field name",
          "location": "body"
        }
      ]
    }
    ```

## Setup Instructions
1. Clone the repository.
2. Navigate to the `Backend` directory.
3. Install the required dependencies:
   ```
   npm install
   ```
4. Set up your environment variables, including `JWT_SECRET` for token generation.
5. Start the server:
   ```
   npm start
   ```

## Usage
You can use tools like Postman or cURL to test the `/users/register` endpoint by sending a POST request with the required JSON body.

## License
This project is licensed under the MIT License.