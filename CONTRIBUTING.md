# Cómo contribuir

Guía rápida del flujo de trabajo del grupo. Todo esto ya lo vimos en el
GitHub Master Class — acá queda por escrito para no perder la referencia.

## Ramas

- `main` — siempre desplegable, solo recibe merges vía Pull Request.
- `develop` — integración de funcionalidades del sprint/Hito actual.
- `feature/nombre-corto` — una por cada Issue en desarrollo.
- `hotfix/nombre-corto` — correcciones urgentes sobre `main`.
- `release/x.y.0` — estabilización antes de cerrar un Hito.

```bash
git checkout -b feature/registro-documentos develop
```

## Commits

Conventional Commits, siempre:

```
feat(documentos): agregar carga de archivos con validación de tipo
fix(auth): corregir expiración del token
docs: actualizar instrucciones de instalación
```

## TDD — el ciclo de cada funcionalidad

1. **Red** — escribí el test que describe el comportamiento esperado. Corré
   `php artisan test` y verificalo en rojo.
2. **Green** — escribí el código mínimo para que ese test pase.
3. **Refactor** — mejorá el código manteniendo los tests en verde.

```bash
php artisan make:test DocumentoUploadTest
# escribís el test primero...
php artisan test --filter=DocumentoUploadTest
```

## Antes de abrir el Pull Request

```bash
vendor/bin/pint --test      # estilo de código backend
php artisan test            # suite completa de tests
npm run lint                # estilo de código frontend (si ya está inicializado)
npm run build                # build de producción del frontend
```

El pipeline de CI (`.github/workflows/ci.yml`) corre exactamente estos mismos
pasos — si pasan en tu máquina, van a pasar en GitHub.

## Pull Request

- Mínimo 1 aprobación antes de mergear a `develop` o `main`.
- El CI tiene que estar en verde.
- Usá la plantilla de PR — no la borres, completala.

## Versionado

Al cerrar cada Hito:

```bash
git checkout main
git merge release/x.y.0
git tag -a vX.Y.0 -m "Hito N: descripción corta"
git push origin main --tags
```

| Hito | Versión |
|------|---------|
| 1 — Análisis y diseño | v1.0.0 |
| 2 — Desarrollo funcional | v2.0.0 |
| 3 — Proyecto final | v3.0.0 |
