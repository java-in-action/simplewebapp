# Despliegue de una aplicación Java en AWS Elastic Beanstalck

Este repositorio contiene una aplicación Java EE sencilla que será desplegada dentro de un servicio de AWS, que nos permitirá crear un proceso de despliegue automatizado en pocos pasos.

El objetivo de este proyecto es poder demostrar lo sencillo que es desplegar una aplicación Java Web en la infraestructura en la nube de AWS. Sin embargo, para un desarrollador que no está acostumbrado a crear infraestructura de software, puede ser un reto. 

## Prerrequisitos
[Contar con una cuenta de AWS](https://aws.amazon.com/es/). En el proceso de crear una cuenta se solicita una tarjeta de crédito, pero no vamos a incurrir en costos para el demo ya que solo vamos a usar unas horas gratuitas de las permitidas por AWS y después eliminar el demo.

[Tener una cuenta de GitHub](https://github.com/). Para descargar el código del ejemplo se necesita tener una cuenta en GitHub.

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

### Eliminar la aplicación

AWS te permite usar sus servicios en un modelo llamado "Free Tier", el cual nos permite usarlos por un tiempo para aprender y probarlos. Llegado el límite del consumo, dependiendo del servicio, te empezara a cobrar a tu tarjeta de crédito.

Es por eso que al termino de este tutorial, les recomendamos eliminar la aplicación desplegada en Amplify para no incurrir en costos.

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

[Free Tier](https://aws.amazon.com/es/free/)



