ntroducción 
En este documento se pretende describir la arquitectura de Plataforma AgenticAI sobre Oracle a alto nivel, de cara a llevar a la práctica el proceso de normalización de la aplicación. Este documento constituye la arquitectura de la solución completa, mostrando una visión lógica de todos los sistemas y aplicaciones que forman parte de la misma.

1.1.	Objetivos del documento
El objetivo de este documento es presentar la solución técnica planteada ejecutada para el proyecto Plataforma AgenticAI sobre Oracle, detallando los siguientes apartados:

•	Definir la arquitectura de aplicaciones de la solución
o	Identificar aplicaciones impactadas
o	Definir los módulos principales y sus relaciones.
o	Definir la integración con terceros. 
o	Definir la arquitectura de datos.

•	Definir la arquitectura tecnológica de la solución
o	Definir la plataforma tecnológica, indicando las capacidades de la misma que se utilizan.
o	Definir la arquitectura de comunicaciones.
o	Definir la arquitectura de desarrollo y gestión del ciclo de vida.

•	Definir la arquitectura de seguridad de la solución
o	Definir los diferentes mecanismos de acceso al sistema. 
o	Definir las implicaciones de seguridad de la solución.

1.2.	Descripción global de la solución

El proyecto busca automatizar la revisión de documentación generada por contratas de ingeniería en proyectos de PDI, con enfoque en requisitos de reglamentación y telecontrol. La solución verificará aspectos clave como títulos, códigos de proyecto, fechas, objeto de la memoria, presupuestos y planos, asegurando el alineamiento y cumplimiento de estándares y mejorando la eficiencia operativa.

A través de algoritmos de procesamiento de texto y IA Generativa, el modelo identificará errores, evaluará consistencia y generará reportes con recomendaciones. Esto optimiza los tiempos de revisión, asegura un control de calidad uniforme y libera recursos para tareas estratégicas, consolidando el compromiso de PDI con la innovación y la excelencia operativa.

Actualmente, la supervisión y validación de los entregables de ingeniería generados por contratas en los proyectos de PDI se realiza de forma manual. Este proceso es laborioso, consume mucho tiempo y está sujeto a errores humanos. Las revisiones abarcan documentación clave, como títulos, códigos de proyecto, fechas, memorias de proyecto, presupuestos, planos, y cumplen con requisitos específicos para reglamentación y telecontrol.

El proceso incluye:
•	Comparación de documentos contra herramientas de presupuestación para validar coherencia.
•	Validación de que los elementos técnicos, como cambios de líneas, apoyos o transformadores, estén reflejados en los planos.
•	Revisión de cumplimiento normativo, incluyendo análisis de casuísticas comunes como distancias antirreglamentarias o defectos de apoyos.
•	Supervisión de solapamientos en proyectos cercanos a través de herramientas como Sistema_externo_1 y Sistema_externo_2.

La revisión se realiza de manera individual para cada documento, lo que incrementa la carga operativa, consume tiempo considerable y puede dar lugar a errores humanos debido a la naturaleza repetitiva y detallada de las tareas. Además, la falta de un proceso automatizado dificulta garantizar la consistencia en la calidad de las validaciones entre distintos proyectos o técnicos.


2.3.	Alcance de la petición
El proyecto tiene como objetivo desarrollar e implementar un sistema automatizado para realizar las validaciones de entregables de ingeniería de PDI. Este sistema integrará algoritmos de inteligencia artificial para analizar automáticamente la documentación y garantizar el cumplimiento de requisitos reglamentarios y técnicos.

El alcance incluye:

•	Automatización de validaciones de documentos clave: títulos, códigos, fechas, presupuestos, planos, objetos de memoria, etc.
•	Validación de casuísticas específicas de reglamentación, como distancias antireglamentarias y sustitución de apoyos en mal estado.
•	Supervisión de proyectos en curso para evitar solapamientos utilizando Sistema_externo_1 y Sistema_externo_2.
•	Verificación de documentación pertinente en estudios finales enviados por la ingeniería (incluyendo requisitos locales y de organismos como confederaciones hidrográficas).
•	Integración con sistemas corporativos, como plataformas de gestión documental, para facilitar la trazabilidad y el seguimiento.
•	Generación de reportes automatizados con observaciones y recomendaciones.

