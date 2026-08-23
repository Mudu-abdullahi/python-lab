# Exercise B — API Reference Entry

## Create a New Project Task

### Endpoint

**Method:** `POST`

**Path:**

```text
/api/v1/projects/{project_id}/tasks
```

### Description

Creates a new task within a specified project for an authenticated user. The task requires a title, assignee, due date, and priority. A description can optionally be included.

## Path Parameters

| Parameter    | Type    | Required | Description                                                      |
| ------------ | ------- | -------- | ---------------------------------------------------------------- |
| `project_id` | integer | Yes      | The unique ID of the project where the new task will be created. |

## Query Parameters

This endpoint does not require query parameters.

## Request Body

The request body must use JSON.

| Parameter     | Type    | Required | Description                                                                |
| ------------- | ------- | -------- | -------------------------------------------------------------------------- |
| `title`       | string  | Yes      | The title or name of the task.                                             |
| `description` | string  | No       | Additional information about the task.                                     |
| `assignee_id` | integer | Yes      | The unique ID of the user who will be assigned the task.                   |
| `due_date`    | string  | Yes      | The task deadline in `YYYY-MM-DD` format.                                  |
| `priority`    | string  | Yes      | The priority of the task. Accepted values are `low`, `medium`, and `high`. |

## Required Headers

```http
Authorization: Bearer <access_token>
Content-Type: application/json
```

### Header Descriptions

* `Authorization` — Required for authentication. The client sends a valid access token using the Bearer authentication scheme.
* `Content-Type` — Specifies that the request body is formatted as JSON.

## Example Request

```http
POST /api/v1/projects/42/tasks
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Type: application/json
```

```json
{
  "title": "Prepare project presentation",
  "description": "Create the presentation slides and review them before the meeting.",
  "assignee_id": 17,
  "due_date": "2026-09-15",
  "priority": "high"
}
```

## Response Codes

### `201 Created`

The task was successfully created.

### `400 Bad Request`

The request contains invalid or missing data, such as an invalid date or missing required field.

### `401 Unauthorized`

The request does not contain valid authentication credentials.

### `403 Forbidden`

The authenticated user does not have permission to create tasks in the specified project.

### `404 Not Found`

The specified project or assignee could not be found.

### `409 Conflict`

The request conflicts with the current state of the project or an existing task.

### `422 Unprocessable Entity`

The request is correctly formatted but one or more values fail validation.

### `500 Internal Server Error`

An unexpected server-side error occurred while processing the request.

## Example Successful Response

**HTTP Status:** `201 Created`

```json
{
  "id": 1058,
  "project_id": 42,
  "title": "Prepare project presentation",
  "description": "Create the presentation slides and review them before the meeting.",
  "assignee_id": 17,
  "due_date": "2026-09-15",
  "priority": "high",
  "status": "todo",
  "created_at": "2026-08-23T14:30:00Z"
}
```

The response confirms that the task was successfully created and provides its unique ID, project ID, title, description, assignee, due date, priority, status, and creation timestamp.
