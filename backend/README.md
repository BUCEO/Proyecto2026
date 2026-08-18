# backend/

Esta carpeta está vacía a propósito. Acá va tu proyecto **Laravel**.

## Para inicializarlo

```bash
cd backend
composer create-project laravel/laravel .
```

Esto instala Laravel completo (con su propio `.gitignore`, `.env.example`,
`tests/Feature` y `tests/Unit` listos para TDD). El `Dockerfile` y el
`docker-compose.yml` de la raíz del proyecto ya están preparados para
levantar esta carpeta con PHP-FPM detrás de Nginx.

## Después de instalarlo

Desde la **raíz** del proyecto (no desde acá adentro):

```bash
cp .env.example .env
docker compose up -d --build
docker compose exec app php artisan key:generate
docker compose exec app php artisan migrate
```

Tu app va a quedar disponible en `http://localhost:8080` (o el puerto que
hayas puesto en `APP_PORT`).

## Tu primer test (TDD)

```bash
docker compose exec app php artisan make:test EjemploTest
docker compose exec app php artisan test
```

Escribí el test antes que el código — es el flujo que vimos en el Master
Class y en la clase de Fundamentos.
