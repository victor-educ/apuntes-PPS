# Glosario

Términos y siglas que aparecen en el módulo, explicados en una a tres líneas y con el enlace a la sesión donde se tratan a fondo. Si un término no está, el buscador de la barra de arriba lo localiza: casi seguro que aparece en alguna unidad.

**Ansible** · Herramienta de gestión de la configuración: ejecuta por SSH tareas descritas en YAML (playbooks) sobre un inventario de máquinas, sin instalar agente en el destino. [UT5, sesión 46](ut/ut5-despliegue-seguro.md#ansible-inventario-modulos-y-playbooks).

**Apache** · Servidor web muy extendido (`httpd`). En el módulo se ejecuta en un contenedor y es la base de las cuatro imágenes de endurecimiento de la UT3. [UT3, sesión 15](ut/ut3-vulnerabilidades-web.md#apache-y-su-configuracion-basica).

**API (interfaz de programación)** · Conjunto de funciones y servicios que un componente ofrece a otros. En Android, el nivel de API identifica la versión de la plataforma (el laboratorio usa la 23). [UT4, sesión 29](ut/ut4-aplicaciones-moviles.md#arquitectura-de-android-e-ios).

**APK** · Paquete en el que se distribuye una aplicación de Android: un fichero comprimido con el manifiesto, el código compilado, los recursos y la firma. Se puede descomprimir y descompilar para inspeccionarlo. [UT4, sesión 29](ut/ut4-aplicaciones-moviles.md#estructura-de-un-apk-y-owasp-mobile-top-10).

**ARM** · Familia de procesadores de bajo consumo que domina en móviles. iOS solo corre sobre ARM y solo se instala en hardware de su fabricante, lo que limita las pruebas sin dispositivo. [UT4, sesión 29](ut/ut4-aplicaciones-moviles.md#arquitectura-de-android-e-ios).

**Artefacto** · Resultado de una etapa del pipeline que se conserva: un paquete, una imagen, un informe de pruebas. Se firma o se calcula su huella para poder comprobar que no ha cambiado. [UT5, sesión 43](ut/ut5-despliegue-seguro.md#secretos-en-el-pipeline-y-firma-de-artefactos).

**ASVS (Application Security Verification Standard)** · Estándar de OWASP con los requisitos de seguridad que se verifican en una aplicación, agrupados por capítulos y por tres niveles (L1, L2 y L3). El nivel se elige según el riesgo de la aplicación. [UT2, sesión 10](ut/ut2-nivel-seguridad.md#owasp-asvs-que-es-y-su-estructura-por-capitulos).

**Bytecode** · Código intermedio que ejecuta una máquina virtual (CPython, JVM, EVM) en lugar de la CPU. Es el tercer modelo de ejecución, junto al compilado y al interpretado. [UT1, sesión 2](ut/ut1-prueba-aplicaciones.md#compilados-interpretados-y-con-maquina-virtual).

**Burp Suite** · Proxy de interceptación con el que se ve, modifica y repite el tráfico HTTP entre el navegador y una aplicación. Es la herramienta de las sesiones 23, 24 y 26. [UT3, sesión 23](ut/ut3-vulnerabilidades-web.md#que-hace-burp-suite).

**CASB (intermediario de seguridad de acceso a la nube)** · Servicio situado entre los dispositivos de una organización y las aplicaciones en la nube que usan, para aplicar sus políticas de seguridad. [UT4, sesión 35](ut/ut4-aplicaciones-moviles.md#casb).

**cgroups** · Mecanismo del núcleo de Linux que limita los recursos (CPU, memoria) de un grupo de procesos. Junto con los namespaces, es lo que aísla un contenedor. [UT2, sesión 12](ut/ut2-nivel-seguridad.md#namespaces-y-cgroups-el-aislamiento-de-un-contenedor).

**Commit** · Punto guardado del historial de Git: una instantánea del proyecto con autor, fecha y mensaje. Las ramas y las fusiones se construyen sobre ellos. [UT1, sesión 7](ut/ut1-prueba-aplicaciones.md#git-ramas-fusiones-y-remotos).

**Compilador** · Programa que traduce el código fuente a código de máquina (o a bytecode) antes de ejecutarlo. Se contrapone al intérprete, que traduce mientras ejecuta. [UT1, sesión 2](ut/ut1-prueba-aplicaciones.md#compilados-interpretados-y-con-maquina-virtual).

**Cookie** · Pequeño dato que el servidor entrega al navegador y este devuelve en cada petición; suele guardar el identificador de sesión. Sus atributos (`Secure`, `HttpOnly`, `SameSite`) reducen el robo de sesión. [UT3, sesión 20](ut/ut3-vulnerabilidades-web.md#robo-y-fijacion-de-sesion-atributos-de-las-cookies).

**CORS** · Mecanismo por el que un servidor indica a qué otros orígenes permite leer sus respuestas desde el navegador. Relaja la política del mismo origen, y configurado sin cuidado abre la puerta a robos de datos. [UT3, sesión 26](ut/ut3-vulnerabilidades-web.md#cors-y-la-politica-del-mismo-origen).

**CPU** · Procesador que ejecuta las instrucciones de un programa. Entender qué hace con el código explica los modelos de ejecución y lo que muestra un depurador. [UT1, sesión 2](ut/ut1-prueba-aplicaciones.md#de-la-cpu-al-programa-en-marcha).

**CRS (OWASP Core Rule Set)** · Conjunto de reglas genéricas de la fundación OWASP que ModSecurity aplica para bloquear peticiones con patrones de ataque. Se ajusta con un nivel de paranoia. [UT3, sesión 17](ut/ut3-vulnerabilidades-web.md#modsecurity-y-owasp-crs).

**CSP (Content Security Policy)** · Cabecera HTTP con la que el servidor indica al navegador de dónde puede cargar scripts, estilos e imágenes. Es la contramedida principal contra XSS. [UT3, sesión 16](ut/ut3-vulnerabilidades-web.md#hsts-y-csp).

**CSRF (falsificación de petición en sitios cruzados)** · Ataque que hace que el navegador de una víctima autenticada envíe una petición no deseada a una aplicación. Se frena con tokens antifalsificación y con la cookie `SameSite`. [UT3, sesión 20](ut/ut3-vulnerabilidades-web.md#csrf-y-sus-contramedidas).

**CSV** · Formato de texto para tablas, con los valores separados por comas. ASVS publica en él la lista de requisitos, y hay que descargar la de la versión 4.0.3 para que los identificadores coincidan. [UT2, sesión 11](ut/ut2-nivel-seguridad.md#verificar-un-requisito-donde-con-que-tecnica-y-con-que-prueba).

**CVE** · Identificador único de una vulnerabilidad concreta y conocida (`CVE-año-número`). Es la referencia común entre herramientas, avisos y bases de datos. [UT2, sesión 9](ut/ut2-nivel-seguridad.md#fuentes-abiertas-de-vulnerabilidades-owasp-top-10-cwe-y-cve).

**CVSS** · Sistema que puntúa de 0 a 10 la gravedad de una vulnerabilidad según cómo se explota y qué daño causa. La puntuación ayuda a priorizar, pero no sustituye al contexto de la aplicación. [UT2, sesión 9](ut/ut2-nivel-seguridad.md#cvss-puntuar-la-gravedad).

**CWE** · Catálogo de tipos de debilidad de software (`CWE-79` es el XSS). Clasifica la causa; el CVE identifica cada caso concreto. [UT2, sesión 9](ut/ut2-nivel-seguridad.md#fuentes-abiertas-de-vulnerabilidades-owasp-top-10-cwe-y-cve).

**Denegación de servicio (DoS)** · Ataque que agota los recursos de un servicio para que deje de atender a los usuarios legítimos. En Apache se mitiga con límites de tiempo y de conexiones. [UT3, sesión 18](ut/ut3-vulnerabilidades-web.md#denegacion-de-servicio-y-su-mitigacion-en-apache).

**Dependency-Check** · Herramienta de OWASP que compara las dependencias de un proyecto con las vulnerabilidades conocidas (CVE) y genera un informe. En el pipeline seguro rompe la construcción si supera un umbral de gravedad. [UT5, sesión 43](ut/ut5-despliegue-seguro.md#analisis-de-dependencias-con-owasp-dependency-check).

**Depurador** · Herramienta que ejecuta un programa paso a paso, con puntos de parada, y deja ver registros, memoria y variables. Se usa con ensamblador, Python y Go. [UT1, sesión 3](ut/ut1-prueba-aplicaciones.md#que-hace-un-depurador).

**DevOps** · Forma de trabajar que integra desarrollo y operación con automatización y bucles de retroalimentación rápidos. Su versión con la seguridad incorporada al ciclo se llama a veces DevSecOps. [UT5, sesión 37](ut/ut5-despliegue-seguro.md#principios-y-objetivos-de-devops).

**DIVA (Damn Insecure and Vulnerable App)** · Aplicación de Android vulnerable a propósito, con un reto por cada fallo típico: registros, almacenamiento inseguro, credenciales en el código. Se usa para practicar el análisis estático. [UT4, sesión 31](ut/ut4-aplicaciones-moviles.md#ingenieria-inversa-de-apk-a-codigo-legible).

**Dockerfile** · Fichero con las instrucciones para construir una imagen de contenedor. En el módulo se endurece (usuario sin privilegios, imagen base mínima) y se usa en el pipeline. [UT5, sesión 42](ut/ut5-despliegue-seguro.md#dockerfile-y-compose-de-pps-app).

**DOM (modelo de objetos del documento)** · Representación en árbol de la página que el navegador construye y que el JavaScript modifica. En el XSS basado en DOM el fallo está en el código del cliente, no en la respuesta del servidor. [UT3, sesión 19](ut/ut3-vulnerabilidades-web.md#xss-reflejado-almacenado-y-basado-en-dom).

**DVWA (Damn Vulnerable Web Application)** · Aplicación web vulnerable a propósito, en PHP, con niveles de dificultad. Se ejecuta en un contenedor y en una red aislada para practicar XSS, CSRF, inyecciones y fallos de sesión. [UT3, sesión 19](ut/ut3-vulnerabilidades-web.md#xss-reflejado-almacenado-y-basado-en-dom).

**Ensamblador** · Lenguaje de bajo nivel casi idéntico a las instrucciones de la CPU, con un mnemónico por instrucción. Se lee y se depura para ver qué hace realmente un programa. [UT1, sesión 3](ut/ut1-prueba-aplicaciones.md#que-hace-un-depurador).

**Escalada de privilegios** · Conseguir más permisos de los asignados, ya sea sobre los de otro usuario (horizontal) o sobre los de un rol superior (vertical). Se relaciona con IDOR y con un control de acceso mal hecho. [UT3, sesión 24](ut/ut3-vulnerabilidades-web.md#idor-y-escalada-de-privilegios).

**EVM (máquina virtual de Ethereum)** · Máquina virtual que ejecuta el bytecode de los contratos inteligentes en todos los nodos de la red. Cada operación consume gas, que impide los bucles infinitos. [UT1, sesión 7](ut/ut1-prueba-aplicaciones.md#la-maquina-virtual-de-ethereum).

**Fail2ban** · Servicio que lee los registros, detecta intentos repetidos de acceso fallido y bloquea la IP de origen con el cortafuegos durante un tiempo. [UT3, sesión 25](ut/ut3-vulnerabilidades-web.md#fuerza-bruta-y-bots-limite-de-intentos-captcha-y-fail2ban).

**Firma de artefactos** · Firma criptográfica de un paquete o una imagen para que quien lo despliega compruebe su origen y que no se ha alterado en el camino. [UT5, sesión 43](ut/ut5-despliegue-seguro.md#integridad-y-firma-del-artefacto).

**Fuerza bruta** · Ataque que prueba muchas contraseñas (o valores) hasta acertar. Se frena con un límite de intentos, CAPTCHA y bloqueo por IP. [UT3, sesión 25](ut/ut3-vulnerabilidades-web.md#fuerza-bruta-y-bots-limite-de-intentos-captcha-y-fail2ban).

**Git** · Sistema de control de versiones distribuido. Guarda el historial en commits, permite ramas y fusiones y se sincroniza con remotos como GitHub. [UT1, sesión 7](ut/ut1-prueba-aplicaciones.md#git-ramas-fusiones-y-remotos).

**Gradle** · Sistema de construcción alternativo a Maven, que configura el proyecto con un script en lugar de un XML. En el módulo se desarrolla Maven y este se explica como correspondencia. [UT5, sesión 39](ut/ut5-despliegue-seguro.md#maven-frente-a-gradle).

**Grafana** · Herramienta de paneles y alertas que se conecta a fuentes de datos como Prometheus para mostrar las métricas de un sistema. [UT5, sesión 53](ut/ut5-despliegue-seguro.md#paneles-fuentes-de-datos-y-alertas-en-grafana).

**Hardening (endurecimiento)** · Reducir la superficie de ataque de un sistema: quitar lo que no se usa, aplicar permisos mínimos y configurar las cabeceras y los límites adecuados. [UT3, sesión 18](ut/ut3-vulnerabilidades-web.md#buenas-practicas-de-hardening).

**Hash** · Resumen de longitud fija que se calcula a partir de unos datos y no se puede invertir. Para contraseñas se usa un algoritmo lento con sal (bcrypt, Argon2), no uno rápido como MD5. [UT3, sesión 25](ut/ut3-vulnerabilidades-web.md#almacenamiento-de-contrasenas-hash-sal-y-algoritmos-modernos).

**HMAC** · Código que combina una clave secreta con los datos mediante un hash. Demuestra que el mensaje viene de quien tiene la clave y que no se ha modificado; el servidor de compras de la A4.7 lo usa en los recibos. [UT4, sesión 35](ut/ut4-aplicaciones-moviles.md#validacion-de-compras-integradas).

**HSTS** · Cabecera con la que el servidor ordena al navegador usar solo HTTPS con ese dominio durante un tiempo, lo que evita degradaciones a HTTP. [UT3, sesión 16](ut/ut3-vulnerabilidades-web.md#hsts-y-csp).

**HTML** · Lenguaje de marcado con el que se describe el contenido de una página web. Es también el sitio donde se inyecta el script en un XSS. [UT3, sesión 15](ut/ut3-vulnerabilidades-web.md#arquitectura-de-una-aplicacion-web).

**HTTP** · Protocolo de petición y respuesta entre navegador y servidor: método, ruta, cabeceras, cuerpo y código de estado. Sin cifrar, cualquiera en la red lo lee. [UT3, sesión 15](ut/ut3-vulnerabilidades-web.md#el-protocolo-http).

**HTTPS** · HTTP sobre TLS: el mismo protocolo, cifrado y con el servidor autenticado por un certificado. [UT3, sesión 16](ut/ut3-vulnerabilidades-web.md#certificados-y-tls-en-apache).

**IDOR** · Referencia directa a un objeto sin control de acceso: la aplicación entrega el recurso que indica un identificador de la petición (`?id=7`) sin comprobar que pertenece a quien lo pide. Se corrige comprobando la propiedad en el servidor. [UT3](ut/ut3-vulnerabilidades-web.md#idor-y-escalada-de-privilegios).

**INCIBE** · Instituto Nacional de Ciberseguridad. Su guía sobre ransomware es la lectura de partida de la actividad optativa de análisis de un ransomware de laboratorio. [UT2](ut/ut2-nivel-seguridad.md#act_ut2_4-analisis-de-un-ransomware-optativa).

**Jenkinsfile** · Fichero de texto, guardado en el repositorio junto al código, que describe el pipeline de Jenkins. Al versionarse con la aplicación, cada cambio del proceso queda revisado y con historial. [UT5](ut/ut5-despliegue-seguro.md#el-jenkinsfile-en-el-repositorio).

**MD5** · Función hash rápida y obsoleta. Se diseñó para ser veloz, no para proteger contraseñas: un equipo doméstico calcula miles de millones por segundo, así que no sirve para guardarlas. Se usa bcrypt o argon2. [UT3](ut/ut3-vulnerabilidades-web.md#almacenamiento-de-contrasenas-hash-sal-y-algoritmos-modernos).

**namespace** · Mecanismo del núcleo de Linux que da a un proceso su propia vista de un recurso (procesos, red, montajes, usuarios). Junto con los cgroups, que limitan el consumo, es lo que aísla un contenedor. [UT2](ut/ut2-nivel-seguridad.md#namespaces-y-cgroups-el-aislamiento-de-un-contenedor).

**NASM** · Ensamblador que traduce mnemónicos a código máquina x86-64. Junto con `ld`, que enlaza, produce el ejecutable que se depura en las primeras sesiones. [UT1](ut/ut1-prueba-aplicaciones.md#a12-ensamblador-lectura-y-ejecucion-sesion-2).

**NIA** · Número de identificación del alumno. Forma el nombre de usuario de las cuentas del módulo (`pps<NIA>`). [UT1](ut/ut1-prueba-aplicaciones.md#puesto-de-trabajo-reproducible).

**NVD** · Base de datos nacional de vulnerabilidades de EE. UU. Cada CVE tiene ahí su ficha con la puntuación CVSS y los productos afectados; es la base que descarga Dependency-Check. [UT2](ut/ut2-nivel-seguridad.md#fuentes-abiertas-de-vulnerabilidades-owasp-top-10-cwe-y-cve), [UT5](ut/ut5-despliegue-seguro.md#analisis-de-dependencias-con-owasp-dependency-check).

**PHP** · Lenguaje de servidor en que están escritas DVWA y buena parte de las aplicaciones web vulnerables del curso. Se estudia como ejemplo de aplicación web, no como lenguaje a aprender. [UT3](ut/ut3-vulnerabilidades-web.md#arquitectura-de-una-aplicacion-web).

**pipeline** · Secuencia automática de etapas (construir, probar, analizar, empaquetar, desplegar) que recorre cada cambio del código. Es el sitio donde se colocan los controles de seguridad. [UT5](ut/ut5-despliegue-seguro.md#el-ciclo-de-entrega-y-donde-entra-la-seguridad).

**PIVAA** · Aplicación Android deliberadamente vulnerable que se usa en el taller de vulnerabilidades móviles y en una de las prácticas evaluables de la UT4. [UT4](ut/ut4-aplicaciones-moviles.md#a46-pivaa-sesion-34).

**PPS** · Puesta en producción segura, el módulo profesional 5023 de este curso. Es también el prefijo de las cuentas (`pps<NIA>`) y de la máquina de trabajo `pps01`. [UT1](ut/ut1-prueba-aplicaciones.md#presentacion-y-evaluacion).

**proxy de interceptación** · Programa que se coloca entre el cliente y el servidor para ver y modificar el tráfico. Con Burp Suite en web y con un proxy en el emulador en móvil, es la herramienta para detectar protocolos inseguros. [UT4](ut/ut4-aplicaciones-moviles.md#proxy-de-interceptacion-en-el-emulador), [UT3](ut/ut3-vulnerabilidades-web.md#que-hace-burp-suite).

**pull request** · Petición para fusionar una rama en otra. Con las ramas protegidas, es el punto donde otra persona revisa el cambio y donde se ejecutan las comprobaciones automáticas antes de aceptarlo. [UT5](ut/ut5-despliegue-seguro.md#ramas-protegidas-y-revision-de-cambios).

**RSA** · Algoritmo de cifrado de clave pública. Una clave RSA corta o una firma con hash débil son hallazgos a anotar al verificar la firma de una aplicación. [UT4](ut/ut4-aplicaciones-moviles.md#firma-y-verificacion-de-aplicaciones).

**RTO y RPO** · Tiempo máximo aceptable para volver a dar servicio (RTO) y cantidad máxima de datos que se admite perder (RPO). Dimensionan el plan de recuperación y la frecuencia de las copias. [UT5](ut/ut5-despliegue-seguro.md#plan-de-recuperacion-copias-rto-y-rpo).

**sal** · Valor aleatorio que se añade a cada contraseña antes de calcular su hash, de modo que dos contraseñas iguales no den el mismo resultado y no sirvan las tablas precalculadas. [UT3](ut/ut3-vulnerabilidades-web.md#almacenamiento-de-contrasenas-hash-sal-y-algoritmos-modernos).

**SBOM** · Inventario de los componentes de un software (librerías y versiones) en un formato como CycloneDX. Permite cruzarlo con la NVD y avisar cuando aparece una vulnerabilidad nueva en algo ya desplegado. [UT5](ut/ut5-despliegue-seguro.md#analisis-de-dependencias-con-owasp-dependency-check), [UT2](ut/ut2-nivel-seguridad.md#a24-docker-aislamiento-y-auditoria-sesion-12).

**sandbox** · Entorno aislado donde se ejecuta código sin que pueda afectar al resto del sistema, como un contenedor o el modelo de aplicaciones de Android. No confundir con el entorno de pruebas de una pasarela de pago, que solo evita tocar datos reales. [UT1](ut/ut1-prueba-aplicaciones.md#seguridad-de-los-lenguajes), [UT4](ut/ut4-aplicaciones-moviles.md#modelo-de-permisos).

**seccomp** · Filtro del núcleo que limita las llamadas al sistema que puede hacer un proceso. Docker lo aplica por defecto a los contenedores. [UT2](ut/ut2-nivel-seguridad.md#seccomp-apparmor-y-selinux-limitar-lo-que-hace-un-proceso).

**SHA-1** · Función hash antigua, débil para firmas y para contraseñas. Aparece como hallazgo al verificar la firma de una APK y como ejemplo de hash rápido inadecuado. [UT4](ut/ut4-aplicaciones-moviles.md#firma-y-verificacion-de-aplicaciones), [UT3](ut/ut3-vulnerabilidades-web.md#almacenamiento-de-contrasenas-hash-sal-y-algoritmos-modernos).

**SQL (inyección)** · Lenguaje de consulta de las bases de datos relacionales. Hay inyección cuando la entrada del usuario acaba dentro de la consulta como código; se evita con consultas parametrizadas. [UT3](ut/ut3-vulnerabilidades-web.md#como-se-produce-una-inyeccion-sql).

**SSH** · Protocolo de acceso remoto cifrado. En el módulo se usa una clave SSH para subir código a GitHub sin contraseña y Ansible entra con él en las máquinas. [UT1](ut/ut1-prueba-aplicaciones.md#a11-puesto-de-trabajo-sesion-1), [UT5](ut/ut5-despliegue-seguro.md#ansible-inventario-modulos-y-playbooks).

**SSRF** · Falsificación de petición del lado del servidor: se consigue que el servidor haga peticiones a destinos que el atacante no alcanza, como servicios internos. [UT3](ut/ut3-vulnerabilidades-web.md#divulgacion-de-informacion-y-ssrf).

**Terraform** · Herramienta de infraestructura como código: se describen los recursos en ficheros, se ve el plan de cambios y se aplican; guarda el estado de lo creado. [UT5](ut/ut5-despliegue-seguro.md#terraform-proveedores-recursos-estado-y-ciclo-de-trabajo).

**TLS** · Protocolo que cifra y autentica la comunicación entre cliente y servidor; es lo que hay bajo HTTPS. Se configura con un certificado en Apache. [UT3](ut/ut3-vulnerabilidades-web.md#certificados-y-tls-en-apache).

**URL** · Dirección de un recurso web (esquema, servidor, ruta y parámetros). Sus parámetros son una entrada más del usuario y hay que validarlos. [UT3](ut/ut3-vulnerabilidades-web.md#el-protocolo-http).

**WAF** · Cortafuegos de aplicación web: inspecciona las peticiones HTTP y bloquea las que coinciden con patrones de ataque. En el laboratorio es ModSecurity con las reglas de OWASP CRS. [UT3](ut/ut3-vulnerabilidades-web.md#que-es-un-cortafuegos-de-aplicacion-web).

**XML** · Formato de texto con etiquetas. Aparece en el manifiesto de las APK, en las preferencias compartidas de Android (un XML legible en el directorio de la aplicación) y en los informes de pruebas de Maven. [UT4](ut/ut4-aplicaciones-moviles.md#almacenamiento-seguro-en-el-dispositivo).

**XSS** · Inyección de código de script en una página que otros usuarios van a abrir. Puede ser reflejado, almacenado o basado en DOM; se combate con codificación de salida y CSP. [UT3](ut/ut3-vulnerabilidades-web.md#xss-reflejado-almacenado-y-basado-en-dom).
