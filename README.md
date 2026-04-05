# app-portfolio-5osc

Portfolio web app scaffold with FastAPI frontend + backend, Firestore integration, Cloud Build CI/CD, and Cloud Run deployment.

## GitHub Pages root site

This repo now includes a root `index.html` and `styles.css` so it can render directly at:
`https://luisagcenteno84.github.io/`

## Architecture

- `frontend/`: FastAPI UI service (responsive portfolio page + proxy test endpoint)
- `backend/`: FastAPI API service (`/health`, `/api/v1/test` with Firestore write/read)
- `cloudbuild.yaml`: Builds and deploys both services to Cloud Run
- `scripts/bootstrap_gcp.ps1`: Enables APIs, creates Artifact Registry + Firestore
- `scripts/create_trigger.ps1`: Creates GitHub push trigger for `main`
- `scripts/deploy_once.ps1`: Runs an immediate deployment via Cloud Build

## Local run

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r backend/requirements.txt -r frontend/requirements.txt
docker compose up --build
```

- Frontend: `http://localhost:8080`
- Backend: `http://localhost:8081`
