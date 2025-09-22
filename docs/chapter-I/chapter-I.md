<style>
  body {
    font-family: 'Times New Roman', sans-serif;
    text-align: justify;
    font-size: 12px;
    margin-left: 2em;
    margin-right: 2em;
    line-height: 2;
  }
  
  p {
    text-indent: 2em; /* Sangría en el primer renglón de cada párrafo */
  }

  h1 {
    margin-left: 0; /* No aplica sangría para el título principal */
  }

  h2 {
    margin-left: 0; /* No aplica sangría para subtítulos de nivel 2 */
  }

  h3 {
    margin-left: 2em; /* Aplica una sangría de 2em para subtítulos de nivel 3 */
  }

  h4 {
    margin-left: 4em; /* Aplica una sangría de 4em para subtítulos de nivel 4 */
  }
</style>

# **CAPÍTULO I: INTRODUCCIÓN**

## 1.1. Startup Profile

En un contexto global donde el transporte marítimo moviliza la mayor parte del volumen del comercio internacional, las recientes tensiones geopolíticas han dejado en evidencia la fragilidad de las rutas tradicionales y la necesidad de herramientas que permitan decisiones operativas rápidas y fundadas en datos (United Nations Conference on Trade and Development, 2024). El tránsito marítimo sigue siendo el pilar del comercio mundial, con más del 80 % del volumen moviéndose por mar, lo que magnifica el efecto sistémico de cualquier interrupción en corredores críticos y convierte la optimización del ruteo en una palanca directa para reducir costos y mantener la continuidad de la cadena logística (United Nations Conference on Trade and Development, 2024).

La escalada de incidentes en el corredor del Mar Rojo desde finales de 2023 ha provocado desvíos masivos y cambios estructurales en los flujos marítimos. Se han documentado decenas de incidentes, aproximadamente entre 67 y 69 reportados por la Organización Marítima Internacional en sus comunicados de 2024, y estos episodios han aumentado la percepción de riesgo y empujado a embarcaciones a evitar pasajes anteriormente habituales (International Maritime Organization, 2024). Estos efectos se han traducido en impactos económicos y operativos medibles: durante el período crítico, índices clave del transporte de contenedores mostraron aumentos pronunciados, con incrementos cercanos al 130 % en ciertos índices de contenedor entre noviembre de 2023 y marzo de 2024, mientras que el número de travesías por la zona se redujo drásticamente en meses concretos, afectando la disponibilidad de llamadas portuarias (International Transport Forum, Organisation for Economic Co-operation and Development, 2024; Reuters, 2024). Además, análisis económicos comparativos han estimado que las embarcaciones que evitan el Mar Rojo experimentaron aumentos sustantivos en distancia recorrida y tiempo de tránsito (por ejemplo, incrementos del orden del 48 % para ciertos cargueros y 38 % para petroleros), con el consiguiente impacto en consumo de combustible, costes por demora y presión sobre rutas alternativas (World Bank, 2024).

Además del efecto inmediato sobre costes y tiempos, la complejidad del problema exige soluciones que combinen ingestión de señales en tiempo real (Sistemas de Identificación Automática, datos meteorológicos, avisos de seguridad y estado portuario), modelos predictivos y motores de optimización. La literatura técnica reciente muestra que enfoques basados en aprendizaje automático y redes que preservan la estructura de grafo pueden mejorar de forma sustancial la predicción de trayectorias y la estimación de tiempos: estudios empíricos reportan reducciones del error medio en métricas de desplazamiento en rangos significativos (por ejemplo, reducciones de entre un 44% y 56 % en comparativas experimentales para arquitecturas de Redes de Atención Gráfica con Memoria a Corto y Largo Plazo frente a baselines convencionales), lo que convierte a estas técnicas en insumos valiosos para generar pesos dinámicos y estimaciones de incertidumbre que alimenten motores de ruteo más fiables (Zhao et al., 2023). La combinación de estas capacidades permite no sólo optimizar tiempo y coste, sino también ponderar riesgo y sostenibilidad en decisiones de rerouting en escenarios altamente volátiles.