Este modelo automatizado homogenizará los criterios de revisión, eliminando la variabilidad entre técnicos y proyectos, y optimizando los tiempos de validación. Como resultado, se reducirá significativamente la carga operativa del personal técnico, mejorando la eficiencia y la calidad del proceso de supervisión, así como el cumplimiento de los plazos establecidos.

4.1.	Detalle de necesidades funcionales de usuario

En la siguiente tabla debe desglosarse cada una de las necesidades funcionales del sistema de forma individual. Para facilitar su comprensión ordenar agrupando por proceso afectado.

Para describirlas se debe tener en cuenta: Deben ser precisas, claras y sin  ambigüedades, cuantificables y verificables. Se redactarán en lenguaje natural evitando el uso de frases largas, subordinadas, palabras con más de una interpretación, la presentación de varias necesidades en una única o el uso de sinónimos. 

Cada necesidad debe priorizarse con los valores propuestos para su criticidad: Alta, Media o Baja. 

Duplicar todas aquellas filas/bloques necesarios para especificar todas las necesidades.


El proyecto de supervisión automatizada de entregables de ingeniería responde a la necesidad de optimizar el control de calidad de la documentación técnica generada en proyectos de PDI, reduciendo la dependencia de procesos manuales y garantizando el cumplimiento de los estándares reglamentarios, técnicos y operativos. Actualmente, la revisión de esta documentación es manual, lenta y sujeta a errores humanos, lo que afecta la eficiencia y calidad del proceso.

El proyecto requiere una solución que automatice la validación de entregables de ingeniería, cubriendo múltiples casos de uso. La solución debe ser capaz de manejar grandes volúmenes de datos, garantizar la consistencia en las validaciones y optimizar los recursos técnicos, alineándose con los estándares normativos y operativos. La implementación de este sistema es fundamental para mejorar la eficiencia, calidad y trazabilidad de las supervisiones.

El sistema debe tener como funcionalidades clave los siguientes aspectos:
•	Aceptación y rechazo automático de documentos: Implementar criterios automáticos que determinen la aceptación o rechazo de un documento, con información detallada sobre el motivo de la decisión.
•	Generación de reportes automatizados: Proporcionar informes claros y detallados con los resultados de las validaciones, indicando qué elementos requieren correcciones.
•	Capacidad de escalabilidad: Asegurar que el sistema pueda adaptarse al crecimiento del volumen de expedientes anuales y la incorporación de nuevos casos de uso.

El sistema debe ser capaz de integrarse con las plataformas actuales de gestión documental y presupuestación para:
•	Automatizar el análisis de documentos y la generación de reportes con observaciones y recomendaciones.
•	Garantizar la trazabilidad de las validaciones realizadas, facilitando auditorías futuras y asegurando la transparencia del proceso.
4.2.	Tipologías de documentos y validaciones necesarias

El sistema debe automatizar la validación de diferentes tipos de documentos, abarcando las siguientes categorías clave:
•	Titulos y códigos de proyecto: Verificar que los títulos y códigos de los documentos coincidan con la información registrada en sistemas de presupuestación y bases de datos. Esto incluye asegurar que cada documento está correctamente identificado y vinculado al proyecto correspondiente
•	Fechas y presupuestos: Validar la coherencia entre las fechas de los documentos y el cronograma del proyecto, así como contrastar los presupuestos reflejados en los documentos con los registrados en herramientas de presupuestación
•	Memorias de proyecto: Revisar el objeto de la memoria para garantizar que es consistente con los objetivos y especificaciones del proyecto. Por ejemplo, validar que las descripciones de los trabajos sean coherentes con las casuísticas habituales (apoyos defectuosos, distancias antireglamentarias, etc.).
•	Planos técnicos: Analizar planos generados por las contratas para asegurar que reflejan los cambios previstos (como sustitución de apoyos o modificaciones en líneas). Validar que los planos coincidan con el diseño reflejado en herramientas como Sistema_externo_1 y que no existan solapamientos con proyectos en curso.
•	Documentos de conformidad y permisos: Comprobar la existencia de permisos de organismos relevantes, como confederaciones hidrográficas, y que estén correctamente adjuntos según la ubicación del proyecto.
4.3.	Validaciones específicas para Reglamentación

