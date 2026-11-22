# ipr-hw3

## Описание

В этой работе я запустила Python-приложение и Redis с помощью Docker Compose.

Redis используется для хранения счётчика.

## Запуск

Создаём файл .env:

    cp .env.example .env

Запускаем проект:

    docker compose up -d --build

Проверяем контейнеры:

    docker compose ps

Приложение доступно по адресу: http://localhost:8080

## Проверка

Проверяем приложение:

    curl http://localhost:8080/

Увеличиваем счётчик:

    curl -X POST http://localhost:8080/increment

Проверяем состояние:

    curl http://localhost:8080/healthz
    curl http://localhost:8080/readyz

## Проверка Redis

Останавливаем Redis:

    docker compose stop redis

Запускаем Redis снова:

    docker compose start redis

## Проверка сохранения данных

Останавливаем контейнеры:

    docker compose down

Запускаем снова:

    docker compose up -d

Счётчик сохраняется благодаря Docker volume.

## Остановка

    docker compose down
