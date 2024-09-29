# Numblio API Documentation

Welcome to the **Numblio API**! This API provides access to a comprehensive "Rekenen" (Arithmetic) course designed to help users learn mathematics in Dutch. The API allows you to retrieve information about courses, units, challenges, and answers. You can integrate this API into your applications to provide educational content to your users.

## Table of Contents

- [Base URL](#base-url)
- [Authentication](#authentication)
  - [Register](#register-optional)
  - [Login](#login)
  - [Logout](#logout)
- [Endpoints](#endpoints)
  - [Courses](#courses)
  - [Units](#units)
  - [Challenges](#challenges)
  - [Answers](#answers)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)
- [License](#license)
- [Contact and Support](#contact-and-support)

---

## Base URL

All API requests are made to the following base URL:

```
https://api.numblio.com/api/v2
```

## Authentication

The Numblio API uses token-based authentication provided by **Laravel Sanctum**. Authentication is required for certain endpoints, especially those that reveal sensitive information like the correct answers to challenges.

### Register (Optional)

You can register a new user account to access protected resources.

**Endpoint**

```
POST /register
```

**Request Headers**

- `Content-Type: application/json`

**Request Body**

```json
{
  "name": "Jane Doe",
  "email": "jane.doe@example.com",
  "password": "yourpassword",
  "password_confirmation": "yourpassword"
}
```

**Response**

- **Success (201 Created)**

  ```json
  {
    "message": "Registration successful.",
    "access_token": "your_access_token_here",
    "token_type": "Bearer"
  }
  ```

- **Failure (422 Unprocessable Entity)**

  ```json
  {
    "message": "Validation errors.",
    "errors": {
      "email": ["The email has already been taken."]
    }
  }
  ```

### Login

Authenticate with your credentials to obtain an access token.

**Endpoint**

```
POST /login
```

**Request Headers**

- `Content-Type: application/json`

**Request Body**

```json
{
  "email": "jane.doe@example.com",
  "password": "yourpassword"
}
```

**Response**

- **Success (200 OK)**

  ```json
  {
    "message": "Login successful.",
    "access_token": "your_access_token_here",
    "token_type": "Bearer"
  }
  ```

- **Failure (422 Unprocessable Entity)**

  ```json
  {
    "message": "Invalid credentials provided."
  }
  ```

### Logout

Invalidate your access token.

**Endpoint**

```
POST /logout
```

**Request Headers**

- `Authorization: Bearer your_access_token_here`

**Response**

- **Success (200 OK)**

  ```json
  {
    "message": "Logout successful."
  }
  ```

## Endpoints

### Courses

#### Get All Courses

Retrieve a list of all available courses.

**Endpoint**

```
GET /courses
```

**Response**

- **Success (200 OK)**

  ```json
  [
    {
      "id": 1,
      "name": "Rekenen",
      "description": "Een uitgebreide cursus voor het leren van rekenen in het Nederlands."
    }
  ]
  ```

#### Get Course Details

Retrieve detailed information about a specific course, including its units.

**Endpoint**

```
GET /courses/{course_id}
```

**Path Parameters**

- `course_id` (integer): The ID of the course.

**Response**

- **Success (200 OK)**

  ```json
  {
    "id": 1,
    "name": "Rekenen",
    "description": "Een uitgebreide cursus voor het leren van rekenen in het Nederlands.",
    "units": [
      {
        "id": 1,
        "name": "Optellen",
        "description": "Leer de basis van het optellen.",
        "course_id": 1
      },
      // Additional units...
    ]
  }
  ```

### Units

#### Get Units of a Course

Retrieve all units associated with a specific course.

**Endpoint**

```
GET /courses/{course_id}/units
```

**Path Parameters**

- `course_id` (integer): The ID of the course.

**Response**

- **Success (200 OK)**

  ```json
  [
    {
      "id": 1,
      "name": "Optellen",
      "description": "Leer de basis van het optellen.",
      "course_id": 1
    },
    // Additional units...
  ]
  ```

#### Get Unit Details

Retrieve detailed information about a specific unit, including its challenges.

**Endpoint**

```
GET /units/{unit_id}
```

**Path Parameters**

- `unit_id` (integer): The ID of the unit.

**Response**

- **Success (200 OK)**

  ```json
  {
    "id": 1,
    "name": "Optellen",
    "description": "Leer de basis van het optellen.",
    "course_id": 1,
    "challenges": [
      {
        "id": 1,
        "question": "Wat is 1 + 1?",
        "unit_id": 1
      },
      // Additional challenges...
    ]
  }
  ```

### Challenges

#### Get Challenges of a Unit

Retrieve all challenges (questions) within a specific unit.

**Endpoint**

```
GET /units/{unit_id}/challenges
```

**Path Parameters**

- `unit_id` (integer): The ID of the unit.

**Response**

- **Success (200 OK)**

  ```json
  [
    {
      "id": 1,
      "question": "Wat is 1 + 1?",
      "unit_id": 1
    },
    // Additional challenges...
  ]
  ```

#### Get Challenge Details

Retrieve detailed information about a specific challenge, including its answers.

**Endpoint**

```
GET /challenges/{challenge_id}
```

**Path Parameters**

- `challenge_id` (integer): The ID of the challenge.

**Response**

- **Success (200 OK)**

  ```json
  {
    "id": 1,
    "question": "Wat is 1 + 1?",
    "unit_id": 1,
    "answers": [
      {
        "id": 1,
        "text": "2",
        "challenge_id": 1
      },
      // Additional answers...
    ]
  }
  ```

### Answers

#### Get Answers of a Challenge

Retrieve all possible answers for a specific challenge.

**Endpoint**

```
GET /challenges/{challenge_id}/answers
```

**Path Parameters**

- `challenge_id` (integer): The ID of the challenge.

**Response**

- **Success (200 OK)**

  ```json
  [
    {
      "id": 1,
      "text": "2",
      "challenge_id": 1
    },
    // Additional answers...
  ]
  ```

#### Get Answer Details

Retrieve detailed information about a specific answer.

**Endpoint**

```
GET /answers/{answer_id}
```

**Path Parameters**

- `answer_id` (integer): The ID of the answer.

**Response**

- **Success (200 OK)**

  ```json
  {
    "id": 1,
    "text": "2",
    "challenge_id": 1
  }
  ```

**Note**: The `is_correct` field is only included in the response if the user is authenticated.

## Error Handling

The API uses standard HTTP status codes to indicate the success or failure of an API request. Error responses include a message and may include additional details.

- **200 OK**: The request was successful.
- **201 Created**: A new resource has been successfully created.
- **400 Bad Request**: The request was invalid or cannot be served.
- **401 Unauthorized**: Authentication is required and has failed or has not yet been provided.
- **404 Not Found**: The requested resource could not be found.
- **422 Unprocessable Entity**: The request was well-formed but was unable to be followed due to semantic errors (e.g., validation errors).
- **500 Internal Server Error**: An unexpected condition was encountered.

### Example Error Response

```json
{
  "message": "Invalid credentials provided."
}
```

## Rate Limiting

To ensure fair use of the API, rate limiting is enforced.

- **Unauthenticated Requests**: Limited to a lower number of requests per minute.
- **Authenticated Requests**: Granted a higher rate limit.

If you exceed the rate limit, the API will return a **429 Too Many Requests** status code.

## License

The Numblio API is provided for public use under the following conditions:

- **Attribution**: Please attribute the use of the API in your application.
- **Non-Commercial Use**: The API is intended for educational and non-commercial purposes.
- **Fair Use**: Do not abuse the API by making excessive requests or attempting to disrupt the service.

For more details, please refer to the [Numblio API Terms of Service](https://www.numblio.com/terms).

## Contact and Support

If you have any questions, need support, or wish to provide feedback, please contact us:

- **Email**: [support@numblio.com](mailto:support@numblio.com)
- **Website**: [www.numblio.com](https://www.numblio.com)

---

Thank you for using the Numblio API. We hope it enhances your applications and contributes to effective learning experiences!