La supervisión automatizada debe cubrir distintas casuísticas reglamentarias asociadas a las líneas aéreas y centros de transformación. Entre estas se incluyen:
•	Apoyos en mal estado: Validar que los títulos y descripciones reflejen correctamente el estado del apoyo y los trabajos necesarios para su sustitución. Comparar esta información con los registros históricos de inspección y presupuestación.
•	Distancias antireglamentarias: Verificar que las distancias especificadas cumplen con los estándares reglamentarios y que los trabajos contemplan las acciones correctivas necesarias.
•	Campañas de sustitución de apoyos metálicos: Validar que las memorias y planos reflejan correctamente el alcance de la sustitución y que se ajustan a las normativas aplicables.
4.4.	Validaciones específicas para Telecontrol
Para los proyectos de telecontrol, es esencial que el sistema automatice la supervisión de:
•	Sistemas de control remoto: Verificar que los elementos técnicos descritos en los documentos (equipos de telecontrol, sensores, etc.) cumplen con las especificaciones requeridas para su integración en el sistema general.
•	Consistencia de información técnica: Validar que los presupuestos y planos reflejan correctamente los dispositivos y conexiones asociadas a telecontrol.
4.5.	Supervisión de proyectos en curso

El sistema debe integrarse con herramientas como Sistema_externo_1 para:
•	Identificar proyectos cercanos en curso que puedan solaparse con el nuevo proyecto.
•	Verificar que los apoyos y tramos asociados al proyecto están correctamente registrados y no interfieren con otras actuaciones en la misma infraestructura.
•	Contrastar los planos y diseños cargados en Sistema_externo_1 con las especificaciones del proyecto para asegurar consistencia.

4.6.	Validaciones de documentación final (validacion de un Proyecto, que es un conjunto de documentos)

Cuando la ingeniería envía el estudio final del proyecto, el sistema debe:
•	Asegurar que todos los documentos requeridos están presentes, incluyendo planos, memorias, presupuestos y permisos.
•	Comprobar que los nombres y contenidos de los documentos reflejan adecuadamente el alcance del proyecto y cumplen con los requisitos técnicos y normativos.
•	Validar requisitos específicos según el área geográfica del proyecto, como permisos de organismos regionales o confederaciones hidrográficas.
4.7.	Validaciones a realizar en función de los documentos – MT (Media Tensión)

Situaciones	Validaciones a realizer

Previo a realizar un encargo	
•	Verificar que no existen otros proyectos que solapen Memoria con cálculos descriptivos de la instalación y EBSS completo y Pliego de Condiciones Técnicas	
•	Comprobar que están todos los documentos
•	Coherencia entre memoria y datos en Sistema_externo_2
•	Información del emplazamiento 
•	Análisis de organismos afectados
•	Características técnicas
•	Cálculos mecánicos
Presupuestos – Elaborado en base a las Unidades Compatibles (UUCC)	•	Coherencia entre diseño técnico y UUCC reflejadas en los presupuestos cargados
•	Apoyos, crucetas, puestas a tierra, conductores, desmontajes y CTs (Centros de Transformación)
Planos generales de situación, emplazamiento, obra eléctrica y obra civil	•	Estándares técnicos y reglamentarios
•	Planos CT
•	Perfil longitudinal y de planta en líneas aéreas MT
•	Esquema unifilar de la red de MT
Separatas Organismos afectados	•	Coherencia del volumen de separatas con las incluidas en la memoria
•	Verificación de las afecciones
Relación de bienes y derechos de los afectados (RBDA)	•	Inclusión de espacio adicional requerido en los planos y documentos
•	Permisos de propietarios afectados solicitados
•	Parcelas afectadas y propietarios correctamente registrados en la RBDA
Gestión de permisos	•	Acuerdos entre UFD y propietarios de parcelas afectadas
•	Verificación de referencias catastrales


4.7.1.	Previo a realizar un encargo
Antes de realizar el encargo es necesario que se revise la ficha de apertura, para verificar que no existan otros proyectos que se solapen, así como la comprobación de que se haya abierto bien el proyecto, en la carptea de la gestión documental dentro del expediente de diseño.
 

Se puede confirmar en Sistema_externo_1 si algo sobre el activo o el activo vecino, para que no se solapen proyectos. 

