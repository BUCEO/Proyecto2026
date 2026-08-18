# frontend/

Esta carpeta está vacía a propósito. Acá va tu frontend — el framework lo
elige el equipo (React, Vue, Svelte, lo que prefieran).

## Para inicializarlo (ejemplo con Vite + React)

```bash
cd frontend
npm create vite@latest . -- --template react
npm install
```

Si tu framework preferido usa otro comando de scaffolding, andá con ese —
lo único que importa es que quede un `package.json` con al menos estos
scripts, porque el pipeline de CI y el `docker-compose.yml` los invocan tal
cual:

```json
{
  "scripts": {
    "dev": "vite --port 5173",
    "build": "vite build",
    "lint": "eslint ."
  }
}
```

## Correrlo con Docker

Desde la **raíz** del proyecto:

```bash
docker compose up -d
```

Tu frontend en modo desarrollo va a quedar en `http://localhost:5173` (o el
puerto que hayas puesto en `FRONTEND_PORT`).

## Conectar con el backend

El backend Laravel queda expuesto en `http://localhost:8080`. Configurá esa
URL como base de tu cliente HTTP (fetch/axios) usando una variable de
entorno del frontend (`VITE_API_URL`, `.env` propio de tu framework, etc.) —
no la hardcodees.
