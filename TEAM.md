# 👥 Configuración de Equipo - Proyecto2026

**Guía para configurar correctamente el equipo en el repositorio del proyecto de egreso**

---

## 1. Definir Roles y Responsabilidades

Antes de configurar GitHub, acuerda con tu equipo quién es responsable de cada área.

### Plantilla de Roles

```markdown
| Integrante | Rol Principal | Rol Secundario | GitHub User | Email |
|-----------|---------------|----------------|-------------|-------|
| | Backend/API | Testing | @username | nombre@utu.edu.uy |
| | Frontend/UI | DevOps | @username | nombre@utu.edu.uy |
| | Database/DevOps | Backend | @username | nombre@utu.edu.uy |
| | Testing/QA | Documentación | @username | nombre@utu.edu.uy |
```

**Notas**:
- Cada integrante puede tener responsabilidades en múltiples áreas
- Los roles secundarios ayudan en paralelo
- La rotación de roles es buena práctica (aprender de todo)

---

## 2. Configurar GitHub Usernames

### Obtener tu GitHub Username

1. Va a https://github.com/settings/profile
2. Tu username está en "Public profile"
3. Formato: `@tu-username-sin-espacios`

### Crear tabla en README.md

En la sección **"👥 Equipo"**, completa:

```markdown
### Integrantes del Equipo (Estudiantes)

| Nombre | Rol | GitHub | Email |
|--------|-----|--------|-------|
| Juan Pérez | Full Stack | @juanperez | juan@utu.edu.uy |
| María García | Frontend Lead | @mgarcia2026 | maria@utu.edu.uy |
| Carlos López | DevOps | @carloslopez | carlos@utu.edu.uy |
| Ana Martínez | QA/Testing | @amartinez26 | ana@utu.edu.uy |
```

---

## 3. Configurar Code Owners (.github/CODEOWNERS)

El archivo `.github/CODEOWNERS` define quién **revisa cambios** en cada carpeta.

### Estructura Básica

```
# Formato: ruta    @usuario1 @usuario2

# Backend (API)
backend/         @usuario-backend

# Frontend (UI)
frontend/        @usuario-frontend

# DevOps
docker/          @usuario-devops
docker-compose.yml @usuario-devops

# Documentación (todos revisar)
docs/            @usuario-backend @usuario-frontend @usuario-devops
README.md        @usuario-backend @usuario-frontend @usuario-devops
```

### Pasos para Configurar

1. **Abre** `.github/CODEOWNERS` en VS Code
2. **Reemplaza**:
   - `@usuario-backend` → `@juanperez` (tu user)
   - `@usuario-frontend` → `@mgarcia2026`
   - `@usuario-devops` → `@carloslopez`
3. **Guarda** y **commiteá**:
   ```bash
   git add .github/CODEOWNERS
   git commit -m "chore: configurar code owners para el equipo"
   git push origin develop
   ```

### Resultado: Code Review Automático

Cuando alguien hace un Pull Request a `backend/`:
- ✅ Automáticamente pide review de `@usuario-backend`
- ✅ No se puede mergear sin su aprobación

---

## 4. Invitar Colaboradores en GitHub

### Pasos

1. **Settings** → **Collaborators** → **Add people**
2. Ingresa emails o usernames GitHub de cada integrante
3. Selecciona rol: **Maintain** (para equipos de estudiantes)
4. Envía invitación

### Roles GitHub

| Rol | Permisos |
|-----|----------|
| **Maintain** | Puede mergear PRs, administrar settings |
| **Push** | Puede hacer push y crear PRs |
| **Pull** | Solo lectura |
| **Triage** | Puede cerrar issues |

**Recomendación**: Usa **Maintain** para todos (equipo pequeño de confianza)

---

## 5. Proteger Ramas Principales

Configura reglas para evitar cambios accidentales:

### Configurar Branch Protection

**Para la rama `main`** (producción):

1. **Settings** → **Branches** → **Add rule**
2. **Branch name pattern**: `main`
3. Marca:
   - ✓ Require a pull request before merging
   - ✓ Require approvals (1)
   - ✓ Require status checks to pass
4. Click **Create**

**Para la rama `develop`** (integración):

1. Repite pasos arriba con pattern: `develop`
2. Opcionalmente: ✓ Require approvals (1)

### Resultado

- Solo Pull Requests pueden mergear a estas ramas
- Requieren aprobación (code review)
- Tests deben pasar

---

## 6. Configurar Notificaciones de Equipo

Para que todos estén informados:

### En GitHub

**Settings** → **Notifications**
- Selecciona cómo quieres ser notificado (email, web, etc)
- Marca: "Participating and mentions only"

### Crear Grupo de Comunicación

