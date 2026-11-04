# Flask-API

A small REST API built with Flask, Flask-RESTful and Flask-SQLAlchemy. It stores users (name and email) in a local SQLite database and lets you create, read, update and delete them.

## Requirements

- Python 3 (developed on Python 3.15)
- Git

Package versions are pinned in [requirements.txt](requirements.txt).

## Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/Phebe814/Flask-API.git
   cd Flask-API
   ```

2. **Create and activate a virtual environment**

   Windows (PowerShell):

   ```powershell
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

   Windows (Git Bash):

   ```bash
   python -m venv .venv
   source .venv/Scripts/activate
   ```

   macOS / Linux:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   python -m pip install -r requirements.txt
   ```

4. **Create the database**

   ```bash
   python create_db.py
   ```

   This creates `instance/database.db`. Run it again if you add or rename a model, so the new tables get created.

5. **Run the server**

   ```bash
   python api.py
   ```

   The API runs at <http://127.0.0.1:5000> in debug mode.

## API endpoints

| Method | URL | Body (JSON) | Returns |
|---|---|---|---|
| GET | `/` | – | Welcome page |
| GET | `/api/users/` | – | All users |
| POST | `/api/users/` | `name`, `email` | All users (status 201) |
| GET | `/api/users/<id>` | – | One user, or 404 |
| PATCH | `/api/users/<id>` | `name`, `email` | The updated user, or 404 |
| DELETE | `/api/users/<id>` | – | The deleted user, or 404 |

Each user looks like this:

```json
{ "id": 1, "name": "alice", "email": "alice@example.com" }
```

### Example requests

Using `curl` (on Windows PowerShell, use `curl.exe`):

```bash
# Create a user
curl -X POST http://127.0.0.1:5000/api/users/ \
     -H "Content-Type: application/json" \
     -d '{"name": "alice", "email": "alice@example.com"}'

# List users
curl http://127.0.0.1:5000/api/users/

# Update user 1
curl -X PATCH http://127.0.0.1:5000/api/users/1 \
     -H "Content-Type: application/json" \
     -d '{"name": "alice2", "email": "alice2@example.com"}'

# Delete user 1
curl -X DELETE http://127.0.0.1:5000/api/users/1
```

Tools like Postman or Thunder Client also work.

## Project structure

```
Flask-API/
├── api.py              # Flask app, UserModel, and API routes
├── create_db.py        # Creates the SQLite tables
├── requirements.txt    # Pinned Python dependencies
├── docs/               # Project logs (AI log, decision log)
├── project-details/    # Brief, requirements and notes
└── instance/           # SQLite database (created locally, not in git)
```

## Known limitations

- `name` and `email` must be unique. Sending a duplicate currently returns a 500 error instead of a clear message.
- PATCH needs both `name` and `email`, even if you only want to change one.
