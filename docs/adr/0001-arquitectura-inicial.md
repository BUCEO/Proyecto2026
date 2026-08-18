# ADR 0001 — Registro de decisiones de arquitectura

## Estado

Aceptado

## Contexto

Un ADR (Architecture Decision Record) documenta una decisión técnica
importante: qué se decidió, por qué, y qué alternativas se descartaron.
Es una práctica moderna para que el "por qué" de una decisión no se pierda
con el tiempo ni dependa de que alguien se acuerde de una conversación.

## Decisión

Este proyecto usa:

- **Backend**: Laravel (PHP) — API REST.
- **Frontend**: a definir por el equipo (SPA independiente del backend).
- **Base de datos**: MySQL.
- **Servidor web**: Nginx como reverse proxy hacia PHP-FPM.
- **Contenedores**: Docker Compose para desarrollo local y CI.
- **Testing**: TDD con PHPUnit/Pest en el backend.
- **CI/CD**: GitHub Actions — tests, lint y build en cada Pull Request.

## Consecuencias

- Cualquier integrante puede levantar el proyecto completo con
  `docker compose up`, sin instalar PHP o MySQL en su máquina.
- El frontend y el backend son proyectos separados que se comunican por
  HTTP — permite desarrollarlos y desplegarlos de forma independiente.
- Cada Pull Request corre la suite de tests automáticamente: nada llega a
  `main` sin pasar por CI.

---

_Copiá este archivo como `docs/adr/000N-titulo-de-la-decision.md` cada vez
que el equipo tome una decisión técnica importante (elegir una librería,
cambiar de estrategia de branching, etc.)._
