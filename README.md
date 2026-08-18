# 🎓 Proyecto de Egreso 2026
**Guía Integral para el Proyecto de Pasaje de Grado**  
Tecnicatura en Redes y Software - DGETP-UTU

---

## 📚 Tabla de Contenidos

- [Visión General](#visión-general)
- [📖 Guías Principales](#-guías-principales)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Requisitos Previos](#requisitos-previos)
- [Instalación Rápida](#instalación-rápida)
- [Arquitectura](#arquitectura)
- [Desarrollo](#desarrollo)
- [Fases del Proyecto](#fases-del-proyecto)
- [Estándares de Calidad](#estándares-de-calidad)
- [Documentación](#documentación)
- [Preguntas Frecuentes](#preguntas-frecuentes)
- [Soporte](#soporte)

---

## 🎯 Visión General

Este repositorio contiene la **estructura base y guía de desarrollo** para los proyectos de egreso de la Tecnicatura en Redes y Software. Es un espacio donde los estudiantes **integran y aplican** los conocimientos de toda la carrera en un proyecto real.

### ✨ Características Principales

- ✅ **Stack Moderno**: PHP/Laravel + MySQL + React/Vue + Nginx
- ✅ **Containerizado**: Docker & docker-compose para ambiente reproducible
- ✅ **Seguro por Diseño**: Alineado con estándares ISO 27001
- ✅ **Documentación Completa**: ADRs, API spec, guías de contribución
- ✅ **Listo para Producción**: Estructura profesional y escalable

---

## 📖 Guías Principales

### 🚀 Para Comenzar
- **[SETUP.md](SETUP.md)** — Instalación paso a paso (empieza aquí)
- **[TEMPLATE.md](TEMPLATE.md)** — Qué es este template y cómo usarlo
- **[TEAM.md](TEAM.md)** — Configurar tu equipo en GitHub

### 📚 Para Desarrollar
- **[CONTRIBUTING.md](CONTRIBUTING.md)** — Flujo de trabajo Git y TDD
- **[backend/API/README.md](backend/API/README.md)** — Diseño de APIs RESTful
- **[docs/adr/](docs/adr/)** — Architecture Decision Records

### 🔒 Para Asegurar
- **[docs/ISOs/](docs/ISOs/)** — Mapeo ISO 27001 y 25001
- **[backend/README.md](backend/README.md)** — Setup seguro de Laravel

---

## 📁 Estructura del Proyecto

```
proyecto2026/
├── backend/                      # 🔧 API REST (Laravel)
│   ├── API/README.md            # 📋 Guía completa de diseño de API
│   └── README.md                # Setup de Laravel
│
├── frontend/                     # 💻 Interfaz de Usuario
│   └── README.md                # Setup de frontend
│
├── docker/                       # 🐳 Configuración Docker
│   ├── mysql/                   # Base de datos
│   ├── nginx/                   # Servidor web
│   └── php/                     # Runtime PHP
│
├── docs/                         # 📖 Documentación
│   ├── adr/                     # Architecture Decision Records
│   └── ISOs/                    # Estándares de seguridad
│
├── docker-compose.yml           # 🐳 Orquestación de servicios
├── .env.example                 # Variables de entorno (plantilla)
├── CONTRIBUTING.md              # 🤝 Guía de contribución
├── CHANGELOG.md                 # 📝 Historial de cambios
├── LICENSE                      # ⚖️ Licencia del proyecto
└── README.md                    # 📄 Este archivo

```

---

## 🔧 Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:

| Herramienta | Versión Mínima | Propósito |
|-------------|----------------|----------|
| **Docker** | 20.10+ | Containerización |
| **Docker Compose** | 1.29+ | Orquestación |
| **Git** | 2.25+ | Control de versiones |
| **Node.js** | 16+ | Frontend tooling (opcional) |
| **PHP** | 8.1+ | Si desarrollas localmente sin Docker |

### Verificar instalación:
```bash
docker --version
docker-compose --version
git --version
```

---

## 🚀 Instalación Rápida

### 1. Clonar el repositorio
```bash
# Para usar este template como base
git clone https://github.com/UTU-DGETP/proyecto2026.git proyecto-mi-equipo
cd proyecto-mi-equipo

# O: Usar "Use this template" en GitHub para crear un repositorio propio
# Settings → Template repository (marcado)
```

### 2. Preparar variables de entorno
```bash
cp .env.example .env
# Editar .env con tus configuraciones
```

### 3. Levantar los servicios con Docker
```bash
docker-compose up -d --build
```

### 4. Inicializar la base de datos
```bash
docker-compose exec app php artisan key:generate
docker-compose exec app php artisan migrate
docker-compose exec app php artisan seed:all
```

### 5. Acceder a la aplicación
- **Frontend**: http://localhost:3000 (React/Vue)
- **Backend API**: http://localhost:8080/api/v1
- **Documentación**: http://localhost:8080/api/docs

---

## 🏗️ Arquitectura

### Componentes Principales

```
┌─────────────────────────────────────────────────────┐
│           Cliente (Frontend)                         │
│    React/Vue - Puerto 3000                          │
└────────────────────┬────────────────────────────────┘
                     │ HTTPS REST API
┌────────────────────▼────────────────────────────────┐
│     API REST (Laravel Backend)                      │
│     Puerto 8080 - http://localhost:8080             │
│  ┌────────────────────────────────────────────────┐ │
│  │  Autenticación (JWT + RBAC)                    │ │
│  │  Validación de entrada                        │ │
│  │  Logging y auditoría (ISO 27001)              │ │
│  └────────────────────────────────────────────────┘ │
└────────────────────┬────────────────────────────────┘
                     │ SQL
┌────────────────────▼────────────────────────────────┐
│     Base de Datos (MySQL)                           │
│     Puerto 3306 - Persistencia de datos             │
└─────────────────────────────────────────────────────┘
```

### Tecnologías

| Capa | Tecnología | Propósito |
|------|-----------|----------|
| **Frontend** | React/Vue | Interfaz de usuario interactiva |
| **Backend** | Laravel 10+ | API REST con seguridad integrada |
| **Database** | MySQL 8.0 | Almacenamiento relacional |
| **Server** | Nginx | Proxy inverso y servicio estático |
| **Runtime** | PHP 8.2 | Ejecución de lógica backend |

---

## 💻 Desarrollo

### Trabajar en Backend (Laravel)

```bash
# Crear una migración
docker-compose exec app php artisan make:migration create_usuarios_table

# Crear un modelo
docker-compose exec app php artisan make:model Usuario -m

# Ejecutar tests
docker-compose exec app php artisan test

# Ver logs en tiempo real
docker-compose logs -f app
```

📚 **Guía completa**: [backend/README.md](backend/README.md)

### Trabajar en Frontend

```bash
# Si usas Node.js/npm localmente
cd frontend
npm install
npm run dev

# O dentro de Docker (si está configurado)
docker-compose exec frontend npm run dev
```

📚 **Guía completa**: [frontend/README.md](frontend/README.md)

### Parar los servicios
```bash
docker-compose down
```

---

## 📅 Fases del Proyecto

El desarrollo se organiza en **tres grandes hitos** con entregas progresivas:

### ✏️ Fase 1: Definición (Semanas 1-2)

**Objetivo**: Establecer la base del proyecto

- [ ] Definir idea general del proyecto
- [ ] Obtener aprobación docente
- [ ] Documentar objetivos y alcance
- [ ] Crear plan de trabajo inicial
- [ ] Identificar roles del equipo

**Entregables**:
- Propuesta de proyecto (1-2 páginas)
- Cronograma tentativo
- Asignación de responsabilidades

---

### 📐 Fase 2: Planificación y Diseño (Semanas 3-6)

**Objetivo**: Diseñar la solución antes de codificar

- [ ] Diagrama de arquitectura del sistema
- [ ] Diseño de base de datos (ER)
- [ ] Especificación de API (endpoints, formatos)
- [ ] Diagramas de flujo de procesos clave
- [ ] Matriz de seguridad (ISO 27001)
- [ ] Plan de testing
- [ ] Selección de tecnologías

**Entregables**:
- Architecture Decision Records (ADR)
- [API Design Spec](backend/API/README.md)
- Documentación de base de datos
- Plan de iteraciones/sprints

**Presentación 1** 📊 (Revisión de diseño)

---

### 💻 Fase 3: Desarrollo e Implementación (Semanas 7-14)

**Objetivo**: Construir la solución funcional

- [ ] Implementar backend API
- [ ] Desarrollar frontend
- [ ] Configurar base de datos
- [ ] Pruebas unitarias e integración
- [ ] Pruebas de aceptación
- [ ] Auditoría de seguridad
- [ ] Documentación técnica

**Entregables**:
- Código fuente comentado
- Tests con >80% cobertura
- Manual de usuario
- Guía de administrador
- Logs de auditoría

**Presentación 2** 🚀 (Demostración funcional)  
**Presentación Final** 🎓 (Defensa ante tribunal)

---

## ✅ Estándares de Calidad

### Seguridad (ISO 27001)

Nuestro proyecto implementa los siguientes controles clave:

| Control | Implementación | Validación |
|---------|----------------|-----------|
| **A.5.1** - Políticas de seguridad | CONTRIBUTING.md, .env seguro | Revisión |
| **A.9.1** - Control de acceso | JWT + RBAC | Tests unitarios |
| **A.10.1** - Encriptación | HTTPS, passwords hashed | SSL/TLS |
| **A.12.1** - Logging | Auditoría de cambios | Revisión de logs |
| **A.12.2** - Validación de entrada | Input sanitization | Tests de seguridad |

📖 **Mapeo completo**: [docs/ISOs/](docs/ISOs/)

### Code Quality

- ✅ Linting: PSR-12 (PHP), ESLint (JavaScript)
- ✅ Testing: PHPUnit (backend), Jest (frontend)
- ✅ Cobertura: Mínimo 70%
- ✅ Documentación: PHPDoc, JSDoc en código
- ✅ Revisor: Code review de pares antes de merge

### Performance

- ✅ API response time < 500ms
- ✅ Frontend load time < 3s
- ✅ Database queries optimizadas (índices, N+1 prevention)
- ✅ Caching strategies implementadas

---

## 📖 Documentación Completa

### 🎓 Para Estudiantes (Empieza Aquí)

1. **[SETUP.md](SETUP.md)** — Instalación inicial del proyecto
2. **[TEMPLATE.md](TEMPLATE.md)** — Entiende qué es este template
3. **[TEAM.md](TEAM.md)** — Configura tu equipo
4. **[CONTRIBUTING.md](CONTRIBUTING.md)** — Flujo de trabajo y Git
5. **[backend/API/README.md](backend/API/README.md)** — Cómo diseñar APIs

### 🛠️ Guías Técnicas

- 📘 **[backend/README.md](backend/README.md)** — Instalación y desarrollo Laravel
- 📗 **[frontend/README.md](frontend/README.md)** — Instalación y desarrollo frontend
- 🐳 **[docker-compose.yml](docker-compose.yml)** — Orquestación de servicios
- 🔐 **[.env.example](.env.example)** — Variables de entorno (plantilla)

### 📊 Decisiones de Arquitectura

- 📋 **[docs/adr/0001-arquitectura-inicial.md](docs/adr/0001-arquitectura-inicial.md)** — Decisiones iniciales
- 🔒 **[docs/ISOs/](docs/ISOs/)** — Mapeo ISO 27001 y 25001

### 🤝 Para Docentes

- **[.github/CODEOWNERS](.github/CODEOWNERS)** — Control de revisiones por equipo
- **[.github/workflows/](https://github.com/UTU-DGETP/proyecto2026/tree/main/.github/workflows)** — CI/CD pipelines

---

## ❓ Preguntas Frecuentes

### P: ¿Cómo ejecuto el proyecto en mi máquina?
**R**: Sigue la sección [Instalación Rápida](#instalación-rápida). Docker maneja todas las dependencias.

### P: ¿Qué debo hacer si Docker no inicia?
**R**: 
```bash
# Verificar status
docker-compose logs

# Reconstruir desde cero
docker-compose down -v
docker-compose up -d --build
```

### P: ¿Cómo agrego un nuevo endpoint API?
**R**: Mira la [Guía de Diseño API](backend/API/README.md) sección 5-6. Luego crea un controlador:
```bash
docker-compose exec app php artisan make:controller NuevoController
```

### P: ¿Dónde guardo las contraseñas y claves API?
**R**: **NUNCA** en el código. Usa el archivo `.env` (que es privado):
```bash
cp .env.example .env
# Edita .env con tus secrets
```

### P: ¿Cómo ejecuto los tests?
**R**:
```bash
# Tests del backend
docker-compose exec app php artisan test

# Tests del frontend
docker-compose exec frontend npm test
```

### P: ¿Qué es un ADR (Architecture Decision Record)?
**R**: Un documento que justifica decisiones técnicas importantes. Mira ejemplos en [docs/adr/](docs/adr/).

---

## 🆘 Soporte

### Canales de Comunicación

- 💬 **Equipo**: Reuniones semanales (lunes 15:00)
- 📧 **Docentes**: Consultas puntuales por email
- 📱 **Grupo del curso**: WhatsApp/Discord para coordinación
- 🐛 **Issues**: Reporta bugs en GitHub Issues

### Escalación de Problemas

1. **Problema técnico**: Abre un Issue con descripción y logs
2. **Pregunta de diseño**: Consulta en reunión semanal
3. **Bloqueador crítico**: Contacta docente por email + Teams

### Recursos Externos

- 🎥 **Laravel Docs**: https://laravel.com/docs
- 🎨 **React/Vue Docs**: https://react.dev | https://vuejs.org
- 🗄️ **MySQL Docs**: https://dev.mysql.com/doc/
- 🐳 **Docker**: https://docs.docker.com/
- 🔒 **ISO 27001**: https://www.iso.org/standard/27001

---

## 📋 Checklist de Inicio

Antes de comenzar a programar, completa esto:

- [ ] Clone el repositorio
- [ ] Instale Docker y docker-compose
- [ ] Cree el archivo `.env` desde `.env.example`
- [ ] Levante los servicios: `docker-compose up -d`
- [ ] Ejecute las migraciones
- [ ] Lea [CONTRIBUTING.md](CONTRIBUTING.md)
- [ ] Lea [backend/API/README.md](backend/API/README.md)
- [ ] Haga su primer commit de prueba
- [ ] Agregue su nombre al README (sección de equipo - opcional)

---

## 👥 Equipo

### Docentes Responsables
- 🏛️ **Coordinador General**: [Nombre Docente]
- 💻 **Programación (Backend, Frontend)**: [Nombre Docente]
- 🗄️ **Base de Datos**: [Nombre Docente]
- 🌐 **Sistema (Redes, DevOps)**: [Nombre Docente]
- 🔒 **Seguridad Informática**: [Nombre Docente]

### Integrantes del Equipo (Estudiantes)

| Nombre | Rol | GitHub | Email |
|--------|-----|--------|-------|
| Estudiante 1 | Full Stack | @github-user-1 | estudiante1@utu.edu.uy |
| Estudiante 2 | Backend/DevOps | @github-user-2 | estudiante2@utu.edu.uy |
| Estudiante 3 | Frontend | @github-user-3 | estudiante3@utu.edu.uy |
| Estudiante 4 | Database Admin | @github-user-4 | estudiante4@utu.edu.uy |

*Completa esta tabla cuando tu equipo se forme*

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia [LICENSE](LICENSE). Los estudiantes pueden usar el código como base educativa.

---

## 📞 Contacto y Comunicación

**Correo Coordinador**: [Reemplaza con email del docente coordinador]  
**Reunión semanal**: [Reemplaza con día y hora]  
**Repositorio Template**: https://github.com/UTU-DGETP/proyecto2026  
**Tu Repositorio**: https://github.com/[tu-usuario]/tu-proyecto-2026  

### Canales de Comunicación
- 📧 **Email de coordinación**: [email]
- 💬 **Grupo de WhatsApp/Discord**: [enlace]
- 📋 **Tablero del proyecto**: [GitHub Projects link]
- 📅 **Calendario de entregas**: [Google Calendar link]

---

**Última actualización**: 2026-08-15  
**Versión**: 1.0  
**Estado**: 🟢 Activo - Aceptando estudiantes