En el caso de reglamentación, habría que revisar los defectos reglamentarios y revisar en Sistema_externo_3 la distancia, donde se hace un perfil topográfico con las líneas y las distancias al terreno/vegetación. (NOTA: En Sistema_externo_3 se puede filtrar por Código de Instalación, para poder revisar potencial solape de proyectos).

4.7.2.	Memoria con cálculos descriptivos de la instalación y EBSS completo y Pliego de Condiciones Técnicas

Antes de la revisión, se comprueba que todos los documentos estén cargados en el sistema: CAD capa diseño; Perfil (PDF); Cálculos (PDF y Excel); Planos de obra ejecutada (OE) (PDF); y Planos de obra en construcción (OC) si corresponde (PDF). 

Se verifican la coherencia de la información reflejada en la memoria con los datos del sistema Sistema_externo_2, verificando el título del expediente (que coincida con la apertura del proyecto en Sistema_externo_2), las fechas y código ACT (UD en Sistema_externo_4) que este correctamente registrado y alineado con Sistema_externo_2.

El contenido de la memoria debe ser consistente con los planos, el presupuesto y otros documentos relacionados. Estas validaciones incluyen los cuadrados verdes de los planos con el texto del objeto de la memoria, el número de apoyos, conductor (en caso de líneas) y CT (que estarían pintados como cajas rojas, puesto que si están en color negro es un CT ya existente). Cuando se trata de un desmontaje, la línea se refleja en el plano en color negro y con asteriscos (*), el apoyo no te lo indican, y en el caso del CT se indica un mensaje de “A desmontar”.

  

Respecto a la información del emplazamiento, hay que verificar si lo descrito en el proyecto coincide con la instalación registrada en Sistema_externo_2/Sistema_externo_1. Contrastando la ubicación del término municipal con los datos del sistema, y conrfirmar que el emplazamiento específico está reflejado en el apartado correspondiente del proyecto.

Hay que realizar un análisis exhaustivo de los organismos afectados por el proyecto y se verifica que los permisos requeridos están correctamente adjuntos en la carpeta correspondiente, teniendo que validar:
•	Ríos y cuerpos de agua: Permisos de confederaciones hidrográficas si hay ríos a menos de 100m.
•	Carreteras: Verificar permisos en función de la autoridad responsable (ayuntamiento, diputación, Estado). La distancia mínima debe ser 1,5 veces la altura del apoyo (aproximadamente 25m).
•	Espacios naturales protegidos: Comprobar que están reflejados en Sistema_externo_1 y, si es necesario, validar el impacto ambiental.
•	Patrimonio/Cultura: Identificar elementos patrimoniales o culturales que puedan requerir permisos específicos (e.g., castros protegidos).
•	Propiedades particulares: Relación de Bienes Inmuebles con un tratamiento específico pero sin carpeta de permisos.
•	Otras distribuidoras: Validar permisos de otras eléctricas con base en la información proporcionada por la ingeniería tras visitas de campo.
•	Aeropuertos/Renfe: Verificar que no hay interferencias con aeropuertos o estaciones a menos de 100m.
•	Ayuntamientos: Confirmar la obtención de permisos municipales obligatorios según la ubicación del activo.

Se verifica que las características técnicas reflejadas en la memoria coinciden con los datos de las instalaciones proyectadas. Las validaciones incluyen:
•	Concordancia entre el código de la línea, los apoyos proyectados y los datos registrados en Sistema_externo_2.
•	Validación de actuaciones relacionadas con cambios de conductores.
•	Contraste del objeto del proyecto con los datos del tramo y apoyos registrados en Sistema_externo_2.

Se realiza un chequeo de los cálculos mecánicos asociados a las líneas aéreas para asegurar que:
•	Los apoyos proyectados y los conductores utilizados coinciden con los planos y están correctamente reflejados en los cálculos mecánicos.
•	Los cálculos están respaldados por programas específicos y muestran concordancia con los materiales descritos.
•	Se validan tanto los elementos existentes como los nuevos incluidos en el proyecto.