En respuesta a los desafíos identificados, un equipo de estudiantes de la Universidad Peruana de Ciencias Aplicadas fundó Teemo Solutions, una startup dedicada al desarrollo de soluciones tecnológicas avanzadas para la optimización de rutas navieras. Nuestra propuesta, Mushroom, es una plataforma de software que integra ingestión de datos meteorológicos, avisos de seguridad y estado portuario, junto al uso de Machine Learning, algoritmo A* y un motor de optimización que pondera objetivos múltiples (tiempo, costo, riesgo y emisiones). Mushroom produce rutas recomendadas y alternativas, además de explicar las razones principales detrás de cada recomendación. Esta solución busca reducir la exposición al riesgo operativo, mitigar sobrecostes por desvíos y demora, y proporcionar a embarcaciones, operadores y autoridades portuarias una base de evidencias y trazabilidad para la toma de decisiones en tiempo real (United Nations Conference on Trade and Development, 2024; World Bank, 2024).

### 1.1.1. Descripción de la Startup

- **Misión** 

  Desarrollar soluciones tecnológicas inteligentes, fiables y orientadas a impacto operativo que permitan a operadores logísticos y autoridades portuarias optimizar la gestión de rutas marítimas en entornos volátiles. Nuestra propuesta busca mitigar riesgos y mejorar la resiliencia de la cadena de suministro marítima.<br><br>

- **Visión**
  
  Convertirnos en la plataforma de referencia a nivel internacional en gestión inteligente de rutas navieras, reconocida por ofrecer soluciones que combinan precisión, transparencia y un impacto comprobable en la eficiencia operativa y la sostenibilidad. Aspiramos a que nuestras herramientas sean un estándar de confianza para la industria marítima. <br><br>

- **Valores** 

  En Teemo Solutions, nuestros valores guían la concepción, desarrollo e implementación de cada producto y servicio. Estos principios reflejan nuestro compromiso con la excelencia técnica, la seguridad operacional y la responsabilidad social, y orientan la cultura interna y las relaciones con clientes, socios y reguladores: <br><br> 

  1. **Aprendizaje continuo**
Fomentamos la capacitación, la retroalimentación y el crecimiento profesional dentro del equipo. Valoramos la diversidad de competencias como motor de soluciones más robustas y adaptadas al mundo real.<br><br>

  1. **Calidad**
Sustentamos nuestras decisiones técnicas en evidencia y validación empírica. Nuestras metodologías siguen buenas prácticas y verificación, con métricas objetivas para evaluar desempeño y detectar desviaciones.<br><br>

  1. **Colaboración**
Creemos que la eficiencia del transporte marítimo se alcanza mediante la cooperación entre actores. Facilitamos interfaces y acuerdos de datos que permitan compartir información crítica y coordinar respuestas frente a incidentes.<br><br>

  1. **Eficiencia**
Buscamos optimizar tiempo, costos y recursos mediante soluciones que traduzcan análisis complejos en operaciones concretas y medibles, con métricas claras de mejora.<br><br>

  1. **Ética**
Actuamos bajo principios éticos rigurosos: protección de la privacidad, cumplimiento normativo y uso responsable de datos. Establecemos políticas claras de gobernanza y seguridad para asegurar integridad, confidencialidad y disponibilidad de la información.<br><br>

  1. **Innovación continua**
Fomentamos la investigación aplicada y la experimentación responsable. Adoptamos metodologías ágiles y tecnologías emergentes para convertir datos complejos en acciones útiles y mejorar continuamente las capacidades de la plataforma.<br><br>

  1.  **Responsabilidad social**
