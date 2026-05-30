Estoy trabajando en una rama de git, de Develop.

Revisa todos los commits que he hecho y analiza los cambios.
Con la finalidad de crear 3 documentaciones Tecnica, funcional y Testeo (la de testeo es para que otra persona pueda probar que todo funciona correctamente y como se espera).

Esas 3 documentaciones guardalas en archivos .md.
Que esten en la carpeta Raiz del proyecto dentro de una Carpeta llamad "Docs".
El nombre de los archivos debería contener el nombre de la incidenica del Jira , que esta como nombre en el nombre de la rama.

Es importante que hagas revises la diferencia de commits entre develop y esta rama. 
Porque la finalidad es documentar que cambios se han efectuado.

Haz un plan para hacer esto , y pregúntame todo lo que necesites para poder hacer el plan correctamente.

Todo en español



---

Estoy trabajando en la rama de git [NOMBRE_RAMA] (por ejemplo feature/TICKET-1234-Descripcion).
Quiero que analices los cambios de esta rama respecto a [RAMA_BASE] (normalmente develop) y generes 4 documentos de documentación en la carpeta Docs/ de la raíz del proyecto. Los archivos deben llamarse:
•	[ID_TICKET]-[NombreRama]-Tecnica.md
•	[ID_TICKET]-[NombreRama]-Funcional.md
•	[ID_TICKET]-[NombreRama]-Testeo.md
•	[ID_TICKET]-[NombreRama] - Resumen del desarrollo.md
Requisitos:
•	Ejecuta git log [RAMA_BASE]..HEAD --oneline y git diff [RAMA_BASE]...HEAD para obtener los cambios reales.
•	El documento Técnico debe detallar cada cambio por capa (datos, servicios, controladores, UI), con fragmentos de código antes/después donde sea relevante.
•	El documento Funcional debe explicar el impacto para el usuario final, los cambios de seguridad y las correcciones de comportamiento, sin jerga técnica excesiva.
•	El documento de Testeo debe contener casos de prueba manuales con pasos detallados y una tabla de registro de ejecución. Las pruebas son manuales en entorno local (Debug). Solo incluir los pasos, no datos de prueba concretos.
•	El documento Resumen del desarrollo debe incluir: contexto y decisiones tomadas, tabla de todos los archivos modificados con el motivo, los cambios más relevantes destacados, y referencia a los otros 3 documentos generados. Sin sección de pasos ni Understanding.
•	Usa la misma plantilla de estructura en todos los documentos (índice, secciones estándar, tabla final).
•	Todo en español.




Lo que necesitas tener preparado para que funcione bien:
•	Git accesible en el PATH del terminal (o Visual Studio Agent Mode activo)
•	Rama base conocida (develop, main, etc.)
•	ID del ticket visible en el nombre de la rama