Estas validaciones específicas garantizan que la memoria con cálculos descriptivos, el EBSS y el pliego de condiciones técnicas cumplan con los requisitos técnicos, normativos y operativos del proyecto. La implementación de un sistema automatizado permitirá realizar estas validaciones de forma más rápida, consistente y eficiente, asegurando un control exhaustivo y reduciendo la carga manual sobre los técnicos.

4.7.3.	Presupuestos – Elaborado en base a las Unidades Compatibles (UUCC)

Estas validaciones garantizan la coherencia entre el diseño técnico y los presupuestos cargados, asegurando que las unidades compatibles reflejen con precisión los trabajos proyectados.

Se verifican las Unidades Compatibles (UUCC) asociadas a los elementos clave del proyecto:
•	Apoyos: Validar que los tipos de apoyos proyectados están reflejados correctamente en las UUCC del presupuesto.
•	Crucetas: Comprobar que las crucetas necesarias para los apoyos proyectados están incluidas.
•	Puestas a Tierra: Revisar que las UUCC correspondientes a las puestas a tierra estén consideradas.
•	Conductores: Verificar que los conductores proyectados estén correctamente reflejados en las UUCC, asegurando que las especificaciones técnicas coincidan.
•	Desmontajes: Confirmar que las unidades relacionadas con desmontajes (líneas o apoyos) estén incluidas en el presupuesto.
•	Centros de Transformación: Comprobar las UUCC asociadas a los CTs, validando la tipología de celdas, transformadores y otros elementos relacionados.

El diseño técnico debe estar alineado con las UUCC reflejadas en el presupuesto, incluyendo:
•	Validar que si se proyectan, por ejemplo, 3 apoyos, las UUCC del presupuesto reflejen con precisión esos 3 apoyos, incluyendo su tipología y otros elementos asociados.
•	Revisar que el presupuesto del documento del proyecto coincida con los datos cargados por la ingeniería en el sistema HDTER.

Las ingenierias utilizan HDUF (que funciona solo para Sistema_externo_4 porque Sistema_externo_2 no esta habilitado por el momento), con un plano de objetos tipo desde AutoCad, se saca la modelización del proyecto y lo pasa a presupuesto, y de ahi se carga a HDTER.

Se establecerá un maestro de referencia que incluirá las UUCC esperadas para cada tipo de trabajo o montaje, para permitir validar automaticamente si las UUCC del presupuesto están completas y detectar discrepancias entre el diseño técnico, las UUCC generadas y el presupuesto cargado.

4.7.4.	Planos generales de situación, emplazamiento, obra eléctrica y obra civil

Se realizan validaciones para asegurar que los planos entregados cumplen con los estándares técnicos y reglamentarios, garantizando una correcta ubicación, diseño y alineación con otros proyectos en curso.

El primer paso consiste en confirmar que el proyecto está correctamente ubicado y alineado con los datos registrados en los sistemas corporativos. Se verifica la ubicación en Sistema_externo_1, asegurando que coincide con la ficha técnica de entrada del proyecto, así mismo se verifica si el proyecto se solapa con otros proyectos en curso dentro de la misma instalación o área (si existe algún solapamiento, este debe estar identificado y señalado).

Los planos entregados por la ingeniería deben ser revisados en detalle, asegurando coherencia y precisión en la información proporcionada, así como el perfil y la obra eléctrica.

Según el tipo de instalación puede haber distintos tipos de planos específicos:
•	Planos CT (Cuando existe centro de transformación, incluyendo unifilar): En el plano se tiene que revisar que estar la caja roja, y revisar tambien el plano propio del CT nuevo (dibujo de frontal, lateral, dentro, foto del plano y detalle para que el ayto. dé permisos). Revisar que esté bien el dibujo, así como las coordenadas adecuadas y el mapa
•	Perfil longitudinal y de planta en líneas aéreas MT: Ver el comentario de la revisión de estudio, los apoyos verdes son nuevos y los negros son existentes. Revisar la categoría del apoyo (escrito en verde abajo se muestra una codificación que contrastar: Celosía-Amarre, altura del apoyo, tipo de cruceta, etc). Revisar tambien que coincida la planta del perfil, y que las afecciones marcadas coincidan con los cruzamientos y paralelismos sobre organismos afectados anteriormente comentados en el punto 4.7.2. (ríos, carreteras, etc)
•	Esquema unifilar de la red de MT (si aplica): revisar la representación del circuito, en verde se marca el tramo en el que se va a hacer la obra. En un CT se encuentra el detalle por dentro del CT (número de celdas con salidas correspondientes)

