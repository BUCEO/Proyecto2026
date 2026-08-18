# Documentación de Diseño de API
## Proyecto de Egreso 2026

---

## 1. Fundamentación del Proyecto

Los proyectos de egreso constituyen una instancia académica de gran relevancia dentro de la Tecnicatura en Redes y Software, ya que permiten **integrar y aplicar los conocimientos** adquiridos a lo largo de los dos años de formación.

### Objetivos Principales

✅ Resolver un problema concreto mediante el desarrollo de una **solución informática funcional**  
✅ Cumplir con requerimientos predefinidos con **criterios de calidad profesional**  
✅ Adquirir habilidades transversales: trabajo en equipo, planificación, cumplimiento de plazos  
✅ Demostrar competencias en todas las áreas de la carrera:
- Programación y desarrollo de software
- Diseño y administración de bases de datos
- Redes
- Seguridad informática y buenas prácticas
- Metodologías de trabajo en equipo

---

## 2. Naturaleza del Proyecto y Alcance

Este proyecto desarrolla un **software que resuelve una necesidad específica** dentro del contexto de la carrera. El diseño y desarrollo sigue dos ejes:

| Aspecto | Descripción |
|--------|-------------|
| **Propuesta Creativa** | Libertad para proponer la idea general de la solución |
| **Requerimientos Técnicos** | Definidos por el cuerpo docente para asegurar objetivos formativos |
| **Integración** | El proyecto refleja un sistema profesional con ciclo de vida completo |

---

## 3. Organización y Metodología de Trabajo

El desarrollo se divide en **tres grandes hitos de entrega** con presentaciones parciales quincenales.

### 3.1 Fases del Proyecto

#### **Fase 1: Definición del Proyecto**
- ✏️ Selección de la idea general
- ✓ Aprobación docente (verificación de requerimientos)
- 🎯 Definición de objetivos, alcance y funcionalidades mínimas
- 📋 Plan general de trabajo

#### **Fase 2: Planificación y Diseño**
- 📐 Elaboración de diagramas de arquitectura y base de datos
- 🛠️ Diagramas de flujo y análisis de requisitos
- 🔧 Selección de herramientas tecnológicas (frameworks, lenguajes, entornos)
- 📊 Planificación detallada de tareas y asignación de roles
- ⏱️ Establecimiento de cronogramas

#### **Fase 3: Desarrollo y Pruebas**
- 💻 Implementación según planificación
- ✅ Pruebas unitarias, integrales y de aceptación
- 🔄 Ajustes derivados de resultados

---

## 4. Consideraciones de Seguridad (ISO 27001)

Esta API debe implementarse con principios de **seguridad por diseño**, alineados con la norma ISO 27001 (Sistemas de Gestión de Seguridad de Información).

### 4.1 Controles de Seguridad Clave

| Control ISO 27001 | Implementación en la API | Ejemplo |
|------------------|------------------------|---------|
| **A.5.1 Políticas de Seguridad** | Documentar políticas de acceso y uso | README de seguridad, CONTRIBUTING.md |
| **A.6.1 Organización Interna** | Definir roles y responsabilidades | Roles de desarrollador, admin, usuario |
| **A.9.1 Control de Acceso** | Autenticación y autorización robustas | JWT tokens, OAuth 2.0 |
| **A.9.2 Control de Acceso de Usuario** | Gestión de permisos granulares | RBAC (Role-Based Access Control) |
| **A.10.1 Cifrado** | Protección de datos en tránsito y reposo | HTTPS, encriptación de contraseñas |
| **A.10.2 Gestión de Claves Criptográficas** | Almacenamiento seguro de secrets | Uso de `.env`, no en el código |
| **A.12.1 Monitoreo y Registro** | Logging de acciones críticas | Auditoría de cambios, accesos |
| **A.12.2 Gestión de Vulnerabilidades** | Validación de entrada, sanitización | OWASP Top 10 |

### 4.2 Principios de Seguridad en el Diseño de API

