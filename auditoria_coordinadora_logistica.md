# Taller: Auditoría de Sistemas

**Integrante:** Juan Esteban López Montoya  
**Asignatura:** Auditoría de Sistemas (ET0114) – Sesión 3  
**Fecha de entrega:** 16 de septiembre de 2026

---

## Organización y Contexto

**Organización elegida:** Coordinadora Mercantil S.A.

Coordinadora Mercantil es una empresa de logística que opera en Colombia. Maneja sistemas de seguimiento de envíos, gestión de almacenes, plataformas de cotización online, integración con clientes, y bases de datos de operaciones y transacciones. El contexto específico de esta auditoría son los procesos de despliegue de código y la gestión de cambios técnicos en los sistemas de información críticos.

El problema recurrente observado es: cuando se despliegan nuevos proyectos o ajustes pequeños, funcionalidades existentes se rompen generando cascadas de reportes de usuarios. El origen no está en falta de documentación, sino en dos áreas críticas:

1. **Gestión de cambios débil:** Los despliegues no tienen una evaluación clara de impacto antes de pasar a producción. No se valida si un cambio afectará otras funcionalidades, especialmente en sistemas integrados como seguimiento de envíos o gestión de almacenes.

2. **Falta de gobernanza técnica:** Cada proyecto define su propia arquitectura, parámetros de configuración y decisiones técnicas de forma aislada. Cuando algo falla, no hay claridad sobre si es un problema del proyecto o si un parámetro no está estandarizado. No existe un órgano de gobernanza que comunique estándares ni que audite su cumplimiento. Frases como "no lo conocía, hay que hablarlo con el PM" son síntoma de esta ausencia de gobernanza.

La auditoría se enfoca en responder: ¿hay un proceso estructurado para despliegues que considere impacto en sistemas dependientes? ¿existe una gobernanza clara sobre decisiones técnicas que asegure estandarización y comunicación entre equipos?

---

## Marcos de Auditoría Elegidos

Se aplicarán dos marcos en este orden:

1. **ITIL v4** – Gestión de cambios y despliegues
2. **COBIT 2019** – Gobernanza de decisiones técnicas y estandarización

### ITIL v4 – Gestión de Cambios y Despliegues

ITIL define procesos de Change Management y Release Management que son esenciales para auditar despliegues seguros. En Coordinadora, cada despliegue debería incluir:

- Evaluación de impacto: ¿qué sistemas dependientes podrían verse afectados?
- Plan de pruebas que valide funcionalidades existentes, no solo las nuevas
- Aprobación formal antes de pasar a producción
- Plan de rollback documentado en caso de fallo
- Comunicación y trazabilidad completa del cambio

El problema actual es que los despliegues no tienen una evaluación clara de impacto. Un ajuste pequeño en un proyecto rompe funcionalidades en otro porque no hay validación de dependencias. ITIL proporciona la estructura de control que falta.

### COBIT 2019 – Gobernanza de Decisiones Técnicas

COBIT define procesos de gobernanza que permiten auditar si existe control en las decisiones técnicas y si los estándares son comunicados y respetados. Específicamente, COBIT cubre:

- **APO02 (Estrategia):** Define cómo se toman decisiones tecnológicas y qué estándares se establecen entre proyectos
- **BAI07 (Gestión de cambios):** Complementa a ITIL con evaluación de impacto de cambios en la estrategia de TI
- **EDM04 (Evaluación de riesgos):** Valida que los cambios se evalúen en función de riesgo, no solo de viabilidad técnica

El segundo problema es la falta de estándares técnicos compartidos entre proyectos. Cuando cada proyecto define su propia arquitectura, parámetros de configuración y decisiones de diseño de forma aislada, surgen vacíos: parámetros que existen en un proyecto pero no en otro, decisiones arquitectónicas no documentadas, o desconocimiento entre equipos de cómo otros proyectos están construidos.

