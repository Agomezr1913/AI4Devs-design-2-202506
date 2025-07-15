# Historias de Usuario

---

## Historia de Usuario 1: Filtrado inteligente de candidatos
**Como** reclutador,
**Quiero** que el sistema filtre automáticamente los candidatos según los requisitos de la vacante,
**Para** ahorrar tiempo en la preselección y enfocarme en los perfiles más relevantes.

**Criterios de aceptación:**
- El sistema filtra CVs según criterios configurables por el reclutador.
- El reclutador puede revisar y modificar los filtros en cualquier momento.
- Se muestra un listado ordenado por relevancia y se puede exportar a Excel.

**Prioridad:** Alta
**Dependencias:** Integración con base de datos de candidatos.
**Notas:** Incluir opción de feedback automático para mejorar el algoritmo de filtrado.

---

## Historia de Usuario 2: Postulación rápida de candidatos
**Como** candidato,
**Quiero** poder postularme a una vacante subiendo mi CV en el portal,
**Para** agilizar mi proceso de aplicación y destacar mis habilidades.

**Criterios de aceptación:**
- El candidato puede subir su CV en PDF.
- El sistema confirma la recepción de la postulación por email.
- El candidato puede consultar el estado de su postulación en el portal.

**Prioridad:** Alta
**Dependencias:** Integración con sistema de almacenamiento de archivos.

---

## Historia de Usuario 3: Evaluación colaborativa de candidatos
**Como** manager,
**Quiero** poder evaluar a los candidatos asignados y dejar feedback estructurado junto con el reclutador,
**Para** tomar decisiones de selección más objetivas y colaborativas.

**Criterios de aceptación:**
- El manager puede acceder a la ficha del candidato y dejar comentarios y puntuaciones.
- El feedback es visible para todos los evaluadores asignados a la vacante.
- El sistema notifica al reclutador cuando un manager completa una evaluación.

**Prioridad:** Media
**Dependencias:** Módulo de evaluaciones.

---

# Backlog Priorizado (MoSCoW)

Priorización de las historias de usuario principales del sistema LTI, usando la metodología MoSCoW:

| Historia de Usuario                         | Prioridad | Justificación                                                                                   |
|---------------------------------------------|-----------|-------------------------------------------------------------------------------------------------|
| Filtrado inteligente de candidatos          | Must (M)  | Es esencial para reducir la carga operativa de los reclutadores y mejorar la eficiencia.        |
| Postulación rápida de candidatos            | Must (M)  | Permite captar más candidatos y mejora la experiencia de usuario, clave para el éxito del sistema.|
| Evaluación colaborativa de candidatos       | Should (S)| Aporta valor añadido y mejora la calidad de la selección.     |
| Notificaciones a candidatos     | Could (C) | Mejora la comunicación y experiencia.        |

---

# Tickets Técnicos: Filtrado inteligente de candidatos

Desglose de la historia de usuario principal en tickets técnicos:

1. **Implementar lógica de filtrado configurable**
   - Descripción: Desarrollar el backend que permita definir y aplicar filtros configurables (por experiencia, habilidades, ubicación, etc.) sobre la base de datos de candidatos.
   - Criterios de aceptación:
     * El sistema permite crear y editar filtros desde la interfaz de usuario.
     * Los filtros se aplican correctamente y devuelven resultados relevantes.
     * El código está cubierto por tests unitarios.
   - Estimación de esfuerzo: 5 puntos de historia
   - Asignación sugerida: Equipo backend
   - Prioridad: Alta

2. **Crear interfaz de usuario para gestión de filtros**
   - Descripción: Desarrollar la pantalla en frontend donde el reclutador puede crear, modificar y guardar filtros personalizados para vacantes.
   - Criterios de aceptación:
     * El usuario puede añadir, editar y eliminar filtros desde la UI.
     * Los cambios se guardan y aplican en tiempo real.
     * La interfaz es responsiva, accesible y con las mejores prácticas de diseño UX/UI.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Equipo frontend
   - Prioridad: Alta

