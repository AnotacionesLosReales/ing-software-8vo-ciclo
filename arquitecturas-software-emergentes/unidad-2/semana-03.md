# Semana 3: Low-Code & Mobile Application Platforms

## Low-Code Application Platforms

Low-code hace referencia a la tecnología diseñada para facilitar la accesibilidad de las personas al mundo del desarrollo.
Mediante una interfaz visual “drag and drop” las plataformas low-code facilitan la creación de software o aplicaciones sin requerir la presencia de un desarrollador experto durante el proceso

### Ventajas

- Reducción del tiempo de desarrollo.
- Reducción de los tiempos de mantenimiento.
- Reducción de los costos.
- Mejora la productividad de los desarrolladores.
- Aprovechamiento Cloud.
- Incremento de los recursos.
- Contribución a alinear IT con los objetivos empresariales.

### Principios

- **Model-Driven Development:** Transforma ideas en aplicaciones que entregan valor de negocio a través de abstracción y automatización.
- **The Cloud:** La nube habilita la facilidad y velocidad del despliegue de las aplicaciones que los usuarios exigen.
- **Experimentation & Innovation:** Las herramientas de desarrollo deben ser asequibles y ágiles para que la innovación permita experimentar, explorar y crear.
- **Collaboration:** Aprovechar un lenguaje visual compartido para facilitar el intercambio de conocimientos e ideas entre los expertos en el dominio del negocio y los desarrolladores.
- **Openness:** Todo puede integrarse con una plataforma de desarrollo de aplicaciones empresariales agnóstica; esto elimina las limitaciones sobre lo que se puede construir.
- **Governance & Control:** Son esenciales unos procesos y protocolos sólidos de gobernanza y control.
- **Agility:** Gestionar el ciclo de vida completo de desarrollo de aplicaciones empresariales mediante flujos de trabajo ágiles para eliminar cuellos de botella, facilitar la entrega iterativa y lograr el menor tiempo de obtención de valor.
- **Multi-User Development:** Varios desarrolladores deberían poder trabajar en una aplicación simultáneamente. La plataforma debe admitir y sincronizar su flujo de trabajo.
- **Community:** Una plataforma sin comunidad no es una plataforma en absoluto.

### Low-Code/No-Code Platforms

#### Microsoft Power Platform

- **Power Apps:** Destinado al desarrollo de aplicaciones empresariales.
- **Power Automate:** Destinado a la automatización de procesos usando IA.
- **Power BI:** Destinado a la Business Inteligence y análisis de datos en tiempo real.
- **Power Virtual Agent:** Destinado a la creación de bots inteligentes.

## Mobile Application Platforms

### Recommended App Architecture

- **UI Layer:** On screen data rendering, State holders (ViewModel).
- **Domain Layer:** Use Cases or interactors; Single Functionality Responsibility; Encapsulation.
- **Data Layer:** Exposing Data; Centralizing changes; Resolving conflicts; Abstracting sources of data; Containing business logic.

### Best Practices

- No almacenes datos en los componentes de la aplicación.
- Reducir las dependencias de las clases de Android.
- Establece límites de responsabilidad bien definidos entre los distintos módulos de la aplicación.
- Expón la menor cantidad posible de cada módulo.
- Céntrate en la esencia única de tu aplicación para que destaque frente a otras.
- Considera cómo hacer que cada parte de tu aplicación sea testeable de forma aislada.
