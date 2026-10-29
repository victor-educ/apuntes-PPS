# UT2 · Nivel de seguridad requerido

<p class="ut-meta">12 h · Sesiones 9 a 14 · RA2 CE a, b, c, d</p>

Antes de escribir una línea de código de una aplicación hace falta responder una pregunta previa: ¿cuánta seguridad necesita esta aplicación en concreto? Una tienda con pagos no necesita lo mismo que un blog interno, y tratar a las dos por igual sobra en un caso y falta en el otro. Esta unidad da un criterio para responder esa pregunta con un estándar reconocido, OWASP ASVS, y un vocabulario común para hablar de vulnerabilidades: el catálogo OWASP Top 10, los identificadores CWE y CVE y la puntuación CVSS. También entra en dos casos concretos que muestran por qué el nivel de seguridad no depende solo del código de la aplicación: el aislamiento que ofrece Docker y un ataque real a la cadena de suministro de software. Son seis sesiones (cinco de trabajo y una de margen), tres entregas evaluables, ACT_UT2_1 a ACT_UT2_3, con plazo el 16, el 23 y el 26 de noviembre, y una optativa, ACT_UT2_4. Cada entrega tiene en el aula su enunciado en PDF («Actividad RA2.1. Application Security Verification Standard», «RA2.2. Seguridad en Docker», «RA2.3. Seguridad en Unix» y «RA2.4. Análisis de un Ransomware»), y **el PDF es el que manda**: las hojas siguen su numeración (3.2.1, 4.3.1...) y dicen en cada paso a qué punto responde, y lo que una hoja añade por su cuenta va en «Si te sobra tiempo», que es lo que la rúbrica llama «Extra».

!!! ojo "Solo sobre lo propio o lo autorizado por escrito"
    Esta unidad reproduce vulnerabilidades reales (Log4Shell, la puerta trasera de xz) contra aplicaciones y máquinas deliberadamente vulnerables, en la máquina virtual propia del alumno y sin salida a la red del aula. Acceder sin autorización a un sistema ajeno es delito en España (Código Penal, artículos 197 bis y 264 y siguientes), aunque la intención sea "solo mirar" y aunque no se cause daño. El criterio profesional es siempre el mismo: solo sobre lo propio o lo que se ha autorizado por escrito. Ninguna hoja de esta unidad escribe código de explotación nuevo: se usan las herramientas y los repositorios que documenta el material del curso, siguiendo su propia documentación.

## Sesión 9 · Fuentes de riesgo: OWASP Top 10, CWE y CVE

<p class="ut-meta" markdown>5 de noviembre · Teoría y práctica · <span class="dur" tabindex="0" aria-label="Fuentes abiertas de vulnerabilidades: OWASP Top 10, CWE y CVE · 15 min&#10;CVSS: puntuar la gravedad · 10 min&#10;A2.1 Riesgos de una aplicación · 85 min" data-dur="Fuentes abiertas de vulnerabilidades: OWASP Top 10, CWE y CVE · 15 min&#10;CVSS: puntuar la gravedad · 10 min&#10;A2.1 Riesgos de una aplicación · 85 min">:material-school:<i class="dur-barra" style="--teoria:23%"></i>:material-flask:</span></p>

Al acabar esta sesión hay diez vulnerabilidades reales clasificadas por categoría de OWASP Top 10, identificador CWE y puntuación CVSS, cada una con una explicación del riesgo concreto que supone para una aplicación. Antes de eso, dos apartados cortos dan el vocabulario: de dónde salen estos catálogos y qué significa cada sigla, y cómo se lee una puntuación CVSS. Es la sesión que abre la unidad y también la que sienta el vocabulario de riesgo que se usa el resto del curso. Ninguna entrega la recoge: el enunciado de ACT_UT2_1 empieza en la sesión 10, con ASVS, y lo que se practica hoy (el tipo de cada fallo y su gravedad) es lo que después etiqueta cada requisito de ASVS y puntúa los casos de Log4Shell y xz.

