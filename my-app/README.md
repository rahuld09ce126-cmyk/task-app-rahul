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

### 1️⃣ Clone Repository
```bash
git clone https://github.com/rahuld09ce126-cmyk/task-app-rahul.git
cd my-app
