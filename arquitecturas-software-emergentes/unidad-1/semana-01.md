# Semana 1: Software Architecture Review

## Recordando

- **Microkernel**: La base es igual, pero agrega extensiones como capas (plugins).
- **ADR:** Registro de decisiones arquitectónicas.
- **Trade-off en arquitectura:** Sacrificios de atributos de calidad según priorización. Ejemplo: priorizar seguridad, pero como resultado se debe sacrificar rendimiento.
- **Monolito clásico:** las funcionalidades que comparten tema pueden no estar agrupadas.
- Metodologías para sustentar arquitectura de software: Attribute-Driven Design (ADD), Domain-Driven Design (DDD), Event-Driven Design (EDD).
- Descomposición monolítica: por capacidad (usa juicio experto) y por dominio (DDD).
- **Deuda técnica:** similar a una deuda financiera, si está a tiempo, no genera problemas; pero, cuando se deja sin trabajar por completo (documentar, probar, fuera de tiempo, etc.), se empiezan a ver problemas.

## Introducción

### Punto de partida

- La arquitectura no es solo el dibujo, sino que sirve para comunicar y representar decisiones y perspectivas.
- La arquitectura conecta necesidades y soluciones.
- Toda arquitectura responde a un propósito -> Resultado que orienta prioridades, inversiones y decisiones estructurales.

### Elementos comunes

- **Las restricciones delimitan el espacio de la solución:** presupuesto, disponibilidad del personal, legislación, privacidad, software legacy, plazos de entrega, contratos, estándares de seguridad, tecnología, etc.
- **Los atributos de calidad convierten expectativas en prioridades:** seguridad, disponibilidad, rendimiento, mantenibilidad, escalabilidad, usabilidad, interoperabilidad.
- **Las vistas adaptan la arquitectura a cada audiencia:** cada vista (representaciones) responde a una pregunta concreta y omite detalles que no ayudan a su lector.

### Arquitectura Empresarial

- La Arquitectura Empresarial alinea estrategia y capacidades de negocio.
- **La empresa se entiende mediante dominios conectados:** negocio, información, aplicaciones, tecnología.
- **La Arquitectura Empresarial produce dirección y coherencia:** arquitecturas objetivo, hoja de ruta.

### Arquitectura de Software

- **Define estructuras fundamentales:** incluye principios, restricciones, mecanismos y razones; conecta requisitos con atributos de calidad; debe poder evaluarse mediante escenarios.
- **Integra función, calidad y restricciones:** construcción (estructuras, responsabilidades, contratos, datos, tecnologías) y evolución (modularidad, compatibilidad, pruebas, observabilidad y costo del cambio).

### Decisiones de Software

- **La descomposición define los límites principales:** monolito modular, microservicios, capas, dominios y módulos, funciones.
- **La arquitectura de datos define propiedad y consistencia:** propiedad de datos por dominio o servicio; almacenamiento, caché, replicación; migraciones, compatibilidad.
- **Seguridad y despliegue atraviesan toda la solución:** seguridad (autenticación, autorización, secretos, etc.) y despliegue (procesos, contenedores, nodos, escalado).
- **La evolución exige decisiones explícitas:** modularidad para contener el impacto de los cambios; versionado y compatilibilidad de APIs; pruebas automáticas.

### Drivers Arquitectónicos

- **Los drivers son las fuerzas que más condicionan la arquitectura:** negocio (objetivos, valor, tiempo y costo); funcionalidad crítica; atributos de calidad; restricciones; interesados.
- **El escenario obliga a decidir sobre calidad y riesgo:** control de concurrencia; escalado y capacidad; consistencia y límites; monitoreo; resiliencia y recuperación.

### Relación entre arquitecturas

- **Los tres niveles se complementan y operan con alcances distintos:** Empresa (estrategia, capacidades) -> Sistema (personas, procesos y tecnología) -> Software (productos y componentes)

## Vistas y estructuras arquitectónicas

### Conceptos fundamentales

#### Estructura

- Estructura -> Lo que existe (Código, Runtime, Infraestructura).
- **Elementos reales:** archivos, clases, procesos, hilos, servidores y esquemas.
- Se forma al escribir, compilar, empaquetar, ejecutar y desplegar el software.