1. **Autenticación Obligatoria**: Todo endpoint protegido requiere credenciales válidas
2. **Autorización Granular**: Cada recurso se valida contra permisos del usuario
3. **Validación de Entrada**: Rechazar datos inesperados o maliciosos
4. **HTTPS Obligatorio**: Encriptación en tránsito
5. **Rate Limiting**: Prevenir abuso y ataques DDoS
6. **Versionado**: Mantener compatibilidad y permitir evolución segura
7. **Logging Completo**: Registrar acciones críticas para auditoría

---

## 5. Arquitectura de la API

### 5.1 Stack Tecnológico

```
┌─────────────────────────────────────────────────┐
│           Cliente (Frontend)                     │
│         (React, Vue, etc.)                       │
└──────────────────┬──────────────────────────────┘
                   │ HTTPS/REST
┌──────────────────▼──────────────────────────────┐
│        API REST (Laravel - Backend)              │
│   ┌──────────────────────────────────────────┐  │
│   │  Autenticación & Autorización (Middleware)│ │
│   │  - JWT Tokens                            │ │
│   │  - RBAC (Role-Based Access Control)      │ │
│   └──────────────────────────────────────────┘  │
│   ┌──────────────────────────────────────────┐  │
│   │  Rutas y Controladores                   │ │
│   │  - RESTful Endpoints                     │ │
│   │  - Validación de entrada                 │ │
│   └──────────────────────────────────────────┘  │
│   ┌──────────────────────────────────────────┐  │
│   │  Lógica de Negocio (Models & Services)   │ │
│   │  - Reglas de dominio                     │ │
│   │  - Casos de uso                          │ │
│   └──────────────────────────────────────────┘  │
└──────────────────┬──────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────┐
│        Base de Datos (MySQL)                     │
│   - Tablas normalizadas                         │
│   - Índices y constraints                       │
│   - Encriptación de datos sensibles              │
└─────────────────────────────────────────────────┘
```

### 5.2 Convenciones RESTful

Toda endpoint sigue la estructura REST estándar:

```
METHOD /api/v1/resource/{id}
```

| Método | Operación | Endpoint Ejemplo |
|--------|-----------|------------------|
| `GET` | Obtener recurso(s) | `GET /api/v1/usuarios` |
| `POST` | Crear nuevo recurso | `POST /api/v1/usuarios` |
| `PUT` | Actualizar recurso completo | `PUT /api/v1/usuarios/{id}` |
| `PATCH` | Actualizar parcialmente | `PATCH /api/v1/usuarios/{id}` |
| `DELETE` | Eliminar recurso | `DELETE /api/v1/usuarios/{id}` |

---

## 6. Estructura de Respuestas

Todas las respuestas siguen un formato estándar para consistencia:

### Respuesta Exitosa (2xx)
```json
{
  "success": true,
  "data": {
    "id": 1,
    "nombre": "Juan Pérez",
    "email": "juan@example.com"
  },
  "message": "Recurso obtenido exitosamente"
}
```