!!! consulta "Recursos de la sesión"
    **Para la práctica**

    - [OWASP Top 10:2021](https://owasp.org/Top10/2021/): las diez categorías de riesgo web.
    - [Catálogo CWE](https://cwe.mitre.org/) del MITRE: los tipos de debilidad.
    - [NVD](https://nvd.nist.gov/) del NIST: donde vive cada ficha CVE.
    - [Especificación de CVSS 3.1](https://www.first.org/cvss/v3.1/specification-document): cómo se puntúa la gravedad.

### Fuentes abiertas de vulnerabilidades: OWASP Top 10, CWE y CVE

Antes de clasificar una vulnerabilidad hace falta distinguir tres preguntas distintas que a menudo se confunden: qué tipo de fallo es, qué caso concreto de ese fallo es y qué gravedad tiene. Cada pregunta tiene su propio catálogo.

```mermaid
flowchart LR
    D["<b>OWASP Top 10</b><br><small>categoría de riesgo</small>"]:::ok
    A["<b>CWE</b><br><small>tipo de debilidad</small>"]:::pieza
    B["<b>CVE</b><br><small>caso concreto</small>"]:::dato
    C["<b>CVSS</b><br><small>gravedad, 0 a 10</small>"]:::riesgo
    D --> A --> B --> C
    classDef pieza fill:#64748b22,stroke:#64748b,stroke-width:1.5px
    classDef dato fill:#2563eb22,stroke:#2563eb,stroke-width:1.5px
    classDef riesgo fill:#dc262622,stroke:#dc2626,stroke-width:1.5px
    classDef ok fill:#16a34a22,stroke:#16a34a,stroke-width:1.5px
```

<p class="pie" markdown>De lo general a lo concreto: una categoría amplia del Top 10 (`A03:2021-Injection`) agrupa tipos de debilidad (`CWE-79`, inyección en páginas vistas por otros usuarios), cada tipo se materializa en casos reales (un `CVE` con su ficha en la NVD) y cada caso se puntúa con `CVSS`.</p>

El **CWE** (*Common Weakness Enumeration*, enumeración de debilidades comunes), del MITRE, no describe un fallo que haya ocurrido, describe un tipo de fallo que puede ocurrir: `CWE-89` es "SQL Injection" como concepto, no un caso concreto. Un requisito de ASVS o una vulnerabilidad de la A2.1 se etiquetan con su CWE porque es la forma más precisa de decir "esto es exactamente este tipo de problema", con independencia del lenguaje o del producto donde aparezca.

El **CVE** (*Common Vulnerabilities and Exposures*, vulnerabilidades y exposiciones comunes) identifica un caso concreto, ya descubierto en un producto real y publicado: `CVE-2021-44228` es un fallo concreto de unas versiones concretas de Log4j, no el concepto de inyección. Cada CVE tiene una ficha pública en la **NVD** (*National Vulnerability Database*, base de datos nacional de vulnerabilidades), el catálogo que mantiene el NIST de EE. UU., con su descripción, su CWE asociado y su puntuación CVSS.

El **OWASP Top 10** agrupa los CWE más frecuentes en diez categorías amplias, pensadas para priorizar sin tener que conocer cientos de CWE de memoria. La edición usada en el curso es la de 2021, que es la que sigue el material de referencia de la asignatura; en 2025 OWASP ha publicado una revisión que reordena y renombra varias categorías, y la comparación entre las dos queda en [Para ampliar](../ampliacion.md#ut2-nivel-de-seguridad-requerido).

| Categoría (2021) | De qué trata, en una frase |
|---|---|
| A01: Broken Access Control | Un usuario accede a datos o funciones que no le corresponden |
| A02: Cryptographic Failures | Datos sensibles cifrados de forma débil o transmitidos en claro |
| A03: Injection | Datos del usuario tratados como código o como orden por el servidor |
| A04: Insecure Design | Un fallo de diseño, no de implementación: falta un control en el plano de la aplicación |
| A05: Security Misconfiguration | Configuración por defecto, permisos de más o funciones innecesarias activas |
| A06: Vulnerable and Outdated Components | Una dependencia (librería, framework) con una vulnerabilidad conocida y sin actualizar |
| A07: Identification and Authentication Failures | Autenticación débil: sesión mal gestionada, credenciales predecibles, sin límite de intentos |
| A08: Software and Data Integrity Failures | Código o datos que se aceptan sin comprobar su integridad (una actualización sin firmar, una deserialización insegura) |
| A09: Security Logging and Monitoring Failures | No queda registro de lo que pasó, así que un incidente se detecta tarde o no se detecta |
| A10: Server-Side Request Forgery | El servidor hace una petición a una URL que controla el atacante |

`CVE-2024-3094`, la puerta trasera de las herramientas de compresión `xz`, es a la vez A06 (una dependencia comprometida) y A08 (código que se acepta sin comprobar su integridad); es habitual que un mismo caso encaje en más de una categoría, y la A2.1 pide elegir la que mejor explica el riesgo principal, no la única posible. Ese caso se reproduce en el laboratorio el 19 de noviembre.

### CVSS: puntuar la gravedad

Clasificar por categoría dice de qué tipo es el problema; CVSS dice cuánto importa. La puntuación va de 0,0 a 10,0 y sale de combinar factores objetivos: si se explota desde la red o hace falta acceso local, si necesita que la víctima haga algo, qué privilegios hacen falta y qué se compromete (confidencialidad, integridad, disponibilidad). La cifra final se traduce en una banda de severidad:

| Puntuación CVSS v3.1 | Severidad |
|---:|---|
| 0,0 | Ninguna |
| 0,1 a 3,9 | Baja |
| 4,0 a 6,9 | Media |
| 7,0 a 8,9 | Alta |
| 9,0 a 10,0 | Crítica |

La ficha de la NVD de cada CVE incluye su vector CVSS completo (una cadena como `AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`) y la puntuación ya calculada; para la A2.1 basta con leer la puntuación y la severidad de la ficha, no con calcular el vector a mano. Dos vulnerabilidades de la misma categoría del Top 10 pueden tener puntuaciones muy distintas: lo que cambia el riesgo real no es solo el tipo de fallo, es lo fácil que es explotarlo y lo que se pierde si se explota.

### A2.1 Riesgos de una aplicación (sesión 9)

<span class="et et-obj">Objetivo</span> Diez vulnerabilidades reales clasificadas con su categoría de OWASP Top 10 2021, su CWE, su puntuación CVSS con severidad, y una explicación de dos o tres líneas del riesgo que supone cada una para una aplicación concreta.

<span class="et et-pre">Antes de empezar</span> Un navegador con acceso a la [NVD](https://nvd.nist.gov/) y a [OWASP Top 10:2021](https://owasp.org/Top10/2021/). Se han explicado [las fuentes de vulnerabilidades y sus catálogos](#fuentes-abiertas-de-vulnerabilidades-owasp-top-10-cwe-y-cve) y [cómo se lee una puntuación CVSS](#cvss-puntuar-la-gravedad). Esta hoja no la pide ningún enunciado y no la recoge ninguna entrega: es práctica de vocabulario para el resto de la unidad.

<span class="et et-pas">Pasos</span>

El recorrido va de lo objetivo a lo que exige criterio: primero se copian de la ficha oficial los datos que no se discuten (CWE y CVSS), después se decide la categoría del Top 10 y, al final, se razona el riesgo para una aplicación concreta, que es lo que no se puede copiar de ningún sitio.

1. **Tabla de trabajo.** En el repositorio `pps-entregas`, crea la carpeta `ut2/a21/` y, dentro, la tabla de trabajo con las columnas `CVE`, `Nombre común`, `CWE`, `Categoría OWASP Top 10 2021`, `CVSS (puntuación y severidad)` y `Riesgo para una aplicación concreta`.

2. **CWE y CVSS de la ficha.** Busca en la NVD la ficha de cada una de estas diez vulnerabilidades y anota su CWE y su puntuación CVSS v3.1 con severidad tal como aparecen en la ficha:

    - `CVE-2021-44228` (Log4Shell)
    - `CVE-2014-0160` (Heartbleed)
    - `CVE-2014-6271` (Shellshock)
    - `CVE-2017-0144` (EternalBlue)
    - `CVE-2017-5638` (la de la brecha de Equifax, en Apache Struts)
    - `CVE-2020-11022` (XSS en jQuery)
    - `CVE-2021-26855` (ProxyLogon, en Microsoft Exchange)
    - `CVE-2022-22965` (Spring4Shell)
    - `CVE-2022-40684` (bypass de autenticación en FortiOS)
    - `CVE-2023-34362` (la de MOVEit Transfer)

    *Pista:* el nombre común entre paréntesis solo ayuda a localizar la ficha, no hace falta citarlo en la tabla. Si la ficha muestra varias versiones de CVSS, usa la v3.1 y, si hay dos, la del NIST.

3. **Categoría del Top 10.** Decide para cada una la categoría de OWASP Top 10 2021 que mejor explica su riesgo principal. Si una encaja en más de una (como `CVE-2024-3094` en la teoría), elige la principal y anota entre paréntesis la secundaria.

4. **Riesgo para una aplicación.** Escribe en dos o tres líneas, para cada vulnerabilidad, qué riesgo concreto supondría en una de estas tres aplicaciones, la que tenga más sentido para ella y dilo: una tienda en línea con pagos, un servicio interno de gestión de incidencias o una aplicación de mensajería con archivos adjuntos. Completa el `README.md` con la tabla y súbelo.

<span class="et et-com">Comprobación</span> La tabla tiene diez filas completas, cada CVSS coincide con el que muestra la ficha de la NVD de ese CVE, y ninguna explicación de riesgo es una frase genérica que valdría para cualquier vulnerabilidad de la lista.

<span class="et et-ent">Para practicar</span> Guarda en `ut2/a21/` de `pps-entregas` el `README.md` y la tabla. Ninguna entrega la recoge, pero tenla a mano: el CWE de cada fila es el mismo que llevan los requisitos de ASVS de la hoja de cálculo de ACT_UT2_1, y la ficha de `CVE-2021-44228` es la que se cita en ACT_UT2_2.

## Sesión 10 · ASVS: niveles y requisitos

<p class="ut-meta" markdown>9 de noviembre · Teoría y práctica · <span class="dur" tabindex="0" aria-label="OWASP ASVS: qué es y su estructura por capítulos · 10 min&#10;Elegir el nivel: L1, L2 y L3 · 15 min&#10;A2.2 ASVS: elegir el nivel · 85 min" data-dur="OWASP ASVS: qué es y su estructura por capítulos · 10 min&#10;Elegir el nivel: L1, L2 y L3 · 15 min&#10;A2.2 ASVS: elegir el nivel · 85 min">:material-school:<i class="dur-barra" style="--teoria:23%"></i>:material-flask:</span></p>

Hoy empieza la entrega ACT_UT2_1, cuyo enunciado pide verificar todos los requisitos L1 de ASVS sobre un escenario dado. Al acabar esta sesión está empezada la lectura del estándar, existe la hoja de cálculo de la entrega con plantilla corporativa y los 128 requisitos L1 listados por secciones, y los primeros requisitos están analizados sobre el escenario. Antes de eso, dos apartados: qué es ASVS y cómo se organiza en catorce capítulos, y el criterio para decidir entre sus tres niveles, que explica por qué el escenario de la entrega se queda en L1.

!!! consulta "Recursos de la sesión"
    **Para la práctica**

    - [OWASP ASVS 4.0.3](https://github.com/OWASP/ASVS/tree/v4.0.3_release): el estándar de verificación y su estructura por niveles.
    - La [política de contraseñas de Joomla](https://github.com/joomla/joomla-cms/blob/5.2-dev/libraries/src/Form/Rule/PasswordRule.php): el ejemplo de técnica concreta que da el enunciado.
    - El enunciado de la entrega ACT_UT2_1, «Actividad RA2.1. Application Security Verification Standard», está en el aula con su rúbrica.

### OWASP ASVS: qué es y su estructura por capítulos

ASVS (*Application Security Verification Standard*, estándar de verificación de seguridad de aplicaciones) es un catálogo de requisitos técnicos de seguridad, mantenido por OWASP, pensado para dos usos a la vez: como lista de comprobación para quien construye una aplicación y como criterio común para quien la audita. Cada requisito tiene un identificador con el formato `capítulo.sección.número` (por ejemplo, `V2.1.1` es el requisito 1 de la sección 1 del capítulo 2) y, cuando aplica, su CWE asociado.

El estándar se organiza en catorce capítulos, cada uno con un número distinto de requisitos exigibles en el nivel 1 (L1):

| Capítulo | De qué trata | Requisitos en L1 |
|---|---|---:|
| V1 Arquitectura, diseño y modelado de amenazas | Documentar el diseño de seguridad antes de programar | 0 |
| V2 Autenticación | Contraseñas, factores adicionales, recuperación de acceso | 27 |
| V3 Gestión de sesión | Tokens de sesión, cookies, cierre de sesión | 12 |
| V4 Control de acceso | Que cada usuario llegue solo a lo suyo | 8 |
| V5 Validación, sanitización y codificación | Tratar toda entrada como no confiable | 27 |
| V6 Criptografía almacenada | Cómo se guardan claves y secretos | 1 |
| V7 Gestión de errores y registro | Qué se registra y qué no se muestra al usuario | 3 |
| V8 Protección de datos | Qué datos sensibles se exponen y dónde | 7 |
| V9 Comunicaciones | Cifrado del transporte | 3 |
| V10 Código malicioso | Integridad de actualizaciones y del código que se ejecuta | 3 |
| V11 Lógica de negocio | Límites y orden de los pasos de un proceso | 5 |
| V12 Ficheros y recursos | Subida, descarga y ejecución de ficheros | 11 |
| V13 API y servicios web | Métodos, esquemas y CSRF en servicios REST y SOAP | 6 |
| V14 Configuración | Cabeceras HTTP, componentes actualizados, modo depuración | 15 |

El capítulo V1 no exige ningún requisito en L1: el modelado de amenazas formal empieza a pedirse en L2. Los capítulos con más peso en L1 son Autenticación y Validación, con 27 requisitos cada uno; entre los dos suman más de un tercio de los 128 requisitos de nivel 1.

!!! consulta "La versión 5.0 del estándar"
    OWASP publicó ASVS 5.0 en mayo de 2025, que reorganiza los catorce capítulos en diecisiete y cambia varios identificadores de requisito. El curso usa 4.0.3 porque es la versión del enunciado de la entrega y la que sigue el material de referencia; qué cambia entre las dos versiones queda en [Para ampliar](../ampliacion.md#ut2-nivel-de-seguridad-requerido).

### Elegir el nivel: L1, L2 y L3

El nivel no es una preferencia, es una decisión que depende de lo que la aplicación maneja y de a quién afecta si falla.

| Nivel | Cuándo se aplica | Ejemplo |
|---|---|---|
| L1 | Seguridad básica, exigible a cualquier aplicación | Un blog interno, una página informativa sin cuentas de usuario |
| L2 | Aplicaciones con datos sensibles; es el nivel recomendado para la mayoría de aplicaciones empresariales | Una tienda en línea con pagos, un gestor de incidencias con datos de clientes |
| L3 | Aplicaciones críticas, con transacciones de alto valor o datos muy sensibles | Banca, sanidad, infraestructuras críticas |

El criterio para elegir entre los tres no es solo "cuánto se puede gastar en seguridad", es una pregunta de riesgo: qué pasa si esta aplicación falla. Tres preguntas ayudan a decidir: ¿qué datos maneja (ninguno, personales, financieros o de salud)?, ¿qué pasa si se compromete (una molestia, una pérdida económica, un daño a personas)?, ¿a cuánta gente afecta un fallo? Un blog interno sin cuentas de usuario no pasa de L1 aunque se quiera; una aplicación de banca no debería quedarse en L1 aunque el cliente lo pida, porque el riesgo real no ha cambiado por que alguien decida ignorarlo.

El escenario de la entrega es la arquitectura cliente-servidor de una empresa de compra-venta de robellones que va a pasar a producción, y el enunciado fija su nivel en L1. Con las tres preguntas, una tienda con cuentas de clientes se queda en L1 mientras no guarde datos de pago ni datos sensibles; si los guardara, el riesgo apuntaría a L2. Ese razonamiento es el que pide el CE b: saber decir, no solo qué nivel toca, sino por qué, y cuándo el nivel que da el cliente y el nivel que pide el riesgo no coinciden.

Verificar un requisito no es responder "sí" o "no": es documentar dónde se aplica, con qué técnica o fichero se cumple y qué prueba lo demuestra, en una plantilla como esta:

| Capítulo | Requisito | Checklist | Dónde | Técnica o fichero | Prueba de verificación | Riesgo residual |
|---|---|---|---|---|---|---|
| V2.1 Seguridad de contraseñas | V2.1.1: la contraseña tiene al menos 12 caracteres | Cumplido | Formulario de alta y cambio de contraseña, validación en el servidor | Campo `password` validado con una expresión regular de longitud mínima antes de generar el hash | Dar de alta una cuenta con una contraseña de 8 caracteres y comprobar que el servidor la rechaza con un mensaje genérico | Una contraseña de 12 caracteres previsibles (`contraseña123`) sigue siendo débil; lo complementa V2.1.7 (comprobar contra listas de contraseñas filtradas) |

La columna "riesgo residual" es la que distingue una verificación real de una casilla marcada: dice qué sigue sin cubrir aunque el requisito se cumpla, y con qué otro requisito se complementa. Es la que más falla cuando se rellena una hoja de cálculo deprisa, y la que el propio enunciado pone como ejemplo de lo que hay que documentar.

La columna «Checklist» es la que convierte la tabla en una lista de comprobación, que es el nivel del 90 % de la rúbrica para la tabla: cada fila queda marcada como `cumplido` (el control está previsto en el escenario, con su técnica y su prueba), `no cumplido` (falta, y la fila dice qué habría que hacer) o `no aplica`, con el motivo. Es la marca que propone el propio enunciado: si la aplicación cumple el control, se marca como cumplido para su nivel.

El enunciado pide además indicar **en qué servidor** se aplica cada requisito, y no define ninguno. Para que todas las filas hablen de las mismas máquinas, la hoja parte de una arquitectura mínima de tres servidores, que cada alumno puede ampliar si lo justifica:

| Servidor | Función en el escenario de compra-venta |
|---|---|
| Web | Nginx como proxy inverso: termina TLS y añade las cabeceras HTTP |
| Aplicación | La aplicación (API y lógica de negocio): cuentas, sesiones y validación |
| Base de datos | Almacena usuarios (con la contraseña como hash), catálogo y pedidos |

### A2.2 ASVS: elegir el nivel (sesión 10)

<span class="et et-obj">Objetivo</span> La hoja de cálculo de la Actividad RA2.1 montada con plantilla corporativa y los 128 requisitos L1 de ASVS 4.0.3 listados por secciones (punto 3.2.1), y los doce requisitos de V2.1 (Seguridad de contraseñas) ya analizados y verificados sobre el escenario de compra-venta de robellones (primera parte del punto 3.2.2). Es el fichero que se entrega: lo que no quede hecho hoy se completa sobre él en la A2.3 y en casa.

<span class="et et-pre">Antes de empezar</span> Un programa de hoja de cálculo (LibreOffice Calc o similar) y el enunciado de la Actividad RA2.1 abierto: el escenario está en su apartado 5 y la rúbrica, en el anexo. Se han explicado [qué es ASVS y su estructura por capítulos](#owasp-asvs-que-es-y-su-estructura-por-capitulos) y [cómo se elige el nivel y cómo se verifica un requisito](#elegir-el-nivel-l1-l2-y-l3). Esta hoja forma parte de la entrega **ACT_UT2_1 · OWASP ASVS**, junto con la A2.3.

<span class="et et-pas">Pasos</span>

El recorrido sigue el enunciado: primero la lectura del estándar (3.1.1), que da el contexto; después la tabla con todos los requisitos L1 y su formato (3.2.1), y por último el análisis de los primeros requisitos sobre el escenario (3.2.2), que sigue en la sesión 11. La tabla va antes que el análisis porque es la que muestra, de un vistazo, qué falta.

1. **Lectura (punto 3.1.1).** Lee de ASVS 4.0.3 la parte que explica los niveles y cómo usar el estándar, y el capítulo V2. En la rúbrica pesa 0 %, pero sin ella la tabla se rellena a ciegas: lo que no dé tiempo en clase se termina en casa.

2. **Tabla L1 por secciones (punto 3.2.1).** En `~/pps-entregas/ut2/a22/`, crea `ACT_UT2_1.ods` con los 128 requisitos L1 ya listados, agrupados por capítulo y sección, y las siete columnas de la [plantilla de la teoría](#elegir-el-nivel-l1-l2-y-l3), incluida la de «Checklist».

    *Pista:* el CSV oficial está en el repositorio de ASVS 4.0.3 (`.../4.0/docs_en/OWASP ... 4.0.3-en.csv`); los requisitos L1 son las filas que traen marcada la columna `level1`, 128 en total y ninguno en V1. Da formato de texto a la columna del identificador antes de volcarla, o `V2.1.10` pierde el cero final.

3. **Plantilla corporativa (punto 3.2.1).** Es el nivel del 80 % de la rúbrica de la tabla. Añade una portada con nombre, fecha, el escenario del enunciado, su nivel (L1) y la arquitectura de tres servidores de la teoría, y da a la tabla un formato de empresa coherente: logotipo y colores propios, cabecera fija, filtros por columna y una fila de capítulo que separe cada bloque.

4. **Análisis y verificación de V2.1 (punto 3.2.2).** Resuelve los doce requisitos de V2.1 (V2.1.1 a V2.1.12) sobre el escenario, siguiendo la fila modelo de la teoría: servidor, técnica o fichero concreto, prueba repetible, riesgo residual y su marca en «Checklist». El texto completo de cada requisito está en su propia fila.

    *Pista:* el enunciado pone como ejemplo de técnica la [política de contraseñas de Joomla](https://github.com/joomla/joomla-cms/blob/5.2-dev/libraries/src/Form/Rule/PasswordRule.php): citar el fichero y la regla que lo cumple es el nivel de detalle que pide.

<span class="et et-com">Comprobación</span> La hoja tiene 128 filas L1 agrupadas por capítulo, con portada y formato corporativo; las doce filas de V2.1 tienen las siete columnas completas, ninguna deja «Riesgo residual» en blanco y todas están marcadas en «Checklist».

<span class="et et-ent">Para practicar</span> Guarda la hoja de cálculo en `ut2/a22/` de `pps-entregas` y súbela con un commit de progreso: la A2.3 completa sobre el mismo fichero el resto de los requisitos L1. Lo recoge la entrega **ACT_UT2_1 · OWASP ASVS** (plazo, el 16 de noviembre), que es esta misma hoja de cálculo terminada.

<span class="et et-ext">Si te sobra tiempo</span> Es el «Extra» de la rúbrica, porque el enunciado da el nivel hecho. Aplica el [criterio de elección de nivel](#elegir-el-nivel-l1-l2-y-l3) a dos escenarios, un blog interno de la empresa sin cuentas de usuario y una tienda en línea que procesa pagos con tarjeta, y añade a la portada, en dos o tres líneas cada uno, qué nivel les corresponde y por qué. Después explica con tus palabras qué tendría que cambiar en la empresa de robellones para que el L1 del enunciado dejara de bastar.

## Sesión 11 · ASVS: verificación de los requisitos L1

<p class="ut-meta" markdown>12 de noviembre · Teoría y práctica · <span class="dur" tabindex="0" aria-label="Verificar un requisito: dónde, con qué técnica y con qué prueba · 15 min&#10;A2.3 ASVS: verificación L1 · 95 min" data-dur="Verificar un requisito: dónde, con qué técnica y con qué prueba · 15 min&#10;A2.3 ASVS: verificación L1 · 95 min">:material-school:<i class="dur-barra" style="--teoria:14%"></i>:material-flask:</span></p>

Al acabar esta sesión el capítulo V2 (Autenticación) está completo en la hoja de cálculo de la entrega y el V3 (Gestión de sesión) está empezado, con el resto marcado como pendiente para terminar en casa antes del plazo. Es el punto 3.2.2 del enunciado de la Actividad RA2.1: analizar, indicar y verificar cada requisito L1 sobre el escenario. La sesión abre con un apartado corto que afina la metodología ya vista (qué hace que un "dónde", una "técnica" y una "prueba" sean lo bastante concretos para que otra persona los repita) y da cuatro requisitos más resueltos como modelo, de capítulos que se resuelven en casa.

!!! consulta "Recursos de la sesión"
    **Para la práctica**

    - [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/): la lista completa de requisitos L1 en CSV, que la plantilla de la entrega ya recoge.
    - El enunciado de la entrega ACT_UT2_1, «Actividad RA2.1. Application Security Verification Standard», con el escenario y la rúbrica.

### Verificar un requisito: dónde, con qué técnica y con qué prueba

Tres columnas de la plantilla fallan más que las demás cuando se rellenan sin pensar, y las tres comparten un mismo defecto: la vaguedad.

"Dónde" no es "en el servidor": es en qué componente concreto, con su nombre (el formulario de alta, el middleware de autenticación, la configuración de Apache). Si la aplicación tiene varios servidores (por ejemplo, un frontend y una API), el requisito puede aplicar en uno, en el otro o en los dos, y eso hay que decirlo explícitamente: no todos los requisitos se aplican en todas las máquinas del escenario.

"Técnica o fichero" no es "se valida": es cómo, con qué mecanismo concreto. Puede ser una línea de código, una directiva de configuración, una librería con su nombre, o una política de un proveedor externo (por ejemplo, si la autenticación la delega en un proveedor de identidad, la técnica es "delegado en el proveedor X, ver su documentación de cumplimiento"). Un requisito que no se puede resolver con el código disponible en el escenario se analiza igualmente, con la técnica prevista, aunque no exista código real que revisar: el enunciado pide un análisis técnico, no una implementación completa.

"Prueba de verificación" no es "funciona": es un paso concreto que otra persona podría repetir y que da un resultado observable (un intento que se rechaza, una cabecera que aparece, un registro que se genera). Si la prueba es "se ha comprobado manualmente", falta decir qué se hizo exactamente para comprobarlo.

Un requisito que no aplica al escenario (por ejemplo, uno sobre autenticación multifactor si el escenario no la contempla) se marca `no aplica` en «Checklist» con una frase que explique por qué, no se deja en blanco ni se omite la fila.

Cuatro requisitos más, resueltos como modelo para los capítulos que se hacen en casa, sobre el mismo escenario de compra-venta y sus [tres servidores](#elegir-el-nivel-l1-l2-y-l3):

| Requisito | Servidor y componente | Técnica o fichero | Prueba de verificación | Riesgo residual |
|---|---|---|---|---|
| V3.2.1: nuevo token de sesión al autenticarse (CWE-384) | Aplicación: módulo de login | Regenerar el identificador de sesión justo tras validar las credenciales (`session.regenerate()` o equivalente del framework) | Anotar la cookie de sesión antes y después de iniciar sesión: el valor tiene que cambiar | Un token robado después del login sigue valiendo hasta que caduque (lo cubre V3.3.1, cierre de sesión) |
| V4.1.1: control de acceso en una capa de servicio de confianza (CWE-602) | Aplicación: capa de servicios de la API | Comprobar en el servidor el rol y el propietario del pedido en cada endpoint, no solo ocultar botones en el cliente | Con la sesión de un cliente, pedir por URL el pedido de otro (`/pedidos/1234`): el servidor responde 403 | Un rol con más permisos de los necesarios (revisión de roles en L2) |
| V5.3.4: consultas parametrizadas contra inyección (CWE-89) | Aplicación (acceso a datos) y base de datos | Sentencias preparadas o ORM en todo acceso; usuario de BD sin permisos de esquema | Introducir `' OR '1'='1` en el buscador de catálogo: se trata como texto y no devuelve todo | Consultas dinámicas heredadas que se escapen de la revisión (búsqueda en el código de concatenaciones) |
| V9.1.1: TLS en toda conexión de cliente (CWE-319) | Web: Nginx | Redirección de HTTP a HTTPS y directiva `ssl_protocols TLSv1.2 TLSv1.3;` | `curl -I http://host` devuelve una redirección 301 a `https://`; un cliente forzado a TLS 1.0 es rechazado | Certificado mal gestionado o sin renovar (V9.2, L2) |

### A2.3 ASVS: verificación L1 (sesión 11)

<span class="et et-obj">Objetivo</span> El capítulo V2 (Autenticación) completo y las secciones V3.1 a V3.3 de Gestión de sesión analizados y verificados en la hoja de cálculo (punto 3.2.2 del enunciado), siguiendo la metodología de dónde, técnica y prueba, y el resto (V3.4 en adelante, unos 95 requisitos) marcado en «Checklist» y con su plan para terminarlo en casa antes del plazo.

<span class="et et-pre">Antes de empezar</span> La hoja de cálculo de la A2.2, con el nivel elegido y V2.1 resuelto. Se ha explicado [cómo verificar un requisito de forma concreta](#verificar-un-requisito-donde-con-que-tecnica-y-con-que-prueba). Esta hoja forma parte de la entrega **ACT_UT2_1 · OWASP ASVS**, junto con la A2.2.

<span class="et et-pas">Pasos</span>

Se trabaja por capítulos completos, en el orden del estándar, porque los requisitos de una misma sección comparten servidor y técnica y se resuelven más deprisa juntos; al final de la clase se marca todo lo que queda, para que la hoja diga sola cuánto falta.

1. **V2, Autenticación (punto 3.2.2).** Completa el resto del capítulo V2 (15 filas): V2.2 (seguridad general del autenticador, 3), V2.3 (ciclo de vida del autenticador, 1), V2.5 (recuperación de credenciales, 6), V2.7 (verificador fuera de banda, 4) y V2.8 (verificador de un solo uso, 1). El texto está en la propia fila de la plantilla.

2. **V3.1 a V3.3, Gestión de sesión (punto 3.2.2).** Empieza el capítulo V3 (Gestión de sesión): V3.1 (fundamentos, 1), V3.2 (vinculación de la sesión, 3) y V3.3 (terminación de la sesión, 2). Sigue el modelo V3.2.1 de la teoría.

3. **Checklist y plan para casa (puntos 3.2.1 y 3.2.2).** Marca en «Checklist» todas las filas que faltan (`no aplica` con su motivo cuando se ve a simple vista, `pendiente` en el resto), para que la hoja muestre qué queda, y ordena los capítulos pendientes por tamaño: V5 (27), V14 (15) y V12 (11) son los más largos. Apunta en la portada tu plan de trabajo en casa (unos 3 minutos por requisito, unas 5 horas en total). En la hoja entregada no puede quedar ningún `pendiente`.

<span class="et et-com">Comprobación</span> Las 27 filas de V2 y las 6 de V3.1 a V3.3 tienen las siete columnas completas y ninguna fila de la hoja queda sin marcar en «Checklist».

<span class="et et-ent">Para practicar</span> Haz un commit de progreso con la hoja. Termina **en casa, antes del plazo**, lo que no acabes en clase (es trabajo a ritmo propio y el plazo no se mueve) y guarda en `ut2/a23/` de `pps-entregas` la hoja de cálculo completa, con los 128 requisitos L1 resueltos: es la `ACT_UT2_1.ods` que empezaste en `ut2/a22/`, terminada. Esa hoja de cálculo es la entrega **ACT_UT2_1 · OWASP ASVS** (plazo, el 16 de noviembre): se sube a su tarea de Aules en `.ods` o `.xls`, que es el formato que fija el enunciado.

<span class="et et-ext">Si te sobra tiempo</span> Es el «Extra» de la rúbrica del punto 3.2.2. Elige tres requisitos de V2 o V3 y localiza en el código de Joomla 5, el proyecto que el enunciado pone de ejemplo, el fichero y la regla que los cumplen, con el enlace a la línea concreta, en una pestaña aparte de la hoja: es la diferencia entre una técnica prevista y una comprobada en código real.

## Sesión 12 · Seguridad en Docker

<p class="ut-meta" markdown>16 de noviembre · Teoría y práctica · <span class="dur" tabindex="0" aria-label="Namespaces y cgroups: el aislamiento de un contenedor · 10 min&#10;seccomp, AppArmor y SELinux: limitar lo que hace un proceso · 10 min&#10;La superficie de ataque del demonio · 5 min&#10;A2.4 Docker: aislamiento y auditoría · 85 min" data-dur="Namespaces y cgroups: el aislamiento de un contenedor · 10 min&#10;seccomp, AppArmor y SELinux: limitar lo que hace un proceso · 10 min&#10;La superficie de ataque del demonio · 5 min&#10;A2.4 Docker: aislamiento y auditoría · 85 min">:material-school:<i class="dur-barra" style="--teoria:23%"></i>:material-flask:</span></p>

Al acabar esta sesión hay una imagen deliberadamente vulnerable (Log4Shell) construida, escaneada y corriendo de forma contenida en `pps01`, con su vulnerabilidad comprobada y mitigada, y un perfil de AppArmor aplicado y comprobado sobre un contenedor; la auditoría con `docker-bench-security`, los otros dos escaneos y las lecturas del enunciado se hacen en casa. Antes de eso, tres apartados cortos explican qué aísla realmente a un contenedor, qué mecanismos limitan lo que un proceso puede hacer dentro de él, y dónde está el punto más débil de toda la plataforma: el demonio que lo gestiona todo.

!!! consulta "Recursos de la sesión"
    **Para la práctica**

    - El enunciado de la entrega ACT_UT2_2, «RA2.2. Seguridad en Docker», con su rúbrica y la chuleta de seguridad de Docker del anexo.
    - Las lecturas del punto 4.1.1: *Container security fundamentals* de Datadog, [parte 1](https://securitylabs.datadoghq.com/articles/container-security-fundamentals-part-1/) y [parte 2](https://securitylabs.datadoghq.com/articles/container-security-fundamentals-part-2/), y la [guía de seguridad de Docker](https://docs.docker.com/engine/security/).
    - [Seguridad en Docker](https://psegarrac.github.io/Ciberseguridad-PePS/tema3/seguridad/web/2021/03/10/Seguridad-en-Docker.html): la página donde están las prácticas 1, 2 y 3 del punto 4.2.
    - [log4shell-vulnerable-app](https://github.com/christophetd/log4shell-vulnerable-app), con las lecturas de [INCIBE-CERT](https://www.incibe.es/en/incibe-cert/blog/log4shell-analysis-vulnerabilities-log4j) y [Sophos](https://news.sophos.com/en-us/2021/12/17/inside-the-code-how-the-log4shell-exploit-works/) sobre cómo funciona el ataque (punto 4.3.1).
    - [docker-bench-security](https://github.com/docker/docker-bench-security) (punto 4.4.1) y [AppArmor en Docker](https://docs.docker.com/engine/security/apparmor/) (punto 4.5.1).

### Namespaces y cgroups: el aislamiento de un contenedor

Un contenedor no es una máquina virtual: comparte el mismo kernel Linux que el sistema anfitrión. Lo que lo hace parecer una máquina aparte son dos mecanismos del kernel que Docker combina.

Los **namespaces** dan a un proceso una vista propia de un recurso del sistema, de modo que no ve lo que hay fuera de esa vista aunque comparta el mismo kernel:

| Namespace | Qué aísla |
|---|---|
| PID | Los procesos: un contenedor solo ve los suyos, no los del anfitrión ni los de otros contenedores |
| Network | Las interfaces de red: cada contenedor tiene su propia IP y sus propias reglas |
| Mount | El sistema de ficheros: cada contenedor ve solo los volúmenes que se le asignan |
| UTS | El nombre de host |
| IPC | La comunicación entre procesos (memoria compartida, colas de mensajes) |
| User | El mapeo de usuarios: un proceso puede ser root dentro del contenedor sin serlo en el anfitrión |

```mermaid
flowchart TB
    K["<b>Kernel Linux</b><br><small>uno solo, compartido</small>"]:::infra
    N["<b>Namespaces y cgroups</b><br><small>vista propia de PID, red, ficheros; límite de CPU y memoria</small>"]:::pieza
    C1["<b>Contenedor A</b><br><small>ve solo sus procesos</small>"]:::act
    C2["<b>Contenedor B</b><br><small>ve solo sus procesos</small>"]:::act
    K --> N --> C1
    N --> C2
    classDef infra fill:#a1a1aa14,stroke:#a1a1aa,stroke-width:1.5px
    classDef pieza fill:#64748b22,stroke:#64748b,stroke-width:1.5px
    classDef act fill:#ea580c22,stroke:#ea580c,stroke-width:1.5px
```

<p class="pie" markdown>El kernel es uno solo: lo que separa un contenedor de otro no es hardware, es la vista que los namespaces le dan de ese mismo kernel. Un fallo que se escapa del namespace afecta al anfitrión y a todos los demás contenedores.</p>

Los **cgroups** (*control groups*, grupos de control) hacen el trabajo complementario: no ocultan recursos, limitan cuántos puede consumir un proceso. Una CPU o una memoria sin límite en un contenedor puede dejar sin recursos al anfitrión y a los demás contenedores con un único proceso descontrolado, algo que un namespace por sí solo no evita.

### seccomp, AppArmor y SELinux: limitar lo que hace un proceso

Los namespaces y los cgroups aíslan y limitan recursos, pero no dicen qué puede *hacer* un proceso dentro de su propia vista. Esa capa la cubren tres mecanismos distintos, y conviene no confundirlos:

| Mecanismo | Qué restringe | Dónde se usa en el laboratorio |
|---|---|---|
| seccomp | Las llamadas al sistema (*syscalls*) que un proceso puede hacer al kernel | Activo por defecto en Docker: el perfil estándar bloquea alrededor de 44 llamadas de las más de 300 disponibles |
| AppArmor | Qué ficheros, capacidades y recursos puede usar un proceso concreto, mediante un perfil de texto | El mecanismo de esta sesión, porque `pps01` es Ubuntu y AppArmor es su control de acceso obligatorio por defecto |
| SELinux | Lo mismo que AppArmor (control de acceso obligatorio) pero con un modelo de etiquetas por fichero y proceso, más granular y más complejo de administrar | No se usa en el laboratorio: es el mecanismo por defecto en distribuciones basadas en Red Hat, no en Ubuntu |

seccomp actúa por defecto sin que nadie escriba nada: el perfil estándar de Docker ya bloquea llamadas peligrosas como cambiar la hora del reloj o cargar módulos del kernel. AppArmor y SELinux, en cambio, necesitan un perfil explícito para cada aplicación: sin uno, un contenedor corre con el perfil `docker-default`, que es razonable pero genérico. Un perfil propio, como el que aplica la A2.4, restringe además lo que esa aplicación concreta necesita, no lo que cualquier contenedor podría necesitar.

### La superficie de ataque del demonio

El demonio Docker (`dockerd`) corre como root y es quien de verdad crea, destruye y gestiona los contenedores: cualquiera que pueda hablar con su socket tiene, en la práctica, privilegios de root en el anfitrión. Por eso el grupo `docker` equivale a un grupo con privilegios de administración, y añadir un usuario a ese grupo (paso habitual para no escribir `sudo` en cada orden) es una decisión de seguridad, no solo de comodidad.

La configuración del demonio vive en `/etc/docker/daemon.json`; ahí se desactiva el modo `debug` en producción y se pueden fijar límites (`ulimits`) por defecto para los contenedores que arrancan sin sus propios límites. Otro punto habitual de exposición es montar el socket del demonio dentro de un contenedor (`-v /var/run/docker.sock:/var/run/docker.sock`, un patrón común en pipelines de CI/CD para lanzar Docker dentro de Docker): quien controla ese socket controla el anfitrión, así que ese montaje solo se hace cuando es imprescindible y nunca en un contenedor que también procesa entrada de fuera. `docker-bench-security`, que es la herramienta de la hoja de esta sesión, audita justamente este tipo de configuración: la del demonio, la de los contenedores en marcha y la de las imágenes, contra un catálogo de buenas prácticas.


### A2.4 Docker: aislamiento y auditoría (sesión 12)

<span class="et et-obj">Objetivo</span> Las tres prácticas de escaneo del enunciado de la RA2.2 (la imagen Log4Shell, una imagen antigua de WordPress y un inventario de componentes analizado), la vulnerabilidad de Log4Shell comprobada y mitigada en un contenedor sin salida a Internet, una auditoría con `docker-bench-security` con tres hallazgos explicados y un perfil de AppArmor propio aplicado a un contenedor y comprobado. Son los puntos 4.1.1 a 4.5.1 del enunciado, y con ellos se hace el PDF de ACT_UT2_2.

<span class="et et-pre">Antes de empezar</span> `pps01` encendida con una instantánea reciente, Docker funcionando sin `sudo` y el repositorio `pps-entregas` clonado ([repositorio de entregas](../laboratorio.md#repositorio-de-entregas)). Se han explicado [namespaces y cgroups](#namespaces-y-cgroups-el-aislamiento-de-un-contenedor), [seccomp, AppArmor y SELinux](#seccomp-apparmor-y-selinux-limitar-lo-que-hace-un-proceso) y [la superficie de ataque del demonio](#la-superficie-de-ataque-del-demonio). Esta hoja forma parte de la entrega **ACT_UT2_2 · Seguridad en Docker**. Todo se hace sobre la imagen deliberadamente vulnerable del laboratorio y sin exponerla a la red del aula ([red aislada](../laboratorio.md#red-aislada-y-buenas-practicas)).

<span class="et et-pas">Pasos</span>

En clase se hace lo que necesita el laboratorio de la sesión, en este orden: la imagen de la práctica 1 se escanea antes de arrancarla (4.2.1), después se comprueba y se mitiga su vulnerabilidad dentro de un contenedor sin salida a Internet (4.3.1) y por último se confina un contenedor con AppArmor (4.5.1). La auditoría con `docker-bench-security` (4.4.1), las prácticas 2 y 3 (4.2.2 y 4.2.3) y las lecturas (4.1.1) no dependen de nada de la sesión y **se hacen en casa antes del plazo**. El PDF de la entrega, en cambio, va en el orden del enunciado.

1. **Práctica 1: escaneo de la imagen Log4Shell (punto 4.2.1).** Como pide la práctica, clona el repositorio `log4shell-vulnerable-app` fuera de `pps-entregas`, construye su imagen y escanéala con `trivy` antes de arrancarla, pidiendo solo las vulnerabilidades críticas y guardando la salida en `ut2/a24/trivy-log4shell.txt`. Anota qué paquete de Log4j aparece, con su versión y su CVE, y con qué versión lo corrige.

    *Pista:* `trivy` corre en su propio contenedor (`aquasec/trivy`); para ver una imagen construida en local necesita el socket del demonio montado en solo lectura, el montaje que [la teoría](#la-superficie-de-ataque-del-demonio) reserva para cuando es imprescindible. Si la construcción falla o tarda demasiado, la imagen publicada por digest es la misma aplicación:

    ```bash
    export IMG=ghcr.io/christophetd/log4shell-vulnerable-app@sha256:6f88430688108e512f7405ac3c73d47f5c370780b94182854ea2cddc6bd59929
    ```

2. **Exploit de la práctica 1, contenido (punto 4.3.1).** Arranca la imagen (la construida o la publicada) solo en el bucle local, en el puerto 8082 del anfitrión (el 8080 del contenedor, según [Puertos y nombres](../laboratorio.md#puertos-y-nombres)), corta su salida a Internet con una regla en la cadena `DOCKER-USER`, comprueba que la vulnerabilidad es explotable sin atacar (una expresión `${...}` inofensiva en la cabecera `X-Api-Version`, que el registro muestra ya resuelta) y aplica la mitigación de configuración, tras la cual la misma prueba deja el texto sin resolver. Explica en el `README.md`, con las lecturas de INCIBE-CERT y Sophos del enunciado, qué haría la segunda fase de un ataque real, por qué la mitigación es un parche provisional y cuál es la corrección definitiva.

    *Pista:* la expresión va entre comillas simples, o la shell la expande antes que `curl`; la variable que mitiga es `LOG4J_FORMAT_MSG_NO_LOOKUPS=true` y la corrección definitiva, Log4j 2.17.1 o posterior. La regla de `DOCKER-USER` solo bloquea las conexiones nuevas que salen (`--ctstate NEW`), no lo que entra por el puerto publicado. Sin la cabecera la aplicación responde `HTTP 400`, que ya indica que está viva.

3. **AppArmor (punto 4.5.1).** Crea el perfil de AppArmor `pps-confinado` (parte de un perfil permisivo, donde `file,` permite todo el acceso a ficheros, y añádele denegaciones explícitas de escritura, que siempre prevalecen), cárgalo en el kernel y compruébalo ejecutando dos contenedores de prueba de `ubuntu:24.04`, uno sin perfil y otro con `--security-opt apparmor=pps-confinado`: compara qué puede escribir cada uno en `/tmp` y en `/etc`.

    ```text
    #include <tunables/global>

    profile pps-confinado flags=(attach_disconnected,mediate_deleted) {
      #include <abstractions/base>

      network,
      capability,
      file,
      umount,

      deny /etc/** w,
      deny /root/** w,
      deny /usr/** w,
    }
    ```

    *Pista:* cada regla acaba en coma, incluida la última antes de `}`; se carga con `apparmor_parser -r` y se lista con `aa-status`. Las opciones de `docker run` van antes de la imagen, y `docker inspect -f '{{.AppArmorProfile}}'` confirma el perfil aplicado.

4. **En casa: `docker-bench-security` (punto 4.4.1).** Clona y ejecuta `docker-bench-security` siguiendo su propio README, guarda la salida en `docker-bench.txt` y elige tres hallazgos `[WARN]` de secciones distintas (anfitrión, demonio y contenedores en ejecución, entre ellos `vulnerable-app`), explicando de cada uno en el `README.md` qué comprueba, por qué importa y qué cambio lo resolvería.

    *Pista:* clónalo **fuera de `pps-entregas`** (por ejemplo en `~`); si se clona dentro, `git add` lo trata como un repositorio anidado. Arranca antes `vulnerable-app`, o la sección de contenedores sale vacía.

5. **En casa: prácticas 2 y 3 (puntos 4.2.2 y 4.2.3).** Para la práctica 2, escanea con `trivy` una imagen de WordPress con una etiqueta de hace años, no la última (el enunciado lo pide así para que haya vulnerabilidades que mostrar), guarda la salida en `trivy-wordpress.txt` y resume cuántas críticas hay y por qué la etiqueta antigua es peor. Para la práctica 3, genera con [Syft](https://github.com/anchore/syft) el inventario de componentes (SBOM) de una de las dos imágenes en formato CycloneDX (`sbom.json`), analízalo con [Grype](https://github.com/anchore/grype) y con [Dependency-Track](https://dependencytrack.org/), y explica qué añade un SBOM frente a escanear la imagen directamente.

    *Pista:* Syft y Grype tienen imagen de contenedor, como `trivy`. Dependency-Track se levanta con el compose de su documentación, publicado solo en `127.0.0.1`, y pide unos 4 GB de memoria: arráncalo con el resto de contenedores parados, importa el SBOM en un proyecto nuevo, captura el panel de vulnerabilidades y bájalo al terminar.

6. **En casa: lecturas y evidencias (punto 4.1.1).** Resume en el `README.md`, con palabras propias, las tres lecturas del enunciado (las dos partes de Datadog y la guía de seguridad de Docker), relacionándolas con lo que has visto en los pasos anteriores. Después ordena el `README.md` por los puntos del enunciado, con las salidas y las capturas de cada paso, y sube la carpeta.

<span class="et et-com">Comprobación</span> `trivy` ha localizado Log4j en la imagen; el servicio responde en `http://127.0.0.1:8082/` pero el contenedor no alcanza Internet; la expresión de prueba se resuelve antes de la mitigación y no después; el contenedor con perfil escribe en `/tmp` pero no en `/etc`, mientras que el contenedor sin perfil escribe en los dos sitios; y, de lo que se hace en casa, el escaneo de WordPress muestra vulnerabilidades críticas, `sbom.json` se abre en Dependency-Track y el `README.md` explica tres hallazgos reales de `docker-bench-security`. Si algo falla, revisa [Errores frecuentes](#errores-frecuentes-en-el-laboratorio).

<span class="et et-ent">Para practicar</span> Guarda en `ut2/a24/` de `pps-entregas` el `README.md`, `trivy-log4shell.txt`, `trivy-wordpress.txt`, `sbom.json` con la salida de Grype, `docker-bench.txt`, el perfil `pps-confinado` y las capturas. Con ellos se hace el PDF de la entrega **ACT_UT2_2 · Seguridad en Docker** (plazo, el 23 de noviembre), un capítulo por punto del enunciado.

**Antes del jueves 19 de noviembre, en casa.** La hoja de ese día, la A2.5 sobre el caso xz, crea la VM `debian12` desde una instalación desatendida y necesita la ISO ya descargada. Comprueba con `curl` la última versión 12.x en [cdimage.debian.org](https://cdimage.debian.org/cdimage/archive/latest-oldstable/amd64/iso-cd/) (por ejemplo, `curl -sI https://cdimage.debian.org/cdimage/archive/latest-oldstable/amd64/iso-cd/debian-12.15.0-amd64-netinst.iso` tiene que responder `200`, aunque el número de versión concreto cambie), descárgala en el anfitrión (el equipo donde corre VirtualBox, no en `pps01`) y déjala en `~/iso/`. Son unos 700 MB; hacerlo en casa evita que treinta equipos la pidan a la vez en el aula.

<span class="et et-ext">Si te sobra tiempo</span> Es el «Extra» de la rúbrica de los puntos 4.3.1 y 4.5.1. Endurece el arranque de `vulnerable-app` con las opciones del cheat sheet de Docker del enunciado (`--cap-drop=ALL`, `--security-opt no-new-privileges`, `--read-only` con `--tmpfs /tmp`, `--memory 256m` y `--cpus 0.5`) y comprueba que el servicio sigue respondiendo. Arranca despacio (medio minuto o más en un equipo lento). Anota si alguna de ellas rompe la aplicación y, si es así, por qué; si no rompe ninguna, explica qué protege cada opción.

## Sesión 13 · Cadena de suministro: el caso xz

<p class="ut-meta" markdown>19 de noviembre · Teoría y práctica · <span class="dur" tabindex="0" aria-label="La cadena de suministro: el caso xz · 15 min&#10;A2.5 El caso xz · 95 min" data-dur="La cadena de suministro: el caso xz · 15 min&#10;A2.5 El caso xz · 95 min">:material-school:<i class="dur-barra" style="--teoria:14%"></i>:material-flask:</span></p>

Al acabar esta sesión hay un análisis propio de las dos versiones de una librería del laboratorio, la original y una infectada, con las diferencias que delatan la puerta trasera, y una investigación con `ldd` de qué depende de qué en la cadena que unió esa librería con el servidor SSH. Antes de eso, un único apartado cuenta el caso: cómo una puerta trasera llegó a una librería de compresión muy extendida y por qué ese ataque concreto es un ejemplo de manual de riesgo en la cadena de suministro de software.

!!! consulta "Recursos de la sesión"
    **Para la práctica**

    - [xzbot](https://github.com/amlweems/xzbot): el laboratorio que reproduce el caso.
    - [Ficha CVE-2024-3094](https://nvd.nist.gov/vuln/detail/CVE-2024-3094) en la NVD.
    - El enunciado de la entrega ACT_UT2_3, «RA2.3. Seguridad en Unix», con los tres escenarios del punto 4.
    - [La historia de la puerta trasera de xz](https://securelist.com/xz-backdoor-story-part-1/112354/) (Securelist): la lectura que pide el enunciado.

    **Para ampliar** (opcional)

    - [La cronología completa del caso](https://pentest-tools.com/blog/xz-utils-backdoor-cve-2024-3094).

### La cadena de suministro: el caso xz

Una cadena de suministro de software es la sucesión de piezas de las que depende una aplicación sin haberlas escrito nadie del propio equipo: librerías, compiladores, imágenes base, paquetes del sistema. Cada eslabón que se acepta sin comprobar es un punto donde alguien más puede introducir código. `CVE-2024-3094` es el caso de manual de ese riesgo: no es un fallo de programación, es un ataque deliberado y sostenido en el tiempo contra un eslabón de esa cadena.

`xz` es un formato de compresión y `liblzma` la librería que lo implementa; la usan, entre muchos otros programas, herramientas del sistema como `systemd` (para comprimir sus registros). Entre 2021 y 2024, una identidad que se había ganado la confianza del mantenedor original del proyecto fue introduciendo, de forma progresiva y con *commits* que parecían legítimos, un código que alteraba el proceso de compilación del paquete. Ese código no estaba en el repositorio de control de versiones a la vista de todos: se escondía en los archivos de prueba del propio paquete distribuido (`.tar.xz`), de modo que quien revisara el código fuente en GitHub no lo veía, pero quien compilaba el paquete descargado sí lo ejecutaba.

```mermaid
flowchart TB
    A["<b>Identidad de confianza</b><br><small>gana acceso de mantenimiento en años</small>"]:::act
    B["<b>Código oculto en el paquete</b><br><small>no visible en el repositorio, sí en el .tar.xz</small>"]:::riesgo
    C["<b>liblzma modificada</b><br><small>versiones 5.6.0 y 5.6.1</small>"]:::pieza
    D["<b>Cadena de carga indirecta</b><br><small>sshd carga libsystemd, que carga liblzma</small>"]:::infra
    E["<b>Puerta trasera activa</b><br><small>salta la autenticación SSH con una clave del atacante</small>"]:::riesgo
    A --> B --> C --> D --> E
    classDef act fill:#ea580c22,stroke:#ea580c,stroke-width:1.5px
    classDef riesgo fill:#dc262622,stroke:#dc2626,stroke-width:1.5px
    classDef pieza fill:#64748b22,stroke:#64748b,stroke-width:1.5px
    classDef infra fill:#a1a1aa14,stroke:#a1a1aa,stroke-width:1.5px
```

<p class="pie" markdown>Ningún paso de esta cadena es, por sí solo, un exploit clásico: es una identidad de confianza, un paquete de distribución con un contenido distinto del repositorio y una dependencia indirecta que nadie había pensado en auditar. La puerta trasera solo se activa si las tres piezas coinciden.</p>

El punto que hace este caso tan citado no es la puerta trasera en sí, es dónde vivía: para que `sshd` (el servidor SSH) acabara ejecutando código de `liblzma`, hacía falta una cadena de dependencias indirecta, `sshd` cargando `libsystemd` por otro motivo (notificar su estado al gestor de servicios) y `libsystemd` cargando a su vez `liblzma` para comprimir registros. Ninguna de las dos dependencias parece, vista por separado, relacionada con la autenticación SSH; unidas, permitían que una librería de compresión interceptara una función de verificación de firma RSA y la sustituyera por la comprobación de una clave del atacante. La puntuación CVSS de `CVE-2024-3094` es 10,0, la máxima: ejecución remota de código con privilegios de root, sin necesitar credenciales válidas.

Se descubrió porque un ingeniero que mantenía software de bases de datos notó que las conexiones SSH a una máquina tardaban unos cientos de milisegundos más de lo esperado y no lo dejó pasar: no fue un escáner automático ni una auditoría formal, fue un caso de curiosidad técnica investigando algo pequeño. El fallo se descubrió antes de llegar a ninguna distribución estable: solo afectó a versiones en desarrollo o de pruebas (Debian *unstable*, Fedora *rawhide* y similares), nunca a Debian 12 estable, que sigue usando una versión anterior y no comprometida de `xz`.

### A2.5 El caso xz (sesión 13)

<span class="et et-obj">Objetivo</span> Los tres escenarios del enunciado de la RA2.3 reproducidos en una Debian 12 aislada con el laboratorio de `xzbot` (puntos 4.1, 4.2 y 4.3: `sshd` con la librería original, con la infectada y con la infectada parcheada), con el resultado de cada uno comprobado e interpretado, una investigación con `ldd` de la cadena de dependencias entre `sshd` y `liblzma`, y un análisis de qué controles habrían detectado el ataque antes de que llegara a producción.

<span class="et et-pre">Antes de empezar</span> La ISO de Debian 12 descargada en `~/iso/` del anfitrión, como pide el aviso del final de la [A2.4](#a24-docker-aislamiento-y-auditoria-sesion-12). Esta hoja crea la VM `debian12` al principio y la deja, ya instalada, sin salida a Internet ([máquinas virtuales](../laboratorio.md#maquinas-virtuales)). Se ha explicado [el caso xz](#la-cadena-de-suministro-el-caso-xz). Esta hoja sigue el README de [`amlweems/xzbot`](https://github.com/amlweems/xzbot) paso a paso: cada orden remite a la sección del README que la documenta y ninguna se reproduce aquí. El tercer escenario dispara el backdoor con la clave de investigación que el propio README sustituye por la del atacante (sección "ed448 patch"), nunca con la clave real, y solo en local (`127.0.0.1`), sin exponer nada a la red del aula.

!!! ojo "Solo con la clave de investigación, solo en loopback"
    El tercer escenario ejecuta de verdad el código de explotación que publica `xzbot`, pero con una clave ED448 propia en vez de la del atacante real: es el mecanismo que el propio proyecto documenta para poder estudiar el backdoor sin depender de una clave privada que nadie tiene. Se hace solo contra el `sshd` de prueba de `debian12`, en `127.0.0.1` y sin red externa. Hacerlo contra un servidor ajeno, con la clave real o fuera de esta VM aislada es delito (Código Penal, artículos 197 bis y 264 y siguientes).

<span class="et et-pas">Pasos</span>

El enunciado pide reproducir el exploit en los tres escenarios y analizar su funcionamiento. Antes de ejecutar nada se prepara la máquina y se comparan las tres librerías, porque esa comparación es la que explica después por qué cada escenario da lo que da; los escenarios van en el orden del enunciado, y el análisis y la restauración de la máquina cierran la hoja.

1. **Máquina y lectura.** Crea la VM `debian12` desde el anfitrión con la receta de [Crear `debian12` desde el anfitrión](../laboratorio.md#crear-debian12-desde-el-anfitrion), apuntando a la ISO que descargaste en `~/iso/`. Mientras se instala (10 a 15 min), prepara en `pps01` la herramienta `xzbot` y los dos ficheros de librería de su carpeta `assets/`, y lee el artículo de [Securelist](https://securelist.com/xz-backdoor-story-part-1/112354/) si no lo has hecho.

    *Pista:* `xzbot` se instala con `go install` y los ficheros son `liblzma.so.5.6.0` (infectada) y `liblzma.so.5.6.0.patch` (la infectada con la clave de investigación, sección "ed448 patch" del README).

2. **Las tres librerías, antes de ejecutar nada.** Cuando termine la instalación, fija en `debian12` la IP de la red solo anfitrión, copia desde `pps01` los dos ficheros y el binario `xzbot`, e instala lo que hace falta para arrancar un segundo `sshd` de prueba y comparar bibliotecas. Antes de ejecutar nada, compara las tres librerías (la original del sistema, la infectada y la parcheada) por tamaño, resumen criptográfico y símbolos exportados, y anota la diferencia. Toma la instantánea `antes-a25` y, solo entonces, quita el adaptador NAT: a partir de ahí `debian12` ya no tiene salida a Internet, pero `pps01` (`192.168.56.10`) la sigue viendo en `192.168.56.50` para copiar los resultados de vuelta.

    *Pista:* la IP se fija con `nmcli` sobre la interfaz solo anfitrión (suele ser `enp0s8`); `openssh-server` y `binutils` (trae `nm`) hay que instalarlos con el NAT todavía activo. `nm -D` lista los símbolos exportados: la parcheada solo difiere de la infectada en la clave ED448, mientras que frente a la del sistema (una versión limpia y anterior de `xz`) la diferencia es total. El adaptador NAT se quita con `VBoxManage modifyvm debian12 --nic1 none` y la VM apagada.

3. **Los tres escenarios (puntos 4.1, 4.2 y 4.3).** Reproduce los tres escenarios en un `sshd` de prueba en el puerto 2222 (aislado del `sshd` del sistema). En cada uno, prueba una conexión SSH normal y lanza `xzbot` como indica la sección "backdoor demo" de su README, que es lo que el enunciado llama ejecutar el exploit; anota el resultado y qué diferencia el tercero de los otros dos:

    - **Escenario 1, librería original (punto 4.1).** Con la librería oficial de Debian, sin comprometer: la conexión normal funciona y `xzbot` no consigue nada.
    - **Escenario 2, librería infectada (punto 4.2).** Fuerza la librería infectada con `LD_PRELOAD` (nada se recompila): la conexión normal es idéntica a la del escenario 1 y `xzbot` tampoco consigue nada, porque la puerta trasera solo reacciona ante la clave del atacante, que aquí nadie tiene. Eso es lo que hizo el ataque tan difícil de notar.
    - **Escenario 3, librería infectada parcheada (punto 4.3).** Con la librería parcheada, `xzbot` ejecuta una orden inofensiva sin usuario ni contraseña: se ejecuta como `root` aunque la conexión no llegue a autenticarse. Es la ejecución remota de código que puntúa `CVE-2024-3094` con un CVSS de 10,0.

    *Pista:* las dos librerías copiadas desde `pps01` son `liblzma.so.5.6.0` (infectada) y `liblzma.so.5.6.0.patch` (parcheada); el resultado del escenario 3 queda en `/tmp/xzbot-a25.txt`.

4. **Dependencias con `ldd` (punto 4.1).** El enunciado pide usar `ldd` en el primer escenario para observar las librerías dinámicas del ejecutable. Investiga con `ldd`, sin modificar nada del sistema, la cadena de dependencias real de esta máquina: si `sshd` depende de `libsystemd` y si `libsystemd` depende a su vez de `liblzma`. Explica con tus palabras por qué esa cadena, si existe, es la que un atacante necesitaba para que una librería de compresión pudiera intervenir en la autenticación SSH.

    *Pista:* `ldd` sobre el binario de `sshd` y sobre el `libsystemd.so` que localice `ldconfig -p`. Si la cadena no aparece en esta máquina, es un resultado válido y se anota como tal.

5. **Análisis del funcionamiento (puntos 4.1 a 4.3).** Escribe el análisis final en el `README.md`: qué diferencia el comportamiento observable de los tres escenarios (no el contenido del backdoor en sí), por qué Debian 12 estable no se vio afectado en producción aunque comparta la misma arquitectura de dependencias, y qué controles de cadena de suministro habrían detectado o dificultado este ataque antes de llegar a producción (firma criptográfica de los artefactos publicados, comprobar que el código fuente del repositorio coincide con el del paquete distribuido, reducir el número de dependencias indirectas de un servicio crítico como `sshd`).

6. **Resultados a salvo y máquina restaurada.** Copia la carpeta de resultados de `debian12` a `pps01`, súbela desde `pps01` y vuelve `debian12` a la instantánea `antes-a25` (con la VM apagada desde el anfitrión).

    *Pista:* al restaurar se pierde todo lo hecho dentro de `debian12`, así que la copia a `pps01` va antes.

<span class="et et-com">Comprobación</span> Los tres escenarios se han ejecutado en orden y el resultado de cada uno coincide con lo esperado (conexión normal y `xzbot` sin efecto en el 1 y en el 2, ejecución de `id` sin autenticación en el 3); el apartado de `ldd` dice explícitamente si la cadena `sshd` → `libsystemd` → `liblzma` existe en `debian12`, con la orden y su salida como evidencia; y el análisis final nombra al menos dos controles de cadena de suministro concretos, no genéricos.

<span class="et et-ent">Para practicar</span> Guarda en `ut2/a25/` de `pps-entregas` el `README.md` y las salidas de los tres escenarios (el binario `xzbot` y los ficheros `.so` descargados no hace falta subirlos: están en el repositorio original). Con ellos se hace el PDF de la entrega **ACT_UT2_3 · Seguridad en Unix (xz)** (plazo, el 26 de noviembre), un capítulo por escenario del enunciado.

## Sesión 14 · Margen y repaso de la unidad 2

<p class="ut-meta" markdown>23 de noviembre · Margen · <span class="dur" tabindex="0" aria-label="Repaso y recuperación · 110 min" data-dur="Repaso y recuperación · 110 min">:material-school:<i class="dur-barra" style="--teoria:0%"></i>:material-flask:</span></p>

Esta sesión no trae contenido nuevo: absorbe el retraso de las clases de la unidad que se hayan perdido y, si no se ha perdido ninguna, sirve para repasar la unidad y para la actividad optativa ACT_UT2_4. Hoy vence el plazo de ACT_UT2_2 (Docker) y el de ACT_UT2_3 (xz) vence el jueves 26 de noviembre; los plazos no se mueven aunque se haya perdido una clase, solo se mueve el contenido.

!!! consulta "Recursos de la sesión"
    **Para la práctica**

    - [Guía de ransomware de INCIBE](https://www.incibe.es/sites/default/files/contenidos/guias/doc/guia_ransomware.pdf): la lectura de la actividad.
    - [No More Ransom](https://www.nomoreransom.org/es/index.html): herramientas de descifrado de familias conocidas.
    - El enunciado de la entrega optativa ACT_UT2_4, «RA2.4. Análisis de un Ransomware», con las dos entradas del ransomware de laboratorio que analiza.

**Si se ha perdido alguna clase**

- Recuperar primero lo que tiene plazo más cercano. Hoy vence ACT_UT2_2, así que si falta la [A2.4](#a24-docker-aislamiento-y-auditoria-sesion-12), la de Docker, es lo primero: se siguen sus pasos completos y se sube la carpeta `ut2/a24/` antes de las 23:59.
- Después, lo que vence el jueves 26 de noviembre: la [A2.5](#a25-el-caso-xz-sesion-13), la del caso xz. Necesita la VM `debian12` con su instantánea inicial ([máquinas virtuales](../laboratorio.md#maquinas-virtuales)).
- ACT_UT2_1, la hoja de cálculo de ASVS que sale de la A2.2 y la A2.3, venció el lunes 16 de noviembre. Quien no la haya entregado la sube ya: fuera de plazo y sin causa justificada se corrige sobre el 50 %.
- Solo cuando todo lo obligatorio esté entregado, si queda tiempo, mirar la actividad optativa de más abajo.

**Si no se ha perdido ninguna clase**

- Repasar los criterios de las [prácticas evaluables](#practicas-evaluables-de-la-unidad) y comprobar que cada punto de cada enunciado tiene su evidencia en `pps-entregas` (`ut2/a22/` a `ut2/a25/`).
- Terminar lo que haya quedado a medias de lo que se hace en casa: la hoja de cálculo completa de la A2.3, si ACT_UT2_1 aún no está entregada, y los pasos 4 a 6 de la A2.4 (docker-bench-security, las prácticas 2 y 3 y las lecturas), que vencen hoy con ACT_UT2_2.
- Repasar las [prácticas evaluables](#practicas-evaluables-de-la-unidad) y sus tablas de criterios: cada fila indica de qué hoja sale su evidencia y cuánto pesa.
- Hacer la actividad optativa ACT_UT2_4, descrita a continuación, si el tiempo lo permite.

### ACT_UT2_4 · Análisis de un ransomware (optativa)

**Objetivo.** Entender cómo se comporta un ransomware y, sobre todo, cómo se detecta, se contiene y se previene. Es una actividad de **reserva y optativa**: no tiene hoja, no es necesaria para aprobar la unidad y solo se hace si no se ha perdido ninguna clase y todo lo obligatorio está entregado. Su enunciado es «RA2.4. Análisis de un Ransomware» y cubre los criterios c y d. Si se entrega, sube el nivel de logro de RA2 y su plazo, si se hace, es el jueves 26 de noviembre a las 23:59.

**Qué se hace.** El enunciado fija tres puntos: 3.1.1, leer la guía de ransomware de INCIBE; 3.1.2, ejecutar el ransomware de laboratorio de las dos entradas que enlaza y observar su comportamiento; y 3.1.3, redactar el informe forense. La ejecución del 3.1.2 queda acotada por las precauciones de abajo, y el peso de la entrega está en el **informe de análisis y las medidas de prevención**.

!!! ojo "Malware solo en un laboratorio aislado y con instantánea"
    Ejecutar un ransomware fuera de una máquina virtual aislada puede cifrar datos reales, propios o de la red, sin vuelta atrás. Distribuir o lanzar malware contra sistemas ajenos es delito (Código Penal, artículos 264 y siguientes). Estas guías no incluyen pasos de creación ni de ejecución de malware: quien decida hacer esa parte lo hace siguiendo el enunciado del aula y solo con las cuatro condiciones siguientes.

Las precauciones, todas a la vez:

1. Una máquina virtual **desechable** (no `pps01`, que guarda el repositorio de entregas), con instantánea limpia tomada antes de empezar.
2. **Sin red**: adaptador desconectado, sin carpetas compartidas ni portapapeles compartido con el anfitrión.
3. **Sin datos reales**: solo ficheros de prueba creados para la ocasión.
4. Al terminar, se destruye la máquina o se vuelve a la instantánea, y se comprueba que el anfitrión no ha cambiado.

**Qué se entrega.** Un informe en PDF (formato de la *Normativa de entrega*) con un capítulo por punto del enunciado: en el 3.1.1, el resumen propio de la guía de INCIBE; en el 3.1.2, lo observado al ejecutar el ransomware en el laboratorio aislado, con capturas; y en el 3.1.3, el informe forense, con este guion:

| Apartado | Qué contiene |
|---|---|
| Resumen del caso | Qué es el ransomware analizado, de qué tipo es (cifrado, bloqueo, doble extorsión, como servicio) y qué exige |
| Ciclo del ataque | Infección inicial, cifrado, nota de rescate y consecuencias, con lo que se ha observado en el laboratorio |
| Indicadores de compromiso | Ficheros creados o modificados, extensión añadida, nota de rescate y procesos, tal como se ven en un análisis forense |
| Impacto | Qué datos y servicios se pierden y qué pasa si no hay copia de seguridad |
| Medidas de prevención y contención | Al menos cinco, ligadas a la guía de INCIBE: formación frente al phishing, parches, copias desconectadas de la red y probadas, antivirus y cortafuegos, segmentación de red y mínimos privilegios |
| Recuperación | Qué se haría en una empresa: aislar, no pagar el rescate, restaurar desde copia, denunciar y consultar *No More Ransom* |
| Relación con ASVS | Qué requisitos de la hoja de la A2.3 habrían dificultado la entrada (por ejemplo, subida de ficheros, validación de entradas o integridad de actualizaciones) |

Quien no pueda garantizar las cuatro precauciones no ejecuta nada: lo dice en el capítulo 3.1.2, describe el comportamiento a partir de las dos entradas del enunciado y de una familia ya documentada públicamente, y ese punto se califica sobre el análisis. El criterio d pide reconocer riesgos, no lanzar malware.

!!! examen "Qué se evalúa"
    La calidad del informe: si los indicadores de compromiso son coherentes con el tipo de ransomware, si las medidas de prevención responden a cada fase del ciclo y si la recuperación descarta pagar el rescate con argumentos. Una lista de medidas genéricas sin relación con el análisis se queda en «Funcionamiento correcto» (60 %). El enunciado no trae rúbrica: se aplican los niveles de la de la RA2.2, con los pesos de [su apartado](#act_ut2_4-ransomware-optativa).

## Prácticas evaluables de la unidad

La unidad tiene tres entregas obligatorias, ACT_UT2_1 a ACT_UT2_3, y una optativa, ACT_UT2_4. Ninguna tiene sesión propia: cada una se construye con la hoja o las hojas de las que sale y se cierra por su plazo. La A2.1 (riesgos de una aplicación) no la pide ningún enunciado y no se califica. **Cada entrega tiene en el aula su enunciado en PDF, y lo que dice ese enunciado es lo que se entrega**: este apartado lo resume y dice de qué paso de qué hoja sale cada punto, pero no añade ni quita nada. Lo que las hojas proponen fuera del enunciado está en sus «Si te sobra tiempo» y solo cuenta como «Extra», el nivel más alto de la rúbrica.

| Entrega en Aules | Enunciado (PDF) | Hojas | Plazo | CE |
|---|---|---|---|---|
| ACT_UT2_1 · OWASP ASVS | Actividad RA2.1. Application Security Verification Standard | A2.2 y A2.3 | lunes 16 de noviembre, 23:59 | a, b |
| ACT_UT2_2 · Seguridad en Docker | RA2.2. Seguridad en Docker | A2.4 | lunes 23 de noviembre, 23:59 | c, d |
| ACT_UT2_3 · Seguridad en Unix (xz) | RA2.3. Seguridad en Unix | A2.5 | jueves 26 de noviembre, 23:59 | a, b |
| ACT_UT2_4 · Ransomware (optativa) | RA2.4. Análisis de un Ransomware | reserva de la sesión 14 | jueves 26 de noviembre, 23:59, si se hace | c, d |

**Cómo se entrega.** ACT_UT2_1 es distinta de las demás porque su enunciado fija el formato: se entrega **la hoja de cálculo** (`.ods` o `.xls`) con plantilla corporativa, subida a la tarea de Aules, no un PDF. Las otras tres no fijan formato y se entregan como el resto de entregas en documento del módulo: un PDF en la tarea de Aules con la estructura de la *Normativa de entrega* (portada, índice, introducción, desarrollo, bibliografía y conclusión), con el desarrollo ordenado por los puntos del enunciado (4.1.1, 4.2.1...), y en el texto de la tarea la URL de `pps-entregas`, donde están las carpetas de las hojas con las salidas y las evidencias. Cómo se pasa de los README de las hojas al PDF está en [Del README al PDF de la entrega](../laboratorio.md#del-readme-al-pdf-de-la-entrega); lo que lleva cada capítulo, en el apartado de cada entrega. Los plazos vencen a las 23:59 (hora de Madrid) y una entrega fuera de plazo y sin causa justificada se corrige sobre el 50 %. La ponderación de las entregas entre sí y con el examen está en [el módulo](../modulo.md).

**Cómo se califica.** Los enunciados de RA2.1 y RA2.2 traen rúbrica, y es la que se aplica. Los de RA2.3 y RA2.4 no la traen: se califican con los niveles de la rúbrica de RA2.2, punto por punto, con los pesos que se proponen en su apartado. Cada fila se califica en uno de estos niveles:

| Nivel | RA2.1, punto 3.2.1 | RA2.1, punto 3.2.2 | RA2.2, RA2.3 y RA2.4 |
|---:|---|---|---|
| 40 y 60 % | Tabla L1 | Tabla L1 | Funcionamiento correcto |
| 80 % | Plantilla corporativa | Análisis técnico | Análisis técnico |
| 90 % | Checklist | Validación completa | Validación completa |
| 100 % | Extra | Extra | Extra |

Las filas de lectura (3.1.1 en RA2.1 y 4.1.1 en RA2.2) no tienen niveles en la rúbrica. La nota de cada CE es la media ponderada de sus filas.

### ACT_UT2_1 · OWASP ASVS

Enunciado: «Actividad RA2.1. Application Security Verification Standard». Sale de las hojas [A2.2](#a22-asvs-elegir-el-nivel-sesion-10) y [A2.3](#a23-asvs-verificacion-l1-sesion-11), que trabajan sobre el mismo fichero. Plazo: **lunes 16 de noviembre, 23:59**, el mismo día de la sesión 12. Lo que no se termina en clase (unos 95 requisitos) **se completa en casa antes del plazo**.

| Punto del enunciado | CE | Peso (rúbrica) | De dónde sale |
|---|---|---|---|
| 3.1.1 Lectura Application Security Verification Standard 4.0.3 | a | 0 % | A2.2, paso 1 |
| 3.2.1 Realizar tabla por secciones con todos los elementos L1 | b | 100 % | A2.2, pasos 2 y 3, y A2.3, paso 3 |
| 3.2.2 Analizar, indicar y verificar cada uno de los elementos L1 aplicados al escenario | b | 100 % | A2.2, paso 4, y A2.3, pasos 1 a 3 |

La rúbrica pone el CE a al 0 % y las dos filas del CE b al 100 % cada una: cada fila se califica sobre 100 y la nota del CE b es la media de las dos.

**Qué lleva la hoja de cálculo.** No hay PDF: el entregable es el fichero `ACT_UT2_1.ods` (o `.xls`), con:

1. **Portada.** Nombre y usuario `pps<NIA>`, fecha, el escenario del enunciado (la empresa de compra-venta de robellones y su arquitectura cliente-servidor), el nivel L1 que fija y los tres servidores sobre los que se verifica.
2. **3.2.1 Tabla L1 por secciones.** Los 128 requisitos L1 de ASVS 4.0.3, agrupados por capítulo y sección, con formato corporativo (nivel 80 %) y la columna «Checklist» marcada en todas las filas (nivel 90 %).
3. **3.2.2 Análisis y verificación.** En cada fila, en qué servidor se aplica, el fichero o la técnica concreta, la prueba que lo verifica y el riesgo residual; los que no aplican, con su motivo. Una explicación breve sin fundamento técnico no cuenta: es lo que el enunciado descarta.

Si has hecho algo de los «Si te sobra tiempo» de la A2.2 y la A2.3, va en una pestaña final, «Extra».

### ACT_UT2_2 · Seguridad en Docker

Enunciado: «RA2.2. Seguridad en Docker». Sale de la hoja [A2.4](#a24-docker-aislamiento-y-auditoria-sesion-12). Plazo: **lunes 23 de noviembre, 23:59**, el día de la sesión de margen. Los puntos 4.1.1, 4.2.2, 4.2.3 y 4.4.1 **se hacen en casa antes del plazo**.

| Punto del enunciado | CE | Peso en su CE (rúbrica) | De dónde sale |
|---|---|---|---|
| 4.1.1 Lectura y comprensión | c | sin peso | A2.4, paso 6 |
| 4.2.1 Práctica 1 | c | 35 % | A2.4, paso 1 |
| 4.2.2 Práctica 2 | c | 35 % | A2.4, paso 5 |
| 4.2.3 Práctica 3 | c | 30 % | A2.4, paso 5 |
| 4.3.1 Exploit de la práctica 1 | d | 40 % | A2.4, paso 2 |
| 4.4.1 Aplicar docker-bench-security | d | 30 % | A2.4, paso 4 |
| 4.5.1 Aplicar apparmor | d | 30 % | A2.4, paso 3 |

**Qué lleva el PDF.** Portada, índice e introducción, y en el desarrollo un capítulo por punto:

1. **4.1.1 Lectura y comprensión.** El resumen propio de las tres lecturas: el contenedor como proceso, el aislamiento con namespaces y la guía de seguridad de Docker.
2. **4.2.1 Práctica 1.** Cómo se ha construido la imagen Log4Shell, la orden de `trivy` y su salida, y el paquete de Log4j con su versión, su CVE y la versión que lo corrige.
3. **4.2.2 Práctica 2.** La imagen de WordPress escaneada, con su etiqueta, el resumen de vulnerabilidades críticas y por qué la etiqueta antigua es peor.
4. **4.2.3 Práctica 3.** El SBOM generado con Syft, el análisis con Grype, la captura de Dependency-Track y qué añade un SBOM frente a escanear la imagen.
5. **4.3.1 Exploit de la práctica 1.** El contenedor sin salida a Internet, la prueba con la expresión inofensiva antes y después de la mitigación, qué haría la segunda fase de un ataque real y cuál es la corrección definitiva.
6. **4.4.1 docker-bench-security.** Un fragmento del informe y los tres hallazgos de secciones distintas: qué comprueba cada uno, por qué importa y cómo se resuelve.
7. **4.5.1 AppArmor.** El perfil `pps-confinado`, cómo se carga y la comparación de los dos contenedores en `/tmp` y en `/etc`.

Después, la bibliografía (las lecturas y los repositorios del enunciado) y la conclusión, y el capítulo «Extra» con el endurecimiento de la A2.4 si lo hay.

### ACT_UT2_3 · Seguridad en Unix (xz)

Enunciado: «RA2.3. Seguridad en Unix». Sale de la hoja [A2.5](#a25-el-caso-xz-sesion-13). Plazo: **jueves 26 de noviembre, 23:59**. El enunciado no trae rúbrica: los pesos de esta tabla son una propuesta por punto, con los niveles de la rúbrica de RA2.2, y los CE son los que indica el enunciado (a y b).

| Punto del enunciado | CE | Peso en la entrega | De dónde sale |
|---|---|---|---|
| 4 Lectura del artículo de Securelist | a | 10 % | A2.5, paso 1 |
| 4.1 Reproducir escenario 1: librería original y `ldd` | a | 40 % | A2.5, pasos 2, 3 y 4 |
| 4.2 Reproducir escenario 2: librería infectada | b | 25 % | A2.5, pasos 3 y 5 |
| 4.3 Reproducir escenario 3: librería infectada parcheada | b | 25 % | A2.5, pasos 3 y 5 |

**Qué lleva el PDF.** Portada, índice e introducción, y en el desarrollo un capítulo por punto:

1. **4 Lectura.** El resumen propio del artículo de Securelist: cómo llegó la puerta trasera al paquete y por qué no se veía en el repositorio.
2. **4.1 Escenario 1.** La máquina aislada con su instantánea, la comparación de las tres librerías, la conexión y `xzbot` con la librería original, y la salida de `ldd` con la explicación de la cadena `sshd`, `libsystemd`, `liblzma`.
3. **4.2 Escenario 2.** La librería infectada forzada con `LD_PRELOAD`, el resultado de la conexión y de `xzbot` y por qué es idéntico al del escenario 1.
4. **4.3 Escenario 3.** La librería parcheada, la ejecución de la orden como `root` sin autenticación, por qué Debian 12 estable no se vio afectado y los controles de cadena de suministro que habrían detectado el ataque.

Después, la bibliografía (el repositorio y las lecturas del enunciado) y la conclusión.

### ACT_UT2_4 · Ransomware (optativa)

Enunciado: «RA2.4. Análisis de un Ransomware». Es la actividad de reserva de la [sesión 14](#sesion-14-margen-y-repaso-de-la-unidad-2) y solo suma si el resto de la unidad está entregado. Plazo, si se hace: **jueves 26 de noviembre, 23:59**. El enunciado no trae rúbrica: los pesos son una propuesta por punto, con los niveles de la rúbrica de RA2.2.

| Punto del enunciado | CE | Peso en la entrega | De dónde sale |
|---|---|---|---|
| 3.1.1 Lectura de la guía de INCIBE | c | 20 % | Sesión 14, «Qué se entrega» |
| 3.1.2 Ejecutar el ransomware | d | 30 % | Sesión 14, precauciones |
| 3.1.3 Realizar informe forense del ransomware | c, d | 50 % | Sesión 14, guion del informe |

**Qué lleva el PDF.** Portada, índice e introducción, un capítulo por punto con el contenido que se describe en la [sesión 14](#act_ut2_4-analisis-de-un-ransomware-optativa), la bibliografía y la conclusión.

## Errores frecuentes en el laboratorio

Para lo general (VM que no arranca, disco lleno, Docker sin permisos, puertos ocupados) mira [Si algo se rompe](../laboratorio.md#si-algo-se-rompe). Aquí, lo específico de esta unidad.

**Log4Shell: el registro no muestra nada al enviar la expresión de prueba.** Hay tres causas habituales. La primera, que el argumento de `-H` va entre comillas dobles y la shell intenta expandir `${java:version}` antes de que `curl` lo vea: tiene que ir entre comillas simples, tal como está en el paso 2 de la A2.4. La segunda, que el contenedor acaba de arrancar y todavía no ha registrado la petición: se espera unos segundos y se repite. La tercera, que se está leyendo el contenedor equivocado: `docker ps` dice cuál corre y `docker logs vulnerable-app 2>&1 | grep "API version"` filtra su registro.

**Log4Shell: `docker run` dice que el nombre `vulnerable-app` ya está en uso o que el puerto 8082 está ocupado.** Queda un contenedor de un intento anterior. `docker rm -f vulnerable-app` lo quita y `ss -ltnp | grep 8082` dice si hay otro proceso en ese puerto.

**Log4Shell: el segundo `ping` sigue respondiendo después de la regla de `iptables`.** La regla se puso con una IP y el contenedor tiene otra, casi siempre porque se recreó (paso 2) y Docker le asignó una distinta. Se vuelve a leer la IP con `docker inspect` y se repite la regla. Si `iptables` dice que la cadena `DOCKER-USER` no existe, Docker no está arrancado: `systemctl status docker`.

**`docker pull` o `trivy` fallan con `toomanyrequests`.** Con treinta alumnos descargando a la vez desde la misma red, el registro aplica su límite de peticiones anónimas. Se espera unos minutos y se repite, o se inicia sesión en Docker Hub con la cuenta del curso (`docker login`). La primera ejecución de `trivy` descarga además su base de datos de vulnerabilidades, y esa descarga puede fallar por el mismo motivo: repetir el mismo comando basta.

**`docker-bench-security` deja en la carpeta de la hoja un repositorio anidado.** Si en el paso 4 de la A2.4 el repositorio se clona dentro de `ut2/a24/`, `git add .` avisa de `adding embedded git repository` o sube una referencia vacía. Se evita clonando fuera de `pps-entregas` (por ejemplo en `~/`) y dejando en la carpeta de la hoja solo el `docker-bench.txt`. Si ya se hizo, `git rm --cached docker-bench-security` y se borra la carpeta clonada.

**El `docker-bench.txt` sale con caracteres raros y muchos `[WARN]`.** Los caracteres son los códigos de color del terminal: `sed 's/\x1b\[[0-9;]*m//g' docker-bench.txt` los quita. Los `[WARN]` de la sección 1 (auditoría con `auditd` de los ficheros de Docker) y de la 2 son normales en una máquina de laboratorio recién instalada: el objetivo no es dejar el informe en verde, es entender tres hallazgos. Si sale sin resultados o con `Permission denied`, faltó `sudo`.

**AppArmor: `apparmor_parser: command not found` o `aa-status` no existe.** Faltan los paquetes de AppArmor. `sudo apt install apparmor apparmor-utils` los instala y `cat /sys/module/apparmor/parameters/enabled` tiene que responder `Y`; si responde `N`, AppArmor no está activo en el kernel de esa máquina y el perfil no se aplicará aunque se cargue.

**AppArmor: `apparmor_parser` termina con `syntax error`.** Casi siempre falta una coma al final de una regla (`network,`, `file,`) o una llave. Cada regla de un perfil acaba en coma, incluida la última antes de `}`.

**AppArmor: `docker run` dice que el perfil `pps-confinado` no existe o no está cargado.** Los perfiles cargados con `apparmor_parser -r` viven en el kernel, no en disco: después de reiniciar la VM hay que cargarlos otra vez. `sudo aa-status | grep pps-confinado` lo confirma.

**AppArmor: el contenedor con perfil escribe en `/etc` igualmente.** `docker inspect -f '{{.AppArmorProfile}}' confinado` responde `unconfined` o `docker-default` si la opción `--security-opt apparmor=pps-confinado` se escribió mal o se puso después del nombre de la imagen: las opciones de `docker run` van antes de la imagen, lo que va después es la orden del contenedor.

**xz: `wget` falla en `debian12`.** La máquina no tiene salida a Internet a propósito. Los dos ficheros se descargan en `pps01` y se copian con `scp` por la red solo anfitrión (pasos 1 y 2). Por la misma razón, `binutils` (que trae `nm`) y `openssh-server` se instalan antes de cortar la red, con el adaptador NAT todavía activo (paso 2); sin ellos, `nm: command not found` o `ldd` sobre un `sshd` que no existe.

**xz: `ldd` no muestra `libsystemd` en la salida de `sshd`.** No es un error de la orden: es un resultado, y se anota como tal. La cadena solo existe en los sistemas cuyo `sshd` se compiló con soporte de `systemd`. La hoja pide decir si existe **en esta máquina**, con la orden y su salida como prueba, y explicar qué habría cambiado si existiera.

**xz: `VBoxManage snapshot ... restore` falla o borra los resultados.** Con la VM encendida el comando se niega; hay que apagarla antes (`VBoxManage controlvm debian12 poweroff`). Y al restaurar se pierde todo lo hecho dentro de `debian12` desde la instantánea, así que la carpeta de resultados se copia a `pps01` **antes** (paso 6).

**ASVS: los identificadores de la hoja no coinciden con los del CSV.** Se mezclaron dos versiones del estándar. El curso usa la 4.0.3 (capítulos V1 a V14); la 5.0 tiene otra numeración y otros capítulos. Se descarga el CSV de la versión 4.0.3 y se comprueba que la primera fila indica esa versión.

**ASVS: la hoja lista requisitos de L2 o le faltan de L1.** Al filtrar el CSV por nivel hay que quedarse solo con los marcados para L1: son 128, y V1 no tiene ninguno. El [recuento por capítulo](#owasp-asvs-que-es-y-su-estructura-por-capitulos) sirve para comprobar que no falta ni sobra ninguno.

**ASVS: filas con «Checklist: cumplido» y «dónde: el servidor».** Es la respuesta que el enunciado descarta: no sirve una explicación sin fundamento técnico. Cada fila dice qué servidor (aplicación, base de datos, proxy), qué fichero o técnica y qué prueba concreta; si un requisito no aplica al escenario, se marca `no aplica` y se justifica en una línea.

**Hoja de cálculo: el programa cambia lo que se escribe.** Un identificador escrito sin la `V` inicial (`2.10`) se convierte en número y pierde el cero final; una celda que empieza por `=`, `+` o `-` se interpreta como fórmula y aparece `#NAME?`. Se da formato de texto a la columna antes de pegar y se escribe el identificador completo (`V2.1.10`). Un CSV importado con los acentos rotos se importa de nuevo indicando codificación UTF-8.

**Hoja de cálculo: `git` sube ficheros temporales.** LibreOffice deja un `.~lock.<nombre>#` junto al fichero mientras está abierto. Se cierra el programa antes del commit y se añade `.~lock.*` al `.gitignore` del repositorio.

**A2.1: la puntuación CVSS no coincide con la de la ficha de la NVD.** La ficha muestra varias (v2.0, v3.1, v4.0, y la del CNA junto a la del NIST). La hoja usa la **v3.1** y, si hay dos, la del NIST; se anota cuál se ha copiado.

Los enlaces para ampliar y los apartados que van más allá de lo que se hace en clase están en [Para ampliar](../ampliacion.md#ut2-nivel-de-seguridad-requerido).
