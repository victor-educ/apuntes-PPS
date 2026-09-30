# Chuleta de comandos

Lo que se teclea una y otra vez en las hojas, agrupado por herramienta y en el orden en que aparece en las unidades. No sustituye a la documentación: sirve para no tener que buscarlo cada vez. Solo figuran comandos que las hojas usan; cada uno se explica con calma en su unidad.

## Git

```bash
# Configuración inicial y clonado (UT1, A1.1)
git config --global user.name "pps<NIA>"          # identidad para los commits
git config --global user.email "<correo>"
git clone git@github.com:pps<NIA>/pps-entregas.git ~/pps-entregas   # copia local del repositorio
git branch -M main                                # renombra la rama actual a main
git remote -v                                     # a qué URL apunta el remoto
git status                                        # qué ha cambiado y qué está preparado

# Ciclo diario de entrega (todas las hojas)
git add .                                         # prepara los cambios
git commit -m "A1.1 puesto de trabajo"            # los confirma con un mensaje
git push -u origin main                           # los sube (-u solo la primera vez)
git pull                                          # trae los cambios del remoto
git pull --rebase                                 # trae los cambios sin commit de fusión

# Ramas y fusiones (UT1, A1.7; UT5, A5.2)
git log --oneline --graph                         # historial en forma de árbol
git switch -c feature/saludo                      # crea una rama y cambia a ella
git switch main                                   # vuelve a otra rama
git merge <rama>                                  # fusiona una rama en la actual
git merge --abort                                 # deshace una fusión con conflicto
git fetch                                         # baja el remoto sin tocar el trabajo
git push -u origin feature/saludo                 # sube la rama nueva
git commit -am "cambio directo"                   # add + commit de lo ya rastreado

# Revisar antes de subir (UT5, A5.8 y proyecto)
git diff | grep -iE 'password|token|secret'       # busca secretos en el cambio
git grep -n -i -E "password|token|secret" -- Jenkinsfile   # y en los ficheros versionados
git log -p --all | grep -i -E "ghp_|dckr_pat_" | head      # y en todo el historial
git check-ignore -v terraform/terraform.tfstate   # confirma que un fichero se ignora
git remote add origin https://github.com/pps<NIA>/pps-iac.git   # enlaza un remoto nuevo
```

## Ensamblador y depuración (nasm, ld, gdb)

```bash
# Herramientas (UT1, A1.2)
sudo apt install -y nasm gdb strace               # ensamblador, depurador y trazador
nasm -v                                           # versión instalada

# Ensamblar, enlazar y ejecutar
nasm -f elf64 hola_enunciado.asm -o hola_enunciado.o   # ensambla a objeto de 64 bits
ld hola_enunciado.o -o hola_enunciado             # enlaza el ejecutable
./hola_enunciado                                  # lo ejecuta
echo $?                                           # código de salida

# Inspeccionar el binario
readelf -h hola | grep 'Entry point'              # dirección de entrada del ELF
readelf -S hola                                   # secciones del fichero
nm hola                                           # símbolos
objdump -d -M intel hola                          # desensambla en sintaxis Intel
objdump -s -j .data hola                          # vuelca la sección de datos
file hola hola_c                                  # tipo de cada fichero
ldd hola_c                                        # bibliotecas dinámicas que necesita
strace ./hola 2>&1 >/dev/null | wc -l             # cuenta las llamadas al sistema
strace -e trace=write ./hola_c                    # solo las llamadas write

# Depurar con gdb (A1.3)
echo 'set disassembly-flavor intel' >> ~/.gdbinit # sintaxis Intel por defecto
nasm -f elf64 -g -F dwarf hola.asm -o hola.o && ld hola.o -o hola   # con símbolos de depuración
gdb -q ./hola                                     # abre el depurador sin cabecera
```

```text
(gdb) break _start                # punto de parada en la primera instrucción
(gdb) run                         # ejecuta hasta el punto de parada
(gdb) x/8i $rip                   # 8 instrucciones desde la actual
(gdb) info registers rax rdi rsi rdx   # valor de los registros
(gdb) stepi                       # una instrucción cada vez (nexti no entra en llamadas)
(gdb) x/s $rsi                    # memoria como texto
(gdb) x/gx $rsp                   # cima de la pila
(gdb) p $_exitcode                # código de salida del proceso
(gdb) quit                        # salir
```

