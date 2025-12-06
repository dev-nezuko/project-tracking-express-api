# Target project-tracking API

Specification examples for unfinished code; not working responses from this repository.

## API Endpoints Summary

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/projects` | List all projects |
| GET | `/projects?ownerId=:id` | Filter projects by owner |
| GET | `/projects/:id` | Get project with tasks |
| POST | `/projects` | Create a new project |
| GET | `/users/:id/summary` | Get user summary with projects |

All endpoints require the `x-api-key` header (except the API returns 401 without it).

---

## Expected Response Shapes

### GET /projects/:id
```json
{
  "id": "proj-1",
  "name": "Website Redesign",
  "ownerId": "user-1",
  "tasks": [
    { "id": "task-1", "title": "Design mockups", "status": "done", "projectId": "proj-1" }
  ]
}
```

### GET /users/:id/summary
```json
{
  "user": { "id": "user-1", "name": "Alice Johnson", "role": "manager" },
  "projects": [
    { "id": "proj-1", "name": "Website Redesign", "ownerId": "user-1" }
  ],
  "taskCounts": {
    "proj-1": 3
  }
}
```

### POST /projects
Request:
```json
{ "name": "New Project", "ownerId": "user-1" }
```
Response (201):
```json
{ "id": "generated-id", "name": "New Project", "ownerId": "user-1" }
```

---
