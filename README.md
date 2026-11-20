# ProcureFlow AI

ProcureFlow is an early backend for supplier records. It has a FastAPI starter endpoint, PostgreSQL settings, and an Alembic migration for a supplier table with a name, optional contact details, and a creation timestamp.

## Run it locally

Create a PostgreSQL database, then run these commands from the repository root in PowerShell.

```powershell
python -m venv procureflowenv
.\procureflowenv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
Copy-Item .env.example .env
```

Set `DB_NAME`, `DB_USER`, and `DB_PASSWORD` in `.env` to match your local database. Then apply the migration and start the API.

```powershell
python -m alembic upgrade head
python -m uvicorn app.main:app --reload
```

Open the [API docs](http://127.0.0.1:8000/docs) and try `GET /` to confirm the app started. Run `python -m alembic current` to check the database revision.

Supplier endpoints and purchasing workflows are still to come.