## Python y Go: pruebas

```bash
# Python (UT1, A1.4)
python3 hola.py                                   # ejecuta un programa
python3 puertos.py 22 abc                         # con argumentos
python3 -m unittest -v                            # todas las pruebas, cada una con su resultado
python3 -m dis puertos.py | head -30              # bytecode que genera CPython
code --install-extension ms-python.python         # extensión de Python para VS Code

# Go (UT1, A1.5)
sudo apt install -y golang-go                     # instala Go
go version                                        # versión instalada
go mod init puertos                               # crea el módulo (go.mod)
go run . 22 8080 abc                              # compila y ejecuta
go build                                          # genera el binario
go test -v                                        # pruebas, cada una con su resultado
go test -run Rango                                # solo las que casan con el nombre
go test -count=1 -v                               # fuerza la ejecución sin caché
go test -cover                                    # porcentaje de líneas cubiertas
go test -coverprofile=c.out && go tool cover -html=c.out   # informe de cobertura en HTML
go vet                                            # avisa de código sospechoso que compila
gofmt -l .                                        # lista ficheros sin formatear
go install github.com/go-delve/delve/cmd/dlv@latest   # depurador Delve
code --install-extension golang.go                # extensión de Go para VS Code
```

## Bash

```bash
# Ejecutar y depurar scripts (UT1, A1.6)
chmod +x puertos.sh                               # lo hace ejecutable
./puertos.sh 22 abc                               # lo ejecuta
bash -n puertos.sh                                # solo comprueba la sintaxis
bash -x ./puertos.sh 22 abc 2>&1 | tee traza1.txt # traza cada orden (sale por el error estándar)
sed -n '1,115p' LearnBash.sh > bloque1.sh         # extrae un tramo de líneas
bash -c 'echo "$1"' _ "$entrada"                  # pasa el dato como argumento, no como código
```

## Docker y Compose

```bash
# Comprobar y preparar (UT1, A1.1; UT5)
sudo usermod -aG docker "$USER"                   # permite usar Docker sin sudo (reentrar en la sesión)
docker run --rm hello-world                       # prueba mínima de que funciona

# Imágenes y contenedores (UT3, A3.1)
docker build -t pps-base .                        # construye una imagen desde el Dockerfile
docker build -t pps-a31 -f Dockerfile.basico .    # con otro fichero de construcción
docker run -d --rm --name web -p 8080:80 pps-base # arranca en segundo plano y publica el puerto
docker rm -f web                                  # para y borra el contenedor
docker exec web apache2ctl -S                     # ejecuta una orden dentro
docker exec web apache2ctl configtest             # valida la configuración de Apache
docker cp csp.html web:/var/www/html/csp.html     # copia un fichero al contenedor
docker logs vulnerable-app 2>&1 | grep "API version" | tail -1   # busca en el registro (UT2)
docker inspect -f '{{.RestartCount}}' web-con     # lee un campo concreto (UT5)
docker ps -a --filter name=web- --format '{{.Names}} {{.Status}}'   # lista con filtro y formato

# Aislamiento (UT2, A2.4)
docker run -d --name vulnerable-app -p 127.0.0.1:8082:8080 $IMG   # publica solo en local
docker run -d --name confinado --security-opt apparmor=pps-confinado ubuntu:24.04 sleep 300   # con perfil AppArmor
docker run --rm aquasec/trivy image --scanners vuln --severity CRITICAL $IMG   # escanea vulnerabilidades

# Registro (UT3)
docker login -u pps<NIA>                          # inicia sesión en Docker Hub
docker push pps<NIA>/pr1                          # sube la imagen
docker pull pps000000/pps-app:N                   # la baja

# Volúmenes y copias (UT5)
docker volume create jenkins_restaurado           # crea un volumen
docker run -d --name jenkins --restart unless-stopped -p 8090:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home pps-jenkins:1   # datos en volumen y reinicio automático
docker exec -it jenkins bash                      # shell interactiva en el contenedor

# Compose (UT3, UT5)
docker compose build                              # construye las imágenes del compose.yml
docker compose up -d                              # levanta los servicios en segundo plano
docker compose ps                                 # estado de los servicios
docker compose cp dvwa:/var/www/html/vulnerabilities/xss_r/source/low.php ./low.php   # copia desde un servicio
```

