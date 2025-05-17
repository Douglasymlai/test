# MCP Hub

## Technology Stack and Features

- ⚡ [**FastAPI**](https://fastapi.tiangolo.com) for the Python backend API.
    - 🧰 [SQLModel](https://sqlmodel.tiangolo.com) for the Python SQL database interactions (ORM).
    - 🔍 [Pydantic](https://docs.pydantic.dev), used by FastAPI, for the data validation and settings management.
    - 💾 [PostgreSQL](https://www.postgresql.org) as the SQL database.
    - 🗂️ [Supabase](https://supabase.com) for the database real-time features, authentication, and storage.
- 🚀 [Refine](https://refine.dev) for the frontend.
    - 💃 Using TypeScript, Vite, REST API, and React.
    - 🎨 [Shadcn UI](https://ui.shadcn.com/) for the frontend components.
    - 🧪 [Playwright](https://playwright.dev) for End-to-End testing.
- 🔑 [StackAuth](https://stack-auth.com/) for authentication.
- 🐋 [Docker Compose](https://www.docker.com) for local development and debugging environment.
- ✅ Tests with [Pytest](https://pytest.org).
- 🚢 [Dokploy](https://dokploy.com/) for deployment.


## Local Development Environment

### Required
1. Docker and Docker Compose (you can find installation instructions on the [Docker website](https://docs.docker.com/get-docker/))
2. Node.js and npm (using [NVM](https://github.com/nvm-sh/nvm) for environment management)
3. Python 3.10+ (using [Pyenv](https://github.com/pyenv/pyenv) for environment management)

### 1. Clone the Repository
```bash
git clone https://github.com/eigent-ai/eigent-mcp-hub.git
cd eigent-mcp-hub
```

### 2. Create a Local Supabase Test Instance
```bash
npx supabase start

Need to install the following packages:
supabase@2.20.5
Ok to proceed? (y) 

Seeding globals from roles.sql...
WARN: no files matched pattern: supabase/seed.sql
Started supabase local development setup.

         API URL: http://127.0.0.1:54321
     GraphQL URL: http://127.0.0.1:54321/graphql/v1
  S3 Storage URL: http://127.0.0.1:54321/storage/v1/s3
          DB URL: postgresql://postgres:postgres@127.0.0.1:54322/postgres
      Studio URL: http://127.0.0.1:54323
    Inbucket URL: http://127.0.0.1:54324
      JWT secret: super-secret-jwt-token-with-at-least-32-characters-long
        anon key: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZS1kZW1vIiwicm9sZSI6ImFub24iLCJleHAiOjE5ODM4MTI5OTZ9.CRXP1A7WOeoJeXxjNni43kdQwgnWNReilDMblYTn_I0
service_role key: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZS1kZW1vIiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImV4cCI6MTk4MzgxMjk5Nn0.EGIM96RAZx35lJzdJsyH-qQwv8Hdp7fsn3W0YpN81IU
   S3 Access Key: 625729a08b95bf1b7ff351a663f3a23c
   S3 Secret Key: 850181e4652dd023b7a98c58ae0d2d34bd487ee0cc3254aed6eda37307425907
       S3 Region: local
```
Stop Supabase instance (optional)
```bash
npx supabase stop
```

### 3. Install Dependencies and Run the Project
#### 3.1 Backend
```bash
cd backend
# Install uv
curl -Ls https://astral.sh/uv/install.sh | bash
# Create a virtual environment
uv venv
# Activate the virtual environment
source .venv/bin/activate
# Install dependencies
uv sync
# Run the backend project
fastapi run app/main.py --reload
```

#### 3.2 Frontend
```bash
cd frontend
# Install dependencies
npm ci
# Run the frontend project
npm run dev
```

### 4. Debugging Dependency Configuration (Optional)
If you need to test the corresponding environment during frontend and backend development,
you can run the backend and frontend services in the project root directory using the following commands.
#### 4.1 Run Backend (for Frontend Debugging)
```bash
export COMPOSE_PROFILES=backend
docker compose up -d
```

#### 4.2 Run Frontend (for Backend Debugging)
```bash
export COMPOSE_PROFILES=frontend
docker compose up -d
```

#### 4.3 Run All Services
```bash
export COMPOSE_PROFILES=backend,frontend
docker compose up -d
```