COBIT asegura que exista gobernanza sobre esas decisiones: que se documenten, se comuniquen entre equipos, y se audite si se cumplen. Se aplica después de ITIL porque una vez exista un proceso robusto de despliegues, se necesita garantizar que esos despliegues respeten los estándares y decisiones técnicas establecidas a nivel organizacional.

---

## Evidencia Propuesta por Marco

### ITIL v4 – Gestión de Cambios y Despliegues

**Evidencia 1: Análisis de Impacto en Despliegues**

Se solicita el registro de despliegues de los últimos 3 meses. Para cada uno debe constar:
- Qué cambios o proyecto se desplegó
- Matriz de impacto: qué otros sistemas o funcionalidades podrían verse afectados
- Pruebas realizadas en funcionalidades existentes (no solo en las nuevas)
- Quién aprobó el despliegue
- Resultado: si hubo incidentes post-despliegue

Se revisan 5-10 despliegues al azar. Se busca evidencia de que antes de pasar a producción se validó: ¿rompe esto algo que ya funcionaba? Si la mayoría de despliegues no tiene análisis de impacto documentado, hay ausencia de un proceso estructurado.

**Evidencia 2: Plan de Reversión y Gestión de Incidentes**

Se solicita documentación sobre qué ocurre cuando un despliegue causa problemas:
- Procedimiento documentado para hacer rollback
- Registro de al menos dos incidentes en los últimos 6 meses: qué se desplegó, qué funcionó mal, cuánto tiempo tardó en revertirse
- Si hay patrones: despliegues pequeños que rompen funcionalidades grandes (síntoma de falta de análisis de impacto)

### COBIT 2019 – Gobernanza de Decisiones Técnicas

**Evidencia 1: Política de Estándares Técnicos y Plan de Gobernanza**

Se solicita evidencia de que existe una política documentada sobre estándares técnicos:
- Documento que defina qué estándares deben cumplir todos los proyectos (configuración, versionamiento, patrones de código, infraestructura)
- Órgano de gobernanza responsable de revisar y aprobar decisiones técnicas (comité de arquitectura, arquitecto empresarial)
- Actas o registros de decisiones: cuándo se toman, quién participa, cómo se comunican
- Mecanismo para comunicar cambios en estándares a todos los equipos

Si no existe política documentada o si no hay órgano responsable, hay ausencia de gobernanza.

**Evidencia 2: Evaluación de Impacto Estratégico en Cambios**

Se solicita evidencia de que los cambios son evaluados no solo técnicamente, sino en función de alineación con estándares y riesgo organizacional:
- Registro de cambios recientes y su evaluación: ¿se evaluó si respeta estándares actuales? ¿Si no, por qué?
- Ejemplos donde se detectó: "Este proyecto no sigue estándar X, decisión documentada y aprobada por arquitectura"
- Instancias de cambios rechazados porque no se alineaban con estándares establecidos

Esto muestra si hay gobernanza real sobre decisiones técnicas, no solo adocuados administrativos.

---

## Justificación de la Selección

El enfoque de esta auditoría responde a los problemas específicos observados en Coordinadora.

**ITIL v4** se aplica primero porque el problema inmediato es el proceso de despliegues. Cuando un cambio pequeño rompe funcionalidades grandes, significa que no hay un análisis de impacto previo. No se valida qué depende de qué. ITIL proporciona la estructura formal para gestionar cambios de forma ordenada: evaluación de riesgo, pruebas de regresión, aprobación, trazabilidad.

**COBIT 2019** se aplica después porque una vez exista un proceso de despliegues estructurado, se necesita gobernanza sobre las decisiones técnicas que se toman. El problema de vacíos entre proyectos (parámetros no estandarizados, desconocimiento de decisiones técnicas previas) es un problema de gobernanza de arquitectura. COBIT audita si existe un órgano responsable, si se comunican decisiones, si se evalúa impacto estratégico de cambios técnicos, y si se audita cumplimiento de estándares.

En conjunto, permiten auditar si existe control en dos frentes: el proceso de cambios es seguro (ITIL), y existe gobernanza clara sobre decisiones técnicas que hacen los sistemas predecibles y mantenibles (COBIT).
