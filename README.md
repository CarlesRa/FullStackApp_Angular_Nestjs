# Fullstack App Angular + Nestjs

Guia para la creación de una aplicación Full stack  combinando Angular-11 para el Frontend y NestJs para el backend, utilizando NX Workspace.

## Nx Workspace:

Para la creación del proyecto, utilizaremos NX, creado por ex trabajadores de Google y de código habierto. Consiste en un conjunto de herramientas de desarrollo para ayudar a diseñar, probar y construir a cualquier escala, integrándose sin problemas con tecnologías y bibliotecas modernas al tiempo que proporciona una CLI (Comand Line Interface) robusta, almacenamiento en cache, administración de dependencias y más... Soporta la mayoria de tecnologías Frontend y Backend e integra una excelente documentación que se puede consultar en https://nx.dev/

## Instalaciones necesarias

1º- Para empezar tenemos que descargar e instalar Node-js desde https://nodejs.org/en/download/  
2º- Instalamos Angular utilizando el gestor de paquetes NPM: ``` sudo npm install -g @angular/cli ``` (*Es importante instalarlo con privilegios de administrador*)  
3º- Instalamos NestJs tambien con NPM: ``` sudo npm i -g @nestjs/cli ``` (*Es importante instalarlo con privilegios de administrador*)  
4º- Instalamos el CLI de Nx con NPM: ``` sudo npm install -g nx ``` (*Es importante instalarlo con privilegios de administrador*)  

## Creación del workspace (monorepo)

Para crear nustro workspace (monorepo) nos situamos en el directorio donde deseemos crearlo y en la terminal escribimos ``` npx create-nx-workspace@latest ```  
Una vez hecho esto vamos a elegir un nombre para nuestra organización. La organización va a contener los distintos proyectos entre los cuales queramos compartir código.  
Después de esto vamos a seleccionar la opción **"a workspace with a single Angular application"**  
Nx va a generar por nosotros toda la estructura del espacio de trabajo junto con una aplicación Angular funcional.  
Podemos ejecutar la aplicación entrando en el directorio del workspace y escribiendo el siguiente comando ``` npx nx serve <nombre_de_la_aplicacion> ```  
Seguidamente vamos a generar nuestro api NestJS.  
Si ejecutamos el comando ``` nx list ``` podremos observar las distintas opciones que nos ofrece Nx para generar código.  
  
Vamos a ejecutar ``` npm add --dev @nrwl/nest ``` para añadir la capacidad de generar aplicaciones NestJS.  
Después de esto vamos a ejecutar el comando: ``` npx nx g @nrwl/nest:app api --frontendProject=<nombre_de_la_aplicacion_front_end> ```  
Con este comando ya podremos ver nuestro espacio de trabajo conteniendo el código de un api NestJS. 

## Compartir código entre distintas aplicaciones

Una de las ventajas de utilizar librerías de Nx para compartir código es que no necesitaremos procesos extra de despliegue como es el caso de los paquetes privados de NPM donde primero necesitamos desplegar el paquete y luego actualizar la versión en nuestra aplicación. Con Nx es tan sencillo como crear un nuevo pull request.  
Para generar una librería que podamos acceder desde los distintos proyectos vamos a ejecutar el siguiente comando ``` npx nx g @nrwl/workspace:lib data ```  
Con esto ya tenemos una libreria que podemos compartir entre ambas aplicaciones teniendo que crear nuestros modelos tan **solo una vez** y los podemos importar en ambos proyectos.
