# API Reference

MyApp exposes a RESTful JSON API. All endpoints are prefixed with `/api/v1`.

## Table of Contents

1. [Authentication](#1-authentication)
2. [Tasks](#2-tasks)
3. [Team Members](#3-team-members)
4. [Error Responses](#4-error-responses)

---

## Base URL

```
http://localhost:3000/api/v1
```

---

## 1. Authentication

MyApp uses JWT (JSON Web Token) for authentication. Include the token in the `Authorization` header for all protected endpoints.

```
Authorization: Bearer <your-token>
```

### POST `/auth/login`

Authenticate a user and receive a JWT.

**Request body:**

```json
{
  "email": "admin@example.com",
  "password": "Admin1234!"
}
```

**Response `200 OK`:**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expiresIn": 3600,
  "user": {
    "id": "u-001",
    "name": "Admin User",
    "email": "admin@example.com",
    "role": "admin"
  }
}
```

### POST `/auth/logout`

Invalidate the current JWT.

**Response `200 OK`:**

```json
{
  "message": "Logged out successfully"
}
```

### POST `/auth/refresh`

Refresh an expiring JWT.

**Response `200 OK`:**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expiresIn": 3600
}
```

---

## 2. Tasks

### GET `/tasks`

Retrieve a list of tasks.

**Query parameters:**

| Parameter | Type | Description |
|---|---|---|
| `status` | string | Filter by status: `todo`, `in_progress`, `done` |
| `priority` | string | Filter by priority: `low`, `medium`, `high`, `critical` |
| `assignee` | string | Filter by assignee user ID |
| `page` | integer | Page number (default: `1`) |
| `limit` | integer | Items per page (default: `20`, max: `100`) |

**Response `200 OK`:**

```json
{
  "data": [
    {
      "id": "t-001",
      "title": "Fix login redirect bug",
      "description": "Users are redirected to 404 after OAuth login.",
      "status": "in_progress",
      "priority": "high",
      "assignee": {
        "id": "u-002",
        "name": "Jane Doe"
      },
      "dueDate": "2024-05-01",
      "createdAt": "2024-04-10T08:00:00Z",
      "updatedAt": "2024-04-12T14:30:00Z"
    }
  ],
  "meta": {
    "total": 20,
    "page": 1,
    "limit": 20
  }
}
```

### POST `/tasks`

Create a new task.

**Request body:**

```json
{
  "title": "Implement CSV export",
  "description": "Allow users to export their task list as a CSV file.",
  "assigneeId": "u-003",
  "priority": "medium",
  "dueDate": "2024-05-15"
}
```

**Response `201 Created`:**

```json
{
  "id": "t-042",
  "title": "Implement CSV export",
  "status": "todo",
  "priority": "medium",
  "assignee": {
    "id": "u-003",
    "name": "Bob Smith"
  },
  "dueDate": "2024-05-15",
  "createdAt": "2024-04-30T06:00:00Z",
  "updatedAt": "2024-04-30T06:00:00Z"
}
```

### GET `/tasks/:id`

Retrieve a single task by ID.

**Response `200 OK`:** Returns the task object (same shape as above).

### PATCH `/tasks/:id`

Update a task. All fields are optional.

**Request body:**

```json
{
  "status": "done",
  "priority": "low"
}
```

**Response `200 OK`:** Returns the updated task object.

### DELETE `/tasks/:id`

Delete a task.

**Response `204 No Content`**

---

## 3. Team Members

### GET `/members`

List all team members.

**Response `200 OK`:**

```json
{
  "data": [
    {
      "id": "u-001",
      "name": "Admin User",
      "email": "admin@example.com",
      "role": "admin",
      "joinedAt": "2023-12-01T00:00:00Z"
    },
    {
      "id": "u-002",
      "name": "Jane Doe",
      "email": "jane@example.com",
      "role": "member",
      "joinedAt": "2024-01-15T09:30:00Z"
    }
  ]
}
```

### POST `/members/invite`

Invite a new team member via email.

**Request body:**

```json
{
  "email": "newuser@example.com",
  "role": "member"
}
```

**Response `200 OK`:**

```json
{
  "message": "Invitation sent to newuser@example.com"
}
```

### DELETE `/members/:id`

Remove a team member.

**Response `204 No Content`**

---

## 4. Error Responses

All errors follow this structure:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The 'title' field is required.",
    "details": [
      {
        "field": "title",
        "issue": "required"
      }
    ]
  }
}
```

**Common HTTP status codes:**

| Status | Meaning |
|---|---|
| `400` | Bad Request — invalid input |
| `401` | Unauthorized — missing or invalid token |
| `403` | Forbidden — insufficient permissions |
| `404` | Not Found — resource does not exist |
| `409` | Conflict — duplicate resource |
| `422` | Unprocessable Entity — validation failed |
| `500` | Internal Server Error |
