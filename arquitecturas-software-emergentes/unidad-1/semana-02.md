# Semana 2: Architecture Design Review

## Attribute-Driven Design

### Definición de ADD

- El diseño de la arquitectura es llevada a cabo mediante una serie de rondas a través del proyecto de desarrollo de software.
- Dentro de las rondas de diseño, una serie de iteraciones de diseño es ejecutada.
- La característica más importante de ADD es que provee una guía detallada del paso a paso de las tareas a ejecutar dentro de las iteraciones.

### Drivers Arquitectónicos

- **Design Purpose:** Para qué se está diseñando la arquitectura, objetivos de negocio, etc.
- **Primary Functionality:** Aquellas historias de usuario que sobresalen en importancia y que son capaces de modificar la arquitectura de software para su funcionamiento.
- **Quality Attributes:** Referidos también a los requisitos no funcionales que definen cómo debe comportarse el sistema.
- **Architectural Concerns:** Se refiere a las expectativas o requisitos por parte de los stakeholders del proyecto.
- **Constraints:** Son aquellos aspectos o decisiones que limitan la arquitectura de software. Por ejemplo, la elección de una tecnología o estilo arquitectónico.

### ADD Steps

- **Paso 1:** Revisar las entradas.
- **Paso 2:** Establecer el objetivo de la iteración al seleccionar drivers.
- **Paso 3:** Escoger uno o más elementos del sistema para refinar.
- **Paso 4:** Escoger uno o más conceptos de diseño que satisfagan los drivers seleccionados.
- **Paso 5:** Instanciar elementos arquitectónicos, asignar responsabilidades y definir interfaces.
- **Paso 6:** Dibujar las vistas y registrar las decisiones arquitectónicas.
- **Paso 7:** Realizar el análisis el diseño actual y revisar el objetivo de la iteración y el logro del propósito del diseño.

## Domain-Driven Design

### Cuándo sí y cuándo no

- Conviene cuando es un dominio complejo, con múltiples áreas, conocimientos, reglas críticas y colaboración constante con expertos.
- Puede ser excesivo para un CRUD pequeño, página informativa, formulario básico, etc.

### Subdominios

- **Core:** Forman la sección especial del software. Es aquella que genera valor en la solución.
- **Supporting:** No generan valor al negocio directamente, pero lo apoyan con reglas particulares.
- **Generic:** Posee una capacidad común que puede comprarse o integrarse. Por ejemplo: identidad, SMS, correo.

### Lenguaje Ubicuo

- Aparece en conversaciones, historias de usuario y documentación.
- Se refleja en clases, métodos, eventos y pruebas.
- Se actualiza cuando el equipo aprende algo nuevo.
- Es específico de un contexto: no exige un diccionario universal.
- Hace visibles contradicciones y conceptos ambiguos.

### Bounded Contexts

- Define una frontera semántica, no necesariamente una frontera física.
- Permite modelos diferentes para conceptos aparentemente iguales.
- Reduce modelos gigantes y acoplamiento accidental.
- Facilita ownership de equipos y evolución independiente.

### DDD Estratégico

- Identificar dominio y subdominios.
- Clasificar Core, Supporting y Generic.
- Construir el Lenguaje Ubicuo.
- Definir Bounded Contexts mediante Eventstorming.
- Elaborar Context Maps y patrones de relación (Context Mapping).
- Relacionar contextos con equipos y sistemas.

#### Context Mapping

- Identifica qué contexto provee y cuál consume información.
- Explicita APIs, eventos, traducciones y lenguaje publicado.
- Conecta arquitectura del dominio con responsabilidades de equipos.
- Permite discutir riesgos antes de implementar la integración.

##### Partnership

- Ambos contextos planifican cambios y resultados de manera conjunta.
- Ejemplo: Matrícula y Evaluación coordinan la validación de prerrequisitos.
- Ventaja: decisiones alineadas y colaboración directa.

##### Shared Kernel

- La reutilización reduce duplicación, pero aumenta la necesidad de coordinación.
- Ejemplo: CourseId y StudentId compartidos entre Matrícula y Evaluación.
- Regla: compartir solo lo estrictamente necesario y gobernar cada cambio.

##### Customer-Supplier

- El proveedor debe considerar necesidades del downstream sin perder su autonomía.
- Upstream: Payment ofrece datos o capacidades de pago.
- Downstream: Enrollment consume esa información.

##### Conformist

- Reduce el esfuerzo inicial, aunque el lenguaje ajeno puede contaminar el dominio interno.
- Riesgo: conceptos externos poco adecuados condicionan el diseño propio.
- Todo lo que se haga en el contexto supplier se verá afectado en el contexto customer.

##### Anticorruption Layer

- La capa evita que términos, estados y errores de otro sistema invadan el dominio.
- Convierte datos externos en objetos internos.
- Traduce estados técnicos a estados del negocio.
- Aísla cambios de APIs o modelos de terceros.

##### Big Ball of Mud

- La ausencia de límites convierte cualquier cambio en un riesgo sistémico (viola Single Responsibility).
- Clases gigantes y responsabilidades mezcladas (viola Open/Closed Principle).
- Modelos acoplados y dependencias circulares.
- Reglas duplicadas y modelos inconsistentes.

#### Comunicación

- **Inbound:** REST, comandos, eventos o mensajes que llegan desde usuarios y sistemas.
- **Outbound:** Eventos publicados, APIs externas, colas, consultas y notificaciones.

### Eventstorming

- Los eventos se escriben en pasado porque ya ocurrieron.
- El Big Picture distribuye eventos en el tiempo.
- Las políticas conectan eventos con nuevos comandos.
