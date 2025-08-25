# Тестовое задание: Сервис авторизации (FastAPI + PostgreSQL + Docker)

Коротко
- Реализован сервис авторизации с регистрацией, входом, обновлением токена и простой проверкой аутентификации.
- Технологии: Python 3.12, FastAPI, PostgreSQL, Alembic, Docker/Compose, SQLAlchemy.

Быстрый старт
1) Скопировать переменные окружения:
   cp auth-service/.env.example auth-service/.env
   (при необходимости отредактировать секреты)
2) Запуск контейнеров:
   docker compose up --build
3) Применить миграции:
   docker compose exec app alembic upgrade head

Проверка
- Swagger UI: http://localhost:8000/docs
- Здоровье сервиса: GET http://localhost:8000/health

Ключевые эндпоинты
- POST /auth/register — регистрация (email, password) -> access/refresh
- POST /auth/login — вход (email, password) -> access/refresh
- POST /auth/refresh — обновление по refresh_token -> access/refresh
- GET  /auth/me — авторизованный эндпоинт (Authorization: Bearer <access>)

Структура
- docker-compose.yml — оркестрация БД и приложения
- auth-service/ — код сервиса (FastAPI, миграции, конфигурации)
  - src/ — приложение
  - alembic/ — миграции БД
  - README.md — детали по сервису

Подробнее см. auth-service/README.md