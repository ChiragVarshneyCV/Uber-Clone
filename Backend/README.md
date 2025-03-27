# User API Documentation

## Register User
Registers a new user in the system.

### Endpoint
```
POST /users/register
```

### Request Body
```json
{
  "fullname": {
    "firstname": "string",     // required, min 3 characters
    "lastname": "string"       // optional, min 3 characters
  },
  "email": "string",          // required, valid email format
  "password": "string"        // required, min 6 characters
}
```

### Response

#### Success Response
- **Status Code**: 201 (Created)
- **Response Body**:
```json
{
  "token": "jwt_token_string",
  "user": {
    "fullname": {
      "firstname": "string",
      "lastname": "string"
    },
    "email": "string",
    "_id": "string"
  }
}
```

#### Error Responses
- **Status Code**: 400 (Bad Request)
  - When validation fails
```json
{
  "errors": [
    {
      "msg": "error message",
      "param": "field_name"
    }
  ]
}
```

### Validation Rules
- First name must be at least 3 characters long
- Email must be valid and at least 5 characters long
- Password must be at least 6 characters long

### Example Responses

#### Success Example
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "fullname": {
      "firstname": "John",
      "lastname": "Doe"
    },
    "email": "john.doe@example.com",
    "_id": "507f1f77bcf86cd799439011"
  }
}
```

#### Validation Error Example
```json
{
  "errors": [
    {
      "msg": "First name must be at least 3 characters long",
      "param": "fullname.firstname"
    },
    {
      "msg": "Invalid email format",
      "param": "email"
    }
  ]
}
```