### Respuesta de Error (4xx, 5xx)
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Los datos enviados no son válidos",
    "details": {
      "email": "El email no es válido"
    }
  }
}
```

---

## 7. Autenticación y Autorización

### 7.1 Flujo de Autenticación (JWT)

```
1. Cliente envía credenciales → POST /api/v1/auth/login
2. API valida credenciales
3. API genera JWT token (contiene: user_id, roles, permisos)
4. Cliente almacena token
5. Cliente envía token en header: Authorization: Bearer <token>
6. API valida token en cada request
```

### 7.2 Niveles de Acceso (RBAC)

| Rol | Permisos |
|-----|----------|
| **Administrador** | Acceso completo a todos los recursos |
| **Moderador** | Lectura y moderación de contenido |
| **Usuario** | Acceso a propios recursos y contenido público |
| **Invitado** | Solo lectura de contenido público |

---

## 8. Validación y Manejo de Errores

### 8.1 Validación de Entrada

Todos los datos entrantes se validan contra reglas:

```
- Email: formato válido
- Contraseña: mínimo 8 caracteres, mayúsculas, números
- Números: rango permitido, tipo correcto
- Strings: longitud máxima, caracteres permitidos
- Fechas: formato ISO 8601
```

### 8.2 Códigos de Error

| Código | Significado | HTTP |
|--------|------------|------|
| `VALIDATION_ERROR` | Datos inválidos | 422 |
| `UNAUTHORIZED` | Sin autenticación | 401 |
| `FORBIDDEN` | Sin autorización | 403 |
| `NOT_FOUND` | Recurso no existe | 404 |
| `CONFLICT` | Conflicto (ej: email duplicado) | 409 |
| `INTERNAL_ERROR` | Error del servidor | 500 |

---

## 9. Logging y Auditoría

Todas las acciones críticas se registran:

- ✅ Autenticaciones exitosas y fallidas
- ✅ Cambios de datos (CREATE, UPDATE, DELETE)
- ✅ Accesos denegados (403, 401)
- ✅ Errores (500)
- ✅ Acceso a datos sensibles

**Formato de Log**:
```
[TIMESTAMP] [LEVEL] [USER_ID] [ACTION] [RESOURCE] [STATUS] [DETAILS]
2026-08-15T10:30:45Z INFO user_123 UPDATE usuarios/456 SUCCESS "Nombre actualizado"
```

---

## 10. Versionado de API

La API soporta múltiples versiones para compatibilidad hacia atrás:

- `/api/v1/...` - Versión actual (estable)
- `/api/v2/...` - Nueva versión (en desarrollo)

El versionado permite:
- Cambios sin romper clientes existentes
- Migración gradual de clientes a nuevas versiones
- Sunset de versiones antiguas con tiempo

---

## 11. Testing y Calidad

### 11.1 Niveles de Test

```
┌─────────────────────────────────────┐
│   Pruebas Unitarias                 │
│   (Models, validación, lógica)      │
└──────────────┬──────────────────────┘
               ▼
┌─────────────────────────────────────┐
│   Pruebas de Integración            │
│   (Controladores, base de datos)    │
└──────────────┬──────────────────────┘
               ▼
┌─────────────────────────────────────┐
│   Pruebas de Aceptación (E2E)       │
│   (Flujos completos del usuario)    │
└─────────────────────────────────────┘
```

### 11.2 Cobertura Mínima

- **Lógica de negocio**: 80% de cobertura
- **Controladores**: 70% de cobertura (endpoints críticos 100%)
- **Autenticación/Autorización**: 100% de cobertura

---

## 12. Documentación de Endpoints

Cada endpoint debe documentarse con:

```markdown
### GET /api/v1/usuarios/{id}

**Descripción**: Obtiene un usuario específico

**Autenticación**: Requerida (JWT)  
**Autorización**: Propio usuario o Administrador

**Parámetros**:
- `id` (path, int, requerido): ID del usuario

**Respuesta Exitosa** (200):
{
  "success": true,
  "data": { ... }
}

**Errores Posibles**:
- 401: No autenticado
- 403: Sin permiso
- 404: Usuario no existe
```

---

## 13. Próximos Pasos

1. **Definir el modelo de datos** (Fase 2)
2. **Especificar endpoints concretos** para tu caso de uso
3. **Implementar autenticación** (JWT + RBAC)
4. **Escribir tests** (TDD - Test-Driven Development)
5. **Documentar API** (Swagger/OpenAPI)
6. **Realizar auditoría de seguridad** (ISO 27001 mapping)

---

## 14. Referencias y Recursos

- **RESTful API Design**: https://restfulapi.net/
- **ISO 27001 Controls**: https://www.iso.org/standard/27001
- **OWASP Top 10**: https://owasp.org/www-project-top-ten/
- **JWT Best Practices**: https://tools.ietf.org/html/rfc7519
- **Laravel Documentation**: https://laravel.com/docs

---

## 📋 Checklist de Diseño API

- [ ] Definir todos los recursos principales (usuarios, proyectos, etc.)
- [ ] Especificar roles y permisos (RBAC)
- [ ] Documentar todas las endpoints
- [ ] Definir estrategia de autenticación (JWT)
- [ ] Planificar logging y auditoría
- [ ] Identificar controles ISO 27001 a implementar
- [ ] Crear tests para casos críticos
- [ ] Documentar manejo de errores
- [ ] Validar formato de respuestas
- [ ] Revisar seguridad con equipo docente

---

**Última actualización**: 2026-08-15  
**Versión**: 1.0  
**Responsables**: Equipo de Estudiantes - Proyecto de Egreso 2026
