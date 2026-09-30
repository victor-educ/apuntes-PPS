# Bibliografía y enlaces

Los enlaces concretos de cada unidad están en la página [Para ampliar](ampliacion.md), junto con los apartados que van más allá de lo que se hace en clase, y el material del curso anterior que se conserva está en [Material de partida](material.md). Aquí está lo transversal: documentación de referencia, libros que merecen la pena y sitios donde practicar. Todo en línea y gratuito salvo los libros, y todos los enlaces se comprobaron al escribir esta página.

## Documentación oficial

La primera fuente siempre. Cuando un comando de los apuntes no funcione en una versión concreta, la respuesta está aquí.

| Herramienta | Enlace | Qué mirar |
|-------------|--------|-----------|
| Git | [git-scm.com/doc](https://git-scm.com/doc) | Referencia de comandos y el libro Pro Git en español |
| GitHub | [docs.github.com](https://docs.github.com/) | Roles del repositorio, reglas de rama, Actions |
| Python | [docs.python.org/es/3](https://docs.python.org/es/3/) | Biblioteca estándar, en especial `unittest` |
| Go | [go.dev/doc](https://go.dev/doc/) | Instalación y el paquete `testing` |
| GDB | [sourceware.org/gdb](https://sourceware.org/gdb/current/onlinedocs/gdb.html) | Puntos de ruptura, registros y examen de memoria |
| NASM | [nasm.us/docs.php](https://www.nasm.us/docs.php) | Sintaxis del ensamblador de las prácticas de la UT1 |
| Bash | [gnu.org/software/bash/manual](https://www.gnu.org/software/bash/manual/bash.html) | Manual de referencia del intérprete |
| Apache HTTP Server | [httpd.apache.org/docs/2.4](https://httpd.apache.org/docs/2.4/) | Módulos, cabeceras, endurecimiento |
| Nginx | [nginx.org/en/docs](https://nginx.org/en/docs/) | Directivas de configuración |
| OpenSSL | [openssl.org/docs](https://www.openssl.org/docs/) | Certificados, claves y resúmenes |
| Docker | [docs.docker.com](https://docs.docker.com/) | Dockerfile, Compose y [seguridad del motor](https://docs.docker.com/engine/security/) |
| Burp Suite | [portswigger.net/burp/documentation](https://portswigger.net/burp/documentation/desktop) | Proxy, Repeater e Intruder |
| DVWA | [github.com/digininja/DVWA](https://github.com/digininja/DVWA) | Instalación y niveles de dificultad |
| MDN Web Docs | [developer.mozilla.org/es](https://developer.mozilla.org/es/docs/Web/Security) | Cabeceras de seguridad, CSP, HSTS |
| ASVS | [owasp.org/www-project-application-security-verification-standard](https://owasp.org/www-project-application-security-verification-standard/) | Niveles y requisitos de verificación |
| OWASP Top 10 | [owasp.org/Top10/2021](https://owasp.org/Top10/2021/) | Categorías de riesgo y cómo prevenirlas |
| OWASP Cheat Sheets | [cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/) | Guías cortas por tema, como el [almacenamiento de contraseñas](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html) |
| OWASP MAS | [mas.owasp.org](https://mas.owasp.org/) | MASVS y MASTG para aplicaciones móviles |
| Android | [developer.android.com](https://developer.android.com/guide/topics/permissions/overview) | Permisos, [almacenamiento de datos](https://developer.android.com/training/data-storage) y [firma con apksigner](https://developer.android.com/studio/command-line/apksigner) |
| jadx y Apktool | [github.com/skylot/jadx](https://github.com/skylot/jadx), [apktool.org](https://apktool.org/) | Decompilación e ingeniería inversa de APK |
| CVSS | [first.org/cvss](https://www.first.org/cvss/) | Especificación de la puntuación de gravedad |
| NVD y CWE | [nvd.nist.gov](https://nvd.nist.gov/), [cwe.mitre.org](https://cwe.mitre.org/) | Fichas de CVE y catálogo de debilidades |
| Maven | [maven.apache.org/guides](https://maven.apache.org/guides/) | Ciclo de vida, POM, plugins |
| Jenkins | [jenkins.io/doc](https://www.jenkins.io/doc/) | Sintaxis de pipeline, credenciales, Docker |
| K3s | [docs.k3s.io](https://docs.k3s.io/) | Instalación, arquitectura, redes |
| Kubernetes | [kubernetes.io/es](https://kubernetes.io/es/docs/home/) | Conceptos, objetos y `kubectl` |
| K9s | [k9scli.io](https://k9scli.io/) | Atajos y vistas del terminal |
| Terraform | [developer.hashicorp.com/terraform](https://developer.hashicorp.com/terraform/docs) | Lenguaje, estado, variables y salidas |
| Ansible | [docs.ansible.com](https://docs.ansible.com/ansible/latest/) | Guía del usuario e índice de módulos |
| Prometheus | [prometheus.io/docs](https://prometheus.io/docs/) | Conceptos, PromQL, exporters |
| Grafana | [grafana.com/docs/grafana](https://grafana.com/docs/grafana/latest/) | Fuentes de datos y paneles |

## Libros

- Scott Chacon y Ben Straub, *Pro Git*. Gratis y en español en [git-scm.com/book/es/v2](https://git-scm.com/book/es/v2). Los capítulos de ramas y de Git en el servidor cubren lo que pide la UT5 sobre control de versiones.
- OWASP, *Web Security Testing Guide*. Gratis en [owasp.org](https://owasp.org/www-project-web-security-testing-guide/). Es la metodología completa de pruebas de una aplicación web, y el hilo natural tras la UT3.
- Dafydd Stuttard y Marcus Pinto, *The Web Application Hacker's Handbook* (Wiley, 2ª ed.). De pago y de 2011, así que algunas tecnologías han cambiado, pero la forma de razonar un ataque web sigue siendo la misma. Sus autores son los creadores de Burp Suite.
- Nigel Poulton, *Docker Deep Dive*. De pago. Es el libro que el aula del curso anterior ya usaba como consulta para la parte de contenedores (ver [Material de partida](material.md)).
- Gene Kim, Jez Humble, Patrick Debois y John Willis, *The DevOps Handbook* (IT Revolution, 2ª ed.). De pago. Justifica la cultura, la entrega continua y la realimentación entre equipos que evalúan el RA5.
- Betsy Beyer y otros, *Site Reliability Engineering* (Google). Gratis en [sre.google/books](https://sre.google/books/). Los capítulos de monitorización y de respuesta a incidencias sirven de fondo a la última parte de la UT5.

## Para practicar fuera del aula

- [PortSwigger Web Security Academy](https://portswigger.net/web-security): teoría y laboratorios gratuitos por categoría de vulnerabilidad. Es la base de las entregas de la UT3, y los [itinerarios de aprendizaje](https://portswigger.net/web-security/learning-paths) ordenan los laboratorios por nivel.
- [Atenea](https://atenea.ccn-cert.cni.es/registro), la plataforma de retos del CCN-CERT, con cuenta de correo institucional. Forma parte de las prácticas de cada RA (ver [Presentación y evaluación](modulo.md)).
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/): tienda web deliberadamente vulnerable que se ejecuta en local con la [imagen oficial de Docker](https://hub.docker.com/r/bkimminich/juice-shop) y cubre todo el Top 10.
- [TryHackMe](https://tryhackme.com/): salas guiadas en el navegador, con nivel gratuito, incluida una [sala sobre Juice Shop](https://tryhackme.com/room/owaspjuiceshop).
- [Learn Git Branching](https://learngitbranching.js.org/?locale=es_ES) y [CryptoZombies](https://cryptozombies.io): las dos plataformas de la UT1.
- [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) si la terminal de Linux no está fina.
- [Play with Docker](https://labs.play-with-docker.com/) y [KillerCoda](https://killercoda.com/) para probar Docker, Kubernetes y CI sin instalar nada.
- [DVWA](https://github.com/digininja/DVWA) y [Juice Shop](https://github.com/juice-shop/juice-shop) en local, si se quiere repetir un ataque sin límite de tiempo.

## Comunidades y noticias

- [CCN-CERT](https://www.ccn-cert.cni.es/), el centro criptológico nacional: guías y alertas, y alojamiento de Atenea.
- [INCIBE-CERT](https://www.incibe.es/incibe-cert) y su [blog](https://www.incibe.es/incibe-cert/blog): avisos de vulnerabilidades y casos reales en español. [Aprende ciberseguridad](https://www.incibe.es/aprendeciberseguridad) reúne los recursos formativos de INCIBE.
- [OWASP](https://owasp.org/): proyectos, guías y capítulos locales.
- [MITRE ATT&CK](https://attack.mitre.org/) para situar cada técnica de ataque en su fase y con su nombre estándar.
- [CVE](https://www.cve.org/) y [NVD](https://nvd.nist.gov/) para seguir las vulnerabilidades publicadas.
- [Blog de PortSwigger](https://portswigger.net/research) para las técnicas nuevas de ataque web.

## Normativa

- [Real Decreto 479/2020, de 7 de abril](https://www.boe.es/diario_boe/txt.php?id=BOE-A-2020-4963), por el que se establece el curso de especialización en ciberseguridad en entornos de las tecnologías de la información y se fijan los aspectos básicos del currículo. Define los cinco resultados de aprendizaje y sus criterios de evaluación; el resumen en lenguaje llano está en la [página del módulo](modulo.md).
- Currículo de la Comunitat Valenciana: se publica en el [Diari Oficial de la Generalitat Valenciana](https://dogv.gva.es/) y la Conselleria de Educación mantiene la [página de formación profesional](https://ceice.gva.es/es/web/formacion-profesional).
- [Todofp](https://www.todofp.es/), portal estatal de formación profesional, con la oferta de cursos de especialización.

## Créditos del material del curso anterior

Este sitio parte del material con el que se impartió la asignatura en el curso 2024-25. Se cita por su autoría y no se copia; qué hay en cada carpeta del aula y en qué sesión se usa está en [Material de partida](material.md).

| Material | Autoría y licencia | Origen |
|----------|--------------------|--------|
| *Ciberseguridad-PePS*, apuntes de la asignatura | Víctor Ponz Artero; sin licencia declarada, por lo que solo se enlaza | [github.com/victorponz/Ciberseguridad-PePS](https://github.com/victorponz/Ciberseguridad-PePS) |
| Copia publicada de los mismos apuntes | Bifurcación (fork) del repositorio anterior, con la misma autoría | [psegarrac.github.io/Ciberseguridad-PePS](https://psegarrac.github.io/Ciberseguridad-PePS/) |
| *PPS*, apuntes y prácticas de la asignatura | Eloy Albiach Forner, © 2023, CC BY-NC-SA 4.0 (el `LICENSE` del repositorio dice BY-SA y su Readme BY-NC-SA; se respeta la más restrictiva) | [github.com/EloyAlbiach/PPS](https://github.com/EloyAlbiach/PPS) |
| PDF, enunciados y rúbricas del aula de Aules | Material de terceros: solo consulta, no se publica aquí | Aula de Aules del curso |

El texto propio de estos apuntes se publica con licencia [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.es).
