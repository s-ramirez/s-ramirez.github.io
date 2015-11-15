---
title:  "Angular 2 + TypeScript: Primeros pasos"
description: Dando los primeros pasos en la siguiente versión de este popular framework.
name: angular-2-quickstart
---
Esta guía plantea la utilización de **TypeScript** para la creación de una aplicación simple y básica utilizando el framework AngularJS 2.0 (versión 2.0.0-ALPHA.44) y está basada en la [guía de inicio rápido oficial](https://angular.io/docs/ts/latest/quickstart.html) de Angular 2.0.

### TypeScript
[TypeScript](http://www.typescriptlang.org/) se autodenomina como un superconjunto de JavaScript, desarrollado por [Microsoft](https://github.com/Microsoft/TypeScript/), cuya finalidad es agregar tipado estático al lenguaje. El código escrito en TypeScript es compilado en JavaScript limpio y simple que puede ser utilizado tanto en los navegadores web como en Node.js y nos da un paso adelante en el futuro al permitirnos compilar nuestro código tanto en la especificación popular ECMAScript5 como en la nueva [ES6](http://www.ecma-international.org/ecma-262/6.0/).

Admito que en un inicio solía pensar que la existencia de TypeScript era innecesaria, creía que JavaScript era suficiente para mi y estaba decidido a seguir utilizándolo.

Un día decidí darle una oportunidad y en cuestión de un par de horas ya manejaba la sintaxis básica y llegué a darme cuenta de lo útil que podía ser contar con tipajes. Además de la cantidad de errores que podía solucionar en tiempo de compilación (intentar acceder nombres de propiedades erróneos, tipos de retorno equivocados, entre otros descuidos), mi código final era mucho más legible y organizado sin la necesidad de un esfuerzo extra por lograrlo.

## Requisitos
La única herramienta necesaria para empezar es **Node.js**. Para realizar esta tarea existen muchas guías útiles, [esta](http://www.desarrolloweb.com/articulos/instalar-node-js.html) es una de las más detalladas que encontré y explica los pasos a seguir en los tres sistemas operativos más populares.

## Configuración Inicial
### Estructura
Inicialmente creamos la estructura del proyecto en una nueva carpeta llamada `angular-prueba`. Adentro de esta colocamos otra carpeta llamada `src` donde almacenaremos nuestro código fuente.

Luego creamos una nueva carpeta a la que llamaremos `app` donde pondremos nuestro código TypeScript.

Finalmente creamos dos archivos con los siguientes nombres
* `app/app.ts` - El archivo principal de nuestra aplicación con extensión TypeScript.
* `index.html` - Nuestra página HTML.

La estructura debe verse de la siguiente manera.
```
angular-prueba
└── src
    ├── app
    │   └── app.ts
    └── index.html
```

### Instalando dependencias
Utilizaremos `npm` para instalar las dependencias de nuestra aplicación. Para esto abrimos una línea de comandos (cmd o terminal) en la ráiz de nuestro proyecto y escribimos los siguientes comandos.
1. Inicializamos el sistema de manejo de paquetes de Node en nuestro proyecto
```
npm init -y
```
2. Instalamos las librerías `angular2` y `systemjs`, esta última permite la carga de *módulos* como veremos más adelante.
```
npm install angular2 systemjs --save
```
3. Instalamos dos dependencias para la hora de desarrollar. Estas son `typescript`, el compilador del lenguaje que estaremos utilizando, y `live-server`, el cual permite la creación de un servidor local para probar nuestra aplicación que incluye una recarga automática del navegador cuando se realizan cambios en los archivos.
```
npm install typescript live-server --save-dev
```
Una vez que hayamos instalado nuestras dependencias, podemos ver que se ha creado el archivo `package.json`, el cual almacena lo que hemos instalado gracias a la utlización de `--save` y `--save-dev`, y la carpeta `node_modules` donde se encuentran los archivos que hemos instalado.

Lo siguiente será abrir el archivo `package.json` y editar la sección `scripts` agregando las siguientes líneas de código.

```json
"scripts": {
    "tsc": "tsc -p src",
    "start": "live-server --open=src"
 }
```

Gracias a esto, de ahora en adelante podremos correr los commandos `npm tsc` para compilar nuestro código TypeScript (luego de realizar su configuración) y `npm start` para iniciar nuestro servidor local.

### Configurando el compilador de TypeScript
Es necesario agregar un archivo `tsconfig.json` en la carpeta `src` de nuestro proyecto el cual almacenará la configuración del compilador de TypeScript. En este nuevo archivo agregaremos las siguientes líneas.
```json
{
  "compilerOptions": {
    "target": "ES5",
    "module": "commonjs",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "removeComments": false,
    "noImplicitAny": false
  }
}
```
*Más información sobre el archivo tsconfig.json puede encontrarse en su [documentación oficial](https://github.com/Microsoft/TypeScript/wiki/tsconfig.json) lastimosamente esta sólo se encuentra disponible en inglés*

## Hola Angular 2.0
Luego de completar todos los pasos necesarios para la configuración inicial, finalmente llegó la hora de desarrollar.

Es hora de juntar todas las librerías que instalamos previamente en nuestro `index.html`. Como estas se encuentran en la carpeta `node_modules`, debemos identificar correctamente su ruta.
```html
<html>
  <head>
    <title>Probando Angular2</title>
    <!-- Librerias -->
    <script src="../node_modules/systemjs/dist/system.src.js"></script>
    <script src="../node_modules/angular2/bundles/angular2.dev.js"></script>
  </head>
  <body>
  </body>
</html>
```

Después de agregar estas líneas, aprovecharemos la inclusión de `systemjs` para cargar los módulos en formato `.js` que obtendremos una vez que nuestro código TypeScript haya sido compilado.

En este proyecto, el único módulo que estaremos desarrollando se llamará `app`.
```html
<html>
  <head>
    <title>Probando Angular2</title>
    <!-- Librerias -->
    <script src="../node_modules/systemjs/dist/system.src.js"></script>
    <script src="../node_modules/angular2/bundles/angular2.dev.js"></script>
    <!-- Importar modulos -->
    <script>
      System.config({
        packages: {'app': {defaultExtension: 'js'}}
      });
      System.import('app/app');
    </script>
  </head>
  <body>
  </body>
</html>
```

### Nuestro primer componente
Iniciaremos editando el archivo `app.ts` que creamos previamente. Agregamos la siguiente línea
```js
import {Component} from 'angular2/angular2';
```
La utilización de `import` permite obtener definiciones de clases det tal manera que nuestro código TypeScript ahora será capaz de conocer las propiedades y métodos de estas.

En este caso hemos importado la clase `Component` proveniente de las declaraciones ubicadas en `angular2/angular2`.

Ahora que nuestro compilador conoce qué es un `Component` podremos definir uno de la siguiente manera.

```js
import {Component} from 'angular2/angular2';

@Component({
    selector: 'app-prueba',
    template: '<h1>Hola Angular2</h1>'
})
```
Hemos declarado `@Component` y le hemos agregado dos propiedades. El símbolo `@` le indica al compilador de TypeScript que `Component` es una *decoración*
> Un Decorador es una función que modifica una clase, propiedad, método o parámetro de un método.

En este caso lo utilizamos para declarar metadata de la clase. Angular es capaz de identificar esta metadata y procesarla apropiadamente.

Las dos propiedades que hemos agregado son `selector` y `template`. La primera indica el **tag de html** que será reemplazado por nuestro componente. La segunda es el **código html** que reemplazará el tag seleccionado.

El siguiente paso será crear la *clase* donde podremos definir la lógica de nuestro componente más adelante. Para esto agregamos las siguientes líneas al final de nuestro `app.ts`.

```js
class Componente { }
```

Finalmente tendremos que utilizar el método `bootstrap` de Angular 2 para indicar que deseamos iniciar nuestra aplicación utilizando esta clase como *raíz* al inicio de nuestra ejecución.

Para este paso tendremos que agregar el método `bootstrap` a nuestra línea de `import` al inicio de `app.ts` para que quede de la siguiente manera.

```js
import {Component, bootstrap} from 'angular2/angular2';
```
De ahora en adelante podremos usar el método `bootstrap`, lo usaremos al final del archivo para agregar el componente que hemos creado.

```js
bootstrap(Componente);
```

Al finalizr, nuestro `app.ts` se verá de la siguiente manera.
```js
import {Component, bootstrap} from 'angular2/angular2';

@Component({
    selector: 'app-prueba',
    template: '<h1>Hola Angular2</h1>'
})

class Componente { }

bootstrap(Componente);
```

### Agregando el componente
Anteriormente, al definir nuestro componente, escogimos el selector que deseabamos utilizar en el código html. Es hora de agregarlo en el `<body></body>` de nuestro `index.html` para obtener lo siguiente.

```html
<html>
  <head>
    <title>Probando Angular2</title>
    <!-- Librerias -->
    <script src="../node_modules/systemjs/dist/system.src.js"></script>
    <script src="../node_modules/angular2/bundles/angular2.dev.js"></script>
    <!-- Importar modulos -->
    <script>
      System.config({
        packages: {'app': {defaultExtension: 'js'}}
      });
      System.import('app/app');
    </script>
  </head>
  <body>
    <app-prueba></app-prueba>
  </body>
</html>
```
## Compilando TypeScript
Antes de probar nuestro código en el navegador, es necesario compilar nuestro código TypeScript utilizando `tsc` gracias a la configuración que realizamos al inicio.

Abrimos una línea de comandos en la raíz de nuestro proyecto y ejecutamos el siguiente comando.
```
npm run tsc
```
Si el proceso se completa correctamente, deberíamos obtener el código `.js` respectivo a nuestros archivos `.ts`.

## Ejecutando la aplicación

Finalmente es hora de probar nuestra aplicación en el navegador.

En la misma línea de comando escribiremos lo siguiente.

```
npm start
```
Esto iniciará nuestro `live-server` y nos dará un url donde podremos ver nuestro componente en ejecución.

## Resultados
Hemos logrado completar un "Hola Mundo" utilizando Angular 2 y TypeScript. Utilizamos únicamente un componente y configuramos un ambiente que podrá ser utilizado en el futuro para desarrollar proyectos un poco más ambiciosos.

### El siguiente paso
Hay que recordar que Angular 2 aún no se encuentra en su versión final y no existe una fecha para su lanzamiento sin embargo es posible prepararnos para este cambio.
