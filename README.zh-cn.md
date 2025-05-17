# MCP Hub

## 技术栈

- ⚡ [**FastAPI**](https://fastapi.tiangolo.com)：后端框架。
    - 🧰 [SQLModel](https://sqlmodel.tiangolo.com)：ORM（对象关系映射）工具。
    - 🔍 [Pydantic](https://docs.pydantic.dev)：数据验证和设置管理。
    - 💾 [PostgreSQL](https://www.postgresql.org)：PostgreSQL数据库。
    - 🗂️ [Supabase](https://supabase.com)：提供实时功能、身份验证和存储。
- 🚀 [Refine](https://refine.dev)：前端框架。
    - 💃 使用 TypeScript、Vite、REST API 和 React。
    - 🎨 [Shadcn UI](https://ui.shadcn.com/)：使用Shadcn UI作为组件库。
    - 🧪 [Playwright](https://playwright.dev)：端到端测试工具。
- 🔑 [StackAuth](https://stack-auth.com/)：身份验证模块。
- 🐋 [Docker Compose](https://www.docker.com)：基于Docker Compose的本地开发调试环境。
- ✅ [Pytest](https://pytest.org)：使用Pytest作为测试框架。
- 🚢 [Dokploy](https://dokploy.com/)：使用Dokploy作为部署工具。


## 本地开发环境

### 必要环境
1. Docker 和 Docker Compose (你可以在 [Docker 官网](https://docs.docker.com/get-docker/) 找到安装说明。)
2. Node.js 和 npm (使用 [NVM](https://github.com/nvm-sh/nvm) 进行环境管理)
3. Python 3.10+ (使用 [Pyenv](https://github.com/pyenv/pyenv) 进行环境管理)

### 1. 克隆仓库
```bash
git clone https://github.com/eigent-ai/eigent-mcp-hub.git
cd eigent-mcp-hub
```

### 2. 创建本地Supabase测试实例
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
停止Supabase实例（可选）
```bash
npx supabase stop
```

### 3. 安装依赖
#### 3.1 后端
```bash
cd backend
# 安装uv
curl -Ls https://astral.sh/uv/install.sh | bash
# 创建uv虚拟环境
uv venv
# 激活虚拟环境
source .venv/bin/activate
# 安装依赖
uv sync
# 运行后端服务
fastapi run app/main.py --reload
```

#### 3.2 前端
```bash
cd frontend
# 安装依赖
npm ci
# 运行前端程序
npm run dev
```

### 4. 调试依赖配置（可选）
如果在开发前后端时，需要对应的环境进行测试，则可以在项目根目录下，使用以下命令来运行后端和前端的服务。
#### 4.1 运行后端（供前端调试）
```bash
export COMPOSE_PROFILES=backend
docker compose up -d
```

#### 4.2 运行前端（供后端调试）
```bash
export COMPOSE_PROFILES=frontend
docker compose up -d
```

#### 4.3 运行所有服务
```bash
export COMPOSE_PROFILES=backend,frontend
docker compose up -d
```