## Apache y curl

Servidor web de las unidades 2 y 3 y la herramienta para interrogarlo. Se usa Apache dentro de un contenedor.

```bash
# Peticiones con curl (A3.1)
curl -i http://localhost:8080/                   # cabeceras y cuerpo
curl -I http://localhost:8080/                   # solo cabeceras
curl -i -X OPTIONS http://localhost:8080/        # métodos que admite el servidor
curl -s -o /dev/null -w '%{http_code}\n' -X POST http://localhost:8080/   # solo el código de estado
curl -s -c jar.txt -o /dev/null http://localhost:8080/                    # guarda las cookies en jar.txt
curl -sv -b jar.txt -o /dev/null http://localhost:8080/ 2>&1 | grep -i '^> cookie'   # comprueba que la cookie se reenvía
curl -kI https://localhost:8443/                 # HTTPS con certificado autofirmado (-k no lo valida)
curl -skG https://localhost:8443/ --data-urlencode "q=<script>alert(1)</script>" -o /dev/null -w 'xss %{http_code}\n'   # prueba de una regla del WAF
curl -s -c - -X POST http://127.0.0.1:8081/vulnerabilities/weak_id/ --cookie "security=medium; PHPSESSID=<tu PHPSESSID>" | grep dvwaSession   # cookie de sesión que emite la aplicación

# Estado y módulos de Apache (A3.1)
docker exec web apache2ctl -S                    # sitios virtuales cargados
docker exec web apache2ctl -M | head -20         # módulos activos
docker exec web ls /etc/apache2/conf-enabled /etc/apache2/sites-enabled   # configuración activada
docker exec web apache2ctl configtest            # valida la sintaxis antes de recargar

# Activar y desactivar piezas en el Dockerfile (A3.2)
a2enmod ssl headers                              # activa módulos
a2dismod -f autoindex                            # desactiva el listado de directorios
a2dissite 000-default                            # desactiva el sitio por defecto
a2enconf seguridad && a2ensite sitio             # activa la configuración y el sitio propios

# Comprobar el endurecimiento (A3.4)
curl -skI https://localhost:8443/ | grep -i '^server'    # el servidor no debe revelar versión
for m in GET POST PUT DELETE TRACE OPTIONS; do curl -sk -o /dev/null -w "$m %{http_code}\n" -X $m https://localhost:8443/; done   # solo los métodos permitidos
docker exec web ls -ld /var/www/html /var/www/html/index.html   # permisos del contenido
ab -n 200 -c 10 https://localhost:8443/ 2>&1 | grep -i 'Complete requests\|Failed requests\|Non-2xx'   # carga para activar mod_evasive
(printf 'GET / HTTP/1.1\r\nHost: localhost\r\n'; sleep 12) | nc localhost 8080 | head -3   # cliente lento: debe cortarse por tiempo

# Registro del WAF, ModSecurity (A3.3)
docker exec web sh -c "grep -o '\[id \"[0-9]*\"\] \[msg \"[^\"]*\"\]' /var/log/apache2/error.log | sort | uniq -c | sort -rn | head"   # reglas que más saltan
docker exec web sh -c "sed -i 's/^SecRuleEngine On/SecRuleEngine DetectionOnly/' /etc/modsecurity/modsecurity.conf && apache2ctl graceful"   # de bloquear a solo detectar
```

## TLS y certificados (openssl)

Certificado autofirmado para el laboratorio. No sirve para producción: allí firma una autoridad de certificación.

```bash
# Certificado autofirmado para Apache (A3.2)
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -subj "/C=ES/O=PPS/CN=localhost" \
  -keyout apache.key -out apache.crt              # clave sin cifrar y certificado válido un año
chmod 600 /etc/ssl/pps/apache.key                 # la clave privada solo la lee su propietario
```

