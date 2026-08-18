# 📋 Proyecto2026 - Template Oficial

**Plantilla profesional para proyectos de egreso de la Tecnicatura en Redes y Software - UTU DGETP**

---

## ¿Qué es Proyecto2026?

Es un **template completamente funcional** que proporciona:

✅ Estructura lista para producción (PHP/Laravel + MySQL + React/Vue + Docker)  
✅ Documentación exhaustiva sobre API design, seguridad (ISO 27001) y arquitectura  
✅ Configuración Docker dockerized para desarrollo reproducible  
✅ Guías de contribución y flujo de trabajo  
✅ Ejemplos de Architecture Decision Records (ADR)  
✅ Checklist de calidad y testing  

No necesitas empezar de cero. Solo **clona/usa este template** como base y personalízalo para tu proyecto.

---

## 🎯 Para Quién es Este Template

- **Estudiantes de la Tecnicatura**: Punto de partida para proyectos de egreso
- **Docentes**: Base estructurada para enseñar desarrollo profesional
- **Equipos**: Estructura escalable para trabajo colaborativo

---

## 📦 Qué Incluye

```
proyecto2026/
├── backend/
│   └── API/README.md          ← GUÍA de diseño API (empieza aquí)
├── frontend/                  ← Configurado para React/Vue
├── docker/                    ← Nginx, PHP, MySQL containerizados
├── docs/
│   ├── adr/                   ← Architecture Decision Records
│   └── ISOs/                  ← Mapeo ISO 27001, 25001
├── .github/
│   └── CODEOWNERS            ← Control de revisiones
├── README.md                  ← Esta guía (actualizable)
├── CONTRIBUTING.md            ← Flujo de trabajo
├── SETUP.md                   ← Instalación inicial
├── TEMPLATE.md                ← Este archivo
└── docker-compose.yml         ← Orquestación de servicios
```

---

## 🚀 Primeros Pasos

### Para Estudiantes
1. **Lee [README.md](README.md)** — Entiende la estructura general
2. **Sigue [SETUP.md](SETUP.md)** — Configura tu repositorio
3. **Lee [backend/API/README.md](backend/API/README.md)** — Aprende diseño de API
4. **Lee [CONTRIBUTING.md](CONTRIBUTING.md)** — Entiende el flujo de trabajo

### Para Docentes
1. **Personaliza** README.md, CODEOWNERS con datos reales
2. **Comparte** el link del template con los estudiantes
3. **Explica** que usen "Use this template" para crear su repositorio
4. **Monitorea** Pull Requests y cambios

---

## 💡 Cómo Usar Este Template

### Opción 1: GitHub "Use this template" (RECOMENDADO)

```
1. En GitHub: UTU-DGETP/proyecto2026
2. Botón verde "Use this template"
3. Crea un nuevo repo desde la plantilla
4. Clona y personaliza para tu equipo
```

### Opción 2: Clonar Directamente

```bash
git clone https://github.com/UTU-DGETP/proyecto2026.git mi-proyecto
cd mi-proyecto
# Personaliza y pushea a tu repo propio
```

---

## 🎓 Estructura de Fases de Proyecto

El template está diseñado para acompañar todo el ciclo:

### Fase 1: Definición
- [ ] Propuesta de proyecto
- [ ] Aprobación docente
- [ ] Cronograma inicial

**Usa**: README.md, CONTRIBUTING.md como base

### Fase 2: Planificación y Diseño
- [ ] Diagramas de arquitectura
- [ ] Diseño de base de datos
- [ ] Especificación de API

**Usa**: 
- [backend/API/README.md](backend/API/README.md) — Guía de API design
- [docs/adr/0001-arquitectura-inicial.md](docs/adr/0001-arquitectura-inicial.md) — Decisiones de arquitectura

### Fase 3: Desarrollo e Implementación
- [ ] Código funcional
- [ ] Tests y auditoría
- [ ] Documentación técnica

**Usa**:
- CONTRIBUTING.md — Flujo de trabajo
- docker-compose.yml — Ambiente consistente
- GitHub Issues & Pull Requests — Seguimiento

---

## 🔒 Seguridad Incluida

El template está alineado con **ISO 27001** desde el diseño:

