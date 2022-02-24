# Despliegue de una aplicación Java en AWS Elastic Beanstalk

En este tutorial vamos a usar un repositorio en GitHub que contiene una aplicación Java J2EE (archivo WAR) que será desplegada dentro de la nube de AWS usando un servicio llamado Elastic Beanstalk, el cual nos permitirá desplegar la aplicación automáticamente. 

El objetivo de este proyecto es poder demostrar lo sencillo que es desplegar una aplicación Java Web en la infraestructura en la nube de AWS. Sin embargo, analizaremos todo lo que el servicio hace por detrás, cuestiones de configuración y hablaremos acerca de la integración con otros servicios.

## Prerrequisitos

[Contar con una cuenta de AWS](https://aws.amazon.com/es/). Para crear una cuenta les va a solicitar un número de tarjeta de crédito, pero no vamos a incurrir en gastos por que vamos a usar el “Free Tier” de AWS y al final vamos a eliminar el demo.

[Tener una cuenta de GitHub](https://github.com/). Para poder hacer fork del proyecto y descargar el archivo WAR..

Conocimientos de JAVA J2EE, Despliegue con Tomcat y AWS Básico.

## Pasos

### Descargar el archivo WAR

1) Ir al repositorio de la aplicación: https://github.com/java-in-action/simplewebapp
2) Descargar el archivo: simplewebapp/target/**simplewebapp.war**, el cual vamos a utilizar en el siguiente paso


### Desplegar la aplicación Java Web en AWS Elastic Beanstalk

1) Iniciar sesión en [AWS Console](https://aws.amazon.com/es/)
2) Buscar el servicio **Elastic Beanstalk**
3) Dar clic en **Create Application** 
![Crear aplicación](/img/create_app.jpg)
4) Introducir la información de la aplicación, primero el nombre de la aplicación: **SimpleJavaAppAWS**  
![Nombre de la aplicación](/img/nombre_app.jpg)  
5) Introducir los datos de la Plataforma, seleccionar **Tomcat** y dejar los valores recomendados por defecto  
![Nombre de la aplicación](/img/datos_plataforma.jpg)
6) En código de la aplicación seleccionar **Cargar el código**  
![Cargar código](/img/cargar_codigo.jpg)
8) Buscar archivo que descargamos en el paso anterior, **simplewebapp.war**
9) Clic en crear una aplicación.

### Salidas esperadas:

Veremos un mensaje diciendo:  
**Creando Simplejavaappaws-env**  
Este proceso tardará unos minutos...

![Inicio del proceso de despliege](/img/creando_app.jpg)

Después de unos minutos (5 aprox.) veremos una bandera verde indicando que la aplicación fue desplegada en una plataforma construida automáticamente por AWS, que contiene un Servidor Tomcat. 

![Aplicación desplegada en Tomcat](/img/app_creada.jpg)

Ahora identifica la liga donde se desplego la aplicación (cuadro en rojo) y dale clic, para ver la aplicación desplegada en el servidor de AWS.

![Página JSP - Hola Mundo!](/img/hello_world_page.jpg)

El tutorial termina en este punto. 

### ¿Cómo AWS Elastic Beanstalk cobra el consumo del servicio?
No se aplican cargos adicionales por utilizar AWS Elastic Beanstalk. Solo tiene que pagar por los recursos de AWS (por ejemplo, instancias EC2 o buckets de S3) creados para almacenar y ejecutar la aplicación.

El costo de ejecutar un sitio web mediante Elastic Beanstalk puede variar según distintos factores, como el número de instancias de Amazon EC2 necesarias para administrar el tráfico del sitio web, el ancho de banda consumido por la aplicación y qué base de datos u opciones de almacenamiento usa la aplicación. El principal costo para una aplicación web normalmente será para las instancias de Amazon EC2 y para el Elastic Load Balancing que distribuye el tráfico entre las instancias que ejecutan la aplicación.

### Eliminar la aplicación

Para evitar cargos más adelante, procedemos a terminar el ambiente y eliminar la aplicación. AWS permite usar sus servicios por un periodo de prueba "Free Tier" o por cierto límite de consumo, cuando nos acercamos a ese punto (85% aprox) recibiremos un correo anunciando que estamos por llegar al límite gratuito y nos empezarán a cobrar el consumo. Es decir mientras no lleguemos a ese límite podemos usar los serivios para aprender y practicas.

Una practica recomendada es detener los servicios cuando no se estén utilizando o eliminarlos definitivamente. También se pueden poner alarmas para avisar cuando se llegué a un punto determinado o crear tareas automatizadas para iniciar y detener ciertos servicios, estos temas están fuera del alcance de este tutorial pero se recomienda que conozcan más al respecto.

1) Abrir Elastic Beanstalk
2) Seleccionar la aplicación: SiompleJavaWebAppAWS
3) Clic en el botón Acciones > Terminar el entorno 
![Eliminar el app al final de este tutorial](/img/delete_app.jpg)
Nota: Esperamos a que termine de terminar el proceso. El cual va a detener la aplicación y así podremos eliminarla por completo.
4) Una vez terminado el proceso de terminación. Seleccionamos la aplicación y damos clic en Accioones > Eliminar app.


### Ventajas de usar AWS Elastic Beanstalk

A simple vista parece muy sencillo ver la aplicación desplegada, después de haber seleccionado archivo y dado algunos parámetros de entrada. Sin embargo, hay muchos pasos intermedios que no tuvimos que ejecutar, como: crear una máquina virtual que tenga un sistema operativo, descargar e instalar Java, descargar e instalar Tomcat, etc. 


Elastic Beanstalk es un servicio de infraestructura como plataforma o IaaS (infraestructure as a service) y no solamente nos permite comenzar fácil y rápido con una aplicación web, también tiene los siguientes beneficios:

* Escalación automática. En caso de necesitar más recursos como memoria o procesador, se puede ajustar a las necesidades; de ahí el concepto de elasticidad. 

* Prevención de despliegues fallidos. Este servicio cuenata con sistema de control de versiones de archivos de despliegue. En caso de que el archivo contenga errores el proceso se cancela y se conserva en línea la última versión desplegada con exito.

* Además, tenemos acceso a características como: Monitoreo, Logs, Alarmas, etc. 

### Desventajas

Por mencionar algunas desventajas de este entorno, es que no tenemos acceso a la máquina virtual (EC2) donde está instalado, por lo que para aplicaciones que manejan cuestiones muy específicas que necesiten un control de la máquina, esta opción no es tan recomendable, lo mejor sería crear una EC2 e instalar todo el ambiente. 

La configuración de seguridad es compleja al inicio, se necesitan conocimientos de redes, seguridad informática y de nube para cuestiones más avanzadas, como interacción con otros servicios, bases de datos, permisos, políticas, etc.

## Conclusión

En este ejemplo sencillo hemos desplegado una aplicación web en un servicio de AWS llamado Elastic Beanstalk. Si bien, es un ejemplo sencillo nos ayudará a entender cómo funcionan los servicios en la nube de AWS y nos podrá servir de base para otros tutoriales más avanzados.

### Referencias

[AWS Elastic Beanstalk - Información General](https://aws.amazon.com/es/elasticbeanstalk/)

[Precios de AWS Elastic Beanstalk](https://aws.amazon.com/es/elasticbeanstalk/pricing/)



