# cloud-services-engineer-docker-project-sem2

## Описание

Многоуровневое приложение на Go и Vue.js, предназначенное для демонстрации работы с Docker, микросервисами и современными веб-технологиями.

## Стек технологий

- Go
- Vue.js
- TypeScript / JavaScript
- Docker
- npm

## Установка

1. Клонируйте репозиторий:
```shell
git clone git@github.com:paponova-vika/cloud-services-engineer-docker-project-sem2.git
```

2. Перейдите в директорию проекта:
```shell
cd cloud-services-engineer-docker-project-sem2
``` 
3. Соберите и запустите контейнеры локально: 
```shell
docker compose up -f docker-compose.dev.yml --d
```
4. Откройте браузер и перейдите по адресу: 
```shell
http://localhost:8080
```

## В продакшн-режиме используйте:
```shell
docker compose up -d
```

Проект доступен по адресу:
```shell
http://localhost
```

## Структура проекта
- `backend/` - Сервис на Go, обрабатывающий API-запросы.
- `frontend/` - Веб-приложение на Vue.js, предоставляющее пользовательский интерфейс.
- `docker-compose.dev.yml` - Конфигурация Docker Compose для разработки.
- `docker-compose.yml` - Конфигурация Docker Compose для продакшн-режима.
- `README.md` - Документация проекта.
- `.github/workflows/deploy.yaml` - GitHub Actions для автоматической сборки и деплоя Docker-образов.