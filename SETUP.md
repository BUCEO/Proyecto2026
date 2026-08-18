# 🚀 SETUP Inicial - Proyecto 2026

**Template Oficial**: Guía paso a paso para configurar tu proyecto de egreso basado en Proyecto2026.

---

## 1️⃣ Usar este Template

Tienes dos opciones:

### Opción A: Usar "Use this template" en GitHub (RECOMENDADO)

```
1. Ve a: https://github.com/UTU-DGETP/proyecto2026
2. Haz clic en "Use this template" → "Create a new repository"
3. Nombre: tu-proyecto-2026 (o como prefieras)
4. Descripción: Proyecto de egreso de [tu equipo]
5. Selecciona "Private" (mejor para equipos de clase)
6. Haz clic en "Create repository from template"
```

### Opción B: Clonar y cambiar remoto

```bash
git clone https://github.com/UTU-DGETP/proyecto2026.git tu-proyecto-2026
cd tu-proyecto-2026
git remote remove origin
git remote add origin https://github.com/[tu-usuario]/tu-proyecto-2026.git
git branch -M main
git push -u origin main
```

---

## 2️⃣ Configurar el Repositorio

### Actualizar archivos clave

#### A. `README.md`
```markdown
En la sección "Equipo", reemplaza:
- [Nombre Docente] → Nombres reales de docentes
- github-user-1, etc → Usuarios GitHub del equipo
- @utu.edu.uy → Emails reales
```

#### B. `.github/CODEOWNERS`
```
Reemplaza:
- @usuario-backend → Tu user de GitHub (backend)
- @usuario-frontend → Tu user de GitHub (frontend)
- @usuario-devops → Tu user de GitHub (DevOps)
```

#### C. `.env.example` (SIN cambiar contraseñas)
```bash
# Simplemente revisar que esté correcto
# NO cambies las contraseñas aquí (son ejemplos)
# Cada equipo configura su .env local
```

### Habilitar ramas protegidas

```
Settings → Branches → Add rule
  Branch name pattern: main
  ✓ Require a pull request before merging
  ✓ Require approvals (1 approval)
  ✓ Require status checks to pass
  
Settings → Branches → Add rule
  Branch name pattern: develop
  ✓ Require a pull request before merging
  ✓ Require approvals (1 approval)
```

---

## 3️⃣ Configurar Variables de Entorno Locales

```bash
# Desde la raíz del proyecto
cp .env.example .env

# Edita .env con tus valores LOCALES
# Ejemplo:
APP_NAME="Tu Proyecto 2026"
APP_DEBUG=true
DB_DATABASE=proyecto2026_dev
DB_USERNAME=dev_user
DB_PASSWORD=dev_password_segura
```

⚠️ **IMPORTANTE**: Nunca commits `.env` al repo. Está en `.gitignore`.

---

## 4️⃣ Instalar Dependencias Locales

### Backend (Laravel)

```bash
cd backend
composer install
cd ..
```

### Frontend

```bash
cd frontend
npm install
cd ..
```

---

## 5️⃣ Inicializar Docker

```bash
# Levantar todos los servicios
docker-compose up -d --build

# Ejecutar migraciones
docker-compose exec app php artisan migrate

# (Opcional) Seed con datos de prueba
docker-compose exec app php artisan db:seed
```

Verifica:
- Backend: http://localhost:8080
- Frontend: http://localhost:3000 (o según tu config)
- MySQL: localhost:3306

---

## 6️⃣ Primer Commit de Equipo

```bash
# Asegúrate de estar en develop
git checkout develop

# Haz cambios al README y CODEOWNERS
git add README.md .github/CODEOWNERS .env.example

# Commit
git commit -m "chore: configurar template para [nombre equipo]"

# Push
git push origin develop

# Crea un Pull Request en GitHub para mergear a main
```

---

## 7️⃣ Invitar Colaboradores

```
Settings → Collaborators → Add people
Invita a todos los integrantes del equipo como "Maintainer"
```

Cada integrante debe:
1. Aceptar la invitación en su email
2. Clonar el repositorio: `git clone [tu-repo-url]`
3. Crear su rama de trabajo: `git checkout -b develop`

---

## 8️⃣ Configurar Integrantes en el Equipo

Completa esta tabla en `README.md`:

```markdown
| Nombre | Rol | GitHub | Email |
|--------|-----|--------|-------|
| Juan Pérez | Backend | @juanperez | juan@utu.edu.uy |
| María García | Frontend | @mgarcia | maria@utu.edu.uy |
| Carlos López | DevOps | @carloslopez | carlos@utu.edu.uy |
| Ana Martínez | Database | @amartinez | ana@utu.edu.uy |
```

---

## ✅ Checklist Final

- [ ] Repositorio creado desde template Proyecto2026
- [ ] README.md actualizado con datos del equipo
- [ ] `.github/CODEOWNERS` configurado con usuarios GitHub del equipo
- [ ] `.env` creado localmente (NO en repo)
- [ ] Dependencias instaladas (composer + npm)
- [ ] Docker levantado y funcionando
- [ ] Migraciones ejecutadas
- [ ] Primer commit de configuración hecho
- [ ] Colaboradores invitados
- [ ] CODEOWNERS habilitados en Settings
- [ ] Ramas protegidas configuradas (main y develop)
- [ ] Grupo de comunicación creado (WhatsApp, Discord, etc.)

---

## 🆘 Problemas Comunes

### "Permission denied" en Docker
```bash
sudo usermod -aG docker $USER
# Cierra sesión y abre terminal nueva
```

### "Port already in use 8080"
```bash
# Ver qué usa puerto 8080
lsof -i :8080

# Cambiar puerto en docker-compose.yml o .env
APP_PORT=8081
```

### "mysql container exits immediately"
```bash
# Ver logs
docker-compose logs mysql

# Reintentar
docker-compose down -v  # elimina volúmenes
docker-compose up -d --build
```

---

## 📚 Próximos Pasos

1. **Lee [CONTRIBUTING.md](CONTRIBUTING.md)** — Flujo de trabajo del equipo
2. **Lee [backend/API/README.md](backend/API/README.md)** — Diseño de API
3. **Define tu primer sprint** — Tareas en GitHub Issues
4. **Comienza Fase 1** — Propuesta inicial del proyecto

---

**Última actualización**: 2026-08-15  
**Template Version**: 1.0  
**Status**: ✅ Listo para usar