| Control ISO 27001 | Implementado en Template |
|-------------------|--------------------------|
| A.5.1 Políticas | Documentado en README, CONTRIBUTING |
| A.9.1 Acceso | JWT + RBAC en API guide |
| A.10.1 Cifrado | HTTPS, .env secrets |
| A.12.1 Logging | Logging guide en API README |
| A.12.2 Validación | Input validation patterns en backend |

Mira [docs/ISOs/](docs/ISOs/) para el mapeo completo.

---

## 🐳 Docker Incluido

No necesitas instalar manualmente PHP, MySQL, etc.

```bash
# Todo listo con un comando
docker-compose up -d --build

# Acceso inmediato a:
# - Backend: localhost:8080
# - Frontend: localhost:3000
# - MySQL: localhost:3306
```

Totalmente reproducible en cualquier máquina.

---

## 📊 Control de Código

`.github/CODEOWNERS` define quién revisa qué:

```
backend/   @responsable-backend
frontend/  @responsable-frontend
docker/    @responsable-devops
```

Cada Pull Request requiere aprobación de los owners.

---

## 📚 Documentación Exhaustiva

### Para Aprender
- **[backend/API/README.md](backend/API/README.md)** — Cómo diseñar APIs RESTful profesionales
- **[CONTRIBUTING.md](CONTRIBUTING.md)** — Flujo Git, Conventional Commits, TDD
- **[docs/adr/](docs/adr/)** — Cómo documentar decisiones técnicas

### Para Desarrollar
- **[backend/README.md](backend/README.md)** — Setup Laravel
- **[frontend/README.md](frontend/README.md)** — Setup frontend
- **[docker-compose.yml](docker-compose.yml)** — Orquestación de servicios

---

## ✅ Estándares de Calidad

El template fuerza:

- **Testing**: Mínimo 70% cobertura (PHPUnit + Jest)
- **Code Style**: PSR-12 (backend), ESLint (frontend)
- **Git Flow**: feature branches → develop → main
- **Code Review**: Todo PR requiere aprobación
- **Documentation**: PHPDoc, JSDoc, ADRs, README

---

## 🤝 Flujo de Trabajo Colaborativo

```
main (producción)
  ↑
develop (integración)
  ↑
feature/nombre (desarrollo)
```

1. Crea rama desde `develop`
2. Desarrolla + testes
3. Pull Request a `develop`
4. Code Review de pares
5. Merge a `develop`
6. Cuando está listo → PR a `main`

Ver [CONTRIBUTING.md](CONTRIBUTING.md) para detalles.

---

## 🛠️ Personalización Típica

Para cada nuevo equipo/proyecto:

```markdown
En README.md:
  - Título del proyecto
  - Descripción específica
  - Nombres de docentes
  - Integrantes del equipo
  
En .github/CODEOWNERS:
  - Usuarios GitHub del equipo
  
En .env.example:
  - Valores según proyecto
  
En backend/API/README.md:
  - Endpoints específicos del proyecto
  
En docs/adr/:
  - ADRs específicas del proyecto
```

---

## 📞 Soporte

### Documentación Oficial
- 📖 Laravel: https://laravel.com/docs
- 🎨 React: https://react.dev
- 🐳 Docker: https://docs.docker.com

### Contacto
- **Email**: Coordinador del proyecto
- **Reuniones**: Semanales (día/hora a definir)
- **Issues**: GitHub repository issues

---

## 📄 Versiones

| Versión | Fecha | Cambios |
|---------|-------|---------|
| 1.0 | 2026-08-15 | Release inicial |

---

## 📝 Licencia

Este template se distribuye bajo [LICENSE](LICENSE). Los estudiantes pueden:
- ✅ Usarlo para proyectos de egreso
- ✅ Modificarlo según necesidades
- ✅ Colaborar mejorando el template

---

## 🎯 Próximos Pasos

1. **Si eres estudiante**: Sigue [SETUP.md](SETUP.md)
2. **Si eres docente**: Personaliza este template para tu clase
3. **Si eres desarrollador**: Contribuye mejorando el template (Pull Requests bienvenidos)

---

**Template Oficial**: UTU-DGETP/proyecto2026  
**Última actualización**: 2026-08-15  
**Status**: ✅ Activo - Listo para usar

