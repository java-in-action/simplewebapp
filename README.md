# Despliege de una aplicación Java en AWS

Este repositorio contiene una aplicación Java EE sencilla que será desplegada dentro de un servicio de AWS, que nos nos permitirá crear un proceso de despliege automatizado en pocos pasos.

El objetivo de este proyecto es poder demostrar lo sencillo que es desplegar una aplicación Java Web en la infraestrtura en la nube de AWS. Sin embargo, para un desarrollador que no esta acostumbrado a crear infraestructura de software, puede ser un reto. 

## Prerrequisitos
[Contar con una cuenta de AWS](https://aws.amazon.com/es/). En el proceso de crear una cuenta se solicita una tarjeta de crédito, pero no vamos a incurrir en costos para el demo ya que solo vamos a usar unas horas gratuitas de las permitidas por AWS y después eliminar el demo.

[Tener una cuenta de GitHub](https://github.com/). Para descargar el código del ejemplo se necesita tener una cuenta en GitHub.

[Tener instalado y configurado Maven](https://maven.apache.org/index.html). Se utilizará Maven para crear una aplicación Java Web sencilla. En este ejercicio no vamos usar IDE por cuestiones practicas y de rapidez. 

## Pasos

### Crear la aplicación Java Web: SimpleWebApp

Te recomendamos que crees la aplicación desde cero. Los siguientes pasos automatizan la creación una aplicación Java WEB sencilla y creando un archivo de despliege (WAR), usando un arquetipo de Maven y pasando parametros para no interactuar con la consola. Si quieres saltar a la sección de despliege en AWS, el archivo WAR que utilizarás, lo encontrarás en : /target/**simplewebapp.war** .

1) Abre una consola de comandos y ejecuta el siguiente comando en la carpeta que desees crear la aplicación:

`mvn archetype:generate -DgroupId=talent.fest -DartifactId=simplewebapp -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-webapp -DarchetypeVersion=1.4 -DinteractiveMode=false`


2) Ve a la carpeta (creada en el paso anterior) simplewebapp, y ejecuta el siguiente comando:

`mvn install`

Este comando va a crear un archivo **simplewebapp.war** dentro del directorio /target, el cuál vamos a utilizar más adelante.


### Desplegar la aplicación web en AWS

1) Iniciar sesión en AWS
2) Buscar el servicio **Elastic Beanstalk**
3) Click en **Create Application**
4) Introducir el nombre de la aplicación: **SimpleJavaAppAWS**
5) En Plataforma seleccionar **Tomcat** y dejar los valores recomendados por defecto
6) En código de la aplicación seleccionar **Cargar el código**
7) En Origen del código fuente, click en **Elegir archivo**
8) Seleccionar el archivo que creamos en el paso 1, /simplewebapp/target/**simplewebapp.war**
9) Click en crear una aplicación.

### Salidas esperadas:

Veremos un mensaje diciendo:  
**Creando Simplejavaappaws-env**  
Este proceso tardará unos minutos...

![Inicio del proceso de despliege](/img/creando_app.jpg)

Después de unos minutos (5 aprox.) veremos una bandera verde indicando que la aplicación fue desplegada en una plataforma construida automáticamente por AWS, que contiene un Servidor Tomcat. 

![Aplicación desplegada en Tomcat](/img/app_creada.jpg)

Ahora identifica la liga donde se desplego la aplicación (cuadro en rojo) y dale click, para ver la aplicación desplegada en el servidor de AWS.

![Página JSP - Hola Mundo!](/img/hello_world_page.jpg)

El tutorial termina en este punto. 

### Ventajas de usar AWS Elastic Beanstalk

A simple vista parece muy sencillo ver la aplicación desplegada, después de haber seleccionado archivo y dado algunos paramétros de entrada. Sin embargo, hay muchos pasos intermedios que no tuvimos que ejecutar, como: crear una máquina virtual que tenga un sistema operativo, descargar e instalar Java, descargar e instalar Tomcat, etc. 


Elastic Beanstalk es un servicio de infraestructura como plataforma o IaaS (infraestructure as a service) y no solamente nos permite comenzar fácil y rápido con una aplicación web, también tiene los siguientes beneficios:

* Escalación automática. En caso de necesitar más recursos como memoria o procesador, se puede ajustar a las necesidades; de ahí el concepto de elasticidad. 

* Prevención de desplieges fallidos. Este servicio tiene un control de versiones de los archivos de despliege, en caso de que el archivo contenga errores el proceso de despliege no se completa y se conserva en línea la última versión desplegada con exito del archivo.

* Además tenemos acceso a carácteristicas como: Monitoreo, Logs, Alarmas, etc. 

### Desventajas

Por mecionar algunas desventajas de este entorno, es que no tenemos acceso a la máquina virtual (EC2) donde esta instalado, por lo que para aplicaciones que menejan cuestiones muy especificas que necesiten un control de la máquina, esta opción no es tan recomendable, lo mejor sería crear una EC2 e instalar todo el ambiente. 

La configuración de seguridad es compleja al inicio, se necesitan conocimientos de redes, seguridad informática y de nube para cuestiones más avanzadas, como interacción con otros servicios, bases de datos, permisos, políticas, etc.

## Conclusión

En este ejemplo sencillo hemos desplegado una aplicación web en un servicio de AWS llamado Elastic Beanstalk. Si bien, es un ejemplo sencillo nos ayudará a entender como funcionan los servicios en la nube de AWS y nos podrá servir de base para otros tutoriales más avanzados.

### Referencias

[AWS Elastic Beanstalk - Información General](https://aws.amazon.com/es/elasticbeanstalk/)

[Generate a WAR File in Maven](https://www.baeldung.com/maven-generate-war-file)

[Stack overflow:Generating project in Interactive mode Taking lot of time](stackoverflow.com/questions/17524148/generating-project-in-interactive-mode-taking-lot-of-time)

[Maven Webapp Archetype](https://maven.apache.org/archetypes/maven-archetype-webapp/)



