# Task Management Application (Laravel 10 + Vue 3)

This project is a **Task Management Application** developed as part of a **Senior Laravel Developer Technical Assessment**.  
It demonstrates clean backend architecture using **Laravel 10** and a simple functional frontend built with **Vue.js 3**.

The focus of this project is **code quality, REST API design, validation, testing, and best practices**, not UI styling.

---
## Repository Structure
task-app-rahul/
 └── my-app/
     ├── app/
     ├── database/
     ├── resources/
     ├── routes/
     ├── tests/
     ├── composer.json
     └── package.json

---

## Tech Stack

### Backend
- Laravel 10
- PHP 8.1+
- RESTful API
- PHPUnit (Feature Tests)

### Frontend
- Vue.js 3 (Composition API)
- Axios
- Vite

### Database
- MySQL

---

## Features

### Backend (Laravel API)
- Task CRUD operations
- Task status management (`pending`, `in_progress`, `completed`)
- Filtering by status (`?status=pending`)
- Pagination (10 items per page)
- Soft deletes
- Form Request validation
- API Resource response formatting
- Proper HTTP status codes
- Feature tests

### Frontend (Vue 3)
- List all tasks
- Create a new task
- Update task status
- Delete a task
- Pagination using API links (`next` / `prev`)

---

## Database Schema

### `tasks` table

| Column | Type |
|------|-----|
| id | bigint |
| title | string |
| description | text (nullable) |
| status | enum |
| due_date | date (nullable) |
| created_at | timestamp |
| updated_at | timestamp |
| deleted_at | timestamp (soft delete) |

---

## 🔧 Project Setup

### Clone Repository

git clone https://github.com/rahuld09ce126-cmyk/task-app-rahul.git
cd my-app

   | Description            |
|--------|------------------|----------------------|
| GET    | `/api/tasks`       | List all tasks        |
| POST   | `/api/tasks`       | Create a new task     |
| GET    | `/api/tasks/{id}`  | Get task details      |
| PUT    | `/api/tasks/{id}`  | Update a task         |
| DELETE | `/api/tasks/{id}`  | Delete a task         |

### Example: Create Task
```bash
curl -X POST http://127.0.0.1:8000/api/tasks `
-H "Content-Type: application/json" `
-d '{"title":"My first task"}'
```

Response:
```json
{
  "data": {
    "id": 1,
    "title": "My first task"
  }
}
```

---

## Running Tests

Laravel Feature tests can be run with:

```bash
php artisan test
```

---

## Laravel server
- Start Laravel server
```bash
php artisan serve
```
---

## Frontend (Vue 3)

- Main component: `resources/js/components/TaskApp.vue`  
- Entry point: `resources/js/app.js`  
- Compile assets:
```bash
npm run dev      # development
npm run build    # production
```


- Include the div in your Blade template:
```html
<div id="app"></div>
@vite('resources/js/app.js')
```
-----

## HTTP Status Codes Used

| Code | Meaning |
|------|---------|
| 200  | OK (success with response data) |
| 201  | Created (resource successfully created) |
| 204  | No Content (resource deleted successfully) |
| 422  | Unprocessable Entity (validation failed) |

---

## Notes / Tips

- Use **PHP 8.1+** for Laravel 10 compatibility  
- Use MySQL 5.7+ or MariaDB 10.4+ for UTF8 `utf8mb4` support  
- `204` is returned for DELETE success, `201` for POST create success  
- Use `php artisan migrate:fresh` to reset the database during development  
- You can extend Vue components into smaller pieces: `TaskList`, `TaskItem`, `TaskForm`

---
