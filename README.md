# Physical Fitness & Training Web Application
This project was developed for the **COMP2850 Software Engineering** module at the **University of Leeds**.

FitTrack is a web application designed to help users plan, record, and monitor their physical fitness activities. The system supports both casual users who want to maintain a healthy lifestyle and more competitive users who may be training for events such as races or triathlons.

## Features

The application currently supports:

- User registration and login
- Secure password hashing for user accounts
- PostgreSQL database storage
- Logging physical activities such as running, cycling, swimming, walking, gym workouts, yoga, hiking, rowing, and other activities
- Viewing activity history
- Searching and filtering activity records
- Editing and deleting logged activities
- Dashboard statistics based on real user activity data
- Recent activity preview on the dashboard
- Dashboard charts and visualisations
- Exercise plans for structured training
- Community feed for public activity sharing
- GPX upload support for route-based activities
- Race tracker for upcoming and completed races
- Recording race results and personal bests

## Technologies

The project uses:

- Python
- Flask
- PostgreSQL
- HTML
- CSS
- JavaScript
- Chart.js
- Werkzeug Security for password hashing
- python-dotenv for environment variables
- psycopg2 for PostgreSQL connection
- gpxpy for GPX route file support
- GitHub for version control, issues, pull requests, and project management

## Setup Instructions

### Prerequisites

- Python 3.10 or higher
- Docker for the Codespaces database setup below
- Git if cloning the repository

### 1. Clone the Repository

If you opened a GitHub Codespace from this repository, the code is already there—skip this step. Otherwise, clone it.

```bash
git clone https://github.com/OmarAli-258/Omar-Fitness-project.git
cd Omar-Fitness-project
```

### 2. Create a Virtual Environment (Recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux and Codespaces
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Create a .env File

In Codespaces, copy the example settings file:

```bash
cp .env.example .env
```

Open `.env` and replace its contents with:

```text
DATABASE_URL=postgresql://fitness:fitness_local_password@127.0.0.1:5433/fittrack
```

This address matches the local Docker database in step 5. `.env` contains database credentials and is ignored by Git; do not commit it.

### 5. Set Up the Database

In a Codespace, create a local PostgreSQL database with Docker:

```bash
docker run --name fitness-postgres -e POSTGRES_USER=fitness -e POSTGRES_PASSWORD=fitness_local_password -e POSTGRES_DB=fittrack -p 127.0.0.1:5433:5432 -d postgres:16
```

The application creates its tables when it starts. If you return to this Codespace later and the database container is stopped, run `docker start fitness-postgres`.

### 6. Run the Application

```bash
python app.py
```

The app should run on `http://localhost:8081`. In Codespaces, open its forwarded port 8081.

The app currently runs with Flask debug mode enabled. Use these instructions for local development and demonstration, not for a public deployment.

### Troubleshooting

| Issue | Solution |
|-------|----------|
| "Module not found" error | Run `pip install -r requirements.txt` again |
| Database connection error | Check `.env` has the correct `DATABASE_URL` and the database container is running |
| Port already in use | Check whether the app is already running before starting another copy |
| Import errors | Ensure all dependencies from `requirements.txt` are installed |

---

## Project Structure

- `app.py` — starts the Flask app
- `routes/` — handles the app’s pages and features
- `data/` — database setup and queries
- `templates/` — HTML pages
- `static/` — CSS, JavaScript, and images
- `tests/` — automated tests
- `requirements.txt` — Python packages
- `.env.example` — example database setting

## Development Workflow

1. Create a new branch for your feature: `git checkout -b feature/your-feature`
2. Make changes and commit them with clear messages
3. Push to GitHub and create a Pull Request
4. After review, merge into the main branch

## Database

The system currently uses PostgreSQL to store application data persistently.

**Tables include:**
- Users
- Activities
- Races

The project originally used SQLite during early development because it was simple for local testing. It later moved to PostgreSQL so that the team could connect to a shared database more easily.

Passwords are not stored as plain text. The system uses Werkzeug Security to hash passwords before saving them to the database.

## Project Management

The project was organised using GitHub tools:

- **Wiki** – Project documentation including requirements, personas, user stories, job stories, wireframes, system design, and testing plan
- **Project Board** – Kanban board used to manage development tasks
- **Issues** – Used to track individual tasks, bugs, and feature development
- **Branches and Pull Requests** – Used to manage individual contributions before merging into the main branch

## Team Members

- Omar
- Ben
- Justin
- Ibrahim
- Safyan

## Documentation

Detailed documentation for the project can be found in the GitHub Wiki.