## Hashes y contraseñas

Por qué un hash rápido no protege una contraseña y cómo se comprueba (A3.11).

```bash
openssl passwd -1 -salt abcdefgh estrella7 > debil.txt   # hash MD5 al estilo crypt de una contraseña de la lista
sudo apt install -y john                          # John the Ripper (el de Ubuntu no trae raw-md5)
john --format=md5crypt --wordlist=lista.txt debil.txt   # rompe el hash con un diccionario
john --show debil.txt                             # muestra lo que ha conseguido romper
python3 -c "import bcrypt; print(bcrypt.hashpw(b'estrella7', bcrypt.gensalt()))"   # el mismo cálculo con bcrypt, con sal y lento
```

## Aplicaciones móviles (adb, apktool, jadx, apksigner)

Se instala la aplicación en el móvil de laboratorio con `adb`, se desmonta con `apktool` (Smali editable) y `jadx` (Java legible), y se firma de nuevo con `apksigner` (A4.1 a A4.6).

```bash
# Herramientas y conexión con el dispositivo (A4.1)
sudo apt update && sudo apt install -y adb apktool apksigner sqlite3 unzip
~/jadx/bin/jadx --version                        # comprueba que jadx funciona
adb connect <IP de movil01>:5555                 # conecta con el dispositivo por red
adb devices                                      # lista los dispositivos visibles
adb install diva-beta.apk                        # instala la APK
adb uninstall jakhar.aseem.diva                  # la desinstala por su nombre de paquete

# Desmontar una APK
apktool d diva-beta.apk -o ~/laboratorio-movil/diva/smali   # a Smali, con manifiesto y recursos
~/jadx/bin/jadx -d ~/laboratorio-movil/diva/java diva-beta.apk   # a Java aproximado, para leer
unzip -o ~/laboratorio-movil/apk/APK_1/APKs/diva-beta.apk 'lib/x86/*' -d /tmp/diva-lib   # saca las bibliotecas nativas
strings /tmp/diva-lib/lib/x86/libdivajni.so      # cadenas legibles del binario

# Inspeccionar el manifiesto y la firma (A4.2)
grep 'uses-permission' ~/laboratorio-movil/diva/smali/AndroidManifest.xml   # permisos que pide
grep -B2 'exported="true"' ~/laboratorio-movil/diva/smali/AndroidManifest.xml   # componentes abiertos a otras apps
grep -B4 'intent-filter' ~/laboratorio-movil/diva/smali/AndroidManifest.xml     # cómo se les puede llamar
grep -o 'allowBackup="[a-z]*"' ~/laboratorio-movil/diva/smali/AndroidManifest.xml   # si permite copias de seguridad
apksigner verify --verbose --print-certs diva-beta.apk   # quién ha firmado la APK

# Análisis estático y modificación (A4.3)
apktool b diva/smali -o diva-sin-firmar.apk      # reempaqueta
keytool -genkeypair -keystore clave-lab.jks -alias lab -keyalg RSA -keysize 2048 -validity 365   # clave de firma del laboratorio
apksigner sign --ks clave-lab.jks --out diva-mod.apk diva-sin-firmar.apk   # firma la APK modificada
apksigner verify --print-certs diva-mod.apk      # comprueba la firma nueva
adb shell am start -a jakhar.aseem.diva.action.VIEW_CREDS   # lanza una actividad expuesta

# Almacenamiento inseguro en el dispositivo (A4.4)
adb shell ls /data/data/jakhar.aseem.diva/shared_prefs/   # preferencias de la app
adb shell cat /data/data/jakhar.aseem.diva/shared_prefs/jakhar.aseem.diva_preferences.xml   # su contenido
adb pull /data/data/jakhar.aseem.diva/databases/ids2 /tmp/ids2   # copia una base de datos al equipo
sqlite3 /tmp/ids2 "select * from myuser;"        # la consulta en claro
adb shell ls -a /sdcard/                         # ficheros en almacenamiento externo, incluidos los ocultos
adb logcat -d | grep -i diva                     # secretos que la app escribe en el log

# Análisis automático (A4.6, PIVAA)
docker run --rm -p 8000:8000 -d --name mobsf opensecurity/mobile-security-framework-mobsf   # MobSF en el puerto 8000
docker run -it --rm drozerdocker/drozer:2.4.4 console connect --server <IP de movil01>  # consola de drozer (la imagen ya arranca drozer) conectada al agente del móvil
```