En WhatsApp/Discord:
```
Proyecto 2026 - [Tu Equipo]

Compartir:
- Links de PRs urgentes
- Decisiones de arquitectura
- Problemas bloqueantes
- Reunión semanal de sincronización
```

---

## 7. Definir Horarios y Reuniones

### Reunión Semanal

```markdown
📅 Día: [Día de la semana]
⏰ Hora: [HH:MM]
📍 Lugar: [Aula/Virtual]
⏱️ Duración: 30-45 minutos

Agenda:
1. Revisión de sprint actual
2. Problemas bloqueantes
3. Próximos pasos
4. Code review rápida si es necesario
```

**Actualiza esto en README.md** en la sección de "Contacto"

---

## 8. Crear Tablero del Proyecto

### GitHub Projects

1. **Projects** (en tu repo) → **New**
2. Template: **Kanban** o **Table**
3. Crea columnas:
   - **Backlog** — Ideas y features no iniciadas
   - **In Progress** — Trabajando actualmente
   - **In Review** — En Pull Request
   - **Done** — Completado

4. Asigna cada Issue a un integrante
5. Actualiza estado mientras trabajas

### Resultado

Todos ven qué está haciendo quién, en tiempo real.

---

## 9. Crear Issues y Tareas

Para organizar el trabajo:

### Template de Issue

```markdown
## Descripción
[Qué hay que hacer]

## Criterios de Aceptación
- [ ] Criterio 1
- [ ] Criterio 2

## Tareas
- [ ] Subtarea 1
- [ ] Subtarea 2

## Asignado a
@usuario

## Labels
`backend`, `feature`, `priority:high`
```

### Tipos de Issues

- **Feature**: Nuevo endpoint, nueva página, etc
- **Bug**: Algo no funciona
- **Docs**: Documentación
- **Chore**: Tareas administrativas
- **Security**: Correcciones de seguridad

---

## 10. Documentar Decisiones

Cada decisión importante → ADR (Architecture Decision Record)

### Ubicación

`docs/adr/0002-nombre-decision.md`

### Plantilla

```markdown
# ADR 0002: [Título de la decisión]

## Contexto
[Por qué necesitábamos decidir esto]

## Decisión
[Qué decidimos]

## Consecuencias
[Positivas y negativas de la decisión]

## Alternativas Consideradas
[Qué otras opciones había]

## Decided By
@usuario1 @usuario2
```

### Ejemplo

```markdown
# ADR 0002: Usar JWT para autenticación

## Contexto
Necesitamos autenticar usuarios en la API

## Decisión
Usar JSON Web Tokens (JWT) en lugar de sesiones

## Consecuencias
+ Stateless, escalable
+ Compatible con frontend SPA
- Requiere refresh token strategy

## Alternativas
- Sessions (state full)
- OAuth (más complejo)

## Decided By
@backend-team (2026-08-15)
```

---

## ✅ Checklist de Configuración de Equipo

- [ ] Definir roles y responsabilidades
- [ ] Obtener GitHub usernames de todos
- [ ] Completar tabla de equipo en README.md
- [ ] Configurar .github/CODEOWNERS con users
- [ ] Invitar colaboradores a GitHub
- [ ] Proteger ramas main y develop
- [ ] Configurar notificaciones
- [ ] Definir horario de reunión semanal
- [ ] Crear GitHub Projects/Kanban
- [ ] Crear primer ADR de decisiones
- [ ] Crear grupo de WhatsApp/Discord
- [ ] Primer commit: "chore: configurar equipo"

---

## 🆘 Problemas Comunes

### P: "No veo CODEOWNERS funcionando"
**R**: 
1. Verifica que los usernames sean correctos (@, sin espacios)
2. El archivo debe estar en `.github/CODEOWNERS`
3. Requiere que haya protección de rama en Settings

### P: "No recibo notificaciones de PRs"
**R**: 
1. Ve a tu repo → **Watching** (esquina superior)
2. Selecciona **All activity** o **Custom**
3. Verifica Settings de notificaciones personales

### P: "Alguien hace merge sin review"
**R**: 
1. Habilita "Branch protection" en main/develop
2. Marca "Require approvals before merging"

### P: "Queremos usar diferentes ramas por rol"
**R**: Crea ramas específicas:
```
feature/backend/nuevo-endpoint
feature/frontend/nueva-pagina
hotfix/seguridad-critica
```

---

## 📚 Recursos Adicionales

- [GitHub Docs - Collaborators](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories)
- [GitHub Docs - Code Owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
- [GitHub Docs - Branch Protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches)
- [ADR Best Practices](https://adr.github.io/)

---

**Última actualización**: 2026-08-15  
**Versión**: 1.0  
**Para**: Template Proyecto2026