4.7.5.	Separatas Organismos afectados

Comprobación junto con el estudio que coinciden el número de separatas con las incluidas en la memoria. Chequeo de las afecciones, aunque debe ser la ingeniería quien vea esto con detalle en los diversos sistemas (SALEM), tanto documentos como organismos afectados detectados. Cada organismo tiene que tener su separata.
 
4.7.6.	Relación de bienes y derechos de los afectados (RBDA)

En proyectos con sustitución de apoyos, se verifica que el espacio adicional requerido esté reflejado en los planos y documentos, y que los permisos de los propietarios afectados se hayan solicitado correctamente.

Se consultan las parcelas impactadas en el catastro, identificando las referencias catastrales precisas. Posteriormente, se genera una petición en Lizentia para obtener los datos de los propietarios, los cuales son remitidos a la ingeniería para su gestión. Este proceso, aunque fuera de sistemas, debe estar documentado y trazado.

Las validaciones aseguran que todas las parcelas afectadas y sus propietarios estén correctamente registrados en la RBDA, junto con las autorizaciones pertinentes, garantizando trazabilidad, cumplimiento normativo y transparencia en la gestión.

Se genera una tabla con la identificación catastral (apoyos, m² afectados, vuelo y servidumbres), junto con el nombre del propietario, dirección, teléfono y naturaleza del terreno. Desde PDI se solicitan los datos registrales a través de Lizentia, que se incorporan al expediente y se comparten con las ingenierías para facilitar la gestión de permisos. Se comprueba el Excel con la relación individual, cuando la ingeniería utiliza formatos diferentes se tiene que unificar y cruzar la información del número de fincas y permisos con el Excel del detalle. 

Este Excel se incluye en la documentación inicial bajo el nombre “[Código proyecto]+RBD”, y se contrasta con el PDF “perm” del proyecto (el que hay que unificar el formato). Cuando en el Excel se refleja un NO, es necesario un fichero de expropiación “tramitaciones – expropiación”, con una portada (con el número de expediente, número de fincas y ayuntamiento y código de trabajo coincidentes) y el detalle de la relación de propietarios, bienes y derechos – expropiación (tiene que coincidir que todos los que tienen NO en el Excel, tienen que aparecer en el Word). Nota: se cruza la información por el número de apoyo.

Respecto a los planos complementarios de la RBD con la información georreferenciada y ortofoto de una parcela, estos planos tendrán representada la afección (zona de seguridad, ocupación, etc) y acotación a los elementos particulares (caminos, lindes, etc). Confirmar que hay un archivo DWG y que existe imagen aérea de las referencias catastrales . Tambien hay que cruzar la foto con el nombre del paraje con códigos.

4.7.7.	Gestión de permisos

El documento de permisos centraliza la validación de acuerdos entre UFD y los propietarios de las parcelas afectadas, asegurando la obtención de autorizaciones para paso y ubicación de instalaciones. Actualmente, la documentación es aportada por la ingeniería en distintos formatos (PDF, Excel, JPG) y requiere una unificación estandarizada para facilitar su revisión.

La validación comienza con la verificación de referencias catastrales para determinar cuántos permisos deben gestionarse. Luego, se revisa el informe PDF que resume los afectados, los acuerdos alcanzados y los intentos de consecución de permisos. Se clasifica la información en:
•	Parcelas gestionadas: Se confirma la documentación de contacto con los propietarios y la obtención del permiso. (Nota importante: En Coruña y Lugo, tramos no legalizados sin consecución de los permisos no se puede tramitar ni ejecutar)
•	Parcelas sin gestión: Casos donde no se logró contactar con el propietario.

Para la aprobación del permiso, se requiere acreditar la titularidad con documentos como certificado catastral, recibo de IBI, escritura de propiedad o justificante de pago. La validación finaliza con la aprobación de la Gestión de Permisos, tras la cual el proyecto puede ser aprobado automáticamente.

Este proceso garantiza la correcta gestión y trazabilidad de los permisos, evitando retrasos y asegurando la conformidad legal en cada proyecto.

