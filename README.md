# Task Management System 

Full-stack CRUD application with Spring Boot backend + React frontend.

## Features

### Backend (Spring Boot)
-  Service layer architecture
-  Bean validation (@NotBlank, @Size)
-  Global exception handling
-  Lombok for boilerplate reduction
-  Unit tests (JUnit + Mockito)
-  H2 in-memory database
-  Auto-managed timestamps

### Frontend (React)
-  Single component
-  All CRUD operations
-  Table-based UI
-  Error handling

## Quick Start

### Backend (Terminal 1)
```bash
cd task-management-complete
mvn clean install
mvn spring-boot:run
```
Backend runs on: http://localhost:8080

### Frontend (Terminal 2)
```bash
cd task-management-complete/frontend
npm install
npm start
```
Frontend runs on: http://localhost:3000

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /tasks | Get all tasks |
| GET | /tasks/{id} | Get task by ID |
| POST | /tasks | Create new task |
| PUT | /tasks/{id} | Update task |
| DELETE | /tasks/{id} | Delete task |

## Example Request

**POST /tasks**
```json
{
  "title": "Complete assessment",
  "description": "Finish CRUD application",
  "status": "Pending"
}
```

**Response:**
```json
{
  "id": 1,
  "title": "Complete assessment",
  "description": "Finish CRUD application",
  "status": "Pending",
  "createdAt": "2025-11-22T14:30:00Z",
  "updatedAt": "2025-11-22T14:30:00Z"
}
```

## Testing

### Run Backend Tests
```bash
mvn test
```

### Test with cURL
```bash
# Get all tasks
curl http://localhost:8080/tasks

# Create task
curl -X POST http://localhost:8080/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Test Task","description":"Testing","status":"Pending"}'

# Update task
curl -X PUT http://localhost:8080/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{"title":"Updated","description":"Updated desc","status":"Completed"}'

# Delete task
curl -X DELETE http://localhost:8080/tasks/1
```

## Database Access

H2 Console: http://localhost:8080/h2-console

- JDBC URL: `jdbc:h2:mem:tasksdb`
- Username: `sa`
- Password: (leave empty)

## Notes

- Backend focuses on proper architecture (Service layer, validation, exception handling)
- Frontend is minimal
- All data is in-memory (resets on restart)
- CORS enabled for local development
- Validation errors return proper messages
- Timestamps auto-managed by JPA
