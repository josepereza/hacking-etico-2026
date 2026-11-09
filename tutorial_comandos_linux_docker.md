# Tutorial de comandos Linux para hacking ético con Docker

Guía de referencia para el laboratorio de hacking ético con Docker y la administración de VPS. Se conservan las 84 secciones del tutorial original, sus explicaciones, sintaxis, flags y ejemplos.

## Índice por secciones

- [1. Cómo leer un comando Linux](#seccion-01)

- [2. SSH](#seccion-02)

- [3. Túnel SSH local -L](#seccion-03)

- [4. Túnel SSH reverso -R](#seccion-04)

- [5. ss — conexiones y puertos](#seccion-05)

- [6. Nmap](#seccion-06)

- [7. Docker](#seccion-07)

- [8. Docker Compose](#seccion-08)

- [9. Curl](#seccion-09)

- [10. curl -i](#seccion-10)

- [11. curl -I](#seccion-11)

- [12. curl -s](#seccion-12)

- [13. curl -o](#seccion-13)

- [14. curl -w](#seccion-14)

- [15. Curl POST](#seccion-15)

- [16. Curl con Authorization](#seccion-16)

- [17. Métodos HTTP](#seccion-17)

- [18. Códigos HTTP importantes](#seccion-18)

- [19. Grep](#seccion-19)

- [20. grep -i](#seccion-20)

- [21. grep -n](#seccion-21)

- [22. grep -r](#seccion-22)

- [23. grep -v](#seccion-23)

- [24. grep -o](#seccion-24)

- [25. grep -E](#seccion-25)

- [26. grep -oE](#seccion-26)

- [27. Expresiones regulares — Regex](#seccion-27)

- [28. Regex útiles](#seccion-28)

- [29. Encontrar rutas JavaScript](#seccion-29)

- [30. Buscar rutas API](#seccion-30)

- [31. sort](#seccion-31)

- [32. head](#seccion-32)

- [33. tail](#seccion-33)

- [34. jq](#seccion-34)

- [35. jq -r](#seccion-35)

- [36. Variables Bash](#seccion-36)

- [37. printf](#seccion-37)

- [38. Base64](#seccion-38)

- [39. Netcat nc](#seccion-39)

- [40. ip](#seccion-40)

- [41. hostname](#seccion-41)

- [42. ping](#seccion-42)

- [43. DNS con dig](#seccion-43)

- [44. whoami](#seccion-44)

- [45. id](#seccion-45)

- [46. Usuarios](#seccion-46)

- [47. Grupos](#seccion-47)

- [48. Privilegios con sudo](#seccion-48)

- [49. Propietarios](#seccion-49)

- [50. Permisos Linux](#seccion-50)

- [51. UFW](#seccion-51)

- [52. Procesos con ps](#seccion-52)

- [53. pgrep](#seccion-53)

- [54. kill](#seccion-54)

- [55. systemctl](#seccion-55)

- [56. journalctl](#seccion-56)

- [57. Navegación básica](#seccion-57)

- [58. Archivos](#seccion-58)

- [59. find](#seccion-59)

- [60. which](#seccion-60)

- [61. whereis](#seccion-61)

- [62. file](#seccion-62)

- [63. strings](#seccion-63)

- [64. wc](#seccion-64)

- [65. Pipes |](#seccion-65)

- [66. Redirecciones](#seccion-66)

- [67. /dev/null](#seccion-67)

- [68. &&](#seccion-68)

- [69. ;](#seccion-69)

- [70. ||](#seccion-70)

- [71. tee](#seccion-71)

- [72. env](#seccion-72)

- [73. export](#seccion-73)

- [74. Información del sistema](#seccion-74)

- [75. Recursos](#seccion-75)

- [76. Puertos: flujo de diagnóstico recomendado](#seccion-76)

- [77. Ejemplo completo con Juice Shop](#seccion-77)

- [78. Ejemplo completo con túnel SSH](#seccion-78)

- [79. Combinaciones especialmente útiles](#seccion-79)

- [80. Los flags que más merece la pena memorizar](#seccion-80)

- [81. Cómo consultar ayuda](#seccion-81)

- [82. Tabla mental para diagnosticar problemas](#seccion-82)

- [83. Chuleta rápida](#seccion-83)

- [84. Lo que conviene dominar primero](#seccion-84)


## Índice alfabético de comandos

- [`adduser`](#seccion-46)

- [`apt`](#seccion-48)

- [`base64`](#seccion-38)

- [`cat`](#seccion-58)

- [`cd`](#seccion-57)

- [`chmod`](#seccion-50)

- [`chown`](#seccion-49)

- [`cp`](#seccion-58)

- [`curl`](#seccion-09)

- [`df`](#seccion-75)

- [`dig`](#seccion-43)

- [`docker`](#seccion-07)

- [`docker compose`](#seccion-08)

- [`docker compose down`](#seccion-08)

- [`docker compose logs`](#seccion-08)

- [`docker compose ps`](#seccion-08)

- [`docker compose up`](#seccion-08)

- [`docker exec`](#seccion-07)

- [`docker images`](#seccion-07)

- [`docker logs`](#seccion-07)

- [`docker ps`](#seccion-07)

- [`docker restart`](#seccion-07)

- [`docker rm`](#seccion-07)

- [`docker rmi`](#seccion-07)

- [`docker start`](#seccion-07)

- [`docker stop`](#seccion-07)

- [`du`](#seccion-75)

- [`echo`](#seccion-36)

- [`env`](#seccion-72)

- [`export`](#seccion-73)

- [`file`](#seccion-62)

- [`find`](#seccion-59)

- [`free`](#seccion-75)

- [`grep`](#seccion-19)

- [`groups`](#seccion-47)

- [`head`](#seccion-32)

- [`hostname`](#seccion-41)

- [`htop`](#seccion-75)

- [`id`](#seccion-45)

- [`ip`](#seccion-40)

- [`journalctl`](#seccion-56)

- [`jq`](#seccion-34)

- [`kill`](#seccion-54)

- [`less`](#seccion-58)

- [`ls`](#seccion-57)

- [`man`](#seccion-81)

- [`mv`](#seccion-58)

- [`nc / netcat`](#seccion-39)

- [`nmap`](#seccion-06)

- [`passwd`](#seccion-46)

- [`pgrep`](#seccion-53)

- [`ping`](#seccion-42)

- [`printf`](#seccion-37)

- [`ps`](#seccion-52)

- [`pwd`](#seccion-57)

- [`regex`](#seccion-27)

- [`rm`](#seccion-58)

- [`sort`](#seccion-31)

- [`ss`](#seccion-05)

- [`ssh`](#seccion-02)

- [`ssh -L (local)`](#seccion-03)

- [`ssh -R (reverso)`](#seccion-04)

- [`strings`](#seccion-63)

- [`su`](#seccion-46)

- [`sudo`](#seccion-48)

- [`systemctl`](#seccion-55)

- [`tail`](#seccion-33)

- [`tee`](#seccion-71)

- [`top`](#seccion-75)

- [`touch`](#seccion-58)

- [`ufw`](#seccion-51)

- [`uname`](#seccion-74)

- [`usermod`](#seccion-47)

- [`wc`](#seccion-64)

- [`whereis`](#seccion-61)

- [`which`](#seccion-60)

- [`whoami`](#seccion-44)


---


Esta guía reúne los comandos más utilizados durante un laboratorio de hacking ético con Docker, redes y administración Linux.

Está pensada para trabajar únicamente sobre sistemas propios, laboratorios autorizados y entornos como OWASP Juice Shop, DVWA y contenedores Docker.

---

<a id="seccion-01"></a>

## 1. Cómo leer un comando Linux

La estructura habitual es:

```bash
comando [opciones] [argumentos]
```

Ejemplo:

```bash
curl -s http://127.0.0.1:3000
```

Aquí:

```text
curl
│
└── comando

-s
│
└── opción o flag

http://127.0.0.1:3000
│
└── argumento
```

Las opciones también se llaman **flags**.

Normalmente comienzan por:

```bash
-
```

o:

```bash
--
```

Ejemplo:

```bash
curl -I
```

y:

```bash
curl --include
```

---

<a id="seccion-02"></a>

## 2. SSH

SSH permite conectarse de forma segura a otro equipo.

Sintaxis básica:

```bash
ssh usuario@servidor
```

Ejemplo:

```bash
ssh jose@192.168.1.50
```

También puedes indicar un puerto diferente:

```bash
ssh -p 2222 jose@192.168.1.50
```

### Flags SSH habituales

| Flag | Significado |

|---|---|

| `-p` | puerto SSH |

| `-i` | archivo de clave privada |

| `-L` | túnel local |

| `-R` | túnel remoto/reverso |

| `-N` | no ejecutar una shell remota |

| `-v` | mostrar información de depuración |

---

<a id="seccion-03"></a>

## 3. Túnel SSH local `-L`

Un túnel local permite acceder desde tu ordenador a un servicio que solamente está disponible desde el servidor remoto.

Ejemplo:

```bash
ssh -L 8080:127.0.0.1:8080 usuario@IP_VPS
```

La estructura es:

```text
-L PUERTO_LOCAL:DESTINO:PUERTO_DESTINO
```

En nuestro ejemplo:

```text
8080
│
└── puerto que se abrirá en tu PC

127.0.0.1
│
└── destino visto desde el VPS

8080
│
└── puerto del servicio en el VPS
```

Si DVWA está funcionando en:

```text
127.0.0.1:8080
```

dentro del VPS, puedes abrir en tu ordenador:

```text
http://127.0.0.1:8080
```

El recorrido sería:

```text
Tu PC
127.0.0.1:8080
       │
       │ SSH cifrado
       ▼
VPS
127.0.0.1:8080
       │
       ▼
DVWA
```

No necesitas abrir públicamente el puerto `8080` del VPS.

Una forma especialmente útil es:

```bash
ssh -N -L 8080:127.0.0.1:8080 usuario@IP_VPS
```

`-N` significa:

```text
No abrir una terminal remota.
Solo mantener el túnel SSH.
```

Para cerrar el túnel:

```text
Ctrl + C
```

---

<a id="seccion-04"></a>

## 4. Túnel SSH reverso `-R`

El túnel reverso funciona en dirección contraria.

Sintaxis:

```bash
ssh -R PUERTO_REMOTO:DESTINO:PUERTO_LOCAL usuario@servidor
```

Ejemplo en un laboratorio controlado:

```bash
ssh -R 9000:127.0.0.1:3000 usuario@servidor
```

Significa:

```text
servidor:9000
       │
       │ túnel SSH
       ▼
tu-PC:3000
```

Puede utilizarse legítimamente para exponer temporalmente un servicio de desarrollo a un servidor remoto sin publicar directamente el puerto.

Con `-N`:

```bash
ssh -N -R 9000:127.0.0.1:3000 usuario@servidor
```

---

<a id="seccion-05"></a>

## 5. `ss` — conexiones y puertos

`ss` permite ver conexiones de red y puertos abiertos.

Uno de los comandos más útiles:

```bash
ss -tulpn
```

Flags:

```text
-t    conexiones TCP
-u    conexiones UDP
-l    solamente puertos escuchando
-p    proceso que utiliza el puerto
-n    no resolver nombres; mostrar IP y puerto
```

Ejemplo:

```bash
sudo ss -tulpn
```

Podrías obtener:

```text
LISTEN 0 511 0.0.0.0:22
LISTEN 0 511 127.0.0.1:3000
LISTEN 0 511 127.0.0.1:8080
```

Para buscar solamente el puerto `3000`:

```bash
ss -tulpn | grep 3000
```

---

<a id="seccion-06"></a>

## 6. Nmap

Nmap sirve para descubrir hosts, puertos y servicios.

Uso básico:

```bash
nmap IP
```

Ejemplo:

```bash
nmap 127.0.0.1
```

En un laboratorio Docker:

```bash
nmap 172.18.0.2
```

### Flags Nmap más útiles

| Flag | Significado |

|---|---|

| `-p` | seleccionar puerto |

| `-p-` | todos los puertos TCP |

| `-sV` | identificar versiones |

| `-sC` | scripts básicos de Nmap |

| `-Pn` | asumir que el host está activo |

| `-O` | intentar identificar sistema operativo |

| `-v` | salida más detallada |

| `-oN` | guardar resultado en texto |

Buscar un puerto:

```bash
nmap -p 3000 127.0.0.1
```

Varios puertos:

```bash
nmap -p 22,80,443,3000 127.0.0.1
```

Rango:

```bash
nmap -p 1-1000 127.0.0.1
```

Todos:

```bash
nmap -p- 127.0.0.1
```

Detectar versiones:

```bash
nmap -sV 127.0.0.1
```

Ejemplo:

```text
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH
3000/tcp open  http    Node.js Express
```

Una combinación habitual en laboratorio:

```bash
nmap -sV -sC -p 3000 127.0.0.1
```

---

<a id="seccion-07"></a>

## 7. Docker

Docker es una parte central de nuestro laboratorio.

Ver contenedores ejecutándose:

```bash
docker ps
```

Ver también contenedores detenidos:

```bash
docker ps -a
```

Ejemplo:

```text
CONTAINER ID   IMAGE                  PORTS
11275b017e8e   bkimminich/juice-shop 127.0.0.1:3000->3000/tcp
```

Esto:

```text
127.0.0.1:3000->3000/tcp
```

significa:

```text
VPS:3000
   │
   ▼
contenedor:3000
```

### Entrar dentro de un contenedor

```bash
docker exec -it nombre-contenedor bash
```

Ejemplo:

```bash
docker exec -it attacker bash
```

Flags:

```text
-i    modo interactivo
-t    crea una terminal
```

Juntas:

```bash
-it
```

Algunos contenedores solamente tienen `sh`:

```bash
docker exec -it juice-shop sh
```

### Logs

```bash
docker logs juice-shop
```

Seguir logs en tiempo real:

```bash
docker logs -f juice-shop
```

`-f`:

```text
follow
```

### Detener

```bash
docker stop juice-shop
```

Iniciar:

```bash
docker start juice-shop
```

Reiniciar:

```bash
docker restart juice-shop
```

Eliminar:

```bash
docker rm juice-shop
```

Eliminar imagen:

```bash
docker rmi imagen
```

Ver imágenes:

```bash
docker images
```

---

<a id="seccion-08"></a>

## 8. Docker Compose

Cuando tienes varios servicios:

```bash
docker compose up
```

En segundo plano:

```bash
docker compose up -d
```

`-d`:

```text
detached
```

El terminal queda libre.

Detener el entorno:

```bash
docker compose down
```

Ver servicios:

```bash
docker compose ps
```

Logs:

```bash
docker compose logs
```

Logs continuos:

```bash
docker compose logs -f
```

---

<a id="seccion-09"></a>

## 9. Curl

`curl` es probablemente uno de los comandos más importantes del curso.

Permite enviar peticiones HTTP directamente desde la terminal.

Petición básica:

```bash
curl http://127.0.0.1:3000
```

---

<a id="seccion-10"></a>

## 10. `curl -i`

```bash
curl -i http://127.0.0.1:3000
```

`-i` incluye las cabeceras HTTP.

Ejemplo:

```text
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234

<html>
...
```

---

<a id="seccion-11"></a>

## 11. `curl -I`

Mayúscula:

```bash
curl -I http://127.0.0.1:3000
```

Solicita principalmente las cabeceras.

Resultado:

```text
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234
```

Muy útil para comprobar rápidamente un servidor.

---

<a id="seccion-12"></a>

## 12. `curl -s`

```bash
curl -s http://127.0.0.1:3000
```

`-s`:

```text
silent
```

Elimina información adicional de progreso.

Es especialmente útil cuando combinamos `curl` con otros comandos:

```bash
curl -s http://127.0.0.1:3000 | grep script
```

---

<a id="seccion-13"></a>

## 13. `curl -o`

Guardar respuesta:

```bash
curl -o pagina.html http://127.0.0.1:3000
```

`-o` significa:

```text
output
```

Ahora puedes:

```bash
cat pagina.html
```

---

<a id="seccion-14"></a>

## 14. `curl -w`

Permite imprimir información adicional.

Ejemplo:

```bash
curl -s -o /dev/null -w "%{http_code}\n" http://127.0.0.1:3000
```

Resultado:

```text
200
```

Muy útil para comprobar códigos HTTP.

---

<a id="seccion-15"></a>

## 15. Curl POST

Ejemplo genérico contra una API de laboratorio:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-d '{"name":"test"}' \
http://127.0.0.1:3000/api/test
```

Aquí:

```text
-X POST
```

selecciona el método HTTP.

```text
-H
```

añade una cabecera.

```text
-d
```

envía datos.

---

<a id="seccion-16"></a>

## 16. Curl con Authorization

Para una API propia o laboratorio:

```bash
curl -H "Authorization: Bearer TOKEN" \
http://127.0.0.1:3000/api/profile
```

`-H` añade:

```text
Authorization: Bearer TOKEN
```

---

<a id="seccion-17"></a>

## 17. Métodos HTTP

Los principales que encontrarás son:

```text
GET
POST
PUT
PATCH
DELETE
```

Ejemplo:

```bash
curl -X GET http://127.0.0.1:3000/api/products
```

Normalmente `GET` es el método predeterminado, por lo que basta:

```bash
curl http://127.0.0.1:3000/api/products
```

---

<a id="seccion-18"></a>

## 18. Códigos HTTP importantes

```text
200    OK
201    creado correctamente
204    correcto, sin contenido

301    redirección permanente
302    redirección temporal

400    petición incorrecta
401    no autenticado
403    prohibido
404    recurso no encontrado

500    error interno del servidor
502    Bad Gateway
503    servicio no disponible
```

---

<a id="seccion-19"></a>

## 19. Grep

`grep` busca texto.

Ejemplo:

```bash
grep "admin" archivo.txt
```

Buscar dentro de la salida de otro comando:

```bash
docker ps | grep juice
```

---

<a id="seccion-20"></a>

## 20. `grep -i`

Ignorar mayúsculas y minúsculas:

```bash
grep -i "admin" archivo.txt
```

Encontrará:

```text
admin
Admin
ADMIN
```

---

<a id="seccion-21"></a>

## 21. `grep -n`

Mostrar número de línea:

```bash
grep -n "password" archivo.txt
```

Ejemplo:

```text
34:password
89:password
```

---

<a id="seccion-22"></a>

## 22. `grep -r`

Buscar recursivamente:

```bash
grep -r "localhost" .
```

`.` significa:

```text
directorio actual
```

---

<a id="seccion-23"></a>

## 23. `grep -v`

Mostrar lo que NO coincide:

```bash
grep -v "INFO" log.txt
```

Muy útil para eliminar ruido.

---

<a id="seccion-24"></a>

## 24. `grep -o`

Mostrar únicamente la coincidencia.

Ejemplo:

```bash
echo 'src="main.js"' | grep -o 'main.js'
```

Resultado:

```text
main.js
```

---

<a id="seccion-25"></a>

## 25. `grep -E`

Activa expresiones regulares extendidas.

```bash
grep -E 'jpg|png|gif' archivo.txt
```

Equivale también a:

```bash
egrep
```

aunque hoy es preferible:

```bash
grep -E
```

---

<a id="seccion-26"></a>

## 26. `grep -oE`

Una combinación que utilizamos mucho:

```bash
grep -oE 'href="[^"]+"'
```

`-o`:

```text
mostrar únicamente coincidencia
```

`-E`:

```text
expresión regular extendida
```

Ejemplo:

```bash
curl -s http://127.0.0.1:3000 |
grep -oE 'src="[^"]+"'
```

Puede producir:

```text
src="runtime.js"
src="polyfills.js"
src="main.js"
```

---

<a id="seccion-27"></a>

## 27. Expresiones regulares — Regex

Una regex describe un patrón.

Ejemplo:

```regex
[0-9]+
```

Significa:

```text
[0-9]    cualquier número

+        una o más veces
```

Encontraría:

```text
1
123
5000
```

---

<a id="seccion-28"></a>

## 28. Regex útiles

Cualquier carácter:

```regex
.
```

Cero o más:

```regex
*
```

Uno o más:

```regex
+
```

Cero o uno:

```regex
?
```

Inicio de línea:

```regex
^
```

Final:

```regex
$
```

Números:

```regex
[0-9]
```

Letras:

```regex
[a-zA-Z]
```

Negación dentro de corchetes:

```regex
[^"]
```

significa:

```text
cualquier carácter excepto "
```

Por eso:

```regex
"[^"]+"
```

encuentra contenido entre comillas.

---

<a id="seccion-29"></a>

## 29. Encontrar rutas JavaScript

Ejemplo:

```bash
curl -s http://127.0.0.1:3000 |
grep -oE 'src="[^"]+\.js"'
```

Podría producir:

```text
src="runtime.js"
src="polyfills.js"
src="main.js"
```

---

<a id="seccion-30"></a>

## 30. Buscar rutas API

En una aplicación propia de laboratorio:

```bash
grep -oE '/api/[A-Za-z0-9/_-]+' main.js
```

Después:

```bash
grep -oE '/api/[A-Za-z0-9/_-]+' main.js | sort -u
```

---

<a id="seccion-31"></a>

## 31. `sort`

Ordenar:

```bash
sort archivo.txt
```

Ordenar y eliminar duplicados:

```bash
sort -u archivo.txt
```

`-u`:

```text
unique
```

Ejemplo:

```bash
printf "banana\nmanzana\nbanana\n" | sort -u
```

Resultado:

```text
banana
manzana
```

---

<a id="seccion-32"></a>

## 32. `head`

Mostrar las primeras líneas:

```bash
head archivo.txt
```

Por defecto muestra 10.

Mostrar 20:

```bash
head -n 20 archivo.txt
```

---

<a id="seccion-33"></a>

## 33. `tail`

Mostrar las últimas líneas:

```bash
tail archivo.log
```

Seguir un log en tiempo real:

```bash
tail -f archivo.log
```

Muy útil para:

```text
Nginx
Node.js
servicios Linux
logs de seguridad
```

Por ejemplo:

```bash
sudo tail -f /var/log/nginx/access.log
```

---

<a id="seccion-34"></a>

## 34. `jq`

`jq` procesa JSON.

Ejemplo:

```bash
echo '{"name":"Jose","age":30}' | jq
```

Salida formateada:

```json
{
  "name": "Jose",
  "age": 30
}
```

Seleccionar un campo:

```bash
echo '{"name":"Jose"}' | jq '.name'
```

Resultado:

```text
"Jose"
```

---

<a id="seccion-35"></a>

## 35. `jq -r`

```bash
jq -r '.name'
```

`-r`:

```text
raw
```

Elimina las comillas.

Sin `-r`:

```text
"Jose"
```

Con `-r`:

```text
Jose
```

Muy útil para variables:

```bash
TOKEN=$(cat respuesta.json | jq -r '.token')
```

Después:

```bash
echo "$TOKEN"
```

---

<a id="seccion-36"></a>

## 36. Variables Bash

Crear una variable:

```bash
NOMBRE="Jose"
```

Mostrar:

```bash
echo "$NOMBRE"
```

Guardar la salida de un comando:

```bash
IP=$(hostname -I)
```

Mostrar:

```bash
echo "$IP"
```

---

<a id="seccion-37"></a>

## 37. `printf`

`printf` imprime texto con mucho más control que `echo`.

Ejemplo:

```bash
printf "Hola\n"
```

`\n` significa:

```text
salto de línea
```

Ejemplo:

```bash
printf "Usuario: %s\n" "jose"
```

Resultado:

```text
Usuario: jose
```

---

<a id="seccion-38"></a>

## 38. Base64

Codificar:

```bash
printf 'hola' | base64
```

Resultado parecido a:

```text
aG9sYQ==
```

Decodificar:

```bash
printf 'aG9sYQ==' | base64 -d
```

Resultado:

```text
hola
```

`-d`:

```text
decode
```

Esto resulta útil para comprender formatos como JWT, donde algunas partes usan codificación Base64URL.

Codificación no significa cifrado.

---

<a id="seccion-39"></a>

## 39. Netcat `nc`

Netcat sirve para comprobar conexiones TCP/UDP y enviar datos entre servicios en un laboratorio.

Comprobar un puerto:

```bash
nc -vz 127.0.0.1 3000
```

Flags:

```text
-v    verbose
-z    comprobar puerto sin enviar datos
```

Resultado:

```text
Connection to 127.0.0.1 3000 port [tcp/*] succeeded!
```

Muy útil para comprobar:

```bash
nc -vz servidor 22
nc -vz servidor 80
nc -vz servidor 443
```

Escuchar en un puerto dentro de un entorno controlado:

```bash
nc -l 9000
```

`-l`:

```text
listen
```

En otra terminal:

```bash
nc 127.0.0.1 9000
```

Ahora puedes escribir texto entre las dos terminales.

---

<a id="seccion-40"></a>

## 40. `ip`

Mostrar interfaces:

```bash
ip addr
```

Abreviado:

```bash
ip a
```

Mostrar rutas:

```bash
ip route
```

o:

```bash
ip r
```

Ejemplo:

```text
default via 192.168.1.1 dev eth0
```

---

<a id="seccion-41"></a>

## 41. `hostname`

Nombre del equipo:

```bash
hostname
```

Mostrar direcciones IP:

```bash
hostname -I
```

---

<a id="seccion-42"></a>

## 42. `ping`

Comprobar conectividad:

```bash
ping 8.8.8.8
```

Enviar solamente cuatro paquetes:

```bash
ping -c 4 8.8.8.8
```

`-c`:

```text
count
```

---

<a id="seccion-43"></a>

## 43. DNS con `dig`

Consultar DNS:

```bash
dig example.com
```

Mostrar solamente la respuesta:

```bash
dig +short example.com
```

Ejemplo:

```text
93.184.216.34
```

Consultar un registro específico:

```bash
dig A example.com
```

```bash
dig MX example.com
```

```bash
dig TXT example.com
```

---

<a id="seccion-44"></a>

## 44. `whoami`

Muestra el usuario actual:

```bash
whoami
```

Ejemplo:

```text
jose
```

---

<a id="seccion-45"></a>

## 45. `id`

Información del usuario:

```bash
id
```

Resultado:

```text
uid=1000(jose) gid=1000(jose) groups=1000(jose),27(sudo)
```

Esto permite ver:

```text
UID
grupo principal
grupos adicionales
```

---

<a id="seccion-46"></a>

## 46. Usuarios

Crear usuario:

```bash
sudo adduser laboratorio
```

Cambiar contraseña:

```bash
sudo passwd laboratorio
```

Cambiar de usuario:

```bash
su - laboratorio
```

---

<a id="seccion-47"></a>

## 47. Grupos

Ver grupos:

```bash
groups
```

Ver grupos de otro usuario:

```bash
groups jose
```

Añadir usuario a un grupo:

```bash
sudo usermod -aG docker jose
```

Aquí:

```text
-a    append, añadir sin eliminar otros grupos

-G    grupos suplementarios
```

Muy importante:

No utilices solamente:

```bash
usermod -G docker jose
```

porque podrías sustituir sus grupos actuales.

---

<a id="seccion-48"></a>

## 48. Privilegios con sudo

Ejecutar como administrador:

```bash
sudo comando
```

Ejemplo:

```bash
sudo apt update
```

Abrir shell root:

```bash
sudo -i
```

Ver qué puede ejecutar el usuario con sudo:

```bash
sudo -l
```

---

<a id="seccion-49"></a>

## 49. Propietarios

Ver:

```bash
ls -l
```

Ejemplo:

```text
-rw-r--r-- 1 jose jose 2048 archivo.txt
```

Cambiar propietario:

```bash
sudo chown jose archivo.txt
```

Propietario y grupo:

```bash
sudo chown jose:jose archivo.txt
```

Recursivo:

```bash
sudo chown -R jose:jose directorio/
```

`-R`:

```text
recursive
```

---

<a id="seccion-50"></a>

## 50. Permisos Linux

Ejemplo:

```text
-rwxr-xr--
```

Se divide:

```text
rwx    propietario
r-x    grupo
r--    otros
```

Donde:

```text
r    read
w    write
x    execute
```

Valores:

```text
r = 4
w = 2
x = 1
```

Por ejemplo:

```bash
chmod 755 script.sh
```

significa:

```text
7 = rwx
5 = r-x
5 = r-x
```

Para un archivo privado:

```bash
chmod 600 clave
```

Resultado:

```text
rw-------
```

---

<a id="seccion-51"></a>

## 51. UFW

UFW administra el firewall de Ubuntu.

Estado:

```bash
sudo ufw status
```

Más información:

```bash
sudo ufw status verbose
```

Antes de activar UFW en un VPS asegúrate de permitir SSH:

```bash
sudo ufw allow OpenSSH
```

Después:

```bash
sudo ufw enable
```

Permitir HTTP:

```bash
sudo ufw allow 80/tcp
```

HTTPS:

```bash
sudo ufw allow 443/tcp
```

Eliminar regla:

```bash
sudo ufw delete allow 3000/tcp
```

En un laboratorio con Docker es perfectamente razonable dejar aplicaciones como Juice Shop ligadas solamente a:

```text
127.0.0.1
```

y acceder a ellas mediante túneles SSH.

Eso evita exponerlas directamente a Internet.

---

<a id="seccion-52"></a>

## 52. Procesos con `ps`

Mostrar procesos:

```bash
ps aux
```

Buscar Node:

```bash
ps aux | grep node
```

Buscar Docker:

```bash
ps aux | grep docker
```

---

<a id="seccion-53"></a>

## 53. `pgrep`

Más limpio que:

```bash
ps aux | grep nginx
```

puedes utilizar:

```bash
pgrep nginx
```

Con información:

```bash
pgrep -a nginx
```

---

<a id="seccion-54"></a>

## 54. `kill`

Finalizar proceso:

```bash
kill PID
```

Ejemplo:

```bash
kill 1234
```

Si no responde:

```bash
kill -9 1234
```

`-9` envía `SIGKILL`.

Conviene utilizarlo solamente cuando una terminación normal no funciona.

---

<a id="seccion-55"></a>

## 55. `systemctl`

Gestionar servicios Linux.

Estado:

```bash
sudo systemctl status nginx
```

Iniciar:

```bash
sudo systemctl start nginx
```

Detener:

```bash
sudo systemctl stop nginx
```

Reiniciar:

```bash
sudo systemctl restart nginx
```

Recargar configuración:

```bash
sudo systemctl reload nginx
```

Activar al arrancar:

```bash
sudo systemctl enable nginx
```

---

<a id="seccion-56"></a>

## 56. `journalctl`

Consultar logs de systemd.

Por ejemplo:

```bash
sudo journalctl -u nginx
```

Últimos mensajes:

```bash
sudo journalctl -u nginx -n 50
```

Seguir en tiempo real:

```bash
sudo journalctl -u nginx -f
```

---

<a id="seccion-57"></a>

## 57. Navegación básica

Directorio actual:

```bash
pwd
```

Listar:

```bash
ls
```

Detalles:

```bash
ls -l
```

Incluyendo archivos ocultos:

```bash
ls -la
```

Entrar:

```bash
cd directorio
```

Subir un nivel:

```bash
cd ..
```

Ir a tu home:

```bash
cd ~
```

---

<a id="seccion-58"></a>

## 58. Archivos

Crear:

```bash
touch archivo.txt
```

Ver:

```bash
cat archivo.txt
```

Ver paginado:

```bash
less archivo.txt
```

Copiar:

```bash
cp origen destino
```

Mover:

```bash
mv origen destino
```

Eliminar:

```bash
rm archivo
```

Eliminar directorio:

```bash
rm -r directorio
```

Ten especial cuidado con:

```bash
rm -rf
```

`-r` significa recursivo.

`-f` significa forzar.

Un comando incorrecto ejecutado como root puede eliminar una gran cantidad de datos.

---

<a id="seccion-59"></a>

## 59. `find`

Buscar archivos.

Ejemplo:

```bash
find /var/www -name "*.js"
```

Buscar solamente archivos:

```bash
find . -type f
```

Directorios:

```bash
find . -type d
```

Buscar archivos `.log`:

```bash
find /var/log -type f -name "*.log"
```

---

<a id="seccion-60"></a>

## 60. `which`

Ver dónde está instalado un comando:

```bash
which curl
```

Ejemplo:

```text
/usr/bin/curl
```

---

<a id="seccion-61"></a>

## 61. `whereis`

Más información:

```bash
whereis nginx
```

Puede mostrar:

```text
nginx: /usr/sbin/nginx /etc/nginx /usr/share/nginx
```

---

<a id="seccion-62"></a>

## 62. `file`

Identificar un archivo:

```bash
file archivo
```

Ejemplo:

```bash
file programa
```

Salida posible:

```text
ELF 64-bit LSB executable
```

---

<a id="seccion-63"></a>

## 63. `strings`

Extraer cadenas legibles de un archivo:

```bash
strings archivo
```

Buscar después:

```bash
strings archivo | grep -i http
```

Es útil para análisis básico de binarios propios o archivos de laboratorio.

---

<a id="seccion-64"></a>

## 64. `wc`

Contar líneas:

```bash
wc -l archivo.txt
```

Palabras:

```bash
wc -w archivo.txt
```

Bytes:

```bash
wc -c archivo.txt
```

También:

```bash
grep ERROR log.txt | wc -l
```

para contar errores.

---

<a id="seccion-65"></a>

## 65. Pipes `|`

El pipe es una de las ideas más importantes de Linux.

```bash
comando1 | comando2
```

La salida del primero pasa al segundo.

Ejemplo:

```bash
docker ps | grep juice
```

Otro:

```bash
curl -s http://127.0.0.1:3000 |
grep -oE 'src="[^"]+\.js"' |
sort -u
```

El recorrido es:

```text
curl
  ↓
HTML
  ↓
grep
  ↓
archivos JavaScript
  ↓
sort -u
  ↓
resultado limpio
```

---

<a id="seccion-66"></a>

## 66. Redirecciones

Guardar salida:

```bash
comando > archivo.txt
```

Esto sobrescribe el archivo.

Añadir:

```bash
comando >> archivo.txt
```

Ejemplo:

```bash
nmap -sV 127.0.0.1 > scan.txt
```

---

<a id="seccion-67"></a>

## 67. `/dev/null`

Es como un agujero negro.

Todo lo enviado allí desaparece.

Ejemplo:

```bash
curl -s -o /dev/null http://127.0.0.1:3000
```

Muy útil combinado con:

```bash
curl -s -o /dev/null -w "%{http_code}\n" http://127.0.0.1:3000
```

---

<a id="seccion-68"></a>

## 68. `&&`

Ejecuta el siguiente comando solamente si el anterior funcionó.

```bash
sudo apt update && sudo apt upgrade
```

Si `apt update` falla, `apt upgrade` no se ejecutará.

---

<a id="seccion-69"></a>

## 69. `;`

Ejecuta el siguiente comando independientemente del resultado anterior:

```bash
comando1 ; comando2
```

---

<a id="seccion-70"></a>

## 70. `||`

Ejecuta el segundo comando si el primero falla.

Ejemplo:

```bash
curl http://127.0.0.1:3000 || echo "Servidor no disponible"
```

---

<a id="seccion-71"></a>

## 71. `tee`

Permite mostrar y guardar a la vez.

```bash
comando | tee resultado.txt
```

Ejemplo:

```bash
nmap -sV 127.0.0.1 | tee scan.txt
```

Verás el resultado en pantalla y además quedará guardado.

Añadir en lugar de sobrescribir:

```bash
tee -a archivo
```

---

<a id="seccion-72"></a>

## 72. `env`

Mostrar variables de entorno:

```bash
env
```

Buscar una concreta:

```bash
env | grep PATH
```

Mostrar:

```bash
echo "$PATH"
```

---

<a id="seccion-73"></a>

## 73. `export`

Crear una variable de entorno:

```bash
export API_URL="http://127.0.0.1:3000"
```

Después:

```bash
curl "$API_URL"
```

---

<a id="seccion-74"></a>

## 74. Información del sistema

Kernel:

```bash
uname -a
```

Distribución:

```bash
cat /etc/os-release
```

Arquitectura:

```bash
uname -m
```

---

<a id="seccion-75"></a>

## 75. Recursos

Memoria:

```bash
free -h
```

`-h`:

```text
human readable
```

Disco:

```bash
df -h
```

Uso de un directorio:

```bash
du -sh directorio
```

Procesos:

```bash
top
```

Una alternativa cómoda si está instalada:

```bash
htop
```

---

<a id="seccion-76"></a>

## 76. Puertos: flujo de diagnóstico recomendado

Cuando una aplicación no responde, una secuencia muy útil es:

```bash
docker ps
```

Después:

```bash
ss -tulpn
```

Después:

```bash
curl -I http://127.0.0.1:3000
```

Después:

```bash
nc -vz 127.0.0.1 3000
```

Y finalmente, en tu propio laboratorio:

```bash
nmap -sV -p 3000 127.0.0.1
```

Cada comando comprueba una capa diferente.

---

<a id="seccion-77"></a>

## 77. Ejemplo completo con Juice Shop

Comprobar Docker:

```bash
docker ps
```

Buscar:

```bash
docker ps | grep juice
```

Comprobar puerto:

```bash
ss -tulpn | grep 3000
```

Comprobar HTTP:

```bash
curl -I http://127.0.0.1:3000
```

Comprobar estado HTTP:

```bash
curl -s -o /dev/null \
-w "%{http_code}\n" \
http://127.0.0.1:3000
```

Descargar página:

```bash
curl -s http://127.0.0.1:3000 > pagina.html
```

Buscar JavaScript:

```bash
grep -oE 'src="[^"]+\.js"' pagina.html
```

Eliminar duplicados:

```bash
grep -oE 'src="[^"]+\.js"' pagina.html | sort -u
```

---

<a id="seccion-78"></a>

## 78. Ejemplo completo con túnel SSH

Imaginemos que Juice Shop está:

```text
VPS
127.0.0.1:3000
```

Por seguridad no exponemos el `3000` públicamente.

Desde nuestro PC:

```bash
ssh -N -L 3000:127.0.0.1:3000 usuario@IP_VPS
```

Después abrimos:

```text
http://127.0.0.1:3000
```

La aplicación viaja mediante el túnel SSH.

No necesitas una regla:

```bash
ufw allow 3000
```

De hecho, mantenerlo ligado a `127.0.0.1` es preferible para un laboratorio vulnerable.

---

<a id="seccion-79"></a>

## 79. Combinaciones especialmente útiles

Encontrar un proceso:

```bash
ps aux | grep nginx
```

Puertos abiertos:

```bash
sudo ss -tulpn
```

Buscar puerto concreto:

```bash
sudo ss -tulpn | grep 3000
```

Comprobar servicio HTTP:

```bash
curl -I http://127.0.0.1:3000
```

Código HTTP:

```bash
curl -s -o /dev/null -w "%{http_code}\n" http://127.0.0.1:3000
```

JSON bonito:

```bash
curl -s http://127.0.0.1:3000/api/products | jq
```

Extraer propiedad:

```bash
curl -s URL | jq -r '.name'
```

Buscar texto:

```bash
grep -i "error" archivo.log
```

Buscar recursivamente:

```bash
grep -ri "localhost" .
```

Archivos JavaScript:

```bash
find . -type f -name "*.js"
```

Logs Docker:

```bash
docker logs -f juice-shop
```

Logs servicio:

```bash
journalctl -u nginx -f
```

Firewall:

```bash
sudo ufw status verbose
```

---

<a id="seccion-80"></a>

## 80. Los flags que más merece la pena memorizar

### SSH

```text
-p     puerto
-i     identidad/clave privada
-L     túnel local
-R     túnel remoto
-N     solamente túnel
-v     verbose
```

### Curl

```text
-s     silent
-i     incluir cabeceras
-I     solamente cabeceras
-X     método HTTP
-H     cabecera
-d     datos
-o     archivo de salida
-w     formato de salida
-L     seguir redirecciones
```

### Grep

```text
-i     ignorar mayúsculas
-n     número de línea
-r     recursivo
-v     excluir coincidencia
-o     solamente coincidencia
-E     regex extendida
```

### Nmap

```text
-p     puerto
-p-    todos los puertos
-sV    detectar versión
-sC    scripts básicos
-Pn    no hacer descubrimiento previo
-O     intentar identificar SO
-v     verbose
-oN    guardar salida
```

### Docker

```text
-a     incluir detenidos
-it    terminal interactiva
-f     seguir logs
-d     segundo plano en Docker Compose
```

### Netcat

```text
-l     escuchar
-v     verbose
-z     comprobar puerto
```

### Linux general

```text
-h     formato legible
-r/-R  recursivo
-f     force/follow según comando
-a     all
-n     número/no resolver nombres según comando
-v     verbose
```

Recuerda que un mismo flag puede significar algo diferente dependiendo del comando.

Por ejemplo:

```bash
curl -s
```

significa:

```text
silent
```

pero:

```bash
grep -s
```

tiene otro significado.

Por eso siempre conviene pensar:

```text
comando + flag
```

como una unidad.

---

<a id="seccion-81"></a>

## 81. Cómo consultar ayuda

La forma rápida:

```bash
comando --help
```

Ejemplo:

```bash
curl --help
```

Manual completo:

```bash
man comando
```

Ejemplo:

```bash
man ssh
```

Buscar dentro del manual:

```text
/
```

Escribes después una palabra:

```text
/LocalForward
```

Siguiente resultado:

```text
n
```

Salir:

```text
q
```

---

<a id="seccion-82"></a>

## 82. Tabla mental para diagnosticar problemas

Cuando algo falla, piensa aproximadamente así:

```text
¿Está funcionando el proceso?
        │
        ├── ps
        ├── systemctl
        └── docker ps

        ↓

¿Está escuchando el puerto?
        │
        └── ss -tulpn

        ↓

¿Puedo conectar?
        │
        └── nc -vz

        ↓

¿Responde HTTP?
        │
        └── curl

        ↓

¿Qué servicio/version hay?
        │
        └── nmap -sV

        ↓

¿Qué dicen los logs?
        │
        ├── docker logs
        ├── journalctl
        └── tail
```

Esta forma de pensar es mucho más importante que memorizar cientos de comandos.

---

<a id="seccion-83"></a>

## 83. Chuleta rápida

```bash
# Usuario
whoami
id
groups

# Sistema
uname -a
cat /etc/os-release

# Red
ip a
ip r
ss -tulpn
ping -c 4 IP

# DNS
dig +short dominio

# Puertos
nc -vz IP PUERTO
nmap -sV -p PUERTO IP

# HTTP
curl URL
curl -I URL
curl -s URL
curl -s URL | jq

# Archivos
pwd
ls -la
cat archivo
less archivo
find . -name "*.js"

# Texto
grep -i palabra archivo
grep -ri palabra .
grep -oE 'regex' archivo
sort -u
head
tail

# Docker
docker ps
docker ps -a
docker logs -f contenedor
docker exec -it contenedor bash
docker stop contenedor
docker start contenedor

# Docker Compose
docker compose up -d
docker compose ps
docker compose logs -f
docker compose down

# Servicios
systemctl status nginx
journalctl -u nginx -f

# Firewall
sudo ufw status verbose

# SSH
ssh usuario@IP
ssh -p PUERTO usuario@IP

# Túnel local
ssh -N -L 3000:127.0.0.1:3000 usuario@IP_VPS

# Túnel remoto
ssh -N -R 9000:127.0.0.1:3000 usuario@SERVIDOR

# Recursos
free -h
df -h
du -sh directorio
top
```

---

<a id="seccion-84"></a>

## 84. Lo que conviene dominar primero

Para el curso de hacking ético con Docker, los comandos prioritarios son:

```text
docker
curl
grep
jq
nmap
ss
ssh
nc
ip
find
cat
less
head
tail
sort
printf
chmod
chown
sudo
ufw
systemctl
journalctl
```

Pero todavía más importante es acostumbrarte a combinarlos:

```bash
curl -s URL | grep PATRON
```

```bash
curl -s URL | jq
```

```bash
grep PATRON archivo | sort -u
```

```bash
docker ps | grep nombre
```

```bash
ss -tulpn | grep puerto
```

```bash
journalctl -u servicio -f
```

En Linux, gran parte del poder está precisamente en combinar comandos pequeños mediante pipes.


Esta guía puede servir como base del curso. Según se avance con Juice Shop, DVWA, Docker, redes, SSH y Nginx, se pueden añadir debajo de cada comando los ejemplos reales del laboratorio.