#### Vista

- Vista -> Lo que mostramos (Con propósito y audiencia).
- Puede ser gráfica, textual, tabular o una combinación.
- Se diseña para responder preguntas de una o más stakeholders.
- Representa una o varias estructuras.

### Modelo SEI

- **El SEI clasifica las estructuras en tres familias:** Módulo (Código en reposo); Componentes y Conectores (runtime / ejecución); Asignación (infraestructura).
- **Las tres familias responden preguntas complementarias:** Módulo (¿Cómo se organiza el código para desarrollarlo y mantenerlo?) / Componente y Conector (¿Qué elementos ejecutan trabajo y cómo intercambian información?) / Asignación (¿Dónde se almacena, instala y ejecuta el software?)

#### Estructuras de Módulo

*¿Cómo está organizado el código fuente?*

- **Elementos:** clases, interfaces, paquetes, módulos y capas.
- **Objetivo:** controlar responsabilidades, visibilidad, acoplamiento y evolución.
- **Vistas típicas:** clases, paquetes, módulos y capas.
- **Ejemplos:** Matrícula, Facturación, Inventarios, Usuarios o Reportes.
- El monolito modular conserva un único despliegue.

#### Componente y Conector

*¿Dónde reside y se ejecuta cada parte?*

- **Componentes:** procesos, servicios activos, hilos, instancias y conexión a base de datos.
- **Conectores:** llamadas a métodos, HTTP, sockets, JDBC, eventos, pipes y colas.

### Modelo 4+1

#### Vista lógica

*Explica el dominio y la funcionalidad. Muestra abstracciones que soportan los requisitos del usuario.*

- **Stakeholders:** Usuarios, analistas y desarrolladores.
- **Enfoque:** Conceptos del dominio como Estudiante, Curso y Matrícula.
- **Estructura:** Principalmente la estructura de módulo y colaboraciones lógicas.
- **Diagramas:** Clases, objetos e interacción cuando aportan claridad.
- **Pregunta:** ¿Qué conceptos y responsabilidades realizan la funcionalidad?

#### Vista de desarrollo

*Explica la organización del código.*

- **Stakeholders:** Programadores y responsables de configuración.
- **Enfoque:** Paquetes, módulos, librerías y reglas de capas.
- **Estructura:** Estructura de módulo entre ellas, las unidades de implementación y dependencias.
- **Diagramas:** Paquetes, módulos, capas y dependencias.
- **Pregunta:** ¿Cómo se divide el trabajo y cómo se compila el sistema?

#### Vista de procesos

*Explica comportamiento y concurrencia. Hace visibles rendimiento, sincronización y manejo de fallos.*

- **Stakeholders:** Arquitectos, integradores y especialistas en rendimiento.
- **Enfoque:** Procesos, hilos, comunicación, coordinación y fallos.
- **Estructura:** Componente y conector.
- **Diagramas:** Secuencia, actividad y comunicación.
- **Pregunta:** ¿Qué ocurre cuando múltiples solicitudes se ejecutan?

#### Vista de despliegue

*Conecta software e infraestructura. Permite operar el sistema en un entorno concreto.*

- **Stakeholders:** Ingenieros de sistemas, redes y operaciones.
- **Enfoque:** Distribución de artefactos, procesos, datos y enlaces.
- **Estructura:** Asignación entre software y nodos.
- **Diagramas:** Despliegue UML y topologías de infraestructura.
- **Pregunta:** ¿Dónde se ejecuta y qué ocurre si un nodo falla?

#### Vista de casos de uso o de escenarios

*La vista de escenarios valida la coherencia del conjunto. El +1 demuestra que las otras vistas colaboran para cumplir casos reales.*

- **Escenario:** el alumno intenta matricularse en un curso sin vacantes.
- **Vista lógica:** reglas de Curso, Matrícula y disponibilidad.
- **Vista de desarrollo:** módulos y paquetes responsables.
- **Vista de procesos:** secuencia, concurrencia y control de cupos.
- **Vista de despliegue:** nodos, base de datos y rutas de comunicación.