## Seguridad de contenedores (docker-bench, AppArmor, ldd)

Auditoría del anfitrión Docker, confinamiento de un contenedor con un perfil propio y lectura de las bibliotecas que carga un proceso (A2.4 y A2.5).

```bash
# Auditoría y escaneo (A2.4)
docker run --rm aquasec/trivy image --scanners vuln --severity CRITICAL $IMG | tee trivy-log4shell.txt   # vulnerabilidades críticas de la imagen
cd ~ && git clone https://github.com/docker/docker-bench-security.git
cd docker-bench-security && sudo sh docker-bench-security.sh | tee ~/pps-entregas/ut2/a24/docker-bench.txt   # auditoría de la configuración de Docker

# AppArmor
sudo apparmor_parser -r pps-confinado            # carga o recarga el perfil
sudo aa-status | grep pps-confinado              # comprueba que está cargado
docker run -d --name confinado --security-opt apparmor=pps-confinado ubuntu:24.04 sleep 300   # contenedor con el perfil
docker inspect -f '{{.AppArmorProfile}}' confinado   # perfil aplicado

# Bibliotecas que carga un proceso (A2.5)
ldd "$(command -v sshd || echo /usr/sbin/sshd)"  # dependencias dinámicas de sshd
ldconfig -p | grep -i systemd                    # dónde está libsystemd
```

## Maven

```bash
mvn -B clean verify                        # construir desde cero, probar y empaquetar (lo que ejecuta Jenkins)
mvn -B test surefire-report:report         # pruebas y informe HTML en target/reports/surefire.html
mvn -B clean package                       # compilar, probar y dejar el jar en target/
mvn -q verify && ls Dockerfile             # verificar en silencio y comprobar que existe el Dockerfile
cat target/surefire-reports/es.pps.AppTest.txt   # informe de pruebas en texto
java -jar target/pps-app.jar 8083          # ejecutar el jar en el puerto 8083
```

## Jenkins

```bash
mkdir -p ~/jenkins-lab && cd ~/jenkins-lab
docker build -t pps-jenkins:1 .            # imagen de Jenkins con Maven añadido
docker run -d --name jenkins --restart unless-stopped \
  -p 8090:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home pps-jenkins:1   # controlador con su volumen JENKINS_HOME
docker exec jenkins mvn -v                 # comprobar que Maven está dentro
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword   # contraseña del primer arranque
docker rm -f jenkins                       # borrar el contenedor; el volumen conserva trabajos y credenciales
git add Jenkinsfile && git commit -m "A5.5 Jenkinsfile" && git push   # el pipeline viaja con el código
docker volume create jenkins_restaurado    # volumen nuevo para probar la restauración de una copia
```

## Terraform

```bash
terraform version                          # comprobar la instalación
terraform init                             # descargar el proveedor y preparar el directorio
terraform fmt && terraform validate        # formatear y validar la sintaxis
terraform plan -out=plan.bin               # calcular los cambios y guardarlos en un plan
terraform apply plan.bin                   # aplicar exactamente ese plan
terraform apply                            # planificar y aplicar tras confirmación
terraform show | grep ipv4_address         # ver en el estado la IP de la máquina creada
terraform output ip_destino01              # mostrar una salida declarada
terraform output -raw ip_destino01         # la misma sin comillas, para usarla en scripts
terraform output -raw clave_acceso; echo   # una salida marcada como sensible (sigue en claro en el estado)
grep -n '"result"' terraform.tfstate       # el secreto está en texto claro en el fichero de estado
```

## Ansible