Reconocemos el impacto sistémico del transporte marítimo y trabajamos por soluciones que favorezcan la seguridad de las personas, la estabilidad de las comunidades portuarias y la sostenibilidad económica de las cadenas logísticas a las que servimos.<br><br>

  1. **Seguridad y resiliencia**
Priorizamos la integridad operativa y la protección de las tripulaciones y las mercancías. Diseñamos nuestras soluciones para anticipar y mitigar riesgos y soportar escenarios de alta incertidumbre.<br><br>

  1. **Sostenibilidad**
Promovemos decisiones que reduzcan el impacto ambiental del transporte marítimo, favoreciendo alternativas que optimicen recursos sin comprometer la seguridad ni la eficiencia.<br><br>

  10. **Transparencia**
Garantizamos que las recomendaciones y alertas generadas por nuestras herramientas sean comprensibles y auditables. Proveemos trazabilidad de decisiones para impulsar la confianza y permitir la intervención humana informada.<br><br>

  1.  **Usabilidad**
Diseñamos para quienes operan en la práctica. Nuestras interfaces y flujos priorizan claridad, rapidez de acción y adaptación a los distintos perfiles operativos, reduciendo la fricción en la toma de decisiones.<br><br>

### 1.1.2. Perfiles de Integrantes del equipo

<table>
  <tr>
  <th colspan="2">Mallma Quispe, Ruben Elias</th>
  </tr>
  <tr>
    <td><img src="../../assets/img/chapter-I/rub-wus-here-lmao.png" style="width:700px; height:auto;" alt=""></td>
    <td>Estudiante de 8vo ciclo de ingeniería de software en la UPC. Me percibo como rápido, sencillo y proactivo. Si alguien está leyendo esto, espero que tengas un muy buen día. Ayer fui a pasear y me di cuenta que no tengo tiempo: ¿qué hago paseando cuanto tengo muchas cosas que hacer? Pero aún así decidí pasear porque me hizo feliz por unos momentos.</td>
  </tr>

  <tr>
    <th colspan="2">Riega Salas, Jose Miguel</th>
  </tr>
  <tr>
    <td><img src="../../assets/img/chapter-I/Jose-Riega.jpg" style="width:700px; height:auto;" alt=""></td>
    <td>Estudiante de 7mo ciclo de ingeniería de software en la UPC. Autopercibido como polivalente y responsable con aprendizaje continuo.

  Poseo conocimientos en C + +, HTML, Javascript, Python, desarrollo de aplicaciones web y metodologías ágiles. Mis objetivos son concretarse y seguir aprendiendo y ejerciendo mi carrera desarrollándome a nivel personal y profesional.</td>
  </tr>

  <tr>
  <th colspan="2">Sanchez Zamora, Fabrizio Alessandro</th>
  </tr>
  <tr>
    <td><img src="../../assets/img/chapter-I/Fabrizio-Sanchez.png" style="width:700px; height:auto;" alt=""></td>
    <td>Mi nombre es Fabrizio Alessandro Sanchez Zamora con código de estudiante U202213652, soy estudiante de Ingeniería de Software. Entre mis conocimientos se encuentran el manejo de lenguajes de programacion como C++, JavaScript y Python, asi como también se manejar SQL, Html y CSS. Como miembro del equipo, me comprometo a colaborar con mis compañeros para poder presentar un buen proyecto grupal</td>
  </tr>

  <tr>
  <th colspan="2">Trigueros Chumacero, Flavio Eduardo</th>
  </tr>
  <tr>
    <td><img src="../../assets/img/chapter-I/" style="width:700px; height:auto;" alt=""></td>
    <td></td>
  </tr>

  <tr>
    <th colspan="2">Valenzuela Huillcaya, Aldhair Johan Juan </th>
  </tr>
  <tr>
    <td><img src="../../assets/img/chapter-I/" style="width:700px; height:auto;" alt=""></td>
    <td></td>
  </tr>
</table>

## 1.2. Solution Profile

