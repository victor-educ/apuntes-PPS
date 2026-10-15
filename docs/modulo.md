# Presentación y evaluación

<p class="ut-meta">Módulo 5023 · Puesta en producción segura · Curso de especialización en ciberseguridad en entornos de las tecnologías de la información · 120 h oficiales · 59 sesiones de 1 h 50 min en el centro, lunes y jueves</p>

## De qué va el módulo

Una aplicación no se pone en producción solo porque funcione. Antes hay que saber cómo se ejecuta y cómo se prueba, qué nivel de seguridad exige por los riesgos que corre, qué fallos concretos tiene su versión web o móvil y cómo se despliega de forma reproducible y vigilada. El módulo recorre esas cinco preguntas, una unidad por cada resultado de aprendizaje, y en cada una se practica sobre aplicaciones y máquinas deliberadamente vulnerables del laboratorio, con la corrección al final de cada práctica ofensiva. La presentación con los conceptos que vertebran el curso está en la [página de inicio](index.md).

El módulo se cursa en el centro, sin formación en empresa: 59 sesiones de 110 minutos (unas 108 h) entre el 1 de octubre de 2026 y el 3 de junio de 2027. Hay dos evaluaciones. La primera cierra el 29 de enero, con el examen el jueves 28 de enero (RA1, RA2 y RA3). La segunda cierra el 4 de junio, con el examen el jueves 3 de junio (RA4 y RA5). Seis sesiones son de margen (8, 14, 27, 36, 47 y 58): sirven para recuperar lo perdido y para adelantar entregas, y no llevan hoja. El [calendario](calendario.md) da la fecha y el contenido de cada sesión.

Las prácticas evaluables no tienen sesión propia. Cada entrega se construye con las hojas de práctica de varias sesiones y se cierra por su plazo, que no se mueve aunque se pierda una clase: solo se mueve el contenido, que se recupera en las sesiones de margen o en casa.

## Resultados de aprendizaje

**Cada unidad de trabajo desarrolla un resultado de aprendizaje del currículo: la UT1 es el RA1, la UT2 el RA2, la UT3 el RA3, la UT4 el RA4 y la UT5 el RA5.** La unidad (UT) y el resultado de aprendizaje (RA) son, por tanto, lo mismo visto desde el centro y desde el currículo. Las entregas evaluables se numeran `ACT_UTn_k`, donde `n` es la unidad y `k` la entrega dentro de ella.

