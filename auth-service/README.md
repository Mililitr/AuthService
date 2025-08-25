Auth Service (FastAPI + PostgreSQL + Docker)

Endpoints:
- POST /auth/register {email, password} -> {access_token, refresh_token}
- POST /auth/login {email, password} -> {access_token, refresh_token}
- POST /auth/refresh (body: token string) -> {access_token, refresh_token}
- GET /health -> {status: ok}
- GET /auth/me (header: Authorization: Bearer <access_token>) -> {user_id}

Running:
1) docker compose up --build
2) Apply migrations inside container:
   docker compose exec app alembic upgrade head

Environment:
- Copy auth-service/.env.example to auth-service/.env and change secrets

Notes:
- Uses Alembic migrations for DB schema
- Tokens: JWT HS256; access/refresh lifetimes configurable