En Teemo Solutions diseñamos Mushroom como una plataforma integral pensada para enfrentar de forma práctica y escalable los retos que hoy condicionan el ruteo marítimo: pérdida de visibilidad operacional, riesgos de seguridad en corredores críticos y elevada volatilidad de costos que obligan a desviarse a rutas mucho más largas (United Nations Conference on Trade and Development, 2024; International Maritime Organization, 2024). Mushroom combina ingestión y mezcla de fuentes, modelado predictivo y un motor de optimización multi-criterio para ofrecer rutas recomendadas y alternativas evaluadas según tiempo estimado, coste proyectado, probabilidad de riesgo y métricas de sostenibilidad (emisiones estimadas). 

Funcionalidades principales de Mushroom:

1.  Ingestión y normalización de datos, enlazada con feeds meteorológicos, avisos de autoridades, reportes de incidentes y datos portuarios para generar un contexto operativo unificado en tiempo real.<br><br>

2. Modelos predictivos que estiman tiempo de tránsito por tramo, probabilidad de retraso o incidente y varianza asociada; estos puntajes alimentan el motor de ruteo para calcular caminos óptimos.<br><br>

3. Motor de optimización híbrido (A* + pesos dinámicos generados por Machine Learning) capaz de ofrecer alternativas con explicación de las causas principales que llevaron a cada recomendación. Esta trazabilidad facilita la intervención humana y la auditoría operacional.<br><br>

4. Interfaz operativa orientada a usuarios reales, utilizando un mapa interactivo con rutas, ventanas de detalle, notificaciones configurables y un módulo de historial.<br><br>

El diseño de producto está orientado a generar valor medible desde el primer uso al proporcionar estimaciones más precisas del tiempo de llegada y riesgo. Mushroom pretende reducir desvíos innecesarios, optimizar consumo de combustible y minimizar costes asociados a demoras y envíos perdidos. La propuesta comercial emplea un modelo SaaS por nivel de uso.

Mushroom se concibe no solo como una herramienta de optimización, sino como un componente de resiliencia estratégica para la industria. La plataforma ofrece a capitanes y operadores una capacidad accionable para anticipar, justificar y ejecutar rutas que equilibran seguridad, coste y sostenibilidad, reduciendo vulnerabilidades de la cadena logística global.

### 1.2.1. Antecedentes y Problemática

Los antecedentes son esenciales para una comprensión profunda de la problemática que Teemo Solutions busca abordar. Para ello, se ha aplicado la técnica de análisis "5W 2H" (Who, What, Where, When, Why, How & How Much), que permite estructurar el diagnóstico de la situación desde distintas perspectivas clave:

1. **What (¿Qué está ocurriendo?):**
El comercio marítimo global se encuentra en una situación crítica debido a crecientes tensiones geopolíticas, especialmente en el corredor del Mar Rojo. Esta inestabilidad ha generado interrupciones severas en las rutas tradicionales, ocasionando incrementos en los costos logísticos, tiempos de entrega impredecibles y una sobrecarga significativa en rutas alternativas, como la que rodea el Cabo de Buena Esperanza. Las empresas se ven obligadas a replantear sus estrategias de inventario, distribución y planificación operativa.


2. **Why (¿Por qué está ocurriendo?):**
La causa principal es la escalada del conflicto en Medio Oriente, particularmente los ataques de los hutíes en el Mar Rojo, que han transformado esta vía comercial en una zona de alto riesgo. Esta situación ha generado desvíos masivos de embarcaciones, falta de visibilidad sobre las condiciones en tiempo real y una carencia de herramientas inteligentes para la toma de decisiones logísticas ante escenarios de emergencia.


3. **When (¿Cuándo sucede?):**
El conflicto ha escalado desde finales de 2023 y continúa afectando al comercio internacional durante 2024. Al no existir una fecha de resolución clara, se ha creado un entorno de incertidumbre permanente que demanda soluciones tecnológicas ágiles y adaptables para el corto y mediano plazo.


