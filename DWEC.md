# Diccionario Desarrollo Aplicaciones Web en Entorno Cliente

Diccionario de las tecnologías y conceptos del **desarrollo web en entorno cliente** (*frontend*): lo que se ejecuta en el navegador del usuario. Complementa al [diccionario de entorno servidor](DWES.md).

Cada entrada incluye una definición breve y, cuando resulta útil, un ejemplo en HTML, CSS o JavaScript y referencias a otros términos. Las entradas propias de una tecnología llevan una etiqueta al principio: **(HTML)**, **(CSS)**, **(JavaScript)**, **(React)**, **(Vue)**, **(Angular)**, **(Herramienta)**…

## Índice

[A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · [H](#h) · [I](#i) · [J](#j) · [K](#k) · [L](#l) · [M](#m) · [N](#n) · [O](#o) · [P](#p) · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v) · [W](#w) · [X](#x) · [Y](#y) · [Z](#z)

### Índices temáticos

* **HTML**: [HTML](#html) · [Elemento HTML](#elemento-html) · [Atributo](#atributo) · [HTML semántico](#html-semántico) · [Formulario HTML](#formulario-html) · [Accesibilidad](#accesibilidad) · [ARIA](#aria) · [SEO](#seo) · [Viewport](#viewport) · [Canvas](#canvas) · [SVG](#svg) · [Web Components](#web-components)
* **CSS**: [CSS](#css) · [Selector CSS](#selector-css) · [Pseudoclase y pseudoelemento](#pseudoclase-y-pseudoelemento) · [Cascada](#cascada) · [Especificidad](#especificidad) · [Modelo de caja](#modelo-de-caja) · [Unidades CSS](#unidades-css) · [Posicionamiento](#posicionamiento) · [z-index](#z-index) · [Flexbox](#flexbox) · [Grid](#grid) · [Diseño adaptable](#diseño-adaptable) · [Media queries](#media-queries) · [Mobile first](#mobile-first) · [Variables CSS](#variables-css) · [Animaciones CSS](#animaciones-css) · [Fuentes web](#fuentes-web) · [BEM](#bem) · [Preprocesador CSS](#preprocesador-css) · [Sass](#sass) · [PostCSS](#postcss) · [Tailwind CSS](#tailwind-css) · [Bootstrap](#bootstrap) · [CSS-in-JS](#css-in-js)
* **JavaScript**: [JavaScript](#javascript) · [ECMAScript](#ecmascript) · [var, let y const](#var-let-y-const) · [Ámbito](#ámbito) · [Hoisting](#hoisting) · [Clausura](#clausura) · [Función flecha](#función-flecha) · [this](#this) · [Objeto](#objeto) · [Prototipo](#prototipo) · [Clase](#clase) · [Array](#array) · [Desestructuración](#desestructuración) · [Operador de propagación](#operador-de-propagación) · [Encadenamiento opcional](#encadenamiento-opcional) · [Plantillas literales](#plantillas-literales) · [Módulos ES](#módulos-es) · [Modo estricto](#modo-estricto) · [Inmutabilidad](#inmutabilidad) · [Expresión regular](#expresión-regular) · [Promesa](#promesa) · [async / await](#async--await) · [Event loop](#event-loop) · [TypeScript](#typescript)
* **El navegador y sus APIs**: [Navegador](#navegador) · [Motor de renderizado](#motor-de-renderizado) · [API del navegador](#api-del-navegador) · [BOM](#bom) · [window](#window) · [DOM](#dom) · [Nodo](#nodo) · [Evento](#evento) · [Propagación de eventos](#propagación-de-eventos) · [Delegación de eventos](#delegación-de-eventos) · [Fetch API](#fetch-api) · [XMLHttpRequest](#xmlhttprequest) · [localStorage y sessionStorage](#localstorage-y-sessionstorage) · [IndexedDB](#indexeddb) · [Cookies en el cliente](#cookies-en-el-cliente) · [History API](#history-api) · [Geolocation API](#geolocation-api) · [Intersection Observer](#intersection-observer) · [Web Workers](#web-workers) · [Service Worker](#service-worker) · [WebSocket](#websocket-en-el-cliente) · [Drag and Drop](#drag-and-drop) · [Shadow DOM](#shadow-dom) · [WebAssembly](#webassembly)
* **Frameworks y arquitectura**: [Framework frontend](#framework-frontend) · [Componente](#componente) · [Props](#props) · [Estado](#estado) · [Reactividad](#reactividad) · [Virtual DOM](#virtual-dom) · [Gestor de estado](#gestor-de-estado) · [SPA](#spa) · [MPA](#mpa) · [Enrutamiento en el cliente](#enrutamiento-en-el-cliente) · [CSR](#csr) · [SSR](#ssr) · [SSG](#ssg) · [Hidratación](#hidratación) · [PWA](#pwa) · [React](#react) · [JSX](#jsx) · [Hooks](#hooks) · [Next.js](#nextjs) · [Vue.js](#vuejs) · [Nuxt](#nuxt) · [Angular](#angular) · [Svelte](#svelte) · [jQuery](#jquery) · [Axios](#axios)
* **Herramientas**: [DevTools](#devtools) · [npm](#npm-en-el-cliente) · [Bundler](#bundler) · [Vite](#vite) · [webpack](#webpack) · [Babel](#babel) · [Transpilación](#transpilación) · [Polyfill](#polyfill) · [Minificación](#minificación) · [Tree shaking](#tree-shaking) · [HMR](#hmr) · [Linter](#linter) · [ESLint](#eslint) · [Prettier](#prettier) · [Tests en el cliente](#tests-en-el-cliente) · [Storybook](#storybook) · [Lighthouse](#lighthouse) · [Core Web Vitals](#core-web-vitals)

---

## A

### Accesibilidad
*a11y*. Práctica de diseñar y desarrollar webs que puedan usar todas las personas, incluidas las que tienen alguna discapacidad (visual, auditiva, motora, cognitiva) o usan tecnologías de apoyo como lectores de pantalla. Claves: [HTML semántico](#html-semántico), texto alternativo en las imágenes (`alt`), etiquetas en los formularios (`<label>`), navegación completa con teclado, foco visible, contraste de color suficiente y, cuando haga falta, [ARIA](#aria). La referencia es [WCAG](#wcag).

### addEventListener
**(JavaScript)** Método que registra una función que se ejecutará cuando ocurra un [evento](#evento) sobre un elemento. Admite opciones como `once` (se ejecuta una sola vez), `passive` o `capture`. Se elimina con `removeEventListener`.
```js
const boton = document.querySelector('#enviar');
boton.addEventListener('click', (e) => {
  console.log('Pulsado', e.target);
});
```

### Ámbito
**(JavaScript)** *Scope*. Zona del código en la que una variable es accesible. En JavaScript hay ámbito **global**, **de función** y **de bloque** (`{ }`, solo para `let` y `const`). Las funciones recuerdan el ámbito en el que se definieron. Ver [Clausura](#clausura) y [var, let y const](#var-let-y-const).

### Angular
**(Angular)** [Framework frontend](#framework-frontend) completo mantenido por Google y escrito en [TypeScript](#typescript). Incluye de serie [enrutador](#enrutamiento-en-el-cliente), formularios, cliente HTTP, [inyección de dependencias](DWES.md#inyección-de-dependencias) y una CLI (`ng`). Los [componentes](#componente) se definen con el decorador `@Component`, y la reactividad se basa en **signals** y en RxJS. No debe confundirse con **AngularJS**, su antecesor, ya abandonado.
```ts
@Component({
  selector: 'app-contador',
  template: `<button (click)="sumar()">Clics: {{ clics() }}</button>`,
})
export class ContadorComponent {
  clics = signal(0);
  sumar() { this.clics.update(n => n + 1); }
}
```

### Animaciones CSS
**(CSS)** Cambios visuales animados sin JavaScript:
* `transition`: anima suavemente el cambio de una propiedad entre dos estados (por ejemplo, al pasar el ratón).
* `@keyframes` + `animation`: define animaciones de varios pasos que pueden repetirse.

Para que sean fluidas conviene animar `transform` y `opacity`, que no provocan [reflow](#reflow-y-repaint). Hay que respetar la preferencia `prefers-reduced-motion`.
```css
.boton { transition: transform 0.2s ease; }
.boton:hover { transform: scale(1.05); }

@keyframes girar { to { transform: rotate(360deg); } }
.cargando { animation: girar 1s linear infinite; }
```

### API del navegador
*Web API*. Conjunto de interfaces que el [navegador](#navegador) pone a disposición de JavaScript, además del propio lenguaje: el [DOM](#dom), [Fetch](#fetch-api), [almacenamiento](#localstorage-y-sessionstorage), [History](#history-api), [geolocalización](#geolocation-api), [Canvas](#canvas), [Web Workers](#web-workers), notificaciones, portapapeles, cámara y micrófono (`getUserMedia`)… Su documentación de referencia está en **MDN Web Docs**.

### ARIA
**(HTML)** *Accessible Rich Internet Applications*. Conjunto de atributos (`role`, `aria-label`, `aria-expanded`, `aria-hidden`, `aria-live`…) que aportan información de [accesibilidad](#accesibilidad) a los lectores de pantalla cuando el HTML nativo no basta (menús desplegables, pestañas, ventanas modales). Primera regla de ARIA: si existe un elemento HTML nativo con esa semántica (`<button>`, `<nav>`), úsalo en lugar de ARIA.
```html
<button aria-expanded="false" aria-controls="menu">Menú</button>
<ul id="menu" hidden>...</ul>
```

### Array
**(JavaScript)** Lista ordenada de valores. Sus métodos de orden superior son fundamentales en el JavaScript moderno:
* `map()`: transforma cada elemento y devuelve un array nuevo.
* `filter()`: devuelve los elementos que cumplen una condición.
* `reduce()`: acumula los elementos en un único valor.
* `find()`, `some()`, `every()`, `includes()`, `forEach()`, `sort()`, `toSorted()`…
```js
const precios = [12, 5, 30, 8];
const conIva = precios.map(p => p * 1.21);
const baratos = precios.filter(p => p < 10);
const total = precios.reduce((suma, p) => suma + p, 0);
```

### async / await
**(JavaScript)** Sintaxis para trabajar con [promesas](#promesa) como si fuera código secuencial. Una función `async` siempre devuelve una promesa; `await` espera a que una promesa se resuelva sin bloquear la página. Los errores se capturan con `try/catch`.
```js
async function cargarLibros() {
  try {
    const res = await fetch('/api/libros');
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return await res.json();
  } catch (err) {
    console.error('No se pudieron cargar los libros', err);
  }
}
```

### Atributo
**(HTML)** Información adicional que se añade a la etiqueta de apertura de un [elemento HTML](#elemento-html) en forma de `nombre="valor"`: `id`, `class`, `href`, `src`, `alt`, `type`, `disabled`… Los atributos `data-*` permiten guardar datos propios, accesibles desde JavaScript con `elemento.dataset`.
```html
<button class="btn" data-id="42" disabled>Borrar</button>
```

### Axios
**(JavaScript)** Librería para hacer peticiones HTTP desde el navegador (y desde Node.js). Ofrece conversión automática a [JSON](DWES.md#json), interceptores y cancelación. Hoy la [Fetch API](#fetch-api) nativa cubre la mayoría de sus usos.
```js
const { data } = await axios.get('/api/libros', { params: { pagina: 2 } });
```

---

## B

### Babel
**(Herramienta)** [Transpilador](#transpilación) de JavaScript: convierte código moderno (o [JSX](#jsx)) en código compatible con navegadores más antiguos. Muchos proyectos actuales lo han sustituido por herramientas más rápidas como **esbuild** o **SWC**, integradas en [Vite](#vite) y otros [bundlers](#bundler).

### BEM
**(CSS)** *Block, Element, Modifier*. Convención de nombres para clases CSS que hace el código más predecible y evita conflictos: `bloque__elemento--modificador`.
```css
.tarjeta { }
.tarjeta__titulo { }
.tarjeta--destacada { }
```

### BOM
**(JavaScript)** *Browser Object Model*. Conjunto de objetos que representan el [navegador](#navegador) en sí, más allá del documento: [`window`](#window), `navigator` (información del navegador), `location` (URL actual), `history` ([History API](#history-api)), `screen`, además de los temporizadores `setTimeout` y `setInterval` y los diálogos `alert`, `confirm` y `prompt`.

### Bootstrap
**(CSS)** Framework CSS que ofrece una rejilla adaptable y componentes ya diseñados (botones, formularios, barras de navegación, modales…) que se usan añadiendo clases al HTML. Incluye JavaScript para los componentes interactivos.
```html
<button class="btn btn-primary">Guardar</button>
```

### Bundler
**(Herramienta)** *Empaquetador*. Herramienta que toma el código fuente de un proyecto (módulos JavaScript, CSS, imágenes, dependencias de [npm](#npm-en-el-cliente)) y genera los ficheros optimizados que se sirven al navegador, aplicando [transpilación](#transpilación), [minificación](#minificación) y [tree shaking](#tree-shaking). Ejemplos: [Vite](#vite) (usa Rollup y esbuild), [webpack](#webpack), Parcel, esbuild, Rspack.

---

## C

### Caché del navegador
Almacenamiento local en el que el navegador guarda copias de recursos (HTML, CSS, JS, imágenes) para no descargarlos otra vez. Se controla desde el servidor con [cabeceras HTTP](DWES.md#cabeceras-http) como `Cache-Control` y `ETag`. Para forzar que se descargue una versión nueva tras un despliegue, los [bundlers](#bundler) añaden un *hash* al nombre de los ficheros (`app.3f9a1c.js`). Ver también [Service Worker](#service-worker).

### Canvas
**(HTML)** Elemento `<canvas>` que proporciona una superficie para dibujar píxeles con JavaScript (gráficos, juegos, edición de imágenes). Su contexto `2d` dibuja formas y texto; `webgl` y **WebGPU** permiten gráficos 3D acelerados por la GPU. A diferencia de [SVG](#svg), lo dibujado no forma parte del [DOM](#dom).
```js
const ctx = document.querySelector('canvas').getContext('2d');
ctx.fillStyle = 'tomato';
ctx.fillRect(10, 10, 100, 50);
```

### Cascada
**(CSS)** Algoritmo que decide qué regla CSS se aplica cuando varias afectan a la misma propiedad de un elemento. Tiene en cuenta, por este orden: el origen y la importancia (`!important`), las capas (`@layer`), la [especificidad](#especificidad) del selector y el orden de aparición (la última gana). Es la "C" de CSS.

### Clase
**(JavaScript)** Sintaxis (desde ES2015) para definir plantillas de objetos con constructor, métodos, herencia (`extends`), miembros estáticos y campos privados (`#`). Internamente se basa en [prototipos](#prototipo).
```js
class Libro {
  #precio;
  constructor(titulo, precio) {
    this.titulo = titulo;
    this.#precio = precio;
  }
  get precioConIva() { return this.#precio * 1.21; }
}
```

### Clausura
**(JavaScript)** *Closure*. Función que recuerda las variables del [ámbito](#ámbito) en el que se creó, incluso después de que ese ámbito haya terminado. Se usa para encapsular datos privados, en fábricas de funciones y en los [callbacks](#evento).
```js
function crearContador() {
  let cuenta = 0;
  return () => ++cuenta;
}
const siguiente = crearContador();
siguiente(); // 1
siguiente(); // 2
```

### Componente
Pieza reutilizable e independiente de la interfaz que agrupa su estructura, su estilo y su comportamiento (un botón, una tarjeta, un formulario). Recibe datos mediante [props](#props), puede tener [estado](#estado) propio y se compone con otros para formar la aplicación. Es la unidad básica de [React](#react), [Vue](#vuejs), [Angular](#angular), [Svelte](#svelte) y los [Web Components](#web-components).

### Consola
**(Herramienta)** Panel de las [DevTools](#devtools) que muestra mensajes, errores y advertencias de la página y permite ejecutar JavaScript. Desde el código se escribe en ella con `console.log()`, `console.error()`, `console.warn()`, `console.table()`, etc.

### Cookies en el cliente
**(JavaScript)** Las [cookies](DWES.md#cookie) se pueden leer y escribir desde JavaScript con `document.cookie`, salvo las marcadas como `HttpOnly`, que es lo recomendable para las de sesión, porque así no las puede robar un ataque [XSS](DWES.md#xss). Para guardar datos que solo necesita el cliente es mejor usar [localStorage](#localstorage-y-sessionstorage) o [IndexedDB](#indexeddb).

### Core Web Vitals
Métricas de Google que miden la experiencia de usuario de una página y que influyen en el [SEO](#seo):
* **LCP** (*Largest Contentful Paint*): cuánto tarda en mostrarse el elemento principal. Objetivo: ≤ 2,5 s.
* **INP** (*Interaction to Next Paint*): rapidez de respuesta a las interacciones. Objetivo: ≤ 200 ms.
* **CLS** (*Cumulative Layout Shift*): estabilidad visual, es decir, cuánto "salta" el contenido mientras carga. Objetivo: ≤ 0,1.

Se miden con [Lighthouse](#lighthouse) y las [DevTools](#devtools).

### CORS en el cliente
Política de seguridad del navegador que impide a JavaScript leer respuestas de otro origen salvo que el servidor lo autorice. Cuando una petición con [Fetch](#fetch-api) falla con un error de CORS, la solución está en el servidor, no en el cliente. Ver [CORS](DWES.md#cors).

### CSR
*Client-Side Rendering*. Estrategia en la que el servidor envía un HTML casi vacío junto con JavaScript, y es el navegador quien genera toda la interfaz. Es el modelo clásico de las [SPA](#spa). Ofrece mucha interactividad, pero la primera carga es más lenta y el [SEO](#seo) se resiente. Ver [SSR](#ssr) y [SSG](#ssg).

### CSS
**(CSS)** *Cascading Style Sheets*. Lenguaje que define la presentación de los documentos HTML: colores, tipografía, espaciado, disposición, animaciones y adaptación a distintos dispositivos. Se escribe en reglas formadas por un [selector](#selector-css) y un bloque de declaraciones `propiedad: valor`. Se puede incluir con `<link rel="stylesheet">`, con `<style>` o con el atributo `style`. Ver [Cascada](#cascada), [Flexbox](#flexbox), [Grid](#grid).
```css
.tarjeta {
  padding: 1rem;
  border-radius: 8px;
  background: white;
}
```

### CSS-in-JS
**(CSS)** Técnica que escribe los estilos dentro del código JavaScript de los [componentes](#componente), con ámbito local automático. Ejemplos: styled-components, Emotion. Alternativas sin coste en tiempo de ejecución: **CSS Modules**, [Tailwind CSS](#tailwind-css) o las soluciones de estilos de cada framework (estilos con ámbito en [Vue](#vuejs), [Svelte](#svelte) y [Angular](#angular)).

---

## D

### Debounce y throttle
**(JavaScript)** Técnicas para limitar cuántas veces se ejecuta una función ante [eventos](#evento) muy frecuentes (escribir, hacer *scroll*, redimensionar):
* **Debounce**: ejecuta la función solo cuando el evento deja de producirse durante un tiempo (por ejemplo, buscar cuando el usuario deja de escribir).
* **Throttle**: ejecuta la función como máximo una vez cada cierto intervalo.
```js
function debounce(fn, ms) {
  let t;
  return (...args) => {
    clearTimeout(t);
    t = setTimeout(() => fn(...args), ms);
  };
}
buscador.addEventListener('input', debounce(buscar, 300));
```

### Delegación de eventos
**(JavaScript)** Técnica que consiste en escuchar un [evento](#evento) en un elemento contenedor en lugar de en cada hijo, aprovechando la [propagación](#propagación-de-eventos). Funciona también con elementos añadidos después y ahorra memoria.
```js
document.querySelector('#lista').addEventListener('click', (e) => {
  const item = e.target.closest('li');
  if (item) console.log('Elegido', item.dataset.id);
});
```

### Desestructuración
**(JavaScript)** Sintaxis para extraer valores de [arrays](#array) u [objetos](#objeto) en variables, con valores por defecto y renombrado.
```js
const { titulo, autor = 'Anónimo' } = libro;
const [primero, segundo, ...resto] = [1, 2, 3, 4];
function saludar({ nombre }) { return `Hola, ${nombre}`; }
```

### DevTools
**(Herramienta)** Herramientas para desarrolladores integradas en el navegador (F12). Paneles principales: **Elementos** (inspeccionar y editar el [DOM](#dom) y el CSS), [Consola](#consola), **Fuentes** (depurar JavaScript con puntos de ruptura), **Red** (ver todas las peticiones HTTP, sus cabeceras y tiempos), **Aplicación** (almacenamiento, cookies, [Service Workers](#service-worker)), **Rendimiento** y [Lighthouse](#lighthouse). También permiten simular dispositivos móviles.

### Diseño adaptable
**(CSS)** *Responsive design*. Diseño que se adapta a cualquier tamaño de pantalla (móvil, tableta, escritorio) usando rejillas flexibles ([Flexbox](#flexbox), [Grid](#grid)), [unidades](#unidades-css) relativas, imágenes flexibles y [media queries](#media-queries). Requiere la etiqueta [viewport](#viewport). Ver [Mobile first](#mobile-first).

### DOM
**(JavaScript)** *Document Object Model*. Representación en memoria del documento HTML como un árbol de [nodos](#nodo), que JavaScript puede leer y modificar para cambiar la página sin recargarla.
* Seleccionar: `document.querySelector()`, `querySelectorAll()`, `getElementById()`.
* Crear e insertar: `document.createElement()`, `append()`, `prepend()`, `before()`, `remove()`.
* Modificar: `textContent`, `classList.add()/remove()/toggle()`, `setAttribute()`, `style`, `dataset`.

Hay que evitar `innerHTML` con datos del usuario, porque abre la puerta a [XSS](DWES.md#xss).
```js
const li = document.createElement('li');
li.textContent = nuevoLibro.titulo;   // seguro: se inserta como texto
li.classList.add('libro');
document.querySelector('#lista').append(li);
```

### Drag and Drop
**(JavaScript)** [API del navegador](#api-del-navegador) para arrastrar y soltar elementos, mediante el atributo `draggable="true"` y los eventos `dragstart`, `dragover` y `drop`. También permite soltar ficheros del sistema operativo sobre la página.

---

## E

### ECMAScript
Especificación estándar del lenguaje [JavaScript](#javascript), publicada por Ecma International (comité TC39). Desde 2015 (**ES6** o ES2015, que introdujo `let`/`const`, [clases](#clase), [módulos](#módulos-es), [funciones flecha](#función-flecha) y [promesas](#promesa)) sale una versión nueva cada año: ES2016, ES2017 (`async/await`)… Se suele hablar de **ESNext** para las novedades más recientes.

### Elemento HTML
**(HTML)** Componente básico de un documento HTML, formado normalmente por una etiqueta de apertura con [atributos](#atributo), un contenido y una etiqueta de cierre: `<p class="nota">Texto</p>`. Algunos elementos son *vacíos* y no tienen cierre (`<img>`, `<input>`, `<br>`, `<meta>`). Los elementos pueden ser **de bloque** (`<div>`, `<p>`, `<section>`) o **en línea** (`<span>`, `<a>`, `<strong>`).

### Encadenamiento opcional
**(JavaScript)** Operador `?.` que accede a una propiedad o llama a un método solo si el valor anterior no es `null` ni `undefined`; si lo es, devuelve `undefined` en lugar de lanzar un error. Suele combinarse con el operador de **fusión nula** `??`, que da un valor por defecto solo cuando el valor es `null` o `undefined` (a diferencia de `||`, que también lo aplica a `0` y `''`).
```js
const ciudad = usuario?.direccion?.ciudad ?? 'Desconocida';
```

### Enrutamiento en el cliente
Gestión de las URL en una [SPA](#spa): al navegar, JavaScript cambia la URL con la [History API](#history-api) y muestra el [componente](#componente) correspondiente sin pedir una página nueva al servidor. Librerías: **React Router**, **Vue Router**, el enrutador de [Angular](#angular); en [Next.js](#nextjs) y [Nuxt](#nuxt) las rutas se basan en la estructura de carpetas. Ver [Enrutamiento](DWES.md#enrutamiento).

### ESLint
**(Herramienta)** [Linter](#linter) de JavaScript y [TypeScript](#typescript) más usado. Se configura en `eslint.config.js` y admite reglas y *plugins* para cada framework.

### Especificidad
**(CSS)** Peso de un [selector](#selector-css) que determina qué regla gana en la [cascada](#cascada) cuando varias afectan al mismo elemento. Se calcula como (id, clase, tipo): los selectores de **id** pesan más que los de **clase**, atributo y [pseudoclase](#pseudoclase-y-pseudoelemento), y estos más que los de **tipo** (etiqueta) y pseudoelemento. Los estilos en línea superan a todos, y `!important` lo altera todo (conviene evitarlo).
```css
p { }            /* (0,0,1) */
.nota { }        /* (0,1,0) */
#aviso .nota { } /* (1,1,0) */
```

### Estado
Datos que cambian durante la vida de un [componente](#componente) o de la aplicación (el contenido de un formulario, si un menú está abierto, el usuario conectado…). En los frameworks, cuando el estado cambia la interfaz se actualiza automáticamente. Puede ser **local** (de un componente) o **global** (compartido; ver [Gestor de estado](#gestor-de-estado)). Ver [Reactividad](#reactividad).

### Event loop
**(JavaScript)** *Bucle de eventos*. Mecanismo que permite a JavaScript, que tiene un único hilo, gestionar operaciones [asíncronas](#promesa). El código síncrono se ejecuta en la **pila de llamadas**. Cuando esta queda vacía, el bucle ejecuta primero las **microtareas** (promesas) y después las **tareas** (temporizadores, eventos), y entre medias el navegador pinta la página. Un cálculo largo bloquea el hilo y congela la interfaz; para eso existen los [Web Workers](#web-workers).

### Evento
**(JavaScript)** Señal de que algo ha ocurrido en la página: una acción del usuario (`click`, `input`, `submit`, `keydown`, `scroll`) o del navegador (`DOMContentLoaded`, `load`, `resize`). Se gestionan con [addEventListener](#addeventlistener), y la función recibe un objeto evento con información como `target`, `key` o `clientX`. `preventDefault()` anula la acción por defecto (por ejemplo, el envío del formulario) y `stopPropagation()` detiene la [propagación](#propagación-de-eventos).
```js
formulario.addEventListener('submit', async (e) => {
  e.preventDefault();
  const datos = new FormData(formulario);
  await fetch('/api/contacto', { method: 'POST', body: datos });
});
```

### Expresión regular
**(JavaScript)** Patrón para buscar, validar o reemplazar texto. En JavaScript se escribe entre barras (`/patrón/flags`) y se usa con `test()`, `match()`, `replace()` o `split()`. En HTML, el atributo `pattern` de los `<input>` también admite expresiones regulares.
```js
const cp = /^\d{5}$/;
cp.test('46001'); // true
```

---

## F

### Fetch API
**(JavaScript)** API nativa del navegador para hacer [peticiones HTTP](DWES.md#petición-http) que devuelve [promesas](#promesa). Es la forma moderna de hacer [AJAX](DWES.md#ajax). Ojo: `fetch` solo rechaza la promesa si hay un error de red; las respuestas 4xx y 5xx hay que comprobarlas con `res.ok`.
```js
const res = await fetch('/api/libros', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ titulo: 'El Quijote' }),
});
if (!res.ok) throw new Error(`Error ${res.status}`);
const libro = await res.json();
```

### Flexbox
**(CSS)** Modelo de disposición **unidimensional** (en fila o en columna) para alinear y repartir el espacio entre elementos. El contenedor usa `display: flex`, y sus propiedades principales son `flex-direction`, `justify-content` (eje principal), `align-items` (eje secundario), `flex-wrap` y `gap`. Los hijos se controlan con `flex: 1`, `order` o `align-self`.
```css
.barra {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}
```

### Formulario HTML
**(HTML)** Elemento `<form>` que agrupa controles de entrada (`<input>`, `<select>`, `<textarea>`, `<button>`) para enviar datos al servidor (atributos `action` y `method`) o procesarlos con JavaScript. HTML incluye validación nativa (`required`, `type="email"`, `min`, `max`, `pattern`), pero la [validación en el servidor](DWES.md#validación) sigue siendo obligatoria. Desde JavaScript, `FormData` recoge todos los valores del formulario.
```html
<form action="/registro" method="post">
  <label for="email">Correo</label>
  <input id="email" name="email" type="email" required>
  <button>Registrarse</button>
</form>
```

### Framework frontend
Conjunto de herramientas y convenciones para construir interfaces basadas en [componentes](#componente) con [estado](#estado) y [reactividad](#reactividad). Los más usados son [React](#react) (técnicamente una librería), [Vue.js](#vuejs), [Angular](#angular) y [Svelte](#svelte). Los **metaframeworks** como [Next.js](#nextjs), [Nuxt](#nuxt), SvelteKit o Astro añaden enrutamiento, [SSR](#ssr) y [SSG](#ssg).

### Fuentes web
**(CSS)** Tipografías que se descargan con la página en lugar de depender de las instaladas en el equipo. Se declaran con `@font-face` (el formato recomendado es **WOFF2**) o se cargan desde servicios como Google Fonts. La propiedad `font-display: swap` muestra el texto con una fuente de reserva mientras se descarga.

### Función flecha
**(JavaScript)** *Arrow function*. Sintaxis abreviada para escribir funciones: `(a, b) => a + b`. No tiene su propio [`this`](#this) (hereda el del contexto en el que se define), ni `arguments`, y no puede usarse como constructor. Es ideal para *callbacks*.
```js
const doble = n => n * 2;
const sumar = (a, b) => a + b;
const crear = () => ({ id: 1 }); // devolver un objeto: entre paréntesis
```

---

## G

### Geolocation API
**(JavaScript)** [API del navegador](#api-del-navegador) que obtiene la ubicación del dispositivo, siempre con el permiso previo del usuario y solo en contextos seguros ([HTTPS](DWES.md#https)).
```js
navigator.geolocation.getCurrentPosition(
  ({ coords }) => console.log(coords.latitude, coords.longitude),
  (err) => console.error(err.message),
);
```

### Gestor de estado
Librería que guarda el [estado](#estado) global de la aplicación en un único almacén (*store*) accesible desde cualquier [componente](#componente), evitando tener que pasar [props](#props) a través de muchos niveles (*prop drilling*). Ejemplos: **Redux Toolkit** y **Zustand** (React), **Pinia** (Vue), **NgRx** y los *signals* (Angular). Para datos que vienen del servidor se usan librerías específicas como **TanStack Query**.

### Grid
**(CSS)** *CSS Grid Layout*. Modelo de disposición **bidimensional** (filas y columnas a la vez), ideal para la estructura general de una página o para galerías. El contenedor usa `display: grid` y define pistas con `grid-template-columns` y `grid-template-rows`; la unidad `fr` reparte el espacio libre.
```css
.galeria {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}
```

---

## H

### Hidratación
*Hydration*. Proceso por el que, tras recibir un HTML generado en el servidor ([SSR](#ssr) o [SSG](#ssg)), el JavaScript del framework se "engancha" a ese HTML ya existente, añadiendo los eventos y el estado para volverlo interactivo. Técnicas para reducir su coste: **hidratación parcial**, **islas** (Astro) y **componentes de servidor** (React Server Components).

### History API
**(JavaScript)** [API del navegador](#api-del-navegador) para manipular el historial y la URL sin recargar la página: `history.pushState()` y `history.replaceState()` cambian la URL, y el evento `popstate` avisa cuando el usuario pulsa atrás o adelante. Es la base del [enrutamiento en el cliente](#enrutamiento-en-el-cliente).

### HMR
**(Herramienta)** *Hot Module Replacement*. Función del servidor de desarrollo ([Vite](#vite), [webpack](#webpack)) que sustituye en caliente los módulos modificados en el navegador, sin recargar la página y conservando el [estado](#estado) de la aplicación.

### Hoisting
**(JavaScript)** *Elevación*. Comportamiento por el que las declaraciones se procesan antes de ejecutar el código de su [ámbito](#ámbito). Las declaraciones de función (`function f() {}`) pueden usarse antes de escribirse. Las variables `var` se elevan con valor `undefined`. `let`, `const` y las clases también se elevan, pero no pueden usarse antes de su declaración (la llamada *zona muerta temporal*).

### Hooks
**(React)** Funciones que permiten a los componentes de función de [React](#react) usar [estado](#estado) y otras capacidades. Empiezan por `use` y solo pueden llamarse en el nivel superior del componente:
* `useState`: estado local.
* `useEffect`: efectos secundarios (peticiones, suscripciones) tras el renderizado.
* `useContext`: leer un contexto compartido.
* `useRef`: referencia mutable o acceso a un elemento del [DOM](#dom).
* `useMemo` y `useCallback`: memorizar valores y funciones.
* Se pueden crear hooks propios (`useFetch`, `useLocalStorage`…).

En [Vue](#vuejs), el equivalente son los *composables* de la Composition API.

### HTML
**(HTML)** *HyperText Markup Language*. Lenguaje de marcado que define la **estructura y el contenido** de las páginas web mediante [elementos](#elemento-html). La versión actual es el *HTML Living Standard* (antes HTML5), mantenido por el WHATWG.
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Mi página</title>
  <link rel="stylesheet" href="estilos.css">
  <script src="app.js" type="module"></script>
</head>
<body>
  <h1>Hola, mundo</h1>
</body>
</html>
```

### HTML semántico
**(HTML)** Uso de los [elementos](#elemento-html) según su significado y no según su aspecto: `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`, `<button>` para acciones, `<a>` para navegar, `<h1>`…`<h6>` en orden jerárquico… Mejora la [accesibilidad](#accesibilidad), el [SEO](#seo) y el mantenimiento del código, frente a usar `<div>` para todo.

---

## I

### IIFE
**(JavaScript)** *Immediately Invoked Function Expression*. Función que se define y se ejecuta en el mismo momento, para crear un [ámbito](#ámbito) privado. Era muy habitual antes de que existieran los [módulos ES](#módulos-es).
```js
(() => {
  const privado = 42;
})();
```

### IndexedDB
**(JavaScript)** Base de datos [NoSQL](DWES.md#nosql) integrada en el navegador, que guarda objetos estructurados (incluso ficheros) indexados por clave, con transacciones y capacidad para grandes volúmenes de datos. Su API es asíncrona y algo engorrosa, por lo que se suele usar a través de librerías como **idb** o **Dexie**. Es la base de las aplicaciones que funcionan sin conexión ([PWA](#pwa)).

### Inmutabilidad
Principio por el que los datos no se modifican, sino que se crea una copia nueva con los cambios. Es clave en [React](#react) y en los [gestores de estado](#gestor-de-estado) para detectar qué ha cambiado. En JavaScript se trabaja con el [operador de propagación](#operador-de-propagación), los métodos que no mutan (`map`, `filter`, `toSorted`, `with`), `structuredClone()` o `Object.freeze()`.
```js
const nuevoCarrito = [...carrito, producto];          // no modifica carrito
const usuarioEditado = { ...usuario, nombre: 'Ana' }; // no modifica usuario
```

### Intersection Observer
**(JavaScript)** [API del navegador](#api-del-navegador) que avisa cuando un elemento entra o sale de la zona visible de la pantalla. Se usa para la [carga diferida](#lazy-loading), el *scroll* infinito o las animaciones al hacer *scroll*. APIs similares: `ResizeObserver` (cambios de tamaño) y `MutationObserver` (cambios en el [DOM](#dom)).

---

## J

### JavaScript
**(JavaScript)** Lenguaje de programación de la web, el único que ejecutan los navegadores de forma nativa (junto con [WebAssembly](#webassembly)). Es interpretado (con compilación JIT), de tipado dinámico y multiparadigma, con funciones de primera clase, [prototipos](#prototipo) y un modelo [asíncrono](#event-loop). Está estandarizado como [ECMAScript](#ecmascript). En el cliente manipula el [DOM](#dom), responde a [eventos](#evento) y se comunica con el servidor; también se ejecuta en el servidor con [Node.js](DWES.md#nodejs).

### jQuery
**(JavaScript)** Librería que durante años simplificó la manipulación del [DOM](#dom), los [eventos](#evento), las animaciones y [AJAX](DWES.md#ajax), además de ocultar las diferencias entre navegadores (`$('.boton').on('click', ...)`). Hoy la mayoría de sus funciones existen de forma nativa (`querySelector`, `fetch`, `classList`), pero sigue presente en mucho código heredado y en WordPress.

### JSON en el cliente
**(JavaScript)** En el navegador, el formato [JSON](DWES.md#json) se convierte con `JSON.stringify()` (de objeto a texto) y `JSON.parse()` (de texto a objeto). `response.json()` de la [Fetch API](#fetch-api) hace el *parseo* directamente.

### JSX
**(React)** Extensión de sintaxis de JavaScript que permite escribir marcado parecido a HTML dentro del código. Se [transpila](#transpilación) a llamadas a funciones. Diferencias con HTML: `className` en lugar de `class`, `htmlFor` en lugar de `for`, atributos en *camelCase* (`onClick`), expresiones entre llaves `{ }` y un único elemento raíz (o un fragmento `<>...</>`).
```jsx
function ListaLibros({ libros }) {
  return (
    <ul className="lista">
      {libros.map(l => <li key={l.id}>{l.titulo}</li>)}
    </ul>
  );
}
```

---

## K

### key
**(React)** Atributo especial que identifica de forma única cada elemento de una lista renderizada, para que [React](#react) (o [Vue](#vuejs), con `:key`) sepa qué elementos han cambiado, se han añadido o se han eliminado. Debe ser estable (por ejemplo, el `id` del registro) y no el índice del array si la lista puede reordenarse. Ver el ejemplo de [JSX](#jsx).

---

## L

### Lazy loading
*Carga diferida*. Técnica que retrasa la carga de un recurso hasta que se necesita. En imágenes e *iframes* basta con el atributo `loading="lazy"`. En JavaScript se aplica con `import()` dinámico y la **división de código** (*code splitting*), para descargar cada parte de la aplicación solo al visitarla.
```html
<img src="foto.jpg" alt="Paisaje" loading="lazy" width="800" height="600">
```

### Lighthouse
**(Herramienta)** Herramienta de Google, integrada en las [DevTools](#devtools) de Chrome, que audita una página y la puntúa en rendimiento ([Core Web Vitals](#core-web-vitals)), [accesibilidad](#accesibilidad), buenas prácticas y [SEO](#seo), con recomendaciones concretas de mejora.

### Linter
**(Herramienta)** Herramienta de análisis estático que detecta errores, malas prácticas y problemas de estilo en el código sin ejecutarlo. Ejemplos: [ESLint](#eslint) (JavaScript), **Stylelint** (CSS) y **Biome** (linter y formateador en uno). Ver [Prettier](#prettier).

### localStorage y sessionStorage
**(JavaScript)** *Web Storage*. Almacenamiento clave-valor de cadenas de texto en el navegador, de unos 5 MB por origen:
* `localStorage`: persiste aunque se cierre el navegador.
* `sessionStorage`: se borra al cerrar la pestaña.

Es síncrono y solo guarda texto, así que los objetos se guardan con [JSON](#json-en-el-cliente). No se debe guardar en él información sensible (como [tokens](DWES.md#token)), porque cualquier script de la página puede leerlo.
```js
localStorage.setItem('carrito', JSON.stringify(carrito));
const carrito = JSON.parse(localStorage.getItem('carrito') ?? '[]');
```

---

## M

### Media queries
**(CSS)** Reglas `@media` que aplican estilos solo cuando se cumplen ciertas condiciones del dispositivo: anchura de la pantalla, orientación, preferencia de tema oscuro (`prefers-color-scheme`), de movimiento reducido (`prefers-reduced-motion`) o tipo de medio (`print`). Son la base del [diseño adaptable](#diseño-adaptable). Las **container queries** (`@container`) aplican estilos según el tamaño del contenedor en lugar del de la pantalla.
```css
@media (min-width: 768px) {
  .menu { display: flex; }
}
@media (prefers-color-scheme: dark) {
  body { background: #111; color: #eee; }
}
```

### Mejora progresiva
*Progressive enhancement*. Estrategia que consiste en construir primero una versión básica que funcione en cualquier navegador (HTML con contenido y formularios funcionales) y añadir encima capas de CSS y JavaScript para los navegadores que las soporten. Su enfoque opuesto es la *degradación elegante* (*graceful degradation*).

### Minificación
**(Herramienta)** Proceso que reduce el tamaño del código (JavaScript, CSS, HTML) eliminando espacios, comentarios y saltos de línea y acortando nombres de variables, sin cambiar su comportamiento. Lo hacen los [bundlers](#bundler) al generar la versión de producción. Para poder depurar el código minificado se generan **source maps**.

### Mobile first
**(CSS)** Enfoque de [diseño adaptable](#diseño-adaptable) que empieza por los estilos para pantallas pequeñas y añade mejoras para pantallas más grandes con [media queries](#media-queries) `min-width`. Obliga a priorizar el contenido y suele dar CSS más ligero en los móviles.

### Modelo de caja
**(CSS)** *Box model*. Todo elemento se representa como una caja formada, de dentro hacia fuera, por **contenido**, **relleno** (`padding`), **borde** (`border`) y **margen** (`margin`). Con `box-sizing: border-box`, la anchura (`width`) incluye el relleno y el borde, lo que simplifica mucho los cálculos.
```css
*, *::before, *::after { box-sizing: border-box; }
```

### Modo estricto
**(JavaScript)** Variante más segura de JavaScript que se activa con `'use strict'` y convierte errores silenciosos en excepciones (por ejemplo, asignar a una variable no declarada). Los [módulos ES](#módulos-es) y las [clases](#clase) están siempre en modo estricto.

### Módulos ES
**(JavaScript)** Sistema estándar de módulos de JavaScript: cada fichero tiene su propio [ámbito](#ámbito) y comparte código con `export` e `import`. En el navegador se cargan con `<script type="module">`. El `import()` dinámico carga módulos bajo demanda. Ver [CommonJS / ES Modules](DWES.md#commonjs--es-modules).
```js
// utilidades.js
export const iva = 0.21;
export default function formatearPrecio(p) { return `${p.toFixed(2)} €`; }

// app.js
import formatearPrecio, { iva } from './utilidades.js';
```

### Motor de renderizado
Componente del [navegador](#navegador) que convierte HTML y CSS en píxeles: construye el [DOM](#dom) y el CSSOM, calcula la disposición (*layout*), pinta y compone las capas. Los principales son **Blink** (Chrome, Edge, Opera), **WebKit** (Safari) y **Gecko** (Firefox). Los motores de JavaScript son independientes: V8 (Chrome), JavaScriptCore (Safari) y SpiderMonkey (Firefox). Ver [Reflow y repaint](#reflow-y-repaint).

### MPA
*Multi-Page Application*. Aplicación web tradicional en la que cada navegación pide una página HTML nueva al servidor. Es sencilla, buena para el [SEO](#seo) y funciona sin JavaScript. Opuesta a [SPA](#spa).

---

## N

### Navegador
Aplicación que solicita recursos web mediante [HTTP](DWES.md#http), interpreta HTML, CSS y JavaScript y muestra el resultado al usuario. Ejemplos: Chrome, Firefox, Safari, Edge. Es el entorno de ejecución del desarrollo en cliente, e incluye un [motor de renderizado](#motor-de-renderizado), un motor de JavaScript, numerosas [APIs](#api-del-navegador) y las [DevTools](#devtools). Para saber qué funciones soporta cada navegador se consulta **caniuse.com**.

### Next.js
**(React)** Metaframework de [React](#react) que añade enrutamiento basado en ficheros, [SSR](#ssr), [SSG](#ssg), componentes de servidor, rutas de API y optimización de imágenes. Permite construir aplicaciones *full stack*.

### Nodo
**(JavaScript)** Cada uno de los elementos del árbol del [DOM](#dom). Hay varios tipos: nodos de elemento (etiquetas), de texto, de comentario y el nodo documento. Se recorren con propiedades como `parentElement`, `children`, `firstElementChild` o `nextElementSibling`, y con `closest()`.

### npm en el cliente
**(Herramienta)** Aunque [npm](DWES.md#npm) nació con [Node.js](DWES.md#nodejs), es también el gestor de paquetes del desarrollo frontend: con él se instalan los frameworks, los [bundlers](#bundler) y las demás herramientas. Los paquetes se combinan en el navegador gracias al [bundler](#bundler). Ver [package.json](DWES.md#packagejson).

### Nuxt
**(Vue)** Metaframework de [Vue.js](#vuejs), equivalente a [Next.js](#nextjs): enrutamiento basado en ficheros, [SSR](#ssr), [SSG](#ssg), importaciones automáticas y rutas de servidor.

---

## O

### Objeto
**(JavaScript)** Colección de pares clave-valor (propiedades), donde los valores pueden ser funciones (métodos). Se crean con literales `{ }`, con [clases](#clase) o con `Object.create()`. Métodos útiles: `Object.keys()`, `Object.values()`, `Object.entries()`, `Object.assign()` y `structuredClone()` para copias profundas. Para colecciones con claves de cualquier tipo existen `Map` y `Set`.
```js
const libro = { titulo: 'El Quijote', anyo: 1605, resumen() { return this.titulo; } };
for (const [clave, valor] of Object.entries(libro)) console.log(clave, valor);
```

### Operador de propagación
**(JavaScript)** *Spread* (`...`). Expande los elementos de un iterable o las propiedades de un objeto. Se usa para copiar, combinar o pasar argumentos. En la posición contraria (parámetros, [desestructuración](#desestructuración)) actúa como **parámetro rest**, agrupando los valores restantes.
```js
const todos = [...nacionales, ...extranjeros];
const config = { ...porDefecto, ...opcionesUsuario };
Math.max(...numeros);
function sumar(...valores) { return valores.reduce((a, b) => a + b, 0); }
```

---

## P

### Plantillas literales
**(JavaScript)** *Template literals*. Cadenas delimitadas por comillas invertidas (`` ` ``) que permiten interpolar expresiones con `${ }` y escribir varias líneas. No escapan el contenido, así que no deben usarse para construir HTML con datos del usuario (ver [XSS](DWES.md#xss)).
```js
const mensaje = `Hola, ${usuario.nombre}. Tienes ${avisos.length} avisos.`;
```

### Polyfill
**(Herramienta)** Fragmento de código que implementa una función moderna del navegador o del lenguaje en navegadores que todavía no la soportan. A diferencia de la [transpilación](#transpilación), que transforma la sintaxis, el polyfill añade APIs que faltan (por ejemplo, `Array.prototype.at`). Librería de referencia: **core-js**.

### Posicionamiento
**(CSS)** Propiedad `position`, que controla cómo se coloca un elemento:
* `static`: posición normal en el flujo (valor por defecto).
* `relative`: se desplaza respecto a su posición normal y sirve de referencia a sus hijos absolutos.
* `absolute`: sale del flujo y se coloca respecto al antepasado posicionado más cercano.
* `fixed`: se fija respecto a la ventana (no se mueve al hacer *scroll*).
* `sticky`: se comporta como `relative` hasta llegar a un umbral de *scroll* y entonces se queda fijo.

Se usa con `top`, `right`, `bottom`, `left` (o `inset`) y [z-index](#z-index).

### PostCSS
**(Herramienta)** Herramienta que transforma CSS mediante *plugins*: añadir prefijos de navegador automáticamente (**Autoprefixer**), usar sintaxis futura, minificar… [Tailwind CSS](#tailwind-css) se ha distribuido tradicionalmente como *plugin* de PostCSS.

### Preprocesador CSS
**(CSS)** Lenguaje que extiende CSS con variables, anidamiento, *mixins*, funciones y módulos, y que se compila a CSS normal. El más usado es [Sass](#sass); otros son Less y Stylus. Muchas de sus funciones ya existen en CSS nativo ([variables CSS](#variables-css), anidamiento, `@layer`).

### Prettier
**(Herramienta)** Formateador automático de código (JavaScript, TypeScript, CSS, HTML, JSON, Markdown…) que aplica un estilo uniforme sin discusiones. Se suele combinar con un [linter](#linter).

### Promesa
**(JavaScript)** *Promise*. Objeto que representa el resultado futuro de una operación asíncrona: está *pendiente*, *cumplida* o *rechazada*. Se consume con `.then()`, `.catch()` y `.finally()`, o con [async / await](#async--await). Para combinarlas: `Promise.all()` (todas), `Promise.allSettled()` (todas, aunque alguna falle), `Promise.race()` y `Promise.any()`.
```js
const [usuario, pedidos] = await Promise.all([
  fetch('/api/usuario').then(r => r.json()),
  fetch('/api/pedidos').then(r => r.json()),
]);
```

### Propagación de eventos
**(JavaScript)** Recorrido que hace un [evento](#evento) por el árbol del [DOM](#dom). Primero viaja desde la raíz hasta el elemento objetivo (fase de **captura**) y después sube desde el objetivo hasta la raíz (fase de **burbujeo** o *bubbling*). Por defecto los manejadores se ejecutan en la fase de burbujeo. `stopPropagation()` la detiene. Permite la [delegación de eventos](#delegación-de-eventos).

### Props
Datos que un [componente](#componente) padre pasa a un componente hijo, igual que los atributos de una etiqueta HTML. Son de solo lectura para el hijo: si este necesita comunicar algo al padre, lo hace llamando a una función recibida como prop (React) o emitiendo un evento (Vue y Angular). En Vue se declaran con `defineProps` y en Angular con `input()`.
```jsx
<Tarjeta titulo="El Quijote" precio={12.5} onComprar={añadirAlCarrito} />
```

### Prototipo
**(JavaScript)** Mecanismo de herencia de JavaScript: cada objeto tiene un enlace interno a otro objeto, su prototipo, del que hereda propiedades y métodos. Cuando una propiedad no se encuentra en el objeto, se busca en la **cadena de prototipos**. Las [clases](#clase) son una sintaxis más cómoda sobre este mecanismo.

### Pseudoclase y pseudoelemento
**(CSS)**
* **Pseudoclase** (`:`): selecciona elementos según su estado o posición: `:hover`, `:focus`, `:focus-visible`, `:checked`, `:disabled`, `:invalid`, `:first-child`, `:nth-child(2n)`, `:not()`, `:has()`.
* **Pseudoelemento** (`::`): selecciona o crea una parte de un elemento: `::before`, `::after`, `::placeholder`, `::first-line`, `::selection`.
```css
a:hover { text-decoration: underline; }
.requerido::after { content: ' *'; color: red; }
form:has(input:invalid) button { opacity: 0.5; }
```

### PWA
*Progressive Web App*. Aplicación web que ofrece una experiencia similar a una aplicación nativa: se puede instalar en el dispositivo, funciona sin conexión y puede recibir notificaciones *push*. Requiere [HTTPS](DWES.md#https), un **manifiesto** (`manifest.webmanifest`, con nombre, iconos y colores) y un [Service Worker](#service-worker).

---

## R

### React
**(React)** Librería de JavaScript creada por Meta para construir interfaces de usuario mediante [componentes](#componente) de función escritos en [JSX](#jsx). Se basa en el flujo de datos unidireccional, el [estado](#estado) gestionado con [hooks](#hooks) y la reconciliación (comparación con un [Virtual DOM](#virtual-dom)). Su ecosistema incluye React Router, [Next.js](#nextjs) y React Native (para aplicaciones móviles).
```jsx
import { useState } from 'react';

export function Contador() {
  const [clics, setClics] = useState(0);
  return <button onClick={() => setClics(clics + 1)}>Clics: {clics}</button>;
}
```

### Reactividad
Capacidad de un framework para detectar los cambios en el [estado](#estado) y actualizar automáticamente las partes de la interfaz que dependen de él. Cada framework la implementa de una forma: [React](#react) vuelve a ejecutar el componente y compara el resultado; [Vue](#vuejs) usa *proxies* (`ref`, `reactive`); [Angular](#angular), [Svelte](#svelte) 5 y SolidJS usan **signals**, que actualizan solo lo que cambia.

### Reflow y repaint
Operaciones que realiza el [motor de renderizado](#motor-de-renderizado) cuando cambia la página:
* **Reflow** (o *layout*): recalcula la posición y el tamaño de los elementos. Es costoso; lo provocan los cambios de tamaño, de contenido o de propiedades como `width`, `top` o `margin`.
* **Repaint**: vuelve a pintar los píxeles sin recalcular la disposición (por ejemplo, al cambiar `color` o `background`).

Animar `transform` y `opacity` evita ambos, porque se resuelven en la fase de composición.

---

## S

### Sass
**(CSS)** [Preprocesador CSS](#preprocesador-css) más popular. Su sintaxis SCSS (ficheros `.scss`) es CSS con extras: variables (`$color`), anidamiento, *mixins* (`@mixin`/`@include`), funciones y módulos (`@use`).
```scss
$primario: #0055aa;

.boton {
  background: $primario;
  &:hover { background: darken($primario, 10%); }
}
```

### Selector CSS
**(CSS)** Patrón que indica a qué elementos se aplica una regla CSS:
* De tipo: `p`. De clase: `.nota`. De id: `#menu`. Universal: `*`.
* De atributo: `[type="email"]`, `[href^="https"]`.
* Combinadores: descendiente (`nav a`), hijo directo (`ul > li`), hermano adyacente (`h2 + p`), hermanos siguientes (`h2 ~ p`).
* [Pseudoclases y pseudoelementos](#pseudoclase-y-pseudoelemento).

Los mismos selectores se usan en JavaScript con `querySelector()`. Ver [Especificidad](#especificidad).

### SEO
*Search Engine Optimization*. Conjunto de técnicas para mejorar la posición de una web en los buscadores. En la parte técnica influyen el [HTML semántico](#html-semántico), las etiquetas `<title>` y `<meta name="description">`, las URL legibles ([slugs](DWES.md#slug)), el rendimiento ([Core Web Vitals](#core-web-vitals)), la adaptación a móviles, los datos estructurados (Schema.org), el `sitemap.xml` y el `robots.txt`, y que el contenido esté en el HTML inicial ([SSR](#ssr)/[SSG](#ssg)) en lugar de generarse solo en el cliente.

### Service Worker
**(JavaScript)** Script que el navegador ejecuta en segundo plano, separado de la página, y que actúa como un [proxy](DWES.md#proxy-inverso) entre la aplicación y la red: intercepta las peticiones y puede responderlas desde una caché (la *Cache API*). Permite el funcionamiento sin conexión, las notificaciones *push* y la sincronización en segundo plano. Es una pieza fundamental de las [PWA](#pwa). Solo funciona con [HTTPS](DWES.md#https) (o en `localhost`). Librería de ayuda: **Workbox**.
```js
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/sw.js');
}
```

### Shadow DOM
**(JavaScript)** Árbol [DOM](#dom) encapsulado y oculto que se adjunta a un elemento. Sus estilos y su estructura quedan aislados del resto de la página, de modo que el CSS externo no le afecta y el suyo no sale fuera. Lo usan los [Web Components](#web-components) y algunos elementos nativos, como `<video>` o `<input type="date">`.

### SPA
*Single-Page Application*. Aplicación que carga una única página HTML y, a partir de ahí, actualiza su contenido con JavaScript, pidiendo solo datos ([JSON](DWES.md#json)) a una [API](DWES.md#api) y gestionando la navegación con el [enrutamiento en el cliente](#enrutamiento-en-el-cliente). Ofrece una experiencia fluida, pero la carga inicial es mayor y el [SEO](#seo) es más difícil. Opuesta a [MPA](#mpa). Ver [CSR](#csr).

### SSG
*Static Site Generation*. Estrategia en la que las páginas HTML se generan una sola vez, al compilar el proyecto, y se sirven como ficheros estáticos (normalmente desde un [CDN](DWES.md#cdn)). Es muy rápida y barata, e ideal para blogs, documentación o webs corporativas. Herramientas: Astro, [Next.js](#nextjs), [Nuxt](#nuxt), Hugo, Jekyll, Eleventy. La regeneración incremental (ISR) permite actualizar páginas sin recompilar todo el sitio.

### SSR
*Server-Side Rendering*. El HTML de cada página se genera en el servidor en cada petición y llega completo al navegador, donde luego se [hidrata](#hidratación). Mejora el [SEO](#seo) y el tiempo hasta ver el contenido. Ver [SSR (servidor)](DWES.md#ssr), [CSR](#csr) y [SSG](#ssg).

### Storybook
**(Herramienta)** Entorno para desarrollar, documentar y probar [componentes](#componente) de forma aislada, fuera de la aplicación, mostrando cada uno en sus distintos estados (*stories*). Se usa mucho para construir sistemas de diseño.

### Svelte
**(Svelte)** [Framework frontend](#framework-frontend) que funciona como un compilador: convierte los componentes (ficheros `.svelte`) en JavaScript optimizado que actualiza el [DOM](#dom) directamente, sin [Virtual DOM](#virtual-dom). Svelte 5 usa *runes* (`$state`, `$derived`, `$props`) para la [reactividad](#reactividad). Su metaframework es **SvelteKit**.
```svelte
<script>
  let clics = $state(0);
</script>

<button onclick={() => clics++}>Clics: {clics}</button>
```

### SVG
**(HTML)** *Scalable Vector Graphics*. Formato de gráficos vectoriales basado en [XML](DWES.md#xml): las imágenes se describen con formas (`<circle>`, `<rect>`, `<path>`), por lo que se ven nítidas a cualquier tamaño. Se puede incrustar en el HTML, darle estilos con CSS y manipularlo con JavaScript, porque forma parte del [DOM](#dom). Es ideal para iconos, logotipos, gráficos e ilustraciones.

---

## T

### Tailwind CSS
**(CSS)** Framework CSS *utility-first*: en lugar de componentes ya diseñados, ofrece clases pequeñas de un solo propósito que se combinan directamente en el HTML. Al compilar, solo incluye en el CSS final las clases que se usan.
```html
<button class="px-4 py-2 rounded-lg bg-blue-600 text-white hover:bg-blue-700">
  Guardar
</button>
```

### Tests en el cliente
**(Herramienta)** Pruebas automatizadas del código frontend:
* **Unitarias y de componentes**: **Vitest** o **Jest**, junto con **Testing Library**, que prueba los componentes como lo haría el usuario (buscar por texto o por rol y hacer clic).
* **De extremo a extremo** (*end-to-end*): **Playwright** o **Cypress**, que controlan un navegador real y recorren la aplicación completa.
* **De regresión visual**: comparan capturas de pantalla entre versiones.

Ver [Test](DWES.md#test).

### this
**(JavaScript)** Palabra clave que hace referencia al objeto en cuyo contexto se ejecuta una función, y que depende de **cómo se llame** la función: en un método, es el objeto que lo contiene; en un manejador de [eventos](#evento) clásico, el elemento; en una función suelta en [modo estricto](#modo-estricto), `undefined`. Las [funciones flecha](#función-flecha) no tienen `this` propio. Se puede fijar con `bind()`, `call()` o `apply()`.

### Transpilación
**(Herramienta)** Traducción de código fuente a otro código fuente de nivel similar: [TypeScript](#typescript) o [JSX](#jsx) a JavaScript, o JavaScript moderno a JavaScript compatible con navegadores antiguos. La realizan [Babel](#babel), esbuild, SWC o el compilador de TypeScript (`tsc`). Ver [Polyfill](#polyfill).

### Tree shaking
**(Herramienta)** Optimización de los [bundlers](#bundler) que elimina del paquete final el código que se exporta pero que nunca se importa, reduciendo el tamaño de la descarga. Funciona gracias al análisis estático de los [módulos ES](#módulos-es).

### TypeScript
**(JavaScript)** Superconjunto de JavaScript creado por Microsoft que añade **tipado estático** opcional: tipos, interfaces, genéricos, enumeraciones… El código se comprueba antes de ejecutarse y se [transpila](#transpilación) a JavaScript. Detecta errores pronto y mejora el autocompletado del editor. Es el estándar en [Angular](#angular) y muy habitual en [React](#react), [Vue](#vuejs) y en el servidor ([TypeScript](DWES.md#typescript)).
```ts
interface Libro {
  id: number;
  titulo: string;
  precio?: number;
}

function total(libros: Libro[]): number {
  return libros.reduce((suma, l) => suma + (l.precio ?? 0), 0);
}
```

---

## U

### Unidades CSS
**(CSS)** Unidades para expresar medidas en CSS:
* **Absolutas**: `px` (píxel de referencia), `cm`, `pt` (sobre todo para impresión).
* **Relativas a la fuente**: `em` (tamaño de fuente del elemento), `rem` (tamaño de fuente del elemento raíz `<html>`, la recomendada para textos y espaciados), `ch` (anchura del carácter "0").
* **Relativas a la ventana**: `vw`, `vh` (1 % del ancho o alto de la ventana), y sus variantes para móviles `dvh`, `svh` y `lvh`.
* **Porcentajes** (`%`): relativos al elemento padre.
* `fr`: fracción del espacio libre en [Grid](#grid).

Funciones útiles: `calc()`, `min()`, `max()` y `clamp()` (por ejemplo, para tipografía fluida: `font-size: clamp(1rem, 2.5vw, 2rem)`).

---

## V

### var, let y const
**(JavaScript)** Las tres formas de declarar variables:
* `const`: no se puede reasignar (aunque, si es un objeto, su contenido sí puede cambiar). Debe ser la opción por defecto.
* `let`: se puede reasignar. Tiene [ámbito](#ámbito) de bloque.
* `var`: forma antigua. Tiene ámbito de función, se [eleva](#hoisting) y permite volver a declararla. Debe evitarse.
```js
const PI = 3.1416;
let intentos = 0;
intentos++;
```

### Variables CSS
**(CSS)** *Custom properties*. Propiedades definidas por el desarrollador, con nombres que empiezan por `--`, que se leen con `var()`. A diferencia de las variables de [Sass](#sass), existen en tiempo de ejecución: se heredan, pueden cambiar con [media queries](#media-queries) y se pueden modificar desde JavaScript. Son ideales para temas, como el modo oscuro.
```css
:root {
  --color-primario: #0055aa;
  --espacio: 1rem;
}
.boton {
  background: var(--color-primario);
  padding: var(--espacio);
}
```

### Viewport
**(HTML)** Área visible de la página en la ventana del navegador. En los móviles hay que incluir la etiqueta `<meta name="viewport">` para que la página use la anchura real del dispositivo en lugar de simular una pantalla de escritorio; sin ella, el [diseño adaptable](#diseño-adaptable) no funciona.
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Virtual DOM
Representación ligera del [DOM](#dom) que mantienen en memoria frameworks como [React](#react) y [Vue](#vuejs). Cuando cambia el [estado](#estado), se genera un nuevo árbol virtual, se compara con el anterior (*diffing*) y se aplican al DOM real solo los cambios mínimos necesarios (*reconciliación*). Frameworks como [Svelte](#svelte) o SolidJS prescinden de él.

### Vite
**(Herramienta)** Herramienta de construcción y servidor de desarrollo muy rápido para proyectos frontend. En desarrollo sirve los [módulos ES](#módulos-es) directamente al navegador, con [HMR](#hmr) casi instantáneo, y para producción genera un paquete optimizado. Tiene plantillas para [React](#react), [Vue](#vuejs), [Svelte](#svelte), JavaScript puro y otros, y es la base de [Nuxt](#nuxt), SvelteKit y Astro.
```bash
npm create vite@latest mi-app
cd mi-app && npm install && npm run dev
```

### Vue.js
**(Vue)** [Framework frontend](#framework-frontend) progresivo, creado por Evan You, que se puede adoptar poco a poco. Sus componentes de fichero único (`.vue`) agrupan `<template>`, `<script>` y `<style>`. Ofrece [reactividad](#reactividad) con `ref()` y `reactive()`, directivas en las plantillas (`v-if`, `v-for`, `v-model`, `v-bind` o `:`, `v-on` o `@`) y dos estilos de API: **Composition API** (recomendada, con `<script setup>`) y **Options API**. Su ecosistema incluye Vue Router, **Pinia** y [Nuxt](#nuxt).
```vue
<script setup>
import { ref } from 'vue';
const clics = ref(0);
</script>

<template>
  <button @click="clics++">Clics: {{ clics }}</button>
</template>
```

---

## W

### WCAG
*Web Content Accessibility Guidelines*. Pautas del W3C para la [accesibilidad](#accesibilidad) del contenido web, organizadas en cuatro principios: contenido **perceptible**, **operable**, **comprensible** y **robusto**. Tienen tres niveles de conformidad (A, AA y AAA); el nivel **AA** es el que exige la normativa europea, también para las webs de las administraciones públicas.

### Web Components
Conjunto de estándares del navegador para crear [componentes](#componente) reutilizables, sin framework, que funcionan como etiquetas HTML propias: **Custom Elements** (definir elementos con `customElements.define()`), [Shadow DOM](#shadow-dom) (encapsulación) y **plantillas HTML** (`<template>` y `<slot>`). Librería de ayuda: **Lit**.
```js
class SaludoUsuario extends HTMLElement {
  connectedCallback() {
    this.textContent = `Hola, ${this.getAttribute('nombre')}`;
  }
}
customElements.define('saludo-usuario', SaludoUsuario);
// <saludo-usuario nombre="Ana"></saludo-usuario>
```

### Web Workers
**(JavaScript)** Scripts que se ejecutan en un hilo en segundo plano, separado del hilo principal, para hacer cálculos pesados sin congelar la interfaz. No tienen acceso al [DOM](#dom) y se comunican con la página mediante mensajes (`postMessage` y el evento `message`). Ver [Event loop](#event-loop) y [Service Worker](#service-worker).

### WebAssembly
*Wasm*. Formato binario de bajo nivel que los navegadores ejecutan a una velocidad casi nativa, junto con JavaScript. Se genera compilando lenguajes como C, C++, Rust o Go. Se usa en aplicaciones exigentes: edición de imagen y vídeo, juegos, CAD o emuladores.

### webpack
**(Herramienta)** [Bundler](#bundler) muy configurable que durante años fue el estándar del desarrollo frontend. Lo procesa todo como módulos mediante *loaders* y *plugins*. En los proyectos nuevos se usa cada vez más [Vite](#vite), y su sucesor compatible es **Rspack**.

### WebSocket en el cliente
**(JavaScript)** Desde el navegador, la conexión [WebSocket](DWES.md#websocket) se abre con el objeto `WebSocket`, que permite recibir datos del servidor en tiempo real.
```js
const ws = new WebSocket('wss://ejemplo.com/chat');
ws.addEventListener('message', (e) => console.log('Mensaje:', e.data));
ws.addEventListener('open', () => ws.send('Hola'));
```

### window
**(JavaScript)** Objeto global del navegador en el que se ejecuta el código JavaScript de una página. Representa la ventana o pestaña y contiene el [`document`](#dom), las APIs del [BOM](#bom), los temporizadores y las variables globales. `globalThis` es la forma estándar de referirse al objeto global en cualquier entorno.

---

## X

### XMLHttpRequest
**(JavaScript)** API original del navegador para hacer peticiones HTTP desde JavaScript, la base histórica de [AJAX](DWES.md#ajax). Usa eventos en lugar de [promesas](#promesa) y hoy ha sido sustituida por la [Fetch API](#fetch-api), aunque sigue siendo útil para conocer el progreso de las subidas de ficheros.

---

## Y

### Yarn y pnpm
**(Herramienta)** Gestores de paquetes alternativos a [npm](DWES.md#npm), compatibles con el mismo registro. **pnpm** ahorra espacio en disco y tiempo de instalación guardando cada versión de un paquete una sola vez y enlazándola desde los proyectos. **Yarn** popularizó los ficheros *lock* y los *workspaces* (monorepositorios).

---

## Z

### z-index
**(CSS)** Propiedad que controla el orden de apilamiento de los elementos que se solapan: cuanto mayor es el valor, más arriba se dibuja el elemento. Solo afecta a elementos [posicionados](#posicionamiento) (o hijos de flex y grid), y funciona dentro de su **contexto de apilamiento**, que crean propiedades como `position` con `z-index`, `opacity` menor que 1 o `transform`.
