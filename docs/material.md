# Material de partida

<p class="ut-meta">Recursos · Atribución del material del curso anterior</p>

Esta página recoge todo el material con el que se impartió la asignatura en el curso 2024-25 y dice qué es de quién, dónde está y con qué licencia se puede usar. Es la única página, junto con [Bibliografía y enlaces](recursos.md), donde se nombra a los autores de ese material: las unidades solo dicen qué fichero del aula o qué enlace apoya cada sesión, y remiten aquí para la atribución completa.

## Qué se publica y qué no

Estos apuntes reescriben con palabras propias, con el mismo orden y el mismo alcance, lo que el material anterior explicaba. No copian texto, figuras ni código ajenos. Por eso:

| Material | Qué se hace con él en este sitio |
|---|---|
| Ficheros del aula de 2024-25 (PDF, plantillas, APK, firmware) | No se publican. Siguen en el aula de Aules, donde el alumnado los descarga. Aquí solo se citan por su carpeta y su nombre |
| Apuntes de terceros con licencia libre (Albiach, CC BY-NC-SA 4.0) | Se enlazan y se citan con su atribución. Tampoco se copian párrafos |
| Apuntes de terceros sin licencia declarada (Ponz y su copia en la web del fork) | Se enlazan y se nombran. Sin licencia, todos los derechos quedan reservados a su autor, así que no se copia nada |
| Artículos, libros y presentaciones de terceros | Solo consulta. Se citan con su autor y su sitio de origen |
| Repositorios y aplicaciones vulnerables de práctica | Se enlazan a su repositorio oficial y se usan con las instrucciones de su autor |
| Texto propio de estos apuntes | CC BY-SA 4.0 (ver [Sobre el material](modulo.md#sobre-el-material)) |

!!! ojo "Los PDF del aula no son de estos apuntes"
    Un PDF que está en el aula es material de consulta para el alumnado matriculado. Quien lo tiene no puede redistribuirlo ni subirlo a un repositorio público, y menos si su origen es un libro comercial o un artículo con derechos reservados. Los enunciados y las rúbricas (`ACT_*`, `RA3.x`, `RA5.x`, `R_UD_1.pdf`, `R_ACT_2.pdf`) siguen siendo la referencia de lo que se entrega.

## Material del aula por unidad

Cada tabla dice, para una unidad, el fichero del aula (carpeta de RA y nombre tal como está en Aules), qué contiene, en qué sesiones se apoya la explicación y qué equivalente público existe. La primera columna, Tipo, clasifica cada material por su función pedagógica: **Útil** es el material esencial que la práctica necesita (la teoría de la sesión, los enunciados y rúbricas, las plantillas y las aplicaciones y ficheros que se usan en las hojas) y **Refuerzo** es el que amplía o profundiza pero no es imprescindible (libros de fondo, artículos, vídeos y tutoriales opcionales). Los libros comerciales de solo consulta van siempre en Refuerzo.

Cada unidad de trabajo (UT) se corresponde con un resultado de aprendizaje (RA): por eso las unidades se numeran `UTn` y las carpetas del aula anterior y los resultados de aprendizaje conservan la forma `RA`. La entrega evaluable de cada unidad se nombra `ACT_UTn_k`, aunque el enunciado y la rúbrica sigan guardados en el aula con su nombre de fichero original (`ACT_RA...`, `RA3....pdf`), que no cambia. Las carpetas del aula son las de `aula-2024-25`. Un guion en la última columna significa que no hay equivalente público: el fichero es propio del módulo o no se conserva en línea.

### UT1 · Prueba de aplicaciones

Carpeta del aula: `RA1-Prueba-aplicaciones/`, salvo la primera fila.

| Tipo | Fichero del aula | Qué contiene | Sesiones | Equivalente público |
|---|---|---|---|---|
| Útil | `00-General/01 Plantilla lliurable activitats/Normativa_entrega_trabajos.pdf`, `Plantilla_memoria_tarea.docx` y `.odt` | Formato de los documentos que se entregan y plantilla de memoria | [1](ut/ut1-prueba-aplicaciones.md#sesion-1-presentacion-y-puesto-de-trabajo) | [Plantilla de repositorio](https://github.com/pkaminasfp/template), sin licencia declarada |
| Útil | `01 ACT_RA1_1 - Proves d'aplicacions/UD_1.pdf` y `R_UD_1.pdf` | Enunciado de ACT_UT1_1 (lecturas y programa en ensamblador) y su rúbrica | [2](ut/ut1-prueba-aplicaciones.md#sesion-2-lenguajes-y-modelos-de-ejecucion), [3](ut/ut1-prueba-aplicaciones.md#sesion-3-ensamblador-y-depurador) | - |
| Refuerzo | `02 Fonaments de programació/FUN_PRO.pdf` | Un capítulo de un libro comercial de programación en C++ | [2](ut/ut1-prueba-aplicaciones.md#sesion-2-lenguajes-y-modelos-de-ejecucion) | - (libro comercial, solo consulta) |
| Refuerzo | `04 Material/How Python Works.pdf` y `How Java Works.pdf` | Dos artículos sobre bytecode y máquinas virtuales | [2](ut/ut1-prueba-aplicaciones.md#sesion-2-lenguajes-y-modelos-de-ejecucion), [4](ut/ut1-prueba-aplicaciones.md#sesion-4-python-codigo-fuente-pruebas-y-depuracion) | Ver [artículos de Medium](#articulos-y-libros-de-terceros) |
| Útil | `03 ACT_RA1_2 - Execució d'aplicacions/ACT_2.pdf` y `R_ACT_2.pdf` | Enunciado de ACT_UT1_2 (programa con tests en Python y en Go) y su rúbrica | [4](ut/ut1-prueba-aplicaciones.md#sesion-4-python-codigo-fuente-pruebas-y-depuracion), [5](ut/ut1-prueba-aplicaciones.md#sesion-5-go-pruebas-y-depuracion) | [Pruebas unitarias en Python](https://docs.python.org/es/3/library/unittest.html) y [en Go](https://go.dev/doc/tutorial/add-a-test) |
| Refuerzo | `06 Python/python_1.pdf` y `python_2.pdf` | Instalación de Anaconda y Jupyter; conceptos básicos de Python | [4](ut/ut1-prueba-aplicaciones.md#sesion-4-python-codigo-fuente-pruebas-y-depuracion) | [Documentación de Python](https://docs.python.org/es/3/) |
| Refuerzo | `05 Go/Go.pdf` | El libro *How To Code in Go*, con licencia CC BY-NC-SA 4.0 | [5](ut/ut1-prueba-aplicaciones.md#sesion-5-go-pruebas-y-depuracion) | [Ficha del libro en DigitalOcean](https://www.digitalocean.com/community/books/how-to-code-in-go-ebook) |
| Útil | `07 ACT_RA1_3 - BASH programming/UD_3 .pdf` | Enunciado de ACT_UT1_3 (script en Bash, tutorial y `LearnBash.sh`) | [6](ut/ut1-prueba-aplicaciones.md#sesion-6-bash-y-seguridad-de-los-lenguajes) | [Tutorial de línea de órdenes](https://github.com/krother/bash_tutorial), CC BY-SA 4.0 |
| Refuerzo | `08 Material/LearnBash.sh`, `How Does the Shell Command ls Work Internally.pdf` e `Introduction to Bash Scripting.pdf` | Script comentado de ejemplo y dos artículos sobre el funcionamiento de Bash | [6](ut/ut1-prueba-aplicaciones.md#sesion-6-bash-y-seguridad-de-los-lenguajes) | Ver [artículos de Medium](#articulos-y-libros-de-terceros) |
| Útil | `09 ACT_RA1_4 - Solidity + GIT/ACT_4.pdf` | Enunciado de ACT_UT1_4 (CryptoZombies y Learn Git Branching) | [7](ut/ut1-prueba-aplicaciones.md#sesion-7-contratos-inteligentes-y-control-de-versiones), [8](ut/ut1-prueba-aplicaciones.md#sesion-8-margen-y-repaso-de-la-unidad-1) | [CryptoZombies](https://cryptozombies.io) y [Learn Git Branching](https://learngitbranching.js.org/) |
| Útil | `10 Blockchain/Blockchain.pdf` | Presentación de blockchain y Ethereum | [7](ut/ut1-prueba-aplicaciones.md#sesion-7-contratos-inteligentes-y-control-de-versiones) | - |
| Refuerzo | `11 Material/`: `Blockchain Basics Ethereum Explained.pdf`, `How Ethereum Works Part.pdf`, `Ethereum Virtual Machine.pdf` | Tres artículos sobre Ethereum y su máquina virtual | [7](ut/ut1-prueba-aplicaciones.md#sesion-7-contratos-inteligentes-y-control-de-versiones) | Ver [artículos de Medium](#articulos-y-libros-de-terceros) |

### UT2 · Nivel de seguridad requerido

Carpeta del aula: `RA2-Nivel-seguridad/`.

| Tipo | Fichero del aula | Qué contiene | Sesiones | Equivalente público |
|---|---|---|---|---|
| Útil | `01 Material/Tema_1.pdf` a `Tema_4.pdf` | Diapositivas de metodología de pentesting (descubrimiento, herramientas, clasificación WASC, CWE/SANS Top 25) | [9](ut/ut2-nivel-seguridad.md#sesion-9-fuentes-de-riesgo-owasp-top-10-cwe-y-cve) y, con más detalle, la UT3 | [OWASP Top 10:2021](https://owasp.org/Top10/2021/) y [catálogo CWE](https://cwe.mitre.org/) |
| Útil | `02 ACT_RA2_1 - OWASP - Application Security Verification Standard/ACT_RA2_1.pdf` | Enunciado de ACT_UT2_1: verificar los requisitos L1 de ASVS en una arquitectura cliente-servidor | [9](ut/ut2-nivel-seguridad.md#sesion-9-fuentes-de-riesgo-owasp-top-10-cwe-y-cve), [10](ut/ut2-nivel-seguridad.md#sesion-10-asvs-niveles-y-requisitos), [11](ut/ut2-nivel-seguridad.md#sesion-11-asvs-verificacion-de-los-requisitos-l1) | [OWASP ASVS 4.0.3](https://github.com/OWASP/ASVS/tree/v4.0.3_release) |
| Útil | `03 ACT_RA2_2 -  Seguridad en Docker - log4shell-vulnerable-app/ACT_RA2_2.pdf` | Enunciado de ACT_UT2_2: aislamiento en Docker, laboratorio vulnerable y `docker-bench-security` | [12](ut/ut2-nivel-seguridad.md#sesion-12-seguridad-en-docker) | [log4shell-vulnerable-app](https://github.com/christophetd/log4shell-vulnerable-app), Apache-2.0, y [docker-bench-security](https://github.com/docker/docker-bench-security) |
| Útil | `04 ACT_RA2_3 - Seguridad en Unix - xz-vulnerable-app/ACT_RA2_3.pdf` | Enunciado de ACT_UT2_3: el caso de la puerta trasera en `xz` | [13](ut/ut2-nivel-seguridad.md#sesion-13-cadena-de-suministro-el-caso-xz) | [xzbot](https://github.com/amlweems/xzbot) y [ficha CVE-2024-3094](https://nvd.nist.gov/vuln/detail/CVE-2024-3094) |
| Útil | `05 ACT_RA2_4 - Ransomware/ACT_RA2_4.pdf` | Enunciado de ACT_UT2_4 (optativa): guía de ransomware, laboratorio e informe forense | [14](ut/ut2-nivel-seguridad.md#sesion-14-margen-y-repaso-de-la-unidad-2) | [Guía de ransomware de INCIBE](https://www.incibe.es/sites/default/files/contenidos/guias/doc/guia_ransomware.pdf) y [No More Ransom](https://www.nomoreransom.org/es/index.html) |

### UT3 · Vulnerabilidades web

Carpeta del aula: `RA3-Vulnerabilidades-web/`.

| Tipo | Fichero del aula | Qué contiene | Sesiones | Equivalente público |
|---|---|---|---|---|
| Útil | `01 RA3.1 - Server Hardening/RA3_1.pdf` | Enunciado de ACT_UT3_1: cinco prácticas de hardening con Apache (CSP, certificado, WAF, reglas OWASP, `mod_evasive`) | [16](ut/ut3-vulnerabilidades-web.md#sesion-16-tls-y-politica-de-seguridad-de-contenido), [17](ut/ut3-vulnerabilidades-web.md#sesion-17-cortafuegos-de-aplicacion-web), [18](ut/ut3-vulnerabilidades-web.md#sesion-18-denegacion-de-servicio-y-buenas-practicas-del-servidor) | [Documentación de Apache 2.4](https://httpd.apache.org/docs/2.4/) y [Core Rule Set](https://coreruleset.org/docs/) |
| Refuerzo | `02 Material/RA3_ArquitecturaWeb.pdf`, `RA3_HTTP.pdf` y `RA3_Apache.pdf` | Teoría de arquitectura web, protocolo HTTP y configuración básica de Apache | [15](ut/ut3-vulnerabilidades-web.md#sesion-15-arquitectura-web-y-http) | Apuntes de Ponz, ver [más abajo](#apuntes-de-ponz) |
| Útil | `03 RA3.2 - DVWA/RA3.2.pdf` | Enunciado de ACT_UT3_2: tutoriales de DVWA en los niveles Low y Medium | [19](ut/ut3-vulnerabilidades-web.md#sesion-19-validacion-de-entradas-y-xss), [20](ut/ut3-vulnerabilidades-web.md#sesion-20-sesiones-autenticacion-y-csrf), [21](ut/ut3-vulnerabilidades-web.md#sesion-21-inyeccion-de-comandos-ficheros-y-rutas) | [DVWA](https://github.com/digininja/DVWA), GPL-3.0 |
| Refuerzo | `04 Seguretat web - Validació d'entrades/SEG_WEB_1.pdf` | Teoría de validación de entradas, XSS, robo y fijación de sesión, CSRF | [19](ut/ut3-vulnerabilidades-web.md#sesion-19-validacion-de-entradas-y-xss), [20](ut/ut3-vulnerabilidades-web.md#sesion-20-sesiones-autenticacion-y-csrf) | Apuntes de Ponz, ver [más abajo](#apuntes-de-ponz) |
| Refuerzo | `05 Seguretat web - Autenticació/SEG_WEB_2.pdf` | Teoría de autenticación y almacenamiento de contraseñas | [25](ut/ut3-vulnerabilidades-web.md#sesion-25-contrasenas-seguras-y-proteccion-frente-a-bots) | [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html) |
| Útil | `06 RA3.3 - SQL Injection/RA3.3.pdf` | Enunciado de ACT_UT3_3: laboratorios de inyección SQL de PortSwigger | [22](ut/ut3-vulnerabilidades-web.md#sesion-22-inyeccion-sql) | [Laboratorios de PortSwigger](https://portswigger.net/web-security/all-labs#sql-injection) |
| Útil | `07 RA3.4.1 - Burp Suite - Server Side/RA3.4.1.pdf` | Enunciado de ACT_UT3_4: ocho categorías de laboratorios del lado servidor | [23](ut/ut3-vulnerabilidades-web.md#sesion-23-burp-suite-interceptar-y-repetir), [24](ut/ut3-vulnerabilidades-web.md#sesion-24-control-de-acceso-y-vulnerabilidades-del-servidor) | [Laboratorios de PortSwigger](https://portswigger.net/web-security/all-labs) |
| Útil | `08 RA3.4.2 - Burp Suite - Client Side/RA3.4.2.pdf` | Enunciado de ACT_UT3_5: CSRF, CORS, vulnerabilidades del DOM y XSS | [26](ut/ut3-vulnerabilidades-web.md#sesion-26-burp-suite-lado-cliente) | [Laboratorios de PortSwigger](https://portswigger.net/web-security/all-labs) |

### UT4 · Aplicaciones móviles

Carpeta del aula: `RA4-Moviles/`.

| Tipo | Fichero del aula | Qué contiene | Sesiones | Equivalente público |
|---|---|---|---|---|
| Útil | `01 Material/RA_4.pdf` | Tema completo de la unidad: Android e iOS, estructura de aplicaciones, OWASP Mobile Top 10, análisis estático, dinámico y de red, PoC guiadas | [29](ut/ut4-aplicaciones-moviles.md#sesion-29-arquitectura-de-android-y-owasp-mobile), [30](ut/ut4-aplicaciones-moviles.md#sesion-30-permisos-firma-y-verificacion), [32](ut/ut4-aplicaciones-moviles.md#sesion-32-almacenamiento-de-datos-y-fugas-de-informacion), [33](ut/ut4-aplicaciones-moviles.md#sesion-33-analisis-del-trafico-de-una-aplicacion) | [OWASP MAS](https://mas.owasp.org/) y [OWASP Mobile Top 10](https://owasp.org/www-project-mobile-top-10/) |
| Útil | `02 ACT_RA4_1 - Android App Vulnerable/ACT_RA4_1.pdf` | Enunciado de ACT_UT4_1: ingeniería inversa de DIVA (CE a, b y e) | [31](ut/ut4-aplicaciones-moviles.md#sesion-31-analisis-estatico-de-una-aplicacion-vulnerable) | [DIVA](https://github.com/payatu/diva-android), GPL-3.0 |
| Útil | `03 ACT_RA4_2 - Purposefully Insecure and Vulnerable Android Application/ACT_RA4_2.pdf` | Enunciado de ACT_UT4_2 (CE c, d y e) | [34](ut/ut4-aplicaciones-moviles.md#sesion-34-taller-pivaa), [35](ut/ut4-aplicaciones-moviles.md#sesion-35-compras-integradas-y-casb) | [PIVAA](https://github.com/HTBridge/pivaa), GPL-3.0 |
| Útil | `03 ACT_RA4_2 .../Lab_Movil.pdf` | Taller completo: instalación de Genymotion, MobSF, Drozer y preguntas del taller | [29](ut/ut4-aplicaciones-moviles.md#sesion-29-arquitectura-de-android-y-owasp-mobile), [34](ut/ut4-aplicaciones-moviles.md#sesion-34-taller-pivaa) | [Genymotion](https://www.genymotion.com/download/) |
| Útil | `04 Recursos/APK_1.zip` | `diva-beta.apk` e `InsecureBankv2.apk` | [29](ut/ut4-aplicaciones-moviles.md#sesion-29-arquitectura-de-android-y-owasp-mobile), [31](ut/ut4-aplicaciones-moviles.md#sesion-31-analisis-estatico-de-una-aplicacion-vulnerable), [33](ut/ut4-aplicaciones-moviles.md#sesion-33-analisis-del-trafico-de-una-aplicacion) | [InsecureBankv2](https://github.com/dineshshetty/Android-InsecureBankv2), MIT |
| Útil | `04 Recursos/APK_2.zip` | `pivaa.apk` y `drozer-agent-2.3.4.apk` | [34](ut/ut4-aplicaciones-moviles.md#sesion-34-taller-pivaa) | [PIVAA](https://github.com/HTBridge/pivaa) y [imagen de Drozer](https://hub.docker.com/r/drozerdocker/drozer) |

### UT5 · Despliegue seguro

Carpeta del aula: `RA5-Despliegue-seguro/`.

| Tipo | Fichero del aula | Qué contiene | Sesiones | Equivalente público |
|---|---|---|---|---|
| Útil | `01 Material/01-Infraestructura.pdf` | Escalado vertical y horizontal, balanceo, virtualización y contenedores | [37](ut/ut5-despliegue-seguro.md#sesion-37-devops-y-puesta-segura-en-produccion), [49](ut/ut5-despliegue-seguro.md#sesion-49-k3s-en-un-nodo), [55](ut/ut5-despliegue-seguro.md#sesion-55-recuperacion-ante-desastres-y-retroalimentacion) | - |
| Útil | `01 Material/05-DevOps.pdf` | Cultura DevOps y gestión automatizada de la configuración | [37](ut/ut5-despliegue-seguro.md#sesion-37-devops-y-puesta-segura-en-produccion), [55](ut/ut5-despliegue-seguro.md#sesion-55-recuperacion-ante-desastres-y-retroalimentacion) | - |
| Útil | `01 Material/02-Docker.pdf` | Docker: imágenes, contenedores y volúmenes | [42](ut/ut5-despliegue-seguro.md#sesion-42-docker-en-el-pipeline) | [Documentación de Docker](https://docs.docker.com/) |
| Refuerzo | `01 Material/docker_deep_dive.pdf` | Libro *Docker Deep Dive*, edición de junio de 2023 | [37](ut/ut5-despliegue-seguro.md#sesion-37-devops-y-puesta-segura-en-produccion), [42](ut/ut5-despliegue-seguro.md#sesion-42-docker-en-el-pipeline) | [Sitio del autor](https://www.nigelpoulton.com/books/) (libro comercial, solo consulta) |
| Útil | `01 Material/03-Git.pdf` | Control de versiones y funcionamiento de Git | [38](ut/ut5-despliegue-seguro.md#sesion-38-control-de-versiones-con-roles) | [Learn Git Branching](https://learngitbranching.js.org/) |
| Útil | `01 Material/04-Maven_Gradle.pdf` | Automatización de la construcción: Maven y una introducción a Gradle | [39](ut/ut5-despliegue-seguro.md#sesion-39-automatizacion-de-la-construccion-con-maven), [47](ut/ut5-despliegue-seguro.md#sesion-47-margen-y-repaso-de-la-primera-parte-de-la-unidad-5) | [Maven](https://maven.apache.org/) |
| Útil | `01 Material/06-Ansible.pdf` | Conceptos de Ansible, roles y ejemplos | [46](ut/ut5-despliegue-seguro.md#sesion-46-ansible-inventario-y-playbooks), [48](ut/ut5-despliegue-seguro.md#sesion-48-ansible-despliegue-de-una-aplicacion) | [Documentación de Ansible](https://docs.ansible.com/) |
| Útil | `02 ACT_RA5_1 - Jenkins/RA5.1.pdf` | Enunciado de ACT_UT5_1: Jenkins, `Jenkinsfile` y `jenkinsfile.docker` | [37](ut/ut5-despliegue-seguro.md#sesion-37-devops-y-puesta-segura-en-produccion), [40](ut/ut5-despliegue-seguro.md#sesion-40-jenkins-instalacion-y-primer-trabajo), [41](ut/ut5-despliegue-seguro.md#sesion-41-pipeline-como-codigo-jenkinsfile), [42](ut/ut5-despliegue-seguro.md#sesion-42-docker-en-el-pipeline), [43](ut/ut5-despliegue-seguro.md#sesion-43-pipeline-seguro-componentes-y-secretos) | [Manual de Jenkins](https://www.jenkins.io/doc/book/) y [ejemplos de Docker con Jenkins](https://github.com/pkaminasfp/jenkins), sin licencia declarada |
| Útil | `03 ACT_RA5_2 - Terraform & Ansible/RA5.2.pdf` | Enunciado de ACT_UT5_2: una VM con Terraform, actualizar y desplegar con Ansible | [44](ut/ut5-despliegue-seguro.md#sesion-44-infraestructura-como-codigo-terraform), [45](ut/ut5-despliegue-seguro.md#sesion-45-terraform-variables-estado-y-secretos), [46](ut/ut5-despliegue-seguro.md#sesion-46-ansible-inventario-y-playbooks), [48](ut/ut5-despliegue-seguro.md#sesion-48-ansible-despliegue-de-una-aplicacion) | [Documentación de Terraform](https://developer.hashicorp.com/terraform/docs) |
| Útil | `04 Terraform & Ansible/Terraform_Ansible.pdf` | Índice de diapositivas de Terraform y Ansible | [44](ut/ut5-despliegue-seguro.md#sesion-44-infraestructura-como-codigo-terraform) | - |
| Refuerzo | `05 Material Terraform/`: `Introduction to Terraform.pdf`, `Terraform como Infrastructure as Code.pdf`, `Complete Terraform Tutorial.pdf` | Tres artículos sobre infraestructura como código | [44](ut/ut5-despliegue-seguro.md#sesion-44-infraestructura-como-codigo-terraform), [45](ut/ut5-despliegue-seguro.md#sesion-45-terraform-variables-estado-y-secretos) | Ver [artículos de Medium](#articulos-y-libros-de-terceros) |
| Refuerzo | `06 Material Ansible/`: `Easy Ansible setup using VirtualBox.pdf` y `DVWA .pdf` | Dos artículos sobre Ansible con VirtualBox y sobre aprovisionar DVWA | [46](ut/ut5-despliegue-seguro.md#sesion-46-ansible-inventario-y-playbooks), [48](ut/ut5-despliegue-seguro.md#sesion-48-ansible-despliegue-de-una-aplicacion) | Ver [artículos de terceros](#articulos-y-libros-de-terceros) |
| Útil | `07 ACT_RA5_3 - Prometheus & Grafana/RA5.3.pdf` | Enunciado de ACT_UT5_3: monitorización con Prometheus, `node_exporter` y Grafana | [52](ut/ut5-despliegue-seguro.md#sesion-52-monitorizacion-con-prometheus), [53](ut/ut5-despliegue-seguro.md#sesion-53-monitorizacion-remota-con-grafana) | [Prometheus](https://prometheus.io/docs/introduction/overview/) y [Grafana](https://grafana.com/docs/grafana/latest/) |
| Útil | `08 ACT_RA5_4 - K3s & K9s/RA5.4.pdf` | Enunciado de ACT_UT5_4: K3s en un nodo y en alta disponibilidad, `kubectl` y K9s | [49](ut/ut5-despliegue-seguro.md#sesion-49-k3s-en-un-nodo), [50](ut/ut5-despliegue-seguro.md#sesion-50-k3s-en-alta-disponibilidad), [51](ut/ut5-despliegue-seguro.md#sesion-51-aplicaciones-en-k3s-y-k9s) | [K3s](https://docs.k3s.io/quick-start) y [K9s](https://k9scli.io/) |

### Exámenes, retos y trabajo de ampliación

Carpetas del aula: `01-Examenes/` y `02-Atenea/`.

| Tipo | Fichero del aula | Qué contiene | Uso | Equivalente público |
|---|---|---|---|---|
| Refuerzo | `01 EX_RA1_RA2_RA4/RA_EX.pdf` y `DCS-932L_REVA_FIRMWARE_1.14.04.ZIP` | Examen práctico de reversing del firmware de una cámara IP | Práctica de ampliación en máquina propia, ver [Para ampliar](ampliacion.md) | - |
| Refuerzo | `02 Treball/PPS PoC's.pdf` | Los seis retos del trabajo de ampliación del curso anterior | Ver [Para ampliar](ampliacion.md) | - |
| Útil | `02-Atenea/01 Atenea RA_1 & RA_2/ATENEA.pdf` y `02 Atenea RA_3 & RA_4 & RA_5/ATENEA.pdf` | Guía de acceso y uso de la plataforma de retos, con los retos de cada RA | Retos de la parte de prácticas, ver [Presentación y evaluación](modulo.md#como-se-evalua) | [Atenea](https://atenea.ccn-cert.cni.es/registro) |

El firmware de la cámara es un fichero de un fabricante ajeno: se conserva en el aula para el examen práctico y no se publica ni se redistribuye.

Atenea es la plataforma pública de retos de ciberseguridad del CCN-CERT (el equipo de respuesta ante incidentes del Centro Criptológico Nacional). El alumnado se registra, resuelve los retos asociados a cada resultado de aprendizaje y esos retos cuentan como parte de prácticas de la evaluación; por eso su guía de acceso es material Útil y no de refuerzo.

## Apuntes de terceros usados como referencia

Tres conjuntos de apuntes públicos acompañaron al curso anterior y siguen siendo la lectura complementaria de varias sesiones. Ninguno se copia aquí.

### Apuntes de Albiach

| Dato | Valor |
|---|---|
| Título | *Apuntes de Puesta en Producción Segura* |
| Autor | Eloy Albiach Forner, © 2023 |
| Enlace | <https://github.com/EloyAlbiach/PPS> |
| Licencia declarada | CC BY-NC-SA 4.0 (Atribución, NoComercial, CompartirIgual) |
| Uso en estos apuntes | Referencia de temario en las unidades 1, 2, 3 y 5; se cita con enlace, sin copiar párrafos |

El repositorio no es coherente consigo mismo: su fichero `LICENSE` contiene el texto de la licencia CC BY-SA 4.0 (sin la cláusula NoComercial), pero su `Readme.md` declara «CC BY-NC-SA 4.0». Cuando dos textos del mismo autor discrepan, se aplica la más restrictiva, que es la del Readme. Por eso estos apuntes citan la atribución de esa licencia (autor, título, enlace y licencia) y no reutilizan nada de forma que la cláusula NoComercial pudiera infringirse.

### Apuntes de Ponz

| Dato | Valor |
|---|---|
| Título | *Ciberseguridad-PePS*, apuntes del módulo Puesta en Producción Segura |
| Autor | Víctor Ponz Artero |
| Enlace | <https://github.com/victorponz/Ciberseguridad-PePS> |
| Licencia declarada | Ninguna: el repositorio no tiene `LICENSE` ni la menciona en su `README.md` |
| Uso en estos apuntes | Solo se enlaza y se nombra; se explica el mismo contenido con palabras propias |

Sin licencia declarada, todos los derechos quedan reservados a su autor. Por eso no se copia texto, código ni figuras, aunque el repositorio sea público. Las diapositivas del aula `RA3_ArquitecturaWeb.pdf`, `RA3_HTTP.pdf`, `RA3_Apache.pdf`, `SEG_WEB_1.pdf` y `SEG_WEB_2.pdf` llevan su nombre como autor y corresponden a estas entradas.

### Web del fork

| Dato | Valor |
|---|---|
| Título | *Ciberseguridad-PePS* (sitio publicado del fork del repositorio anterior) |
| Enlace | <https://psegarrac.github.io/Ciberseguridad-PePS/> |
| Licencia declarada | Ninguna (hereda el estado del repositorio original) |
| Uso en estos apuntes | Es la dirección web pública de las entradas de Ponz; las unidades enlazan aquí porque es la versión legible en el navegador |

### Entradas concretas que enlazan las unidades

Las unidades enlazan estas entradas de la web del fork como lectura complementaria. La columna Sesiones dice dónde.

| Entrada | Sesiones | Tema |
|---|---|---|
| Iniciación a la programación (2021-06-01) | [2](ut/ut1-prueba-aplicaciones.md#sesion-2-lenguajes-y-modelos-de-ejecucion) | Fundamentos de programación |
| Aplicación en Python (2021-06-01) | [4](ut/ut1-prueba-aplicaciones.md#sesion-4-python-codigo-fuente-pruebas-y-depuracion) | Programa y pruebas en Python |
| Git (2020-11-01) | [7](ut/ut1-prueba-aplicaciones.md#sesion-7-contratos-inteligentes-y-control-de-versiones), [38](ut/ut5-despliegue-seguro.md#sesion-38-control-de-versiones-con-roles) | Control de versiones |
| Arquitectura web. Conceptos generales, Protocolo HTTP, Configuración básica de Apache (2020-11) | [15](ut/ut3-vulnerabilidades-web.md#sesion-15-arquitectura-web-y-http) | Arquitectura, HTTP y Apache |
| Certificado digital (2020-11-08) | [16](ut/ut3-vulnerabilidades-web.md#sesion-16-tls-y-politica-de-seguridad-de-contenido) | Certificado en Apache |
| Hardening del servidor (2021-03-01) | [16](ut/ut3-vulnerabilidades-web.md#sesion-16-tls-y-politica-de-seguridad-de-contenido), [17](ut/ut3-vulnerabilidades-web.md#sesion-17-cortafuegos-de-aplicacion-web), [18](ut/ut3-vulnerabilidades-web.md#sesion-18-denegacion-de-servicio-y-buenas-practicas-del-servidor) | Cabeceras, WAF y DoS |
| Validación de entradas (2021-01-31) | [19](ut/ut3-vulnerabilidades-web.md#sesion-19-validacion-de-entradas-y-xss), [20](ut/ut3-vulnerabilidades-web.md#sesion-20-sesiones-autenticacion-y-csrf) | Entradas, XSS y sesiones |
| Práctica FileUpload y Command Injection (2021-05) | [21](ut/ut3-vulnerabilidades-web.md#sesion-21-inyeccion-de-comandos-ficheros-y-rutas) | Subida de ficheros y comandos |
| Inyección SQL (2021-04-01) | [22](ut/ut3-vulnerabilidades-web.md#sesion-22-inyeccion-sql) | Inyección SQL |
| Autenticación (2021-02-10) | [25](ut/ut3-vulnerabilidades-web.md#sesion-25-contrasenas-seguras-y-proteccion-frente-a-bots) | Contraseñas |
| Seguridad en Docker (2021-03-10) | [12](ut/ut2-nivel-seguridad.md#sesion-12-seguridad-en-docker) | Aislamiento en Docker |
| Ingeniería inversa en Android (2022-03-01) | [31](ut/ut4-aplicaciones-moviles.md#sesion-31-analisis-estatico-de-una-aplicacion-vulnerable) | Descompilar y reempaquetar DIVA |
| Sistemas de automatización de construcción y Aplicación en Maven (2022-01) | [37](ut/ut5-despliegue-seguro.md#sesion-37-devops-y-puesta-segura-en-produccion), [39](ut/ut5-despliegue-seguro.md#sesion-39-automatizacion-de-la-construccion-con-maven) | Construcción con Maven |
| Jenkins (2022-01-13) | [40](ut/ut5-despliegue-seguro.md#sesion-40-jenkins-instalacion-y-primer-trabajo), [41](ut/ut5-despliegue-seguro.md#sesion-41-pipeline-como-codigo-jenkinsfile) | Instalación con Docker y primer pipeline |
| Análisis de componentes (2022-02-17) | [43](ut/ut5-despliegue-seguro.md#sesion-43-pipeline-seguro-componentes-y-secretos) | Inventario y vulnerabilidades de dependencias |
| Herramientas de simulación de fallos (2022-02-21) | [54](ut/ut5-despliegue-seguro.md#sesion-54-simulacion-de-fallos) | Ingeniería del caos |

## Artículos y libros de terceros

Los PDF del aula que son capturas de artículos web o libros son obra de sus autores y se conservan solo como lectura. Ninguno se redistribuye desde este sitio. Las direcciones de Medium no se enlazan porque la plataforma rechaza las comprobaciones automáticas y no se ha podido verificar que respondan; el título y el autor bastan para encontrarlos.

| Fichero del aula | Título | Autor y origen | Licencia |
|---|---|---|---|
| `How Java Works.pdf` | *How Java Works*, introducción básica a la máquina virtual de Java | rashm1n, Medium | Derechos reservados del autor |
| `How Python Works.pdf` | *How Does Python Really Work?* | Kumuthu Edirisinghe, Medium | Derechos reservados del autor |
| `How Does the Shell Command ls Work Internally.pdf` | *How Does the Shell Command ls Work Internally?* | Brennan D Baraban, Medium | Derechos reservados del autor |
| `Introduction to Bash Scripting.pdf` | *Introduction to Bash Scripting: A Comprehensive Guide for Beginners* | Saquib Khan, Medium | Derechos reservados del autor |
| `Blockchain Basics Ethereum Explained.pdf` | *Blockchain Basics: Ethereum Explained in Simple Points (Part-1)* | Sai Deva Harsha, Medium | Derechos reservados del autor |
| `Ethereum Virtual Machine.pdf` | *Understanding the Ethereum Virtual Machine (EVM)* | Nova Novriansyah, Medium (Novai-Blockchain 101) | Derechos reservados del autor |
| `How Ethereum Works Part.pdf` | *How Ethereum Works Part 2: Smart Contracts, Gas, and Dapps* | Mike Goldin, [blog de Consensys](https://consensys.io/blog), enero de 2016 | Derechos reservados del autor |
| `Introduction to Terraform.pdf` | *Introduction to Terraform: A Beginner's Guide to Infrastructure as Code* | Oladeji Tosin, Medium | Derechos reservados del autor |
| `Terraform como Infrastructure as Code.pdf` | *Terraform como Infrastructure as Code (IaC)* | DeployGuru, Medium | Derechos reservados del autor |
| `Complete Terraform Tutorial.pdf` | *Complete Terraform Tutorial* | Mike Tyson of the Cloud, Medium (Brainboard) | Derechos reservados del autor |
| `Easy Ansible setup using VirtualBox.pdf` | *Easy Ansible setup using VirtualBox* | Linu Bajy, Medium | Derechos reservados del autor |
| `DVWA .pdf` | *Automatización: provisión automática con Vagrant + VirtualBox + Ansible de una máquina DVWA* | [Cross Mind](https://crossmind.technology/2022/08/29/), 29 de agosto de 2022 | Derechos reservados del autor |
| `Go.pdf` | *How To Code in Go*, de Mark Bates, Cory LaNou y Tim Raymond | [DigitalOcean](https://www.digitalocean.com/community/books/how-to-code-in-go-ebook), 2020 | CC BY-NC-SA 4.0 (lo declara la propia edición) |
| `docker_deep_dive.pdf` | *Docker Deep Dive*, edición de junio de 2023 | Nigel Poulton, © 2016 a 2023 | Libro comercial, todos los derechos reservados |
| `FUN_PRO.pdf` | Capítulo de *Programación en C++. Algoritmos, estructuras de datos y objetos* | Libro comercial de McGraw-Hill | Todos los derechos reservados |
| `Tema_1.pdf` a `Tema_4.pdf` | Diapositivas de la asignatura (metodología de pentesting) | Raúl Fuentes Ferrer, en el curso 23AI32CF015 | Sin licencia declarada |

!!! ojo "Libros comerciales: solo consulta"
    `FUN_PRO.pdf` y `docker_deep_dive.pdf` son libros de editorial o de autor que se venden. Están en el aula para que el alumnado los consulte como fondo de lectura, no para copiarlos ni compartirlos. Ninguna hoja depende de ellos: todo lo que las hojas necesitan se explica en las unidades. Si se quiere el libro, se compra a su autor o a su editorial.

`Go.pdf` es la excepción: su licencia (CC BY-NC-SA 4.0) permite compartirlo con atribución, sin uso comercial y con la misma licencia. Aun así, no se aloja en este sitio: se enlaza a su página oficial.

## Repositorios y proyectos de práctica

Las prácticas usan software o aplicaciones deliberadamente vulnerables de otros autores. Se descargan siempre de su repositorio oficial y se usan con sus instrucciones.

| Proyecto | Autor u organización | Licencia declarada | Sesión |
|---|---|---|---|
| [Plantilla de repositorio](https://github.com/pkaminasfp/template) | pkaminasfp | Ninguna | [1](ut/ut1-prueba-aplicaciones.md#sesion-1-presentacion-y-puesto-de-trabajo) |
| [Tutorial de Bash](https://github.com/krother/bash_tutorial) | krother | CC BY-SA 4.0 (en su README) | [6](ut/ut1-prueba-aplicaciones.md#sesion-6-bash-y-seguridad-de-los-lenguajes) |
| [DVWA](https://github.com/digininja/DVWA) | digininja | GPL-3.0 | [19](ut/ut3-vulnerabilidades-web.md#sesion-19-validacion-de-entradas-y-xss) a [21](ut/ut3-vulnerabilidades-web.md#sesion-21-inyeccion-de-comandos-ficheros-y-rutas) |
| [log4shell-vulnerable-app](https://github.com/christophetd/log4shell-vulnerable-app) | christophetd | Apache-2.0 | [12](ut/ut2-nivel-seguridad.md#sesion-12-seguridad-en-docker) |
| [xzbot](https://github.com/amlweems/xzbot) | amlweems | Ninguna | [13](ut/ut2-nivel-seguridad.md#sesion-13-cadena-de-suministro-el-caso-xz) |
| [DIVA](https://github.com/payatu/diva-android) | payatu | GPL-3.0 | [31](ut/ut4-aplicaciones-moviles.md#sesion-31-analisis-estatico-de-una-aplicacion-vulnerable), [32](ut/ut4-aplicaciones-moviles.md#sesion-32-almacenamiento-de-datos-y-fugas-de-informacion) |
| [InsecureBankv2](https://github.com/dineshshetty/Android-InsecureBankv2) | dineshshetty | MIT | [33](ut/ut4-aplicaciones-moviles.md#sesion-33-analisis-del-trafico-de-una-aplicacion) |
| [PIVAA](https://github.com/HTBridge/pivaa) | HTBridge | GPL-3.0 | [34](ut/ut4-aplicaciones-moviles.md#sesion-34-taller-pivaa) |
| [Ejemplos de Jenkins](https://github.com/pkaminasfp/jenkins) | pkaminasfp | Ninguna | [42](ut/ut5-despliegue-seguro.md#sesion-42-docker-en-el-pipeline) |
| [Ejemplo de Prometheus y Grafana](https://github.com/dinesh24murali/example_repo/tree/main/prometheus_grafana_example) | dinesh24murali | Ninguna | [52](ut/ut5-despliegue-seguro.md#sesion-52-monitorizacion-con-prometheus) |
| [Taller de Docker](https://aulasoftwarelibre.github.io/taller-de-docker/dockerfile/#balanceo-de-carga) | Aula de Software Libre | Ninguna en el repositorio | [51](ut/ut5-despliegue-seguro.md#sesion-51-aplicaciones-en-k3s-y-k9s) |

Una herramienta sin licencia declarada se puede ejecutar en el laboratorio, pero no se redistribuye ni se copia su código en los apuntes.

## Qué se ha cambiado respecto al curso anterior

El material anterior se conserva y se sigue en el mismo orden y con el mismo alcance. Solo se ha sustituido lo que ya no funciona tal cual, y cada sesión lo dice en su recuadro de material de partida.

| Material original | Qué pasa | Sustituto |
|---|---|---|
| Instalación de Anaconda y Jupyter (`python_1.pdf`) | Una instalación de varios gigabytes que la práctica no necesita | Python del sistema en la máquina virtual |
| Instalación de Go en Ubuntu 18.04 (`Go.pdf`) | Sistema operativo fuera de soporte | Paquete de Go de Ubuntu 24.04 |
| Depurador web de ensamblador de 32 bits | No ejecuta el programa del enunciado (64 bits, `syscall`) | `gdb` para el programa real y el depurador web con un ejercicio equivalente |
| Curso avanzado de CryptoZombies (Truffle y Ganache) | Herramientas retiradas por su fabricante | Se sigue como lectura; hoy se usa Hardhat o Foundry |
| Maven con JUnit 4 y Java 8 | Versiones antiguas | JUnit 5 y Java 17 |
| Compose del taller de Docker (Traefik 2.3 y socket de Docker) | No existe en K3s | Se traduce a los recursos de K3s |
| Apunte de Heroku | Servicio de pago sin plan gratuito | No se usa |

## Créditos

- Apuntes de Puesta en Producción Segura: Eloy Albiach Forner, CC BY-NC-SA 4.0, <https://github.com/EloyAlbiach/PPS>.
- Ciberseguridad-PePS: Víctor Ponz Artero, sin licencia declarada, <https://github.com/victorponz/Ciberseguridad-PePS>, y su web publicada en <https://psegarrac.github.io/Ciberseguridad-PePS/>.
- Diapositivas de pentesting (`Tema_1.pdf` a `Tema_4.pdf`): Raúl Fuentes Ferrer.
- *How To Code in Go*: Mark Bates, Cory LaNou y Tim Raymond, DigitalOcean, CC BY-NC-SA 4.0.
- *Docker Deep Dive*: Nigel Poulton.
- El resto de artículos, con su autor, en la tabla de [artículos y libros de terceros](#articulos-y-libros-de-terceros).

La lista de fuentes generales de consulta está en [Bibliografía y enlaces](recursos.md).
