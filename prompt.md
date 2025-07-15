
# prompts.md

Prompts usados para diseñar y documentar el sistema LTI (Lean Talent Intelligence), organizados por rol y etapa del proyecto. Cada prompt está diseñado para ejecutar directamente una tarea.

---

## Índice

1. [Product Manager – Investigación y análisis](#product-manager--investigación-y-análisis)
2. [UX/Research Designer – Validación de mercado](#uxresearch-designer--validación-de-mercado)
3. [Business Analyst – Casos de uso](#business-analyst--casos-de-uso)
4. [DBA – Modelado de datos](#dba--modelado-de-datos)
5. [Software Architect – Diseño del sistema](#software-architect--diseño-del-sistema)
6. [Arquitectura C4 – Profundización modular](#arquitectura-c4--profundización-modular)
7. [Documentador Técnico – Entrega final](#documentador-técnico--entrega-final)
8. [Historias de Usuario, Backlog y Tickets](#historias-de-usuario-backlog-y-tickets)

---

## Product Manager – Investigación y análisis

### Objetivo del rol
Identificar las funcionalidades prioritarias del sistema, comprender el valor que ofrece al negocio y sintetizar su modelo de negocio.

**Prompt 1**
Actúas como Product Manager Senior especializado en sistemas ATS. Diseña una primera versión del sistema LTI, detallando:
- Una descripción breve del software
- Los principales beneficios para el usuario (reclutadores, managers, candidatos)
- Las ventajas competitivas frente a ATS tradicionales
- Las funcionalidades clave ordenadas de mayor a menor prioridad

**Prompt 2**
Como experto en startups tecnológicas, genera un diagrama Lean Canvas en formato mermaid que describa el modelo de negocio del sistema LTI, incluyendo:
- Problemas
- Segmentos de clientes
- Propuesta de valor
- Canales
- Fuentes de ingreso
- Actividades clave
- Recursos clave
- Socios clave
- Estructura de costos

---

## UX/Research Designer – Validación de mercado

### Objetivo del rol
Analizar competidores y validar oportunidades del mercado.

**Prompt 3**
Actúa como analista de mercado en software de recursos humanos. Crea una tabla comparativa de los 5 sistemas ATS comerciales más usados, comparando funcionalidades como:
- Gestión de vacantes
- Matching automático
- Entrevistas en video
- IA para filtrado de CVs
- Analítica de procesos
- Integraciones externas

---

## Business Analyst – Casos de uso

### Objetivo del rol
Definir los flujos clave del sistema a través de casos de uso.

**Prompt 4**
Actúas como analista funcional. Define y describe 3 casos de uso principales del sistema LTI:
1. Publicar vacante
2. Postulación de candidatos
3. Evaluación y selección
Incluye objetivos, actores involucrados y pasos principales para cada caso.

**Prompt 5**
Genera un diagrama UML de casos de uso en formato `plantUML`, diferenciando entre:
- Candidato (usuario externo)
- Reclutador (usuario interno)
- Manager (usuario interno)
Aplica relaciones `<<include>>` y `<<extend>>` donde corresponda.

---

## DBA – Modelado de datos

### Objetivo del rol
Diseñar el modelo de datos con entidades, atributos y relaciones.

**Prompt 6**
Actúas como arquitecto de datos experto en diseño de modelos relacionales para sistemas ATS modernos.

Estoy construyendo un sistema llamado LTI (Lean Talent Intelligence), que incluye funcionalidades como publicación de vacantes, postulación de candidatos, evaluaciones, entrevistas y selección.

A partir de los requisitos ya definidos, necesito que diseñes el modelo de datos del sistema.

Incluye las siguientes entidades y define para cada una:
- Nombre de la entidad
- Lista de atributos con su tipo de dato (puedes usar pseudotipo: string, int, datetime, etc.)
- Relaciones con otras entidades (uno a muchos, muchos a muchos, etc.)

Estas son las entidades que debes incluir:

1. **Usuario**
   - `id` (int)
   - `nombre` (string)
   - `correo_electronico` (string)
   - `rol` (string: 'reclutador', 'manager', 'admin')

2. **Vacante**
   - `id` (int)
   - `titulo` (string)
   - `descripcion` (string)
   - `departamento` (string)
   - `ubicacion` (string)
   - `fecha_publicacion` (datetime)
   - `usuario_id` (int) → Relación con Usuario (publicada por)

3. **Candidato**
   - `id` (int)
   - `nombre` (string)
   - `email` (string)
   - `telefono` (string)
   - `cv_url` (string)

4. **Postulacion**
   - `id` (int)
   - `vacante_id` (int)
   - `candidato_id` (int)
   - `estado` (string: 'recibida', 'en revisión', 'entrevista', 'descartado', 'seleccionado')
   - `fecha_postulacion` (datetime)

5. **Entrevista**
   - `id` (int)
   - `postulacion_id` (int)
   - `fecha` (datetime)
   - `tipo` (string: 'video', 'presencial')
   - `notas` (string)

6. **Evaluacion**
   - `id` (int)
   - `postulacion_id` (int)
   - `evaluador_id` (int) → Relación con Usuario
   - `calificacion` (int)
   - `comentarios` (string)

Genera la estructura completa del modelo de datos e indica claramente todas las relaciones entre entidades.

Luego, crea un diagrama ER en formato Mermaid basado en este modelo, indicando claves primarias (PK), claves foráneas (FK), y relaciones entre tablas.

---

## Software Architect – Diseño del sistema

### Objetivo del rol
Proponer la arquitectura del sistema a nivel de componentes y servicios.

**Prompt 7**
Eres un arquitecto senior. Diseña el sistema LTI siguiendo una arquitectura de microservicios. Describe en texto:
- Frontend (web app)
- Backend (servicio de gestión de vacantes y postulaciones)
- Servicio de autenticación
- Módulo de IA para matching
- Servicio de notificaciones
- Base de datos relacional
- Integraciones con sistemas externos (correo, calendario, API de videoentrevistas)

Luego, genera un diagrama de arquitectura de alto nivel en formato Mermaid con todos los componentes anteriores y sus relaciones.

---

## Arquitectura C4 – Profundización modular

### Objetivo del rol
Visualizar la arquitectura del sistema desde múltiples niveles de abstracción.

**Prompt 8**
Genera un diagrama C4 **Nivel 1 (Contexto)** del sistema LTI. Incluye:
- Candidatos
- Reclutadores y Managers
- Sistema LTI
- Sistemas externos como correo, videollamadas y calendarios

Genera un diagrama C4 **Nivel 2 (Contenedores)** detallando:
- Web App (frontend)
- API Gateway
- Servicios internos (vacantes, postulaciones, IA)
- Sistema de autenticación
- Bases de datos
- Servicios de notificación
- Conexión con plataformas externas

Genera un diagrama C4 **Nivel 3 (Componentes)** para el contenedor "ATS Core", incluyendo:
- Módulo de gestión de vacantes
- Módulo de postulaciones
- Módulo de entrevistas
- Módulo de evaluaciones
- Módulo de matching con IA
- Módulo de notificaciones

---

## Documentador Técnico – Entrega final

### Objetivo del rol
Consolidar todos los artefactos en un documento único, claro y legible.

**Prompt 9**
Resume todo el diseño del sistema LTI en un documento Markdown con secciones:
1. Descripción del producto
2. Funcionalidades principales
3. Lean Canvas (diagrama)
4. Casos de uso + diagramas UML
5. Modelo de datos + diagrama ER
6. Diseño del sistema + diagrama
7. C4 niveles 1, 2 y 3

---

## Historias de Usuario, Backlog y Tickets

### Prompts para generación de User Stories, Backlog y Tickets de trabajo

A continuación se presentan los prompts utilizados para generar la documentación de User Stories, Backlog priorizado y descomposición técnica en tickets para el sistema LTI, siguiendo las mejores prácticas y el modelo de documentación del proyecto.

---

### Prompt 1: Generación de User Stories

```
Eres un analista de producto experto en metodologías ágiles y sistemas ATS. Basándote en la siguiente descripción del sistema LTI y su contexto, genera al menos 3 User Stories completas para los principales tipos de usuario (reclutador, manager, candidato), siguiendo el formato y ejemplos concretos del proyecto:

Contexto del sistema:
LTI (Lean Talent Intelligence) es un ATS de nueva generación que automatiza tareas de reclutamiento, facilita la colaboración en tiempo real y utiliza IA para mejorar la eficiencia de RRHH. Incluye publicación de vacantes, portal de candidatos, matching inteligente, agendamiento automatizado, evaluaciones colaborativas, integración con herramientas y panel analítico en tiempo real.

hu 1:
**Título:** Filtrado inteligente de candidatos
Como reclutador,
Quiero que el sistema filtre automáticamente los candidatos según los requisitos de la vacante,
Para ahorrar tiempo en la preselección y enfocarme en los perfiles más relevantes.
Criterios de aceptación:
- El sistema filtra CVs según criterios configurables por el reclutador.
- El reclutador puede revisar y modificar los filtros en cualquier momento.
- Se muestra un listado ordenado por relevancia y se puede exportar a Excel.
Prioridad: Alta
Dependencias: Integración con base de datos de candidatos.
Notas: Incluir opción de feedback automático para mejorar el algoritmo de filtrado.

hu 2:
**Título:** Postulación rápida de candidatos
Como candidato,
Quiero poder postularme a una vacante subiendo mi CV en el portal,
Para agilizar mi proceso de aplicación y destacar mis habilidades.
Criterios de aceptación:
- El candidato puede subir su CV en PDF.
- El sistema confirma la recepción de la postulación por email.
- El candidato puede consultar el estado de su postulación en el portal.
Prioridad: Alta
Dependencias: Integración con sistema de almacenamiento de archivos.

hu 3:
**Título:** Evaluación colaborativa de candidatos
Como manager,
Quiero poder evaluar a los candidatos asignados y dejar feedback estructurado junto con el reclutador,
Para tomar decisiones de selección más objetivas y colaborativas.
Criterios de aceptación:
- El manager puede acceder a la ficha del candidato y dejar comentarios y puntuaciones.
- El feedback es visible para todos los evaluadores asignados a la vacante.
- El sistema notifica al reclutador cuando un manager completa una evaluación.
Prioridad: Media
Dependencias: Módulo de evaluaciones.
Notas: El feedback debe quedar registrado para auditoría.
```

---

### Prompt 2: Generación y Priorización del Backlog

```
Actúa como Product Owner Agile. Tienes la siguiente lista de User Stories para el sistema LTI. Priorízalas usando la metodología MoSCoW (Must, Should, Could, Won't) y justifica brevemente la prioridad asignada a cada una. Devuelve el backlog ordenado y justificado.

User Stories:
1. Filtrado inteligente de candidatos
   Como reclutador, quiero que el sistema filtre automáticamente los candidatos según los requisitos de la vacante, para ahorrar tiempo en la preselección y enfocarme en los perfiles más relevantes.
2. Postulación rápida de candidatos
   Como candidato, quiero poder postularme a una vacante subiendo mi CV, para agilizar mi proceso de aplicación y destacar mis habilidades.
3. Evaluación colaborativa de candidatos
   Como manager, quiero poder evaluar a los candidatos asignados y dejar feedback estructurado junto con el reclutador, para tomar decisiones de selección más objetivas y colaborativas.

Formato de respuesta:
1. Filtrado inteligente de candidatos - Prioridad: Must (M) - Justificación: Es esencial para reducir la carga operativa de los reclutadores y mejorar la eficiencia del proceso de selección.
2. Postulación rápida de candidatos - Prioridad: Must (M) - Justificación: Permite captar más candidatos y mejora la experiencia de usuario, siendo clave para el éxito del sistema.
3. Evaluación colaborativa de candidatos - Prioridad: Should (S) - Justificación: Aporta valor añadido y mejora la calidad de la selección, pero puede implementarse tras las funcionalidades básicas.
```

---

### Prompt 3: Generación de Tickets Técnicos a partir de una User Story

```
Eres Scrum Master y analista técnico. Elige la siguiente User Story y desglósala en tickets de trabajo técnicos siguiendo la plantilla y ejemplos concretos:

User Story seleccionada:
Filtrado inteligente de candidatos
Como reclutador, quiero que el sistema filtre automáticamente los candidatos según los requisitos de la vacante, para ahorrar tiempo en la preselección y enfocarme en los perfiles más relevantes.

Tickets técnicos:

1. Implementar lógica de filtrado configurable
   - Descripción: Desarrollar el backend que permita definir y aplicar filtros configurables (por experiencia, habilidades, ubicación, etc.) sobre la base de datos de candidatos.
   - Criterios de aceptación:
     * El sistema permite crear y editar filtros desde la interfaz de usuario.
     * Los filtros se aplican correctamente y devuelven resultados relevantes.
     * El código está cubierto por tests unitarios.
   - Estimación de esfuerzo: 5 puntos de historia
   - Asignación sugerida: Equipo backend
   - Prioridad: Alta

2. Crear interfaz de usuario para gestión de filtros
   - Descripción: Desarrollar la pantalla en frontend donde el reclutador puede crear, modificar y guardar filtros personalizados para vacantes.
   - Criterios de aceptación:
     * El usuario puede añadir, editar y eliminar filtros desde la UI.
     * Los cambios se guardan y aplican en tiempo real.
     * La interfaz es responsiva, accesible y con las mejores practicas de diseño ux/ui.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Equipo frontend
   - Prioridad: Alta

3. Integrar filtrado con listado de candidatos
   - Descripción: Conectar la lógica de filtrado con el listado de candidatos para que solo se muestren los que cumplen los criterios seleccionados.
   - Criterios de aceptación:
     * El listado de candidatos se actualiza automáticamente al aplicar un filtro.
     * El usuario puede ver el número total de candidatos filtrados.
     * El rendimiento es óptimo para grandes volúmenes de datos.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Fullstack
   - Prioridad: Alta

4. Exportar resultados filtrados a Excel
   - Descripción: Permitir la exportación del listado de candidatos filtrados a un archivo Excel descargable.
   - Criterios de aceptación:
     * El usuario puede descargar los resultados filtrados en formato .xlsx.
     * El archivo contiene todos los campos relevantes de los candidatos.
     * La exportación funciona en todos los navegadores soportados.
   - Estimación de esfuerzo: 2 puntos de historia
   - Asignación sugerida: Fullstack
   - Prioridad: Media

5. Añadir feedback automático para mejorar el filtrado
   - Descripción: Implementar un mecanismo para que el reclutador pueda marcar candidatos como relevantes o no, y que el sistema aprenda de este feedback para ajustar futuros filtrados.
   - Criterios de aceptación:
     * El usuario puede marcar candidatos como relevantes/no relevantes.
     * El sistema ajusta los filtros sugeridos en base al feedback recibido.
     * El feedback queda registrado para auditoría.
   - Estimación de esfuerzo: 5 puntos de historia
   - Asignación sugerida: Backend + IA
   - Prioridad: Media
```

---

### Prompt 4: Estimación de Esfuerzo de los Tickets

```
Actúa como equipo de desarrollo en una sesión de Planning Poker. Estima el esfuerzo de los siguientes tickets usando la serie de Fibonacci (1, 2, 3, 5, 8, 13, 21). Justifica brevemente la estimación de cada ticket.

Tickets:
1. Implementar lógica de filtrado configurable
   - Estimación: 5 puntos de historia
   - Justificación: Requiere lógica de negocio, configuración dinámica y pruebas, pero es un caso común en sistemas ATS.

2. Crear interfaz de usuario para gestión de filtros
   - Estimación: 3 puntos de historia
   - Justificación: Implica desarrollo de UI y validaciones, pero sin lógica compleja.

3. Integrar filtrado con listado de candidatos
   - Estimación: 3 puntos de historia
   - Justificación: Es integración de componentes ya desarrollados.

4. Exportar resultados filtrados a Excel
   - Estimación: 2 puntos de historia
   - Justificación: Uso de librerías para exportación.

5. Añadir feedback automático para mejorar el filtrado
   - Estimación: 5 puntos de historia
   - Justificación: Requiere nuevo objeto de hitorico de feedback
```