# Práctica DevOps Keepcoding - Alberto Casero.

La presente práctica se base en el despliegue de diferentes aplicaciones y páginas web en servidores montados en AWS.

#SOLUCIÓN

Página estática https://saludtecnolab.es (https)
Página con node chat.saludtecnolab.es (https)
Página con node y mongo https://saludtecnolab.es/parse (https)
Página con node y mongo https://nodepop.saludtecnolab.es




#REQUISITOS:

Utilizar node como servidor de aplicación utilizando PM2 como gestor de procesos node para que esté 
siempre en ejecucion. La aplicación node deberá reiniciarse automáticamente al
arrancar el servidor (en el startup).

• Utilizar nginx como proxy inverso que se encargue de recibir las peticiones HTTP y derivárselas
a node.

• Los archivos estáticos de la aplicación (imágenes, css, etc.) deberán ser servidos por nginx (no
por node). Para poder diferenciar quién sirve estos estáticos, se deberá añadir una cabecera
HTTP cuando se sirvan estáticos cuyo valor sea: X-Owner (la X- indica que es una cabecera
personalizada) y el valor de la cabecera deberá ser el nombre de la cuenta de usuario en github
o bitbucket del alumno. Si la solución de la práctica por parte del alumno no tuviera archivos
estáticos, deberá proporcionar el acceso a un archivo estático que se sirva a través de nginx
(por ejemplo a través de la URL <dominio>/public/logo.jpg). En este caso, el alumno deberá
indicar la URL del archivo estático en el archivo README.md del repositorio.

Si se accede al servidor web indicando la dirección IP del servidor en lugar del nombre de
dominio, se deberá mostrar el contenido de alguna plantilla de https://startbootstrap.com. Si lo
desea, el alumno podrá personalizar los textos de la página.





### **Se pueden aplicar filtros usando los parametros siguientes: Nombre, estado (compra o vende), precio, foto, tags.
**
    Añadimos esta etiqueta o varias a la pagina ?nombre=bicicleta1 o directamente ?nombre=bicicleta http://localhost:3000/anuncios?nombre=bicicleta

    Ordenado http://localhost:3000/anuncios?nombre=bicicleta&sort=nombre

    Ordenado descendente http://localhost:3000/anuncios?nombre=bicicleta&sort=-nombre

    Limitado a x anuncios, en este ejmplo1 http://localhost:3000/anuncios?nombre=bicicleta&limit=1

    Limitado a estado compra o vende, este ejemplo compra ordenado precio http://localhost:3000/anuncios?estado=compra&sort=precio>

    Limitado a estado compra o vende, este ejemplo vende ordenado precio descendiente http://localhost:3000/anuncios?estado=vende&sort=-precio

    Listado por precios Busca por precio ("x-" -> Mayor que x || "x-y" -> Entre x e y || "-y" -> Menor qu. En este ejemplo mayor a 600: http://localhost:3000/anuncios?precio=600-

    Listado por precios Busca por precio ("x-" -> Mayor que x || "x-y" -> Entre x e y || "-y" -> Menor que y En este ejemplo menor a 600: http://localhost:3000/anuncios?precio=-600

    En este ejemplo entre 100 y 800: http://localhost:3000/anuncios?precio=100-800&sort=-precio

    Se pueden aplicar filtros para ordenar "sort", limitar "limit", saltar algun valor "skip"

    Listado por nombre = biclice, precio mayor que 600, ordenador precio descendiente, limitada a dos busqueda. http://localhost:3000/anuncios?nombre=bicicle&precio=400-&sort=-precio&limit=1
    tags: Busca por tags o etiquetas ("lifestyle", "motor", "mobile", "work")
### **
###     Todos los ejemplos anteriores pueden realizarse atacando a la api: /apiv1/anuncios
**
    En este ejemplo entre 100 y 800: http://localhost:3000/apiv1/anuncios?precio=100-800&sort=-precio

    Añadir anuncios:

    Realizando una petición post a la dirección http://localhost:3000/apiv1/anuncios se pueden añadir nuevos anuncios a la base de datos.
    Borrar anuncios:

    Realizando una petición delete a la dirección http://localhost:3000/apiv1/anuncios se pueden borrar anuncios a la base de datos.