El currículo (Real Decreto 479/2020) define estos cinco resultados de aprendizaje, uno por unidad. Las tablas recogen los criterios de evaluación (CE) en lenguaje llano, la unidad y la entrega o la hoja de la que sale la evidencia de cada uno. El texto oficial de los criterios está en el [real decreto](https://www.boe.es/diario_boe/txt.php?id=BOE-A-2020-4963). Ningún criterio queda sin entrega.

**RA1. Prueba aplicaciones web y aplicaciones para dispositivos móviles analizando la estructura del código y su modelo de ejecución.** Unidad [UT1](ut/ut1-prueba-aplicaciones.md), 16 h.

| CE | Qué se pide | Evidencia |
|----|-------------|-----------|
| a | Comparar lenguajes de programación por sus características principales | [ACT_UT1_1](ut/ut1-prueba-aplicaciones.md#act_ut1_1-pruebas-de-aplicaciones) y [ACT_UT1_3](ut/ut1-prueba-aplicaciones.md#act_ut1_3-bash-programming) |
| b | Describir los modelos de ejecución de software | ACT_UT1_1 y [ACT_UT1_4](ut/ut1-prueba-aplicaciones.md#act_ut1_4-solidity-git) |
| c | Reconocer los elementos básicos del código fuente y su significado | [ACT_UT1_2](ut/ut1-prueba-aplicaciones.md#act_ut1_2-ejecucion-de-aplicaciones) |
| d | Ejecutar distintos tipos de prueba de software | ACT_UT1_2 |
| e | Evaluar los lenguajes según la infraestructura de seguridad que ofrecen | ACT_UT1_3 y ACT_UT1_4 |

**RA2. Determina el nivel de seguridad requerido por aplicaciones identificando los vectores de ataque habituales y sus riesgos asociados.** Unidad [UT2](ut/ut2-nivel-seguridad.md), 12 h.

| CE | Qué se pide | Evidencia |
|----|-------------|-----------|
| a | Caracterizar los niveles de verificación de ASVS | [ACT_UT2_1](ut/ut2-nivel-seguridad.md#act_ut2_1-owasp-asvs) (A2.2) |
| b | Identificar el nivel que exige una aplicación según sus riesgos | ACT_UT2_1 (A2.2) |
| c | Enumerar los requisitos de verificación del nivel elegido | ACT_UT2_1 (A2.2 y A2.3) y [ACT_UT2_2](ut/ut2-nivel-seguridad.md#act_ut2_2-seguridad-en-docker) |
| d | Reconocer los principales riesgos de las aplicaciones | ACT_UT2_1 (A2.1), ACT_UT2_2 y [ACT_UT2_3](ut/ut2-nivel-seguridad.md#act_ut2_3-seguridad-en-unix-xz) |

**RA3. Detecta y corrige vulnerabilidades de aplicaciones web analizando su código fuente y configurando servidores web.** Unidad [UT3](ut/ut3-vulnerabilidades-web.md), 26 h.

| CE | Qué se pide | Evidencia |
|----|-------------|-----------|
| a | Validar las entradas de los usuarios | [ACT_UT3_2](ut/ut3-vulnerabilidades-web.md#act_ut3_2-dvwa), [ACT_UT3_3](ut/ut3-vulnerabilidades-web.md#act_ut3_3-sql-injection) y [ACT_UT3_4](ut/ut3-vulnerabilidades-web.md#act_ut3_4-burp-suite-lado-servidor) |
| b | Detectar riesgos de inyección en el servidor y en el cliente | ACT_UT3_2, ACT_UT3_3, ACT_UT3_4 y [ACT_UT3_5](ut/ut3-vulnerabilidades-web.md#act_ut3_5-burp-suite-lado-cliente) |
| c | Gestionar correctamente la sesión del usuario | ACT_UT3_2 (A3.6) y ACT_UT3_5 |
| d | Usar roles para el control de acceso | ACT_UT3_4 (A3.10) |
| e | Almacenar contraseñas con algoritmos criptográficos seguros | [ACT_UT3_6](ut/ut3-vulnerabilidades-web.md#act_ut3_6-contrasenas-y-proteccion-frente-a-bots) (A3.11) |
| f | Configurar servidores web para reducir el riesgo de ataques conocidos | [ACT_UT3_1](ut/ut3-vulnerabilidades-web.md#act_ut3_1-server-hardening) (A3.1 a A3.4) |
| g | Frenar ataques a contraseñas, envíos masivos y altas automáticas (bots) | ACT_UT3_6 (A3.11) |

**RA4. Detecta problemas de seguridad en las aplicaciones para dispositivos móviles, monitorizando su ejecución y analizando ficheros y datos.** Unidad [UT4](ut/ut4-aplicaciones-moviles.md), 16 h.

| CE | Qué se pide | Evidencia |
|----|-------------|-----------|
| a | Comparar los modelos de permisos de las plataformas móviles | [ACT_UT4_1](ut/ut4-aplicaciones-moviles.md#act_ut4_1-android-app-vulnerable) (A4.2) |
| b | Describir técnicas de almacenamiento seguro de datos en el dispositivo | ACT_UT4_1 (A4.4) |
| c | Validar las compras integradas en el servidor | [ACT_UT4_2](ut/ut4-aplicaciones-moviles.md#act_ut4_2-pivaa) (A4.7) |
| d | Detectar protocolos inseguros con herramientas de monitorización de tráfico | ACT_UT4_2 (A4.5) |
| e | Inspeccionar binarios de aplicaciones móviles para buscar fugas de información | ACT_UT4_1 (A4.1 y A4.3) y ACT_UT4_2 (A4.6) |

**RA5. Implanta sistemas seguros de desplegado de software, utilizando herramientas para la automatización de la construcción de sus elementos.** Unidad [UT5](ut/ut5-despliegue-seguro.md), 44 h.

| CE | Qué se pide | Evidencia |
|----|-------------|-----------|
| a | Identificar los principios y objetivos de la integración de desarrollo y operación (DevOps) | [ACT_UT5_1](ut/ut5-despliegue-seguro.md#act_ut5_1-jenkins) (A5.1) |
| b | Implantar control de versiones con los roles y permisos pedidos | ACT_UT5_1 (A5.2) |
| c | Instalar, configurar y verificar la integración continua conectada al control de versiones | ACT_UT5_1 (A5.3 a A5.7) y [proyecto integrador](ut/ut5-despliegue-seguro.md#proyecto-integrador) |
| d | Planificar, implementar y automatizar planes de despliegue | [ACT_UT5_2](ut/ut5-despliegue-seguro.md#act_ut5_2-terraform-y-ansible), [ACT_UT5_4](ut/ut5-despliegue-seguro.md#act_ut5_4-k3s-y-k9s) y proyecto integrador |
| e | Evaluar si el sistema desplegado reacciona solo a los fallos | ACT_UT5_4, [ACT_UT5_3](ut/ut5-despliegue-seguro.md#act_ut5_3-prometheus-y-grafana), [ACT_UT5_5](ut/ut5-despliegue-seguro.md#act_ut5_5-fallos-y-recuperacion) y proyecto integrador |
| f | Documentar tareas y procedimientos de recuperación ante desastres | ACT_UT5_5 (A5.18) y proyecto integrador |
| g | Crear bucles de retroalimentación ágiles entre los miembros del equipo | ACT_UT5_5 (retrospectiva de la A5.18) |

## Cómo se evalúa

La nota de cada resultado de aprendizaje sale de dos instrumentos: las prácticas evaluables de su unidad y el examen de su evaluación. Las unidades se evalúan por separado y la nota final del módulo pondera los cinco RA, con un criterio doble: la media entre el peso de cada unidad por horas y su peso por número de criterios de evaluación. Es la propuesta del curso y está pendiente de confirmar con la programación didáctica.

| Resultado de aprendizaje | Peso en la nota final | Evaluación | Examen |
|--------------------------|----------------------:|------------|--------|
| RA1 · Prueba de aplicaciones | 15 % | 1ª | jueves 28 de enero |
| RA2 · Nivel de seguridad requerido | 12 % | 1ª | jueves 28 de enero |
| RA3 · Vulnerabilidades web | 25 % | 1ª | jueves 28 de enero |
| RA4 · Aplicaciones móviles | 16 % | 2ª | jueves 3 de junio |
| RA5 · Despliegue seguro | 32 % | 2ª | jueves 3 de junio |

Dentro de cada RA, **el 40 % son las prácticas evaluables y el 60 % el examen**. Hace falta un 5 en cada RA para aprobar el módulo. Un RA suspendido se recupera con los mismos instrumentos y los mismos pesos.

### Prácticas evaluables y entregas

La parte de prácticas de cada RA se reparte así: **un 10 % son los retos de Atenea** y **el 90 % restante lo reparten las entregas** de la unidad, con los pesos de la tabla siguiente. Los pesos son proporcionales al trabajo de cada entrega (número de hojas de las que sale) y a los criterios que solo ella cubre. Dentro de cada entrega, la tabla de criterios con sus pesos, que suman 100 %, está al final de la unidad, en su sección *Prácticas evaluables de la unidad*. Todos los plazos vencen a las 23:59 (hora de Madrid) del día indicado.

| Entrega | Hojas | Plazo | CE | Peso en las prácticas del RA | Peso en el RA |
|---------|-------|-------|----|-----------------------------:|--------------:|
| ACT_UT1_1 · Pruebas de aplicaciones | A1.2, A1.3 | jueves 22 de octubre | a, b | 22,5 % | 9 % |
| ACT_UT1_2 · Ejecución de aplicaciones | A1.4, A1.5 | jueves 29 de octubre | c, d | 22,5 % | 9 % |
| ACT_UT1_3 · Bash programming | A1.6 | lunes 2 de noviembre | a, e | 22,5 % | 9 % |
| ACT_UT1_4 · Solidity + Git | A1.7 | jueves 5 de noviembre | b, e | 22,5 % | 9 % |
| ACT_UT2_1 · OWASP ASVS | A2.1, A2.2, A2.3 | lunes 16 de noviembre | a, b, c, d | 40 % | 16 % |
| ACT_UT2_2 · Seguridad en Docker | A2.4 | lunes 23 de noviembre | c, d | 25 % | 10 % |
| ACT_UT2_3 · Seguridad en Unix (xz) | A2.5 | jueves 26 de noviembre | d | 25 % | 10 % |
| ACT_UT2_4 · Ransomware (optativa) | reserva de la sesión 14 | jueves 26 de noviembre, si se hace | c, d | sin peso fijo (ampliación) | |
| ACT_UT3_1 · Server hardening | A3.1 a A3.4 | lunes 14 de diciembre | f | 20 % | 8 % |
| ACT_UT3_2 · DVWA | A3.5 a A3.7 | lunes 11 de enero | a, b, c | 20 % | 8 % |
| ACT_UT3_3 · SQL Injection | A3.8 | lunes 25 de enero | a, b | 15 % | 6 % |
| ACT_UT3_4 · Burp Suite, lado servidor | A3.9, A3.10 | lunes 25 de enero | a, b, d | 15 % | 6 % |
| ACT_UT3_5 · Burp Suite, lado cliente | A3.12 | lunes 25 de enero | b, c | 10 % | 4 % |
| ACT_UT3_6 · Contraseñas y protección frente a bots | A3.11 | lunes 25 de enero | e, g | 10 % | 4 % |
| ACT_UT4_1 · Android App Vulnerable | A4.1 a A4.4 | lunes 15 de febrero | a, b, e | 50 % | 20 % |
| ACT_UT4_2 · PIVAA | A4.5 a A4.7 | jueves 25 de febrero | c, d, e | 40 % | 16 % |
| ACT_UT5_1 · Jenkins | A5.1 a A5.7 | jueves 15 de abril | a, b, c | 20 % | 8 % |
| ACT_UT5_2 · Terraform y Ansible | A5.8 a A5.11 | lunes 3 de mayo | d | 12 % | 4,8 % |
| ACT_UT5_4 · K3s y K9s | A5.12 a A5.14 | jueves 13 de mayo | d, e | 12 % | 4,8 % |
| ACT_UT5_3 · Prometheus y Grafana | A5.15, A5.16 | lunes 17 de mayo | e | 10 % | 4 % |
| ACT_UT5_5 · Fallos y recuperación | A5.17, A5.18 | lunes 24 de mayo | e, f, g | 16 % | 6,4 % |
| Proyecto integrador | A5.19, A5.20 | lunes 31 de mayo | c, d, e, f | 20 % | 8 % |

Los pesos de cada RA suman 90 % de la parte de prácticas (RA1: 4 x 22,5; RA2: 40 + 25 + 25; RA3: 20 + 20 + 15 + 15 + 10 + 10; RA4: 50 + 40; RA5: 20 + 12 + 12 + 10 + 16 + 20) y el 10 % que falta es Atenea. La A1.1 (puesto de trabajo) no se califica. ACT_UT5_4 vence antes que ACT_UT5_3 porque sus hojas se dan antes. Los enunciados originales están en el aula; ACT_UT5_5, ACT_UT3_6 y el proyecto integrador son entregas nuevas y su enunciado es el de la unidad.

### Atenea

Atenea es una plataforma web de retos de ciberseguridad del tipo *captura la bandera* (CTF), mantenida por el CCN-CERT, el equipo de respuesta a incidentes del Centro Criptológico Nacional. Aquí sirve para practicar por cuenta propia: se resuelven retos reales de criptografía, seguridad web, análisis forense y otras áreas que refuerzan lo trabajado en clase. Se accede registrándose con el correo de la Generalitat en [https://atenea.ccn-cert.cni.es](https://atenea.ccn-cert.cni.es). Cuenta como **el 10 % de la parte de prácticas de cada RA**: el entregable es la captura del nivel de logro y se califica por regla de tres sobre los puntos conseguidos. Los retos de RA1 y RA2 puntúan en esos dos RA y se entregan hasta el lunes 25 de enero; los de RA3, RA4 y RA5 se reparten a partes iguales entre esos tres RA y se entregan hasta el lunes 31 de mayo.

### Exámenes

Cada examen es una prueba en el laboratorio, con una parte de test y una parte práctica, y tiene una sección por cada RA para que la nota de cada uno se calcule por separado.

| Examen | Fecha | Qué entra |
|--------|-------|-----------|
| 1ª evaluación | jueves 28 de enero de 2027 (sesión 28) | RA1, RA2 y RA3: los contenidos y las técnicas de las hojas de UT1, UT2 y UT3 |
| 2ª evaluación | jueves 3 de junio de 2027 (sesión 59) | RA4 y RA5: los contenidos y las técnicas de las hojas de UT4 y UT5 |

Las sesiones de margen 27 y 58 son el repaso previo de cada examen, y las fechas de los exámenes no se mueven.

!!! examen "Qué se evalúa en el examen"
    Lo que se ha hecho en las hojas: quien ha ejecutado cada práctica y ha entendido su corrección puede repetirla. Los exámenes no piden herramientas que no se hayan usado en el laboratorio.

### Plazos, formato y recuperación

- **Plazo.** Siempre a las 23:59 (hora de Madrid) del día indicado, y no se mueve aunque se pierda una clase. Fuera de plazo y sin causa justificada, la entrega se corrige sobre el 50 %.
- **Formato.** Las entregas que son documento se suben a Aules en PDF con el formato de la *Normativa de entrega de documentos* del aula (`Normativa_entrega_trabajos.pdf`, con la plantilla `Plantilla_memoria_tarea` en `.docx` y `.odt`): portada, índice, introducción, desarrollo, bibliografía y conclusión; márgenes de 3 cm a los lados y 2,5 cm arriba y abajo, texto a 12 pt e interlineado 1,5, y figuras con su pie. Un documento que no la cumple se corrige como no evaluado. Las entregas que son repositorio se entregan con la URL de `pps-entregas` en la tarea, con un `README.md` por hoja (ver [Repositorio de entregas](laboratorio.md#repositorio-de-entregas)).
- **Secretos.** Ninguna contraseña, token ni clave va en un repositorio, en su historial ni en una captura: se descuenta y obliga a rotarlo.
- **Recuperación.** Un RA suspendido se recupera con los mismos instrumentos y los mismos pesos que se aplicaron: las entregas pendientes y el examen de ese RA.
- **Faltas de asistencia.** Las reglas de asistencia, justificación y pérdida de evaluación continua son las de la programación didáctica del módulo y del centro; esta página no las repite.

## Herramientas del módulo

Cada unidad se apoya en un conjunto pequeño de herramientas, todas gratuitas y instaladas en el puesto de trabajo o en las máquinas del [laboratorio](laboratorio.md). La tabla dice para qué sirve cada una y en qué unidad se explica a fondo.

| Herramienta | Para qué se usa | Unidad |
|-------------|-----------------|--------|
| VirtualBox, Ubuntu, Docker, Git y VS Code | Puesto de trabajo (`pps01`) y contenedores para levantar las aplicaciones de práctica | [UT1](ut/ut1-prueba-aplicaciones.md) |
| gdb, `unittest`, `go test`, ShellCheck | Depurar y probar código en ensamblador, Python, Go y Bash, y buscar patrones inseguros | [UT1](ut/ut1-prueba-aplicaciones.md) |
| Solidity y GitHub | Contratos inteligentes y control de versiones, con el repositorio de entregas | [UT1](ut/ut1-prueba-aplicaciones.md) |
| OWASP Top 10, CWE, CVE y ASVS | Catálogos de riesgos y de requisitos para fijar el nivel de seguridad de una aplicación | [UT2](ut/ut2-nivel-seguridad.md) |
| Trivy y Syft | Analizar imágenes de contenedor y listar sus componentes (cadena de suministro) | [UT2](ut/ut2-nivel-seguridad.md) |
| Apache, Nginx, OpenSSL y ModSecurity | Endurecer un servidor web, cifrar con TLS y filtrar peticiones con un cortafuegos de aplicación | [UT3](ut/ut3-vulnerabilidades-web.md) |
| DVWA y Burp Suite | Aplicación vulnerable de práctica y proxy de interceptación para atacarla y corregirla | [UT3](ut/ut3-vulnerabilidades-web.md) |
| fail2ban, bcrypt y argon2 | Frenar ataques a contraseñas y bots, y guardar contraseñas con hashes lentos | [UT3](ut/ut3-vulnerabilidades-web.md) |
| adb, emulador y Genymotion | Instalar, ejecutar y observar aplicaciones Android en un dispositivo virtual | [UT4](ut/ut4-aplicaciones-moviles.md) |
| apktool, JADX y MobSF | Descompilar y analizar de forma estática una aplicación móvil | [UT4](ut/ut4-aplicaciones-moviles.md) |
| drozer y Burp Suite | Explotar componentes expuestos y capturar el tráfico de la aplicación | [UT4](ut/ut4-aplicaciones-moviles.md) |
| Maven, Jenkins y OWASP Dependency-Check | Construir, integrar y analizar dependencias en un pipeline seguro | [UT5](ut/ut5-despliegue-seguro.md) |
| Terraform y Ansible | Crear la infraestructura y configurarla de forma reproducible | [UT5](ut/ut5-despliegue-seguro.md) |
| K3s y K9s (con k3d si el equipo no admite una VM) | Orquestar contenedores que se recuperan solos de un fallo | [UT5](ut/ut5-despliegue-seguro.md) |
| Prometheus y Grafana | Medir el sistema desplegado y visualizar su estado | [UT5](ut/ut5-despliegue-seguro.md) |

Las plataformas de aprendizaje a ritmo propio (CryptoZombies, Learn Git Branching, PortSwigger Academy y Atenea) se tratan en el apartado de [metodología](#metodologia).

## Sobre el material

**Autoría.** Estos apuntes los ha escrito el profesor de la asignatura con el apoyo de Claude, el asistente de IA de Anthropic, que ha intervenido en la redacción, la ampliación y la revisión a partir de la planificación del curso. No se oculta: la revisión final y la responsabilidad de lo que dice el texto son del profesor, y los errores que queden se corrigen durante el curso.

**Licencia.** El texto propio de estos apuntes se publica con la licencia [Creative Commons Reconocimiento-CompartirIgual 4.0 (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.es): se puede copiar, adaptar y redistribuir citando la fuente y manteniendo la misma licencia.

**Material de terceros.** No se copia. Las herramientas, los laboratorios y las aplicaciones vulnerables de las prácticas tienen sus propios autores y licencias: se enlazan a su origen y se usan tal como los publica cada fuente. Los esquemas de estas páginas son propios y no incluyen imágenes de terceros.

**El aula de Aules.** Es el espacio del curso en la plataforma del centro. En ella se entregan las prácticas evaluables y están la normativa y la plantilla de entrega, los enunciados de las entregas y las rúbricas. Estos apuntes explican y guían; el aula recibe el trabajo.

## Metodología

Cada sesión de 110 minutos combina una explicación breve y una parte larga de laboratorio. El [calendario](calendario.md) dice qué se explica y qué se practica cada día, y de qué tipo es la sesión: teoría y práctica, solo práctica, margen o examen.

**Explicación breve.** Cada apartado técnico empieza por lo que se quiere conseguir y qué herramienta se usa para qué, y solo después entra en el detalle. El texto está escrito para leerse por cuenta propia, antes y después de la clase: quien ha faltado a una sesión puede recuperarla con la unidad.

**Hoja de práctica.** Cada sesión con laboratorio tiene su hoja, escrita en segunda persona y con la misma estructura: objetivo, requisitos previos, pasos, comprobación y entrega. Las prácticas ofensivas terminan con la corrección: no basta con encontrar el fallo, hay que arreglarlo y comprobar que el ataque ya no funciona. El detalle que no cambia lo que se teclea o se decide queda fuera del hilo principal.

**Entrega.** Todo lo que se hace se documenta en el momento: una captura con la fecha, la salida de un comando, el fichero de configuración. La práctica evaluable de cada unidad se construye con esa documentación, por lo que quien la va recogiendo sobre la marcha llega al plazo con el trabajo casi hecho. Las entregas son un documento en PDF en Aules o un repositorio de GitHub con un `README.md` por hoja, según indique cada una. Los plazos y las penalizaciones están en [Plazos, formato y recuperación](#plazos-formato-y-recuperacion).

**Márgenes del documento.** Las entregas en documento siguen la *Normativa de entrega de documentos* del aula: márgenes de 3 cm a los lados y 2,5 cm arriba y abajo, texto a 12 pt con interlineado 1,5, portada, índice, introducción, desarrollo, bibliografía y conclusión, y figuras con su pie.

**Plataformas a ritmo propio.** CryptoZombies, Learn Git Branching, PortSwigger Academy y Atenea se empiezan en clase y se completan en casa antes del plazo de la entrega correspondiente. Marcan el ritmo de cada alumno sin depender de la sesión, y su nivel de logro se recoge con una captura. Atenea es, además, un 10 % de la parte de prácticas de cada RA, como se explica en [Atenea](#atenea).