```bash
ansible --version                          # comprobar la instalación
ansible web -m ansible.builtin.ping        # conectividad SSH y Python con el grupo web
ansible-playbook site.yml --syntax-check   # validar la sintaxis del playbook
ansible-playbook site.yml -K --check       # simular sin cambiar nada (-K pide la contraseña de sudo)
ansible-playbook site.yml -K --check --diff   # simular y mostrar las diferencias de los ficheros
ansible-playbook site.yml -K               # aplicar; una segunda vez no debe cambiar nada (idempotencia)
ansible-playbook site.yml -K -e 'mensaje="Ansible sigue rocks"'   # sobrescribir una variable
ansible-playbook -i inventario.ini despliegue-k3s.yml -e build=N   # desplegar en el clúster con inventario propio
```

## Kubernetes y K3s (kubectl, K9s)

```bash
# Instalar K3s (un nodo)
curl -sfL https://get.k3s.io | K3S_KUBECONFIG_MODE="644" sh -s - \
  --node-ip 192.168.56.31 --flannel-iface enp0s8
# Primer servidor de un clúster con etcd embebido
curl -sfL https://get.k3s.io | K3S_TOKEN=secreto-del-laboratorio K3S_KUBECONFIG_MODE="644" sh -s - server \
  --cluster-init --node-ip 192.168.56.31 --flannel-iface enp0s8 --tls-san 192.168.56.31
# Servidores que se unen al clúster
curl -sfL https://get.k3s.io | K3S_TOKEN=secreto-del-laboratorio K3S_KUBECONFIG_MODE="644" sh -s - server \
  --server https://192.168.56.31:6443 --node-ip 192.168.56.32 --flannel-iface enp0s8
/usr/local/bin/k3s-uninstall.sh            # desinstalar K3s y borrar sus datos

# Estado del clúster
kubectl get nodes -o wide                  # nodos, versión e IP
kubectl get nodes -w                       # seguir los nodos en vivo (Ctrl+C para salir)
kubectl get pods -A                        # pods de todos los espacios de nombres
kubectl -n kube-system get svc traefik     # el servicio de Traefik, el ingress de K3s

# Desplegar y escalar
kubectl apply -f nginx.yaml                # crear o actualizar lo que describe el manifiesto
kubectl get deploy,pods,svc -o wide        # despliegue, pods y servicio a la vez
kubectl get pods -w                        # seguir los pods en vivo
kubectl delete pod <nombre de un pod nginx>   # matar un pod: el despliegue lo recrea
kubectl scale deploy nginx --replicas=3    # cambiar el número de réplicas
kubectl apply -f k8s/pps-app.yaml          # desplegar pps-app
curl -s -H "Host: pps.lab" http://192.168.56.31/salud   # probar la ruta del ingress por nombre
ssh vagrant@192.168.56.31 'sudo k3s kubectl get pods,svc -o wide'   # kubectl en un nodo por SSH

# K9s
curl -sL https://github.com/derailed/k9s/releases/latest/download/k9s_Linux_amd64.tar.gz | sudo tar xz -C /usr/local/bin k9s   # instalar
export TERM=xterm-256color                 # colores correctos en la terminal
k9s                                        # interfaz de texto para navegar el clúster
```

## Prometheus y Grafana

```bash
sudo apt update && sudo apt install -y prometheus-node-exporter   # exporter de la máquina vigilada
systemctl is-active prometheus-node-exporter                      # debe decir active
curl -s http://localhost:9100/metrics | grep -m3 node_cpu_seconds_total   # ver métricas en local
curl -s http://192.168.56.20:9100/metrics | head -5               # ver las de otra máquina
docker compose up -d                       # levantar Prometheus y Grafana
docker compose ps                          # comprobar que los servicios están running
sudo systemctl stop prometheus-node-exporter    # simular un fallo: el destino pasa a DOWN
sudo systemctl start prometheus-node-exporter   # recuperarlo
```

Consultas de PromQL (en la pestaña Graph de `http://localhost:9090`; Grafana en el puerto 3000):

```text
up                                                       # 1 si el destino se recogió bien, 0 si falló
rate(node_cpu_seconds_total{mode="idle"}[1m])            # fracción de CPU ociosa en el último minuto
sum by (code) (rate(traefik_service_requests_total[1m])) # peticiones por segundo por código HTTP
container_memory_usage_bytes{name="nodeapp"}             # memoria de un contenedor
```