4. **Where (¿Dónde ocurre?):**
La problemática se concentra en el Mar Rojo, una vía estratégica que conecta Europa, Asia y África. Sin embargo, el impacto se extiende a puertos en ambos continentes, generando cuellos de botella logísticos en zonas clave como el Mediterráneo, el Golfo de Adén y el Canal de Suez.


5. **Who (¿Quiénes están involucrados o afectados?):** <br>
   - Capitanes de embarcaciones y jefes de ruta, responsables de la seguridad y eficiencia del tránsito marítimo.

   - Agencias navieras y operadoras logísticas, que deben ajustar operaciones y comunicaciones en tiempo real.

   - Empresas exportadoras/importadoras, cuya competitividad depende de entregas puntuales y costos controlados.

   - Industria tecnológica, llamada a ofrecer soluciones para afrontar esta nueva realidad.


6. **How (¿Cómo está afectando?):** La inestabilidad ha obligado a adoptar rutas más largas y costosas, lo que incrementa significativamente los precios del transporte, retrasa entregas y congestiona corredores alternativos. Esta situación disminuye la eficiencia operativa del sector y revela una necesidad crítica de herramientas de análisis predictivo que faciliten decisiones logísticas fundamentadas y rápidas.


7. **How much (¿Cuánto cuesta o impacta?):**
   - Se estima que el comercio entre España y Asia podría perder más de 135.000 millones de euros debido a la interrupción de rutas (ABC International, 2024).

   - Empresas como Tesla han detenido su producción en Alemania por problemas de suministro derivados del conflicto.
 
   - Para Teemo Solutions, esta problemática representa una oportunidad estratégica: desarrollar soluciones tecnológicas que minimicen los impactos financieros, mejoren la resiliencia de la cadena logística y mantengan la competitividad en entornos altamente volátiles.



### 1.2.2. Lean UX Process

En esta etapa damos inicio al enfoque Lean UX, una metodología que nos permitirá construir y afinar la visión del modelo de negocio que respaldará nuestra solución digital. Gracias a este enfoque, podremos centrar el diseño de nuestro producto en resolver necesidades concretas y generar valor real para los usuarios.

#### 1.2.2.1  Problem Statement

- **Domain**

La solución se ubica dentro del dominio de la logística marítima global, un sector clave para el comercio internacional, actualmente impactado por conflictos geopolíticos, variabilidad climática y congestión en rutas estratégicas como el Mar Rojo o el Canal de Suez.

- **Customer Segments**
  - Empresas Navieras y Operadoras Logísticas: Gestionan flotas y rutas internacionales de carga.

  - Exportadores e Importadores de Alta Rotación: Empresas industriales con alta dependencia de rutas marítimas estables.

   
- **Pain Points**
  - Rutas tradicionales interrumpidas o congestionadas por conflictos o clima.

  - Falta de visibilidad y datos confiables en tiempo real.

  - Decisiones reactivas y no optimizadas ante desvíos o cierres portuarios.

  - Aumento en los costos operativos y pérdida de competitividad.


- **Gap (Brecha Identificada)**

Actualmente, no existe una herramienta accesible y especializada que integre datos geopolíticos, climáticos y logísticos para ofrecer rutas óptimas, confiables y actualizadas para embarcaciones comerciales. Las decisiones se toman con herramientas fragmentadas, informes desactualizados o sistemas poco adaptables.

- **Vision / Strategy**

Desarrollar Mushroom, una solución SaaS que proporcione recomendaciones de rutas marítimas óptimas, basadas en algoritmos predictivos que combinan inteligencia climática, cierres portuarios, tráfico marítimo y factores geopolíticos. La estrategia es entregar una interfaz intuitiva, modular e integrable con otros sistemas logísticos.

