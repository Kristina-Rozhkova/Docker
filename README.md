# Запуск проекта с Docker

Этот проект использует Docker Compose для развертывания следующих сервисов:
- **Django** (бэкенд)
- **PostgreSQL** (база данных)
- **Redis** (брокер для Celery)
- **Celery Worker** (асинхронные задачи)
- **Celery Beat** (периодические задачи)

# Быстрый старт
1. Склонируйте репозиторий:
   ```bash
   git clone https://github.com/Kristina-Rozhkova/Docker.git
   cd Docker
   ```
2. Создайте файл .env (на основе .env.example):
    ```bash
    cp .env.example .env
    ```
3. Запустите проект:
    ```bash
    docker-compose up -d --build
    ```

# Проверка сервисов

**Django** - Откройте в браузере: http://localhost:8000/admin

**PostgreSQL** - Выполните в контейнере: docker-compose exec db psql -U postgres -d yourdb

**Redis** - Подключитесь клиентом: docker-compose exec redis redis-cli PING (должен ответить PONG)
**Celery** - Просмотрите логи: docker-compose logs celery
**Celery Beat** - Проверьте логи: docker-compose logs celery_beat

# Остановка проекта

```bash
docker-compose down
```