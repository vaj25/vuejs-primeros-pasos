# Ejercicios del libro "Desarrolla aplicaciones con VueJS" de José Dongil 

Notas y ejercicios a partir del libro: [Desarrolla aplicaciones con VueJS](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/)

## Bloque 1. Los conceptos básicos

### [Capítulo 1. The Progressive JavaScript Framework](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/introduccion.html)

La librería se enmarca dentro las arquitecturas de componentes con una gestión interna de modelos basada en el patrón [Model–view–viewmodel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel). Esto quiere decir que los componentes, internamente, tienen mecanismos de doble 'data-binding' para manipular el estado de la aplicación.

- Proporciona componentes visuales de forma reactiva: Piezas de UI bien encapsulados que exponen una API con propiedades de entrada y emisión de eventos.

- Utiliza Virtual DOM.

- Sigue un flujo one-way data-binding para la comunicación entre componentes.

- Sigue un flujo doble-way data-binding para la comunicación de modelos dentro de un componente aislado.

#### Primer ejemplo: 

- [Demo](https://cristinafsanz.github.io/vuejs-primeros-pasos/libro-vue/capitulo1/example-vue)

- [Código](https://github.com/cristinafsanz/vuejs-primeros-pasos/tree/master/libro-vue/capitulo1/example-vue)

- Cómo se ve en el navegador usando la extensión de Chrome de [vue-devtools](https://github.com/vuejs/vue-devtools) después de abrir la consola de JavaScript:

![Screenshot de aplicación en el navegador con extensión de Chrome a la derecha para ver los componentes](imagenes/navegador-vuedev-tools.png?raw=true)

- Pasos:

```

$ cd capitulo1

$ mkdir example-vue

$ cd example-vue

$ npm init

$ npm install vue --save

```

Lo que hacemos ahora es añadir un fichero [index.html](capitulo1/example-vue/index.html) en la raíz e incluimos tanto la librería de Vue (por ahora versión desarrollo), como nuestro fichero JS.

Se añade un elemento HTML que haga de contenedor de nuestra aplicación VueJS:

```
<div id="app"></div>
```

De esta manera, conseguimos delimitar el contexto en el que puede actuar nuestra aplicación.

Lo siguiente que hacemos es crear una instancia de nuestra aplicación VueJS en nuestro fichero [app.js](capitulo1/example-vue/app.js)

Lo que le decimos a VueJS es que genere una nueva instancia que tenga como referencia al elemento HTML que tenga como identificador único la palabra reservada app. 

Los componentes que tenemos en el ejemplo son:

- root (línea [41](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo1/example-vue/app.js#L41)): Contiene los componentes GameHeader, GameAdd y GameList. Tiene en data el array `games` (contiene 3 objetos con el título de los videojuegos).  Con v-bind pasa la propiedad interna `games` al componente GameList. Registra el evento `new` de GameAdd (@new="addNewGame", versión corta de v-on:new="addNewGame") con el nuevo `game` y lo añade al array `games`.

    - game-header (línea [37](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo1/example-vue/app.js#L37)): Sólo muestra el título de la página.

    - game-add (línea [1](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo1/example-vue/app.js#L1)): Contiene un input y un button. Con v-model va rellenando el atributo con lo que se escribe en el input. Emite un evento `new` (this.$emit('new')) mandando el `game` al elemento padre Root cuando se pulsa el botón.

    - game-list (línea [23](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo1/example-vue/app.js#L23)): Contiene los elementos GameItem. Recibe en props el modelo `games` de Root. Se pasa cada `game` mediante un for con :game="item" (es el [shorthand](https://vuejs.org/v2/guide/syntax.html#v-bind-Shorthand) de v-bind).

        - game-item (línea [32](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo1/example-vue/app.js#L32)): Recibe en props el modelo `game` de GameList para pintar el título en la vista.

### [Capítulo 2. Trabajando con templates](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/templates.html)

#### Ejemplo: 

- [Demo](https://cristinafsanz.github.io/vuejs-primeros-pasos/libro-vue/capitulo2/index.html)

- [Código](https://github.com/cristinafsanz/vuejs-primeros-pasos/tree/master/libro-vue/capitulo2)

- Elementos del ejemplo:

    - [Interpolación con filtro](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo2/index.html#L11)

    ![Screenshot con Bienvenido USUARIO al escribir usuario en el input de username](imagenes/interpolacion-filtro.png?raw=true)

    - [Interpolación atributos](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo2/index.html#L31): El botón está deshabilitado mientras el formulario no está relleno. Se utiliza una computada para comprobarlo. 

    - [Interpolación por medio de expresiones](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo2/index.html#L13)

    - [Directivas con argumento](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo2/index.html#L35)

    - [Directivas modificadas](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo2/index.html#L19)

### [Capítulo 3. Enlazando clases y estilos](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/estilos.html)

#### Ejemplo: 

- [Demo](https://cristinafsanz.github.io/vuejs-primeros-pasos/libro-vue/capitulo3/index.html)

- [Código](https://github.com/cristinafsanz/vuejs-primeros-pasos/tree/master/libro-vue/capitulo3)

- Elementos del ejemplo:

    - [Enlazar clases](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo3/index.html#L22)

    ![Screenshot con consola JavaScript para ver clase añadida](imagenes/enlazar-clases.png?raw=true)

    - [Enlazar arrays y objetos](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo3/index.html#L18): que contenga las clases box y winner (ésta última sólo si player1.winner es true).
    

## Bloque 2. La creación de componentes

### [Capítulo 4. Creando componentes](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/componentes.html)

- [Demo](https://cristinafsanz.github.io/vuejs-primeros-pasos/libro-vue/capitulo4)

- [Código](https://github.com/cristinafsanz/vuejs-primeros-pasos/tree/master/libro-vue/capitulo4)

- Cómo se ve en el navegador usando la extensión de Chrome de [vue-devtools](https://github.com/vuejs/vue-devtools) después de abrir la consola de JavaScript:

![Screenshot de aplicación en el navegador con extensión de Chrome a la derecha para ver los componentes](imagenes/marketplace.png?raw=true)

- Propiedades de entrada de un componente en [app.js](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/app.js#L51) y en [index.html](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/index.html#L18)

- Componente [emite evento](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/app.js#L45) y [se registra](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/index.html#L21). Se ejecutará la función addToCart cada vez que el componente emita un evento add.

- [Extender el componente course con mixins](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/app.js#L99): Se definen dos componentes nuevos llamados course-js y course-css donde indicamos en el parámetro mixins que queremos que hereden. Y se añaden los datos que se quieren sobreescribir.

- [Componentes locales](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/app.js#L56): course-header, course-content y course-footer.

- [Componente contenedor y etiqueta slot](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/app.js#L111): Dentro de un componente podemos indicar todos los slot que necesitemos. Simplemente les tendremos que indicar un nombre para que VueJS sepa diferenciarlos.

    - [Explicación slots](https://alligator.io/vuejs/component-slots/).

- [Etiqueta component](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo4/index.html#L14): es una etiqueta de VueJS en la que, en combinación con la directiva :is, podemos cargar componentes de manera dinámica.

### [Capítulo 5. El ciclo de vida de un componente](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/ciclo.html)

- Existen 4 estados posibles. El framework nos va a permitir incluir acciones antes y después de que un componente se encuentre en un estado determinado.

    - Creando el componente

        - beforeCreate

        - created

    - Montando el componente

        - beforeMount

        - mounted

    - Actualizando el componente

        - beforeUpdate

        - updated

    - Destruyendo el componente

        - beforeDestroy

        - destroyed

### [Capítulo 6. Definiendo componentes en un único fichero](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/fichero.html)

- Creando un proyecto con vue-cli: empezar un proyecto VueJS a partir de las plantillas establecidas por la comunidad como estándar

```
$ cd capitulo6

$ npm install -g vue-cli

$ vue init webpack my-new-app

```

- Arrancarlo para verlo en local en localhost:8080

```

$ cd my-new-app

$ npm install

$ npm run dev

```

- Generando versión de distribución para verlo con GitHub Pages (cambiando en config/index.js assetsPublicPath: '' y subiendo el directorio dist con 'git add dist --force')

```

$ npm run build

```

- [Demo](https://cristinafsanz.github.io/vuejs-primeros-pasos/libro-vue/capitulo6/my-new-app/dist/#/)

- [Código](https://github.com/cristinafsanz/vuejs-primeros-pasos/tree/master/libro-vue/capitulo6/my-new-app)

## Bloque 3. La gestión de rutas con vue-router

### [Capítulo 7. Introduciendo rutas en nuestra aplicación](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/rutas.html)

- En el capítulo anterior se inicializó el proyecto incluyendo vue-router, por lo que se tiene creado el fichero [router/index.js](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/libro-vue/capitulo6/my-new-app/src/router/index.js). Se importa tanto la librería de vue como la de vue-router. Lo siguiente es extender VueJS por medio de Vue.use(Router).

- En la [demo](https://cristinafsanz.github.io/vuejs-primeros-pasos/demo/dist/#/about) de la charla se enruta a "About". El código se puede ver en [router/index.js](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/demo/src/router/index.js). Se navega a las rutas en [menu.vue](https://github.com/cristinafsanz/vuejs-primeros-pasos/blob/master/demo/src/components/menu.vue#L7).

### [Capítulo 8. Interceptores de navegación](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/interceptores.html)

- Interceptores globales

    - beforeEach: Registrar un interceptor que se ejecutará cada vez que se realice un cambio de ruta.

    - afterEach: Este interceptor se ejecuta después de que todos los interceptores de los componentes se hayan ejecutado.

- Interceptores locales a una ruta

- Interceptores locales a un componente

    - beforeRouteEnter

    - beforeRouteUpdate

    - beforeRouteLeave

### [Capítulo 9. Conceptos avanzados](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/router-avanzado.html)

- Anidar rutas: Incluir un nuevo parámetro en la ruta llamado children.

- Pasar propiedades a un ComponentView.

- Incluir meta-información de una ruta.

- Poner nuestro sistema de rutas en modo History de HTML5: 

    - Un SPA suele contar con un sistema de rutas precedido por una almohadilla. De esta forma, el navegador sabe que no tiene que resolver la ruta contra un servidor, ni hace una recarga de la página, sino que intenta solucionar la ruta a nivel interno de navegador.

    - Gracias a nuestra librería de rutas vue-router se puede configurar para que se comporte de forma nativa a como lo hace el navegador (con mode: 'history'). Lo malo de esto es que ahora todas las rutas harán una petición a nuestro servidor de aplicaciones.

- Cambiar el comportamiento del scroll.

## Bloque 4. La gestión de estados con vuex

### [Capítulo 10. Introducción](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/vuex.html)

### [Capítulo 11. Los estados y los getters](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/getters.html)

### [Capítulo 12. Las mutaciones y acciones](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/mutaciones.html)

### [Capítulo 13. Los módulos](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/m%C3%B3dulos.html)

## Bloque 5. El empaquetado de la aplicación con webpack

### [Capítulo 14. Conceptos básicos](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/webpack-basico.html)

### [Capítulo 15. Configurando nuestra primera build](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/webpack-avanzado.html)

### [Capítulo 16. Caching, Shimming y Splitting](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/webpack-performance.html)

## Bloque 6. Renderizado en servidor con vue-server-renderer

### [Capítulo 17. Introducción a Server-Side rendering](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/ssr.html)

### [Capítulo 18. Configurando Webpack para SSR](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/ssr-webpack.html)

### [Capítulo 19. Adaptando tu proyecto a SSR](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/ssr-proyecto.html)

## Bloque 7. Otras herramientas

### [Capítulo 20. Aplicando universales con Nuxt](https://jdonsan.gitbooks.io/desarrolla-aplicaciones-con-vuejs/content/nuxt.html)