- **Initial Segment (Primer Segmento a Impactar)**

Empresas navieras con operaciones activas en el corredor del Mar Rojo y el Océano Índico, donde las tensiones actuales han forzado desvíos frecuentes. Este segmento tiene alta urgencia, capacidad de adopción tecnológica y un impacto directo en costos operativos si se mejora la eficiencia de sus rutas.

#### 1.2.2.2 Lean Ux Assumptions 

**Users**:

- Empresas Navieras y Operadoras Logísticas: responsables del trazado y la ejecución de rutas marítimas seguras y eficientes, así como de la optimización de recursos operativos.
- Exportadores e Importadores: empresas que dependen del transporte marítimo para movilizar productos y materias primas, afectadas por retrasos, cambios de ruta y falta de información confiable.

**User Outcomes:** Para ambos segmentos se espera que 

- Reduzcan los tiempos de planificación de rutas ante eventos inesperados.
- Accedan a información integrada, confiable y actualizada en tiempo real.
- Tomen decisiones informadas que reduzcan costos logísticos.
- Aumenten la previsibilidad de sus operaciones marítimas.
- Refuercen la resiliencia de su cadena de suministro ante conflictos geopolíticos y eventos climáticos extremos.

**Business Assumptions**

**Creemos que** los actores de la cadena logística marítima están buscando soluciones proactivas para enfrentar la incertidumbre global.

**Asumimos que** la propuesta de valor de Mushroom atraerá a empresas con operaciones críticas en zonas sensibles como el Mar Rojo.

**Consideramos que** la adopción inicial estará motivada por la necesidad urgente de reducir pérdidas financieras por desvíos y retrasos no planificados.

**Creemos que** el diferencial de Teemo Solutions es la integración de múltiples variables (clima, conflictos, capacidad portuaria) en una sola plataforma visual.

**Asumimos que** nuestros usuarios valorarán especialmente las funcionalidades predictivas y la capacidad de simular escenarios logísticos.

- - - 

**User Assumptions:**

**¿Quién utiliza nuestra plataforma?:**
Planificadores de rutas, analistas logísticos, gerentes de operaciones en navieras, y responsables de logística internacional en empresas exportadoras/importadoras.

**¿Cómo se integra en su rutina?:**
Como herramienta de consulta diaria para el trazado de rutas, evaluación de riesgos y toma de decisiones estratégicas.

**¿Qué desafíos resuelve?**

- Falta de datos unificados en un solo sistema.
- Toma de decisiones basadas en información obsoleta o parcial.
- Aumento de costos por desvíos no anticipados.

**¿Qué imagen queremos proyectar?:** Una solución confiable, especializada en inteligencia logística marítima, robusta pero simple de usar.

**¿Propósito fundamental?:** Optimizar las decisiones de navegación y logística para mantener cadenas de suministro estables y rentables.

**¿Qué funcionalidades destacan?**

- Simulación de rutas con condiciones dinámicas.
- Alertas automatizadas por cambios climáticos o conflictos.
- Comparación de tiempos y riesgos entre rutas.
- Integración con plataformas de gestión logística (TMS, ERP).

#### 1.2.2.3 Lean Ux Process Hypothesis Statement

- Hipótesis 1:<br>
**Creemos que** las empresas navieras y operadoras logísticas adoptarán una plataforma que les permita visualizar, simular y ajustar rutas marítimas en tiempo real, considerando condiciones climáticas y geopolíticas. <br>
**Esto logrará** una toma de decisiones más rápida, reducción de costos imprevistos y mayor eficiencia operativa. <br>
**Sabremos que** esto es cierto cuando al menos el 70% de los usuarios realicen simulaciones de ruta y registren un ahorro operativo en los primeros 3 meses. <br>


