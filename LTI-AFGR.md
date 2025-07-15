
# LTI-AG

## Descripción del Software LTI

**LTI** (Lean Talent Intelligence) es un sistema ATS (Applicant Tracking System) de nueva generación enfocado en potenciar la eficiencia de los departamentos de recursos humanos mediante automatización, colaboración en tiempo real y asistentes de IA. 

### Valor Añadido
- Automatización de tareas repetitivas (filtrado, programación de entrevistas)
- Asistencia de IA en redacción de vacantes, screening de CVs y feedback
- Colaboración entre reclutadores y managers en tiempo real
- Evaluaciones multimedia (entrevistas en video)
- Trazabilidad completa del proceso de selección

### Ventajas Competitivas
- Integración de IA nativa
- Experiencia de usuario moderna
- Modularidad y escalabilidad
- Enfoque colaborativo y analítico

---

## Funciones Principales

- Publicación de vacantes con asistentes IA
- Portal de candidatos para aplicar y subir CVs/videos
- Matching inteligente entre vacantes y candidatos
- Agendamiento de entrevistas automatizado
- Evaluación colaborativa con feedback estructurado
- Integración con herramientas externas (correo, calendario, CRM)
- Panel analítico en tiempo real de métricas de reclutamiento

---

## Lean Canvas

```mermaid
flowchart TB
    A[Problema: Procesos ineficientes de reclutamiento]
    B[Segmento: RRHH de empresas tecnológicas]
    C[Propuesta: ATS moderno con IA y colaboración]
    D[Canales: Web, partners, marketplaces]
    E[Ingresos: Licencias SaaS]
    F[Costos: Infraestructura cloud, IA, soporte]
    G[Actividades Clave: Desarrollo, soporte, IA]
    H[Ventaja Competitiva: UX + IA + tiempo real]

    A --> C
    B --> C
    C --> D
    C --> E
    E --> F
    F --> G
    C --> H
```

---

## Casos de Uso

### 1. Publicar Vacante
```plantuml
@startuml
actor Reclutador
rectangle "Sistema ATS" {
  Reclutador --> (Iniciar sesión)
  Reclutador --> (Publicar Vacante)
  (Publicar Vacante) --> (Completar Formulario Vacante) : <<include>>
  (Publicar Vacante) --> (Guardar Vacante) : <<include>>
}
@enduml
```

### 2. Postulación de Candidato
```plantuml
@startuml
actor Candidato
rectangle "Sistema ATS" {
  Candidato --> (Buscar Vacante)
  Candidato --> (Aplicar a Vacante)
  (Aplicar a Vacante) --> (Subir CV) : <<include>>
  (Aplicar a Vacante) --> (Grabar Video) : <<extend>>
  (Aplicar a Vacante) --> (Confirmar Aplicación)
}
@enduml
```

### 3. Evaluación y Feedback
```plantuml
@startuml
actor Manager
rectangle "Sistema ATS" {
  Manager --> (Ver Postulaciones)
  Manager --> (Agendar Entrevista)
  Manager --> (Registrar Evaluación)
  (Registrar Evaluación) --> (Calificar Candidato) : <<include>>
  (Registrar Evaluación) --> (Enviar Feedback)
}
@enduml
```

---

## Modelo de Datos

### Entidades y Atributos

| Entidad     | Atributo               | Tipo          |
|-------------|------------------------|---------------|
| Usuario     | id_usuario             | UUID          |
|             | nombre                 | VARCHAR(100)  |
|             | email                  | VARCHAR(150)  |
|             | rol                    | ENUM          |
| Vacante     | id_vacante             | UUID          |
|             | titulo                 | VARCHAR(100)  |
|             | descripcion            | TEXT          |
|             | fecha_creacion         | DATE          |
| Postulación | id_postulacion         | UUID          |
|             | id_candidato           | UUID          |
|             | id_vacante             | UUID          |
|             | estado                 | ENUM          |
| Entrevista  | id_entrevista          | UUID          |
|             | fecha                  | TIMESTAMP     |
|             | evaluador              | UUID          |

### Relaciones

```mermaid
erDiagram
  USUARIO ||--o{ VACANTE : crea
  VACANTE ||--o{ POSTULACION : tiene
  CANDIDATO ||--o{ POSTULACION : realiza
  POSTULACION ||--o{ ENTREVISTA : genera
  USUARIO ||--o{ ENTREVISTA : evalua
```

---

## Diseño del Sistema a Alto Nivel

El sistema sigue una arquitectura basada en microservicios con integración de componentes IA y almacenamiento distribuido. Un frontend en React se conecta a una API Gateway que enruta las solicitudes a los diferentes servicios, incluyendo autenticación, core ATS, motor IA y servicios externos.

```mermaid
graph TD
  FE[Frontend React]
  API[API Gateway]
  AUTH[Servicio de Autenticación]
  CORE[ATS Core]
  DB[(PostgreSQL)]
  REDIS[(Redis)]
  IA[Servicio IA]
  EMAIL[Notificaciones Email]

  FE --> API
  API --> AUTH
  API --> CORE
  CORE --> DB
  CORE --> REDIS
  CORE --> IA
  CORE --> EMAIL
```

---

## Diagrama C4

### Nivel 1 - Contexto
```mermaid
graph TB
  HR[Usuario RRHH]
  MGR[Manager Técnico]
  CAND[Candidato]
  ATS[ATS LTI Platform]
  HR --> ATS
  MGR --> ATS
  CAND --> ATS
```

### Nivel 2 - Contenedores
```mermaid
graph TD
  ATS[ATS Core Platform]
  Auth[Servicio de Autenticación]
  API[API Gateway]
  FE[Frontend React]
  DB[(PostgreSQL)]
  Redis[(Redis)]
  IA[Servicio IA (OpenAI)]

  ATS --> DB
  ATS --> Redis
  ATS --> IA
  API --> ATS
  FE --> API
  Auth --> DB
```

### Nivel 3 - Componentes Internos
```mermaid
graph TD
  ATS[ATS Core Platform]
  Vac[Vacantes Module]
  Post[Postulaciones Module]
  Eval[Evaluación Module]
  Match[Matching Engine]
  Notif[Notificaciones]

  ATS --> Vac
  ATS --> Post
  ATS --> Eval
  ATS --> Match
  ATS --> Notif
```