4.8.	Validaciones a realizar en función de los documentos – BT (Baja Tensión)

Situaciones	Validaciones a realizar
Previo a realizar un encargo	•	Verificar la ficha técnica de la actuación a realizar
Memoria con cálculos descriptivos de la instalación y EBSS completo y Pliego de Condiciones Técnicas	•	Comprobar que están todos los documentos
•	Coherencia entre memoria y datos en carpetas de permisos
•	Información del emplazamiento 
•	Análisis de organismos afectados
•	Características técnicas
•	Cálculos mecánicos
•	Cumplimiento de normativa urbanística
Presupuestos – Elaborado en base a las Unidades Compatibles (UUCC)	•	Coherencia entre diseño técnico y UUCC reflejadas en los presupuestos cargados
•	Apoyos, crucetas, puestas a tierra, conductores, desmontajes y CTs (Centros de Transformación)
Planos generales de situación, emplazamiento, obra eléctrica y obra civil	•	Estándares técnicos y reglamentarios
•	Coherencia de infraestructura existente entre planos de obra eléctrica con instalación actual en Sistema_externo_1
Planos específicos	•	Plano licencia calle
•	Plano de perfil (en líneas aéreas) 

4.8.1.	Memoria con cálculos decriptivos de la instalación y EBSS (Estudio Básico de Seguridad y Salud) completo y Pliego de Condiciones Técnicas

En los proyectos de Baja Tensión (BT), la validación de documentos sigue un procedimiento similar al de Media Tensión (MT), con la diferencia de que la información suele encontrarse en las carpetas de permisos, donde se almacena toda la documentación relevante. La carpeta de permisos contiene la memoria, planos y demás documentos técnicos que requieren revisión.

Se incorporan verificaciones adicionales relacionadas con normativa urbanística, ya que cada concejo aplica sus propias Normas Urbanísticas y Ordenanzas de Aplicación, que deben consultarse en SALEM.

Inicialmente se realizan varias validaciones generales:
•	Verificar que el título del expediente coincida con la apertura del proyecto, junto con la validación de fechas y el código UD.
•	Se revisa que lo descrito en la memoria sea coherente con los planos y el presupuesto, asegurando que las actuaciones reflejadas (urbanización, reordenación, etc.) sean correctas.
•	Se confirma que la ubicación del proyecto coincide con la instalación, contrastando los datos con los sistemas internos.

Respecto a la Normativa Urbanística, se validan los siguientes aspectos:
•	Que el documento de memoria y reordenación urbanística incluya los aspectos urbanísticos del proyecto.
•	Se contrasta la normativa vigente de cada concejo, consultando la información disponible en SALEM.

Adicionalmente, se realizan distintas validaciones técnicas y de seguridad:
•	Validación de organismos afectados: Se revisan los permisos requeridos en función de la ubicación y normativa aplicable.
•	Revisión de cruzamientos y paralelismos: Se comprueba que los elementos proyectados no interfieran con otras infraestructuras y que se refleje correctamente en los permisos.
•	Verificación de características técnicas: Se valida que los datos del expediente coincidan con las especificaciones de las instalaciones proyectadas, asegurando coherencia en los elementos eléctricos.
•	Validación de los cálculos mecánicos (solo en líneas aéreas): Se revisa la tipología de conductores y apoyos proyectados. Al utilizarse programas de cálculo, se asume la corrección de los valores, pero se realiza una validación general.

4.8.2.	Presupuesto – Elaborado en base a las UUCC (Unidades Compatibles)

Se verifica que el presupuesto refleje con precisión las UUCC más representativas, asegurando coherencia con la documentación aportada. Se revisan elementos clave como apoyos, crucetas, puestas a tierra, conductores y desmontajes, validando que coincidan con lo proyectado.

Además, se comprueba que el presupuesto cargado por la ingeniería esté alineado con los planos y la memoria del proyecto

4.8.3.	Planos generales de situación, emplazamiento, obra eléctrica y obra civil

Se revisan los planos de obra eléctrica con especial atención, comparándolos con la instalación actual en Sistema_externo_1 para garantizar coherencia con la infraestructura existente. Además, se verifica que los planos de obra civil coincidan con los planos de instalación subterránea del conductor, asegurando una correcta integración del diseño.