- Hipótesis 2:<br>
**Creemos que** los exportadores e importadores utilizarán Mushroom para anticiparse a interrupciones logísticas y ajustar sus decisiones comerciales.  <br>
**Esto logrará** una mejor gestión de inventario, reducción de retrasos y mejora en la coordinación con clientes y proveedores.  <br>
**Sabremos que** esto es cierto cuando los usuarios reporten una disminución del 20% en retrasos logísticos y una mejora en la previsión de entregas dentro de los primeros 2 meses. <br>


- Hipótesis 3:<br>
**Creemos que** integrar fuentes de datos confiables y en tiempo real (meteorología, conflictos, estado portuario) será un valor diferencial clave para los usuarios.  <br>
**Esto logrará** una mayor confianza en la herramienta frente a soluciones genéricas del mercado.  <br>
**Sabremos que** esto es cierto cuando el 80% de los usuarios destaque esta funcionalidad en encuestas de satisfacción y repita su uso semanalmente.<br>



-  Hipótesis 4:<br>
**Creemos que** ofrecer una interfaz visual e intuitiva, adaptable a distintos niveles técnicos, aumentará la adopción de la plataforma.  <br>
**Esto logrará** que tanto técnicos como directivos puedan tomar decisiones basadas en los mismos datos.  <br>
**Sabremos que** esto es cierto cuando al menos 3 perfiles distintos dentro de cada empresa usen la plataforma con frecuencia mensual.<br>


#### 1.2.2.4. Lean UX Canvas

- Mediante la realización Lean UX Canvas podemos mostrar toda información anterior pero de una manera resumida, didáctica y más accesible al lector. También se resume la problemática que estamos abordando y la solución que proponemos, junto con los supuestos de las hipótesis y los puntos más importantes de las mismas.

<p align="center">
  <img src="../../assets/img/chapter-I/lean%20ux%20canvas.png"  style="width:1000px; height:auto;" alt="">
</p>


## 1.3. Segmentos Objetivos

El producto Mushroom, desarrollado por Teemo Solutions, está dirigido a actores clave del ecosistema logístico y naviero internacional, especialmente aquellos que se ven directamente afectados por disrupciones en las rutas marítimas. Los segmentos objetivos se definen de la siguiente manera:

1. **Empresas Navieras y Operadoras Logísticas Globales:** Compañías multinacionales que operan rutas marítimas internacionales, con flotas activas en zonas como el Mar Rojo, Mediterráneo, Canal de Suez y el Océano Índico.


2. **Exportadores e Importadores de Alta Rotación:** Empresas industriales y comerciales que dependen de entregas constantes y puntuales, como fabricantes de vehículos, tecnología, farmacéuticas y bienes de consumo masivo.

<table>
  <thead>
    <tr>
      <th>Característica</th>
      <th>Empresas Navieras y Operadoras Logísticas</th>
      <th>Exportadores e Importadores de Alta Rotación</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Demografía</strong></td>
      <td>+500 empleados, flotas de +50 embarcaciones, presencia intercontinental.</td>
      <td>Ubicadas principalmente en Europa, Asia y América, con alto volumen de exportación/importación.</td>
    </tr>
    <tr>
      <td><strong>Necesidades</strong></td>
      <td>Optimización de rutas, reducción de costos, gestión de riesgos logísticos.</td>
      <td>Visibilidad en tiempo real, planificación de entregas, reducción de impacto por interrupciones.</td>
    </tr>
    <tr>
      <td><strong>Impacto esperado</strong></td>
      <td>Mayor eficiencia operativa, mejor adaptabilidad a crisis geopolíticas.</td>
      <td>Menores pérdidas económicas, continuidad de la cadena de suministro.</td>
    </tr>
    <tr>
      <td><strong>Ejemplo o Dato</strong></td>
      <td>El 80% del comercio mundial se mueve por vía marítima (UNCTAD, 2023).</td>
      <td>Tesla paralizó producción en Alemania por bloqueos en el Mar Rojo (2024).</td>
    </tr>
  </tbody>
</table>
