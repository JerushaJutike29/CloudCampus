# CloudCampus

**Learn Beyond Limits.**

CloudCampus is a computer science learning platform in development, designed to bring study resources, coding practice, assessments, interview preparation, and practical projects into one place.

The goal is to help students manage their learning journey without constantly switching between different tools and websites.

## Project Status

**Early development — initial application setup.**

The repository currently includes:

- A basic HTML welcome page.
- An Express backend with JSON request parsing.
- PostgreSQL connection configuration using environment variables.
- A backend health endpoint.
- A database connectivity test endpoint.
- Initial CSS styles for card layouts.

The learning features described below represent the project roadmap and are not implemented yet.

## Planned Features

- **Lecture Resources:** Access learning content for computer science subjects.
- **Notes:** Create and organize study notes.
- **Coding Practice:** Solve programming problems.
- **Mock Tests:** Practice through assessments.
- **Progress Tracking:** Track learning progress and levels.
- **Interview Preparation:** Prepare for technical interviews.
- **Practical Projects:** Build projects and explore deployment on AWS.
- **Student Accounts:** Register and sign in to a personalized learning space.

## Technology Stack

| Technology | Purpose |
|---|---|
| HTML5 | Initial frontend structure |
| CSS3 | Initial interface styling |
| Node.js | Backend runtime |
| Express.js | Backend routes and request handling |
| PostgreSQL | Relational database |
| node-postgres (`pg`) | PostgreSQL connection pool and queries |
| dotenv | Environment variable configuration |

`bcrypt` is also installed as a dependency for future password hashing. Authentication is not currently implemented.

## Repository Structure

| Path | Description |
|---|---|
| `frontend/index.html` | Basic CloudCampus welcome page |
| `frontend/css/User.css` | Initial card layout styles |
| `backend/package.json` | Backend dependencies and package configuration |
| `backend/package-lock.json` | Dependency lockfile |
| `backend/server.js` | Additional server entry file requiring correction |
| `backend/src/app.js` | Express application, routes, and active server startup |
| `backend/src/db.js` | PostgreSQL connection configuration |
| `backend/src/routes/auth.js` | Empty placeholder for authentication routes |

## Prerequisites

- Node.js and npm.
- A running PostgreSQL server.
- A PostgreSQL database and user with permission to connect.

## Local Setup

### 1. Clone the Repository

```bash
git clone https://github.com/JerushaJutike29/CloudCampus.git
cd CloudCampus
```

### 2. Install Backend Dependencies

```bash
cd backend
npm ci
```

### 3. Configure PostgreSQL

Create a database named `cloudcampus` using pgAdmin or PostgreSQL’s SQL console:

```sql
CREATE DATABASE cloudcampus;
```

Create a `.env` file inside the `backend` directory:

```env
DB_USER=your_postgres_username
DB_HOST=localhost
DB_NAME=cloudcampus
DB_PASSWORD=your_postgres_password
DB_PORT=5432
PORT=5000
```

Replace the example credentials with your local PostgreSQL settings.

Keep `.env` and `node_modules/` out of version control by adding them to a `.gitignore` file.

The current database test only runs `SELECT NOW()`. No application tables or migration scripts are included yet.

### 4. Start the Backend

Run this command from the `backend` directory:

```bash
node src/app.js
```

The backend uses port `5000` by default.

**Current startup note:** Use `node src/app.js` directly. The existing `server.js` calls `app.listen()`, but `src/app.js` already starts the server and does not export the Express application. The entry points need to be consolidated before using `server.js`.

There is currently no `npm start` script.

### 5. Open the Frontend

Open `frontend/index.html` in a browser.

The current page displays:

> Welcome to CloudCampus  
> Learn Beyond Limits.

The frontend is not connected to the backend yet.

## Available Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/` | Confirms that the backend is running |
| GET | `/db-test` | Checks PostgreSQL connectivity |

### Backend Health Check

Open:

```text
http://localhost:5000/
```

Expected response:

```text
CloudCampus Backend is running!
```

### Database Connectivity Check

Open:

```text
http://localhost:5000/db-test
```

A successful response contains a confirmation message and the database timestamp. A connection failure returns HTTP `500`.

## Current Limitations

- Authentication routes are not implemented.
- No student accounts or academic records are stored yet.
- Learning resources, notes, coding exercises, and tests are not implemented.
- The frontend currently contains only a welcome page.
- The existing CSS file is not linked to the welcome page.
- Automated tests are not configured; the existing `npm test` command is a placeholder.
- AWS deployment is part of the roadmap.
- The database test endpoint exposes connection error details and should be revised before public deployment.

## Next Development Steps

1. Consolidate backend startup and add npm scripts.
2. Add database schemas and migrations.
3. Implement registration, login, and protected routes.
4. Build the student dashboard.
5. Connect the frontend to backend APIs.
6. Develop learning resources, notes, coding practice, and assessments.
7. Add automated tests and deployment configuration.

## Project Vision

CloudCampus aims to become a central learning space where computer science students can study, practice, measure their progress, prepare for careers, and gain practical development experience.

**Your college, on the cloud.**
