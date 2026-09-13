# Taller: Auditoría de Sistemas

**Integrante:** Juan Esteban López Montoya  
**Asignatura:** Auditoría de Sistemas (ET0114) – Sesión 3  
**Fecha de entrega:** 16 de septiembre de 2026

---

## Organización y Contexto

**Organización elegida:** Coordinadora Mercantil S.A.

Coordinadora es una empresa de servicios financieros que opera en Colombia. Maneja transacciones entre clientes, bases de datos con información sensible, y plataformas online de acceso para usuarios. Trabajo como Analista en Mesa de Ayuda, y desde esa posición veo de forma directa los problemas que llegan desde producción.

El contexto específico que auditoría es la calidad del software que se desarrolla internamente. Hay un equipo que construye nuevas funcionalidades, y existe un riesgo recurrente: cambios que llegan a producción sin pruebas claras, sin revisión de código, y a veces sin documentación. Eso resulta en errores que ven los usuarios, datos que se pueden perder, y confianza que se quiebra. En una empresa financiera, eso es crítico.

La pregunta de auditoría es simple: ¿cómo se asegura que el software que se escribe es de buena calidad antes de que llegue a los usuarios?

## Marcos de Auditoría Elegidos

Se aplicarán dos marcos en este orden:

1. **ITIL v4** – Gestión de cambios
2. **ISO/IEC 27001** – Seguridad en desarrollo de software

### ITIL v4 – Gestión de Cambios

ITIL define un proceso llamado Change Management que es central para auditar la calidad del software. En Coordinadora, cada cambio que se hace a un sistema (actualización, corrección, nueva función) debería pasar por este proceso:

- Quién solicita el cambio y por qué
- Evaluación de riesgos: qué puede fallar si se implementa
- Pruebas en ambiente de desarrollo antes de producción
- Aprobación de un responsable
- Documentación del cambio

El problema observado es que muchos cambios llegan a producción sin una trazabilidad clara o sin que se prueben adecuadamente. ITIL proporciona la estructura para auditar si existe un proceso real de cambios.

### ISO/IEC 27001 – Seguridad en Desarrollo

ISO/IEC 27001 incluye controles sobre desarrollo seguro de software. No solo importa que el código funcione, sino que sea seguro, especialmente cuando maneja datos de clientes.

Esto incluye validaciones de entrada (para prevenir inyecciones SQL), encriptación de datos en tránsito, registro de accesos a información sensible, y protección del código fuente. En Coordinadora, los errores de seguridad en código pueden exponer datos de clientes, lo que es un riesgo regulatorio y de confianza.

Se aplica después de ITIL porque primero se necesita un proceso de cambios ordenado, y luego garantizar que dentro de ese proceso hay controles de seguridad.

## Evidencia Propuesta por Marco

### ITIL v4 – Gestión de Cambios

**Evidencia 1: Registro de Cambios**

Se solicita el log de cambios de los últimos tres meses. Debe contener para cada cambio:
- Quién solicitó el cambio y cuál es su razón
- Cuándo se ejecutó y en qué ambiente se probó (desarrollo, staging, producción)
- Quién autorizó la implementación
- Resultado: si funcionó correctamente o si hubo un incidente

Se revisan entre 5 y 10 cambios al azar. Si la mayoría no tiene trazabilidad clara o no hay evidencia de pruebas antes de producción, hay un problema de proceso.

**Evidencia 2: Procedimiento de Reversión de Cambios**

Se solicita la documentación que existe sobre qué hacer si un cambio causa un problema en producción. Debe incluir:
- Pasos documentados para revertir un cambio
- Al menos un ejemplo real en los últimos 6 meses de un cambio que se revirtió
- Cuánto tiempo tomó resolver el problema
- Qué se aprendió del incidente

### ISO/IEC 27001 – Seguridad en Desarrollo

**Evidencia 1: Política de Revisión de Código**

Se solicita evidencia de que existe una política de revisión de código antes de pasar a producción. Esto incluye:
- Documento que establece que todo código debe ser revisado por otro desarrollador
- Registros o logs en el sistema de control de versiones que muestren revisiones realizadas
- Ejemplos de revisiones de código recientes: quién revisó, qué problemas encontró, cómo se corrigieron

**Evidencia 2: Pruebas de Seguridad en Código**

Se solicita evidencia de que hay pruebas de seguridad para el código que entra en producción:
- Documentación de validaciones de entrada implementadas
- Herramientas de análisis de código utilizadas (ej: SonarQube, Checkmarx)
- Registro de vulnerabilidades encontradas en los últimos 6 meses y cómo se resolvieron

## Justificación de la Selección

El enfoque de esta auditoría es pragmático. En Coordinadora, los problemas más visibles en calidad de software vienen de dos áreas: falta de un proceso ordenado para cambios (lo que cubre ITIL) y ausencia de revisiones de seguridad en código (lo que cubre ISO/IEC 27001).

ITIL se aplica primero porque sin un proceso de gestión de cambios, no hay base sobre la cual implementar controles adicionales. ISO/IEC 27001 se aplica después porque se necesita garantizar que dentro del proceso de cambios exista un enfoque de seguridad desde el desarrollo.

Juntos, estos marcos permiten auditar si el software que llega a producción cumple con dos criterios esenciales: que fue sometido a un proceso ordenado, y que fue revisado tanto funcionalmente como en términos de seguridad.
