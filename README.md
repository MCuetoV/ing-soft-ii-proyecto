# ing-soft-ii-proyecto
Proyecto grupal del curso Ingeniería de Software II ciclo Verano 2026-0

MiniFlow – Especificación de Requerimientos del
Sistema (SRS)
1. Introducción
MiniFlow es una aplicación desarrollada en Java que permite diseñar y ejecutar
flujos de trabajo (workflows) compuestos por nodos interconectados, inspirada
en herramientas como n8n, pero con un alcance simplificado y académico.
El sistema se divide en dos módulos principales: - Módulo A: Diseñador de
Flujos (Workflow Builder) - Módulo B: Motor de Ejecución (Runtime)
MÓDULO A — Diseñador de Flujos (Workflow
Builder)
Requerimientos Funcionales (RF-A)
Gestión de workflows
• RF-A01. El sistema debe permitir crear un workflow indicando nombre y
descripción.
• RF-A02. El sistema debe permitir listar workflows existentes.
• RF-A03. El sistema debe permitir consultar el detalle completo de un
workflow.
• RF-A04. El sistema debe permitir editar los metadatos de un workflow.
• RF-A05. El sistema debe permitir eliminar un workflow junto con todos
sus nodos y conexiones.
Gestión de nodos
• RF-A6. El sistema debe permitir agregar un nodo a un workflow seleccio-
nando un tipo desde el catálogo.
• RF-A7. El sistema debe permitir editar la configuración de un nodo (ver
configuración de acciones por tipo de nodo).
• RF-A8. El sistema debe permitir duplicar (clonar) un nodo dentro del
mismo workflow.
• RF-A9. El sistema debe permitir eliminar un nodo y sus conexiones
asociadas.
• RF-A10. El sistema debe permitir listar los nodos de un workflow.
1
Configuración de acciones por tipo de nodo
• RF-A11. El sistema debe permitir definir la acción específica que realizará
un nodo según su tipo.
HTTP_REQUEST
• RF-A12. El sistema debe permitir configurar:
– método HTTP,
– URL,
– headers,
– query parameters,
– body (texto o JSON),
– timeout,
– número de reintentos,
– mapeo de respuesta al contexto. (detallar en reuniones con clientes)
COMMAND
• RF-A13. El sistema debe permitir configurar:
– comando a ejecutar,
– argumentos,
– variables de entorno (opcional),
– directorio de ejecución (opcional),
– timeout,
– captura de salida,
– mapeo de salida al contexto. (detallar en reuniones con cliente)
CONDITIONAL
• RF-A14. El sistema debe permitir definir:
– una condición basada en el contexto,
– operadores básicos (==, !=, >, <, contains),
– rutas de salida etiquetadas (TRUE / FALSE).
• RF-A15. El sistema debe permitir definir por nodo una política ante
error: STOP_ON_FAIL o CONTINUE_ON_FAIL.
Gestión de conexiones
• RF-A16. El sistema debe permitir crear conexiones entre nodos (origen
→ destino).
• RF-A17. El sistema debe permitir eliminar conexiones entre nodos.
• RF-A18. El sistema debe permitir definir conexiones etiquetadas para
nodos condicionales.
• RF-A19. El sistema debe impedir conexiones inválidas.
2
Validación del workflow
• RF-A20. El sistema debe permitir validar un workflow antes de su
ejecución.
• RF-A21. La validación debe comprobar que exista exactamente un nodo
START.
• RF-A22. La validación debe comprobar que no existan ciclos.
• RF-A23. La validación debe comprobar que todos los nodos sean alcanz-
ables desde START.
• RF-A24. La validación debe comprobar configuración mínima por tipo
de nodo.
• RF-A25. La validación debe comprobar reglas estructurales por tipo.
• RF-A26. El sistema debe devolver un reporte de validación detallado.
Importación y exportación
• RF-A27. El sistema debe permitir exportar un workflow completo en
formato JSON.
• RF-A28. El sistema debe permitir importar un workflow desde un JSON
válido.
Requerimientos No Funcionales (RNF-A)
• RNF-A01. El sistema debe estar implementado en Java 17 o superior.
• RNF-A02. El backend debe seguir una arquitectura por capas.
• RNF-A03. El sistema debe garantizar consistencia transaccional.
• RNF-A04. La UI debe permitir crear un workflow funcional en menos de
10 minutos.
• RNF-A05. El sistema debe ser extensible para nuevos tipos de nodo.
MÓDULO B — Motor de Ejecución (Runtime)
Requerimientos Funcionales (RF-B)
Ejecución
• RF-B01. El sistema debe permitir iniciar manualmente la ejecución de
un workflow validado.
• RF-B02. El sistema debe impedir ejecutar workflows inválidos.
• RF-B03. El sistema debe crear una entidad Run al iniciar una ejecución.
3
Motor
• RF-B04. El motor debe ejecutar nodos siguiendo las conexiones del
workflow.
• RF-B05. El motor debe mantener un contexto de ejecución compartido.
• RF-B06. Cada nodo debe poder leer y escribir datos en el contexto.
Ejecución por tipo de nodo
• RF-B07. El motor debe ejecutar nodos HTTP_REQUEST.
• RF-B08. El motor debe ejecutar nodos COMMAND.
• RF-B09. El motor debe ejecutar nodos CONDITIONAL.
Estados y errores
• RF-B10. El sistema debe registrar la ejecución de cada nodo como
StepRun.
• RF-B11. Cada StepRun debe registrar estado, timestamps, output y
errores.
• RF-B12. El sistema debe aplicar la política de error configurada por
nodo.
• RF-B13. El sistema debe soportar timeout en nodos HTTP y COM-
MAND.
• RF-B14. El sistema debe soportar reintentos en nodos HTTP.
Consulta y monitoreo
• RF-B15. El sistema debe permitir listar ejecuciones por workflow.
• RF-B16. El sistema debe permitir consultar el detalle completo de una
ejecución.
• RF-B17. El sistema debe permitir consultar logs por ejecución y por
nodo.
Requerimientos No Funcionales (RNF-B)
• RNF-B01. El sistema debe conservar el historial ante fallos.
• RNF-B02. El sistema debe registrar todos los cambios de estado.
• RNF-B03. El motor debe ser extensible para nuevos tipos de nodo.
• RNF-B04. El motor debe almacenar sus datos de la ejecución en un
archivo JSON o en una base de datos.
• RNF-B05. El sistema debe incluir pruebas unitarias críticas.