3. **Integrar filtrado con listado de candidatos**
   - Descripción: Conectar la lógica de filtrado con el listado de candidatos para que solo se muestren los que cumplen los criterios seleccionados.
   - Criterios de aceptación:
     * El listado de candidatos se actualiza automáticamente al aplicar un filtro.
     * El usuario puede ver el número total de candidatos filtrados.
     * El rendimiento es óptimo para grandes volúmenes de datos.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Fullstack
   - Prioridad: Alta

4. **Exportar resultados filtrados a Excel**
   - Descripción: Permitir la exportación del listado de candidatos filtrados a un archivo Excel descargable.
   - Criterios de aceptación:
     * El usuario puede descargar los resultados filtrados en formato .xlsx.
     * El archivo contiene todos los campos relevantes de los candidatos.
     * La exportación funciona en todos los navegadores soportados.
   - Estimación de esfuerzo: 2 puntos de historia
   - Asignación sugerida: Fullstack
   - Prioridad: Media

5. **Añadir feedback automático para mejorar el filtrado**
   - Descripción: Implementar un mecanismo para que el reclutador pueda marcar candidatos como relevantes o no, y que el sistema aprenda de este feedback para ajustar futuros filtrados.
   - Criterios de aceptación:
     * El usuario puede marcar candidatos como relevantes/no relevantes.
     * El sistema ajusta los filtros sugeridos en base al feedback recibido.
     * El feedback queda registrado para auditoría.
   - Estimación de esfuerzo: 5 puntos de historia
   - Asignación sugerida: Backend
   - Prioridad: Media

---

# Tickets Técnicos: Postulación rápida de candidatos

Desglose de la historia de usuario 2 en tickets técnicos:

1. **Implementar carga y almacenamiento de CV en PDF**
   - Descripción: Desarrollar el backend y la integración con el sistema de almacenamiento de archivos para recibir y guardar CVs en PDF.
   - Criterios de aceptación:
     * El candidato puede subir su CV en PDF desde la interfaz.
     * El archivo se almacena correctamente y es accesible para el reclutador.
     * Validación de formato y tamaño de archivo.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Backend + Infraestructura
   - Prioridad: Alta

2. **Desarrollar confirmación automática por email**
   - Descripción: Implementar el envío automático de email de confirmación al candidato tras la postulación.
   - Criterios de aceptación:
     * El sistema envía un email de confirmación al recibir la postulación.
     * El email contiene información relevante y es personalizable.
   - Estimación de esfuerzo: 2 puntos de historia
   - Asignación sugerida: Backend + Notificaciones
   - Prioridad: Alta

3. **Crear módulo de consulta de estado de postulación**
   - Descripción: Desarrollar la funcionalidad en el portal para que el candidato consulte el estado de su postulación.
   - Criterios de aceptación:
     * El candidato puede ver el estado actualizado de su postulación.
     * La información es clara y accesible desde el portal.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Frontend
   - Prioridad: Alta

---

# Tickets Técnicos: Evaluación colaborativa de candidatos

Desglose de la historia de usuario 3 en tickets técnicos:

1. **Desarrollar módulo de evaluación y feedback estructurado**
   - Descripción: Implementar la funcionalidad para que managers y reclutadores puedan dejar comentarios y puntuaciones en la ficha del candidato.
   - Criterios de aceptación:
     * El manager puede acceder a la ficha y dejar comentarios y puntuaciones.
     * El feedback es visible para todos los evaluadores asignados.
     * El feedback queda registrado para auditoría.
   - Estimación de esfuerzo: 5 puntos de historia
   - Asignación sugerida: Backend + Frontend
   - Prioridad: Alta

2. **Implementar notificaciones automáticas al reclutador**
   - Descripción: Desarrollar el sistema de notificaciones para avisar al reclutador cuando un manager completa una evaluación.
   - Criterios de aceptación:
     * El sistema envía una notificación automática al reclutador.
     * La notificación contiene información relevante y es trazable.
   - Estimación de esfuerzo: 2 puntos de historia
   - Asignación sugerida: Backend + Notificaciones
   - Prioridad: Media

