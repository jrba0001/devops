#**Práctica DevOps Keepcoding - Alberto Casero.**

La presente práctica se base en el despliegue de diferentes aplicaciones y páginas web en servidores montados en AWS.

##SOLUCIÓN
* Página estática https://saludtecnolab.es (https).
* Se habilita configuración para acceso por nombre dns.
* Página estática http://52.70.15.100/ (acceso por http)
* Se habilita default para acceso a web estática.
* Se deja como prueba sin certificado para acceso por http.
* Página con node https://chat.saludtecnolab.es (https)
* Se sirven estáticos add_header X-Served-By jrba0001@github.com;
* Página con node y mongo https://saludtecnolab.es/parse (https)
* Página con node y mongo https://nodepop.saludtecnolab.es
* Se sirven estáticos add_header X-Served-By jrba0001@github.com;
* Todas las páginas tienen certificado y se sirven por https.

####Acciones:
* Se ha realizado todas las instalaciones con usuario web
* Se ha habilitado el inicio automático de mongod en el sistema
* Se ha habilitado el arranque automático de pm2
* Se ha configurado pm2 para administrar el servicio de todas las aplicaciones.
* Se ha configurado el servicio crontab para todos los logs de las aplicaciones.
* Se ha instalado servicio fail2ban para securizar servidos
Acceso robomongo por ssh con certificado .pem
* Configuración de puertos: Accesos al servidor: -- http 80 -- https 443 -- ssh 7654

##REQUISITOS:

Utilizar node como servidor de aplicación utilizando PM2 como gestor de procesos node para que esté siempre en ejecución. La aplicación node deberá reiniciarse automáticamente al arrancar el servidor (en el startup).

• Utilizar nginx como proxy inverso que se encargue de recibir las peticiones HTTP y derivárselas a node.

• Los archivos estáticos de la aplicación (imágenes, css, etc.) deberán ser servidos por nginx (no por node). Para poder diferenciar quién sirve estos estáticos, se deberá añadir una cabecera HTTP cuando se sirvan estáticos cuyo valor sea: X-Owner (la X- indica que es una cabecera personalizada) y el valor de la cabecera deberá ser el nombre de la cuenta de usuario en github o bitbucket del alumno. Si la solución de la práctica por parte del alumno no tuviera archivos estáticos, deberá proporcionar el acceso a un archivo estático que se sirva a través de nginx (por ejemplo, a través de la URL /public/logo.jpg). En este caso, el alumno deberá indicar la URL del archivo estático en el archivo README.md del repositorio.

Si se accede al servidor web indicando la dirección IP del servidor en lugar del nombre de dominio, se deberá mostrar el contenido de alguna plantilla de https://startbootstrap.com. Si lo desea, el alumno podrá personalizar los textos de la página.

**Se pueden aplicar filtros usando los parámetros siguientes: Nombre, estado (compra o vende), precio, foto, tags.** 

* Añadimos esta etiqueta o varias a la página ?nombre=bicicleta1 o directamente ?nombre=bicicleta https://nodepop.saludtecnolab.es/anuncios?nombre=bicicleta
Ordenado https://nodepop.saludtecnolab.es/anuncios?nombre=bicicleta&sort=nombre

* Ordenado descendente https://nodepop.saludtecnolab.es/anuncios?nombre=bicicleta&sort=-nombre

* Limitado a x anuncios, en este ejmplo1 https://nodepop.saludtecnolab.es/anuncios?nombre=bicicleta&limit=1

* Limitado a estado compra o vende, este ejemplo compra ordenado precio https://nodepop.saludtecnolab.es/anuncios?estado=compra&sort=precio>

* Limitado a estado compra o vende, este ejemplo vende ordenado precio descendiente https://nodepop.saludtecnolab.es/anuncios?estado=vende&sort=-precio

* Listado por precios Busca por precio ("x-" -> Mayor que x || "x-y" -> Entre x e y || "-y" -> Menor que. En este ejemplo mayor a 600: https://nodepop.saludtecnolab.es/anuncios?precio=600-

* Listado por precios Busca por precio ("x-" -> Mayor que x || "x-y" -> Entre x e y || "-y" -> Menor que y En este ejemplo menor a 600: https://nodepop.saludtecnolab.es/anuncios?precio=-600

* En este ejemplo entre 100 y 800: https://nodepop.saludtecnolab.es/anuncios?precio=100-800&sort=-precio

* Se pueden aplicar filtros para ordenar "sort", limitar "limit", saltar algún valor "skip"

* Listado por nombre = bicicleta, precio mayor que 600, ordenador precio descendiente, limitada a dos búsquedas. https://nodepop.saludtecnolab.es/anuncios?nombre=bicicle&precio=400-&sort=-precio&limit=1
tags: Busca por tags o etiquetas ("lifestyle", "motor", "mobile", "work")
**Todos los ejemplos anteriores pueden realizarse atacando a la api: /apiv1/anuncios**

En este ejemplo entre 100 y 800: https://nodepop.saludtecnolab.es/apiv1/anuncios?precio=100-800&sort=-precio

#####Añadir anuncios: 
Realizando una petición post a la dirección https://nodepop.saludtecnolab.es/apiv1/anuncios se pueden añadir nuevos anuncios a la base de datos.

#####Borrar anuncios: 
Realizando una petición delete a la dirección https://nodepop.saludtecnolab.es/apiv1/anuncios se pueden borrar anuncios a la base de datos.