3. **Crear historial de evaluaciones para auditoría**
   - Descripción: Implementar el registro y consulta de todas las evaluaciones realizadas para fines de auditoría y trazabilidad.
   - Criterios de aceptación:
     * El sistema almacena todas las evaluaciones realizadas.
     * El historial es accesible para usuarios autorizados.
   - Estimación de esfuerzo: 3 puntos de historia
   - Asignación sugerida: Backend
   - Prioridad: Media

---

# Estimación de Esfuerzo de los Tickets (Planning Poker)

Estimación de esfuerzo para los tickets técnicos del filtrado inteligente de candidatos, usando la serie de Fibonacci y justificación:

1. **Implementar lógica de filtrado configurable**
   - Estimación: 5 puntos de historia
   - Justificación: Requiere lógica de negocio, configuración dinámica y pruebas, pero es un caso común en sistemas ATS.

2. **Crear interfaz de usuario para gestión de filtros**
   - Estimación: 3 puntos de historia
   - Justificación: Implica desarrollo de UI y validaciones, pero sin lógica compleja.

3. **Integrar filtrado con listado de candidatos**
   - Estimación: 3 puntos de historia
   - Justificación: Es integración de componentes ya desarrollados.

4. **Exportar resultados filtrados a Excel**
   - Estimación: 2 puntos de historia
   - Justificación: Uso de librerías para exportación.

5. **Añadir feedback automático para mejorar el filtrado**
   - Estimación: 5 puntos de historia
   - Justificación: Requiere nuevo objeto de histórico de feedback y lógica de aprendizaje.

---

Estimación de esfuerzo para los tickets técnicos de la historia de usuario 2 (Postulación rápida de candidatos):

1. **Implementar carga y almacenamiento de CV en PDF**
   - Estimación: 3 puntos de historia
   - Justificación: Requiere integración con almacenamiento y validaciones, pero es funcionalidad estándar.

2. **Desarrollar confirmación automática por email**
   - Estimación: 2 puntos de historia
   - Justificación: Uso de servicios de notificación ya existentes.

3. **Crear módulo de consulta de estado de postulación**
   - Estimación: 3 puntos de historia
   - Justificación: Implica desarrollo de UI y consulta de datos, sin lógica compleja.

---

Estimación de esfuerzo para los tickets técnicos de la historia de usuario 3 (Evaluación colaborativa de candidatos):

1. **Desarrollar módulo de evaluación y feedback estructurado**
   - Estimación: 5 puntos de historia
   - Justificación: Requiere lógica de negocio, registro y visualización colaborativa.

2. **Implementar notificaciones automáticas al reclutador**
   - Estimación: 2 puntos de historia
   - Justificación: Uso de servicios de notificación ya existentes.

3. **Crear historial de evaluaciones para auditoría**
   - Estimación: 3 puntos de historia
   - Justificación: Requiere almacenamiento y consulta, pero es funcionalidad estándar.
---

# Estimación de Esfuerzo de los Tickets (Planning Poker)

Estimación de esfuerzo para los tickets técnicos del filtrado inteligente de candidatos, usando la serie de Fibonacci y justificación:

1. **Implementar lógica de filtrado configurable**
   - Estimación: 5 puntos de historia
   - Justificación: Requiere lógica de negocio, configuración dinámica y pruebas, pero es un caso común en sistemas ATS.

2. **Crear interfaz de usuario para gestión de filtros**
   - Estimación: 3 puntos de historia
   - Justificación: Implica desarrollo de UI y validaciones, pero sin lógica compleja.

3. **Integrar filtrado con listado de candidatos**
   - Estimación: 3 puntos de historia
   - Justificación: Es integración de componentes ya desarrollados.

4. **Exportar resultados filtrados a Excel**
   - Estimación: 2 puntos de historia
   - Justificación: Uso de librerías para exportación.

5. **Añadir feedback automático para mejorar el filtrado**
   - Estimación: 5 puntos de historia
   - Justificación: Requiere nuevo objeto de histórico de feedback y lógica de aprendizaje.