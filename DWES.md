# Diccionario Desarrollo Aplicaciones Web en Entorno Servidor

Esta publicación pretende servir como diccionario de los conceptos que todo desarrollador web debe conocer, con especial atención al **desarrollo web en entorno servidor** (*backend*).

Cada entrada incluye una definición breve y, cuando resulta útil, un ejemplo y referencias a otros términos relacionados. Los ejemplos se dan en los tres ecosistemas más habituales: **PHP** (con Laravel/Symfony), **Java** (con Spring Boot) y **Node.js** (con Express). Las entradas propias de un ecosistema llevan una etiqueta al principio: **(Spring)**, **(Java)**, **(Node.js)**, **(Express)**, **(JavaScript)**…

## Índice

[A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · [H](#h) · [I](#i) · [J](#j) · [K](#k) · [L](#l) · [M](#m) · [N](#n) · [O](#o) · [P](#p) · [Q](#q) · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v) · [W](#w) · [X](#x) · [Y](#y) · [Z](#z)

### Índices temáticos

* **PHP**: [PHP](#php) · [Superglobales](#superglobales) · [Sesión](#sesión) · [PDO](#pdo) · [Composer](#composer) · [Autocarga](#autocarga) · [PSR](#psr) · [PHP-FPM](#php-fpm) · [OPcache](#opcache) · [Xdebug](#xdebug) · [PHPUnit](#phpunit) · [Laravel](#laravel) · [Artisan](#artisan) · [Eloquent](#eloquent) · [Blade](#blade) · [Symfony](#symfony) · [Doctrine](#doctrine) · [Twig](#twig)
* **Java / Spring Boot**: [Java](#java) · [JVM](#jvm) · [Maven](#maven) · [Gradle](#gradle) · [JAR / WAR](#jar--war) · [Jakarta EE](#jakarta-ee) · [Servlet](#servlet) · [Tomcat](#tomcat) · [Spring Framework](#spring-framework) · [Spring Boot](#spring-boot) · [Spring Initializr](#spring-initializr) · [Starter](#starter) · [Anotación](#anotación) · [Anotaciones de Spring](#anotaciones-de-spring) · [Inversión de control](#inversión-de-control) · [ApplicationContext](#applicationcontext) · [Bean](#bean) · [application.properties](#applicationproperties--applicationyml) · [Perfil de Spring](#perfil-de-spring) · [Spring MVC](#spring-mvc) · [DispatcherServlet](#dispatcherservlet) · [ResponseEntity](#responseentity) · [Bean Validation](#bean-validation) · [JDBC](#jdbc) · [JPA](#jpa) · [Entidad](#entidad) · [Hibernate](#hibernate) · [Spring Data JPA](#spring-data-jpa) · [Flyway / Liquibase](#flyway--liquibase) · [Spring Security](#spring-security) · [Thymeleaf](#thymeleaf) · [Lombok](#lombok) · [Actuator](#actuator)
* **Node.js / Express**: [Node.js](#nodejs) · [Event loop](#event-loop) · [Asincronía](#asincronía) · [Callback](#callback) · [Promesa](#promesa) · [async / await](#async--await) · [CommonJS / ES Modules](#commonjs--es-modules) · [npm](#npm) · [package.json](#packagejson) · [node_modules](#node_modules) · [Versionado semántico](#versionado-semántico) · [nodemon](#nodemon) · [dotenv](#dotenv) · [Express](#express) · [req y res](#req-y-res) · [Router de Express](#router-de-express) · [Middleware](#middleware) · [Helmet](#helmet) · [Passport.js](#passportjs) · [EJS](#ejs) · [Pug](#pug) · [Mongoose](#mongoose) · [Prisma](#prisma) · [Stream](#stream) · [PM2](#pm2) · [TypeScript](#typescript) · [NestJS](#nestjs)

---

## A

### ACID
Conjunto de propiedades que garantizan que las [transacciones](#transacción) de una base de datos se procesan de forma fiable:
* **Atomicidad**: la transacción se ejecuta entera o no se ejecuta.
* **Consistencia**: la base de datos pasa de un estado válido a otro estado válido.
* **Aislamiento** (*Isolation*): las transacciones concurrentes no interfieren entre sí.
* **Durabilidad**: una vez confirmada, la transacción persiste aunque falle el sistema.

### Acoplamiento
Grado de dependencia entre dos módulos o clases. Se busca un **bajo acoplamiento**: que los componentes dependan lo mínimo unos de otros (normalmente a través de [interfaces](#interfaz)), para poder modificarlos o sustituirlos sin efectos colaterales. Ver [Inyección de dependencias](#inyección-de-dependencias).

### Actuator
**(Spring Boot)** Módulo que añade [endpoints](#endpoint) de monitorización y gestión a la aplicación: `/actuator/health`, `/actuator/metrics`, `/actuator/info`… Permite comprobar el estado de la aplicación en producción y lo usan orquestadores como [Kubernetes](#kubernetes). Debe protegerse, porque puede exponer información sensible.

### AJAX
*Asynchronous JavaScript And XML*. Técnica por la que el navegador realiza [peticiones HTTP](#petición-http) al servidor en segundo plano (hoy con `fetch()`) sin recargar la página. El servidor suele responder con [JSON](#json) en lugar de HTML completo.

### Anotación
**(Java)** Metadato que se añade a clases, métodos, atributos o parámetros con la sintaxis `@Nombre`. No ejecuta código por sí misma, pero los frameworks la leen (por reflexión en tiempo de ejecución o durante la compilación) para aplicar comportamiento. Es la forma principal de configurar [Spring](#spring-framework) y [JPA](#jpa). Ver [Anotaciones de Spring](#anotaciones-de-spring).

### Anotaciones de Spring
**(Spring)** Las [anotaciones](#anotación) más habituales:

| Anotación | Uso |
|---|---|
| `@SpringBootApplication` | Clase principal. Combina `@Configuration`, `@EnableAutoConfiguration` y `@ComponentScan`. |
| `@Component`, `@Service`, `@Repository` | Registran la clase como [bean](#bean) (genérico, capa de servicio, capa de acceso a datos). |
| `@Controller` / `@RestController` | [Controlador](#controlador) que devuelve vistas / controlador REST que devuelve datos ([JSON](#json)). |
| `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@PatchMapping`, `@DeleteMapping` | Asocian un método con una [ruta](#ruta) y un [método HTTP](#métodos-http). |
| `@PathVariable`, `@RequestParam`, `@RequestBody`, `@RequestHeader` | Extraen datos de la ruta, la [query string](#query-string), el [cuerpo](#body) o las [cabeceras](#cabeceras-http). |
| `@Autowired` | [Inyección de dependencias](#inyección-de-dependencias). Innecesaria si la clase tiene un único constructor. |
| `@Configuration` + `@Bean` | Definen beans manualmente desde un método. |
| `@Value("${clave}")` | Inyecta un valor de configuración. |
| `@Transactional` | Ejecuta el método dentro de una [transacción](#transacción). |
| `@Valid` | Activa la [Bean Validation](#bean-validation) del parámetro. |
| `@Entity`, `@Table`, `@Id`, `@GeneratedValue`, `@Column`, `@OneToMany`, `@ManyToOne`, `@ManyToMany` | Mapeo [JPA](#jpa) de [entidades](#entidad). |
| `@RestControllerAdvice` + `@ExceptionHandler` | Gestión global de [excepciones](#excepción). |
| `@Profile("prod")` | El bean solo existe en ese [perfil](#perfil-de-spring). |
| `@CrossOrigin` | Habilita [CORS](#cors) en un controlador. |

### Apache HTTP Server
[Servidor web](#servidor-web) de código abierto, uno de los más usados históricamente. Se configura mediante ficheros como `httpd.conf`/`apache2.conf`, [hosts virtuales](#host-virtual) y ficheros [.htaccess](#htaccess). Ejecuta PHP mediante `mod_php` o delegando en [PHP-FPM](#php-fpm).

### API
*Application Programming Interface*. Conjunto de operaciones que un componente de software expone para que otros lo utilicen. En desarrollo web suele referirse a un servicio accesible por HTTP que devuelve datos (no páginas). Ver [API REST](#api-rest), [GraphQL](#graphql), [SOAP](#soap).

### API REST
API que sigue el estilo arquitectónico [REST](#rest): los datos se modelan como **recursos** identificados por [URI](#uri), se manipulan con los [métodos HTTP](#métodos-http) y las respuestas son normalmente [JSON](#json).

| Método | URI | Acción |
|---|---|---|
| `GET` | `/api/libros` | Listar libros |
| `GET` | `/api/libros/7` | Obtener el libro 7 |
| `POST` | `/api/libros` | Crear un libro |
| `PUT`/`PATCH` | `/api/libros/7` | Actualizar el libro 7 |
| `DELETE` | `/api/libros/7` | Borrar el libro 7 |

### Aplicación web
Programa al que se accede mediante un navegador a través de una red. Se divide en una parte cliente ([frontend](#frontend)) y una parte servidor ([backend](#backend)) que se comunican mediante [HTTP](#http).

### application.properties / application.yml
**(Spring Boot)** Fichero de configuración principal de la aplicación, situado en `src/main/resources`. Admite variantes por [perfil](#perfil-de-spring) (`application-prod.yml`), y cualquier valor puede sobrescribirse con [variables de entorno](#variable-de-entorno) (`SPRING_DATASOURCE_URL`).
```properties
server.port=8080
spring.datasource.url=jdbc:mysql://localhost:3306/tienda
spring.datasource.username=${DB_USER}
spring.datasource.password=${DB_PASSWORD}
spring.jpa.hibernate.ddl-auto=validate
```

### ApplicationContext
**(Spring)** [Contenedor IoC](#contenedor-de-servicios) de Spring: crea, configura y gestiona el ciclo de vida de los [beans](#bean) y resuelve sus dependencias. Ver [Inversión de control](#inversión-de-control).

### Arquitectura cliente-servidor
Modelo en el que un **cliente** (navegador, app móvil…) envía [peticiones](#petición-http) a un **servidor**, que las procesa y devuelve una [respuesta](#respuesta-http). Es la base de la web.

### Artisan
Herramienta de línea de comandos ([CLI](#cli)) de [Laravel](#laravel). Permite generar código, ejecutar [migraciones](#migración), lanzar el servidor de desarrollo, etc.
```bash
php artisan make:controller LibroController
php artisan migrate
```

### Asignación masiva
*Mass assignment*. Rellenar todos los atributos de un modelo a partir de un array (normalmente los datos del formulario). Es peligroso si el usuario puede enviar campos no previstos (por ejemplo `es_admin=1`). Los [ORM](#orm) lo controlan con listas blancas (`$fillable` en [Eloquent](#eloquent)).

### Asincronía
Forma de ejecutar operaciones (E/S, red, base de datos) sin bloquear el hilo principal mientras se espera el resultado. Es el modelo de [Node.js](#nodejs), basado en el [event loop](#event-loop), los [callbacks](#callback), las [promesas](#promesa) y [async/await](#async--await). En Java, Spring ofrece `@Async` y el modelo reactivo de Spring WebFlux; desde Java 21 los *virtual threads* permiten código bloqueante muy concurrente. Ver también [Cola de trabajos](#cola-de-trabajos).

### async / await
**(JavaScript)** Sintaxis para trabajar con [promesas](#promesa) como si fuera código secuencial. Una función `async` siempre devuelve una promesa, y `await` suspende la función hasta que la promesa se resuelve, sin bloquear el [event loop](#event-loop). Los errores se capturan con `try/catch`. Express 5 pasa automáticamente al middleware de errores los rechazos de los manejadores `async`.
```js
app.get('/libros/:id', async (req, res) => {
  const libro = await Libro.findById(req.params.id);
  if (!libro) return res.status(404).json({ error: 'No encontrado' });
  res.json(libro);
});
```

### Autenticación
Proceso de verificar **quién es** un usuario (usuario y contraseña, [token](#token), certificado, segundo factor…). No confundir con [autorización](#autorización). Ver [Sesión](#sesión), [JWT](#jwt), [OAuth 2.0](#oauth-20).

### Autenticación básica HTTP
*Basic Auth*. Mecanismo de autenticación en el que el cliente envía usuario y contraseña codificados en Base64 en la cabecera `Authorization: Basic ...`. Al no ir cifrados, solo debe usarse sobre [HTTPS](#https).

### Autenticación multifactor
*MFA / 2FA*. Autenticación que exige dos o más factores de distinta naturaleza: algo que sabes (contraseña), algo que tienes (móvil, llave de seguridad) o algo que eres (huella).

### Autocarga
*Autoload*. Mecanismo que carga automáticamente el fichero de una clase la primera vez que se usa, evitando escribir `require` a mano. En PHP se implementa con `spl_autoload_register()` y, en la práctica, con el autoload de [Composer](#composer) siguiendo [PSR-4](#psr).

### Autorización
Proceso de decidir **qué puede hacer** un usuario ya [autenticado](#autenticación): roles, permisos, políticas. Si falla se responde con `403 Forbidden`.

---

## B

### Backend
Parte de una [aplicación web](#aplicación-web) que se ejecuta en el servidor: lógica de negocio, acceso a [base de datos](#base-de-datos), [autenticación](#autenticación), [APIs](#api)… El usuario no la ve directamente. Opuesto a [frontend](#frontend).

### Balanceador de carga
Componente que reparte las peticiones entrantes entre varios servidores para aumentar la capacidad y la disponibilidad. Ejemplos: Nginx, HAProxy, balanceadores de los proveedores cloud. Ver [Escalabilidad](#escalabilidad).

### Base de datos
Conjunto organizado de datos persistentes gestionado por un **SGBD** (Sistema Gestor de Bases de Datos). Ver [Base de datos relacional](#base-de-datos-relacional) y [NoSQL](#nosql).

### Base de datos relacional
Base de datos que organiza la información en **tablas** (relaciones) con filas y columnas, relacionadas mediante [claves](#clave-primaria). Se consulta con [SQL](#sql). Ejemplos: [MySQL/MariaDB](#mysql--mariadb), PostgreSQL, SQLite, Oracle, SQL Server.

### bcrypt
Algoritmo de [hash](#hash) diseñado para contraseñas: es lento a propósito, incluye [sal](#sal) y un factor de coste configurable. Es el algoritmo por defecto de `password_hash()` en PHP. Alternativa moderna: **Argon2**.

### Bean
**(Spring)** Objeto cuya creación y ciclo de vida gestiona el [ApplicationContext](#applicationcontext) de Spring. Se declara anotando la clase con `@Component` (o `@Service`, `@Repository`, `@Controller`) o con un método `@Bean` dentro de una clase `@Configuration`. Por defecto es *singleton* (una única instancia en toda la aplicación). Otros ámbitos posibles son `prototype`, `request` y `session`.

### Bean Validation
**(Java)** Especificación de [Jakarta EE](#jakarta-ee) (Jakarta Validation, cuya implementación de referencia es Hibernate Validator) para declarar reglas de [validación](#validación) con anotaciones sobre los atributos. En Spring se activa con `@Valid`; si la validación falla, se responde con `400 Bad Request`.
```java
public record LibroDTO(
    @NotBlank String titulo,
    @NotNull @PositiveOrZero BigDecimal precio,
    @Email String contacto) {}

@PostMapping("/libros")
public Libro crear(@Valid @RequestBody LibroDTO dto) { ... }
```

### Blade
Motor de [plantillas](#plantilla) de [Laravel](#laravel). Usa la sintaxis `{{ $variable }}` (con [escape](#escape-de-salida) automático) y directivas como `@if`, `@foreach`, `@extends`.

### Body
Cuerpo de una [petición](#petición-http) o [respuesta](#respuesta-http) HTTP. Contiene los datos (HTML, JSON, datos de formulario, un fichero…). Su formato se indica en la cabecera `Content-Type`.

---

## C

### Cabeceras HTTP
*Headers*. Pares `Nombre: valor` que acompañan a cada petición y respuesta HTTP aportando metadatos. Algunas habituales: `Content-Type`, `Content-Length`, `Authorization`, `Cookie`, `Set-Cookie`, `Location`, `Cache-Control`, `Accept`, `User-Agent`. En PHP se envían con `header()` **antes** de cualquier salida.
```php
header('Content-Type: application/json; charset=utf-8');
```

### Caché
Almacenamiento temporal de datos para servirlos más rápido en peticiones posteriores. Puede estar en el navegador (cabeceras `Cache-Control`, `ETag`), en un [CDN](#cdn), en un [proxy inverso](#proxy-inverso), en memoria ([Redis](#redis), Memcached) o en el propio código ([OPcache](#opcache)). La dificultad está en la **invalidación**.

### Callback
**(JavaScript)** Función que se pasa como argumento a otra para que esta la invoque cuando termine una operación. Era el modelo original de [Node.js](#nodejs), con la convención *error-first*: `(err, resultado) => { ... }`. Anidar muchos callbacks produce el llamado *callback hell*, que se resuelve con [promesas](#promesa) y [async/await](#async--await).

### CDN
*Content Delivery Network*. Red de servidores distribuidos geográficamente que sirven contenido (sobre todo estático: imágenes, CSS, JS) desde el nodo más cercano al usuario.

### CGI
*Common Gateway Interface*. Estándar antiguo por el que el servidor web ejecuta un programa externo por cada petición y devuelve su salida al cliente. Sus sucesores son **FastCGI** (procesos persistentes, como [PHP-FPM](#php-fpm)), WSGI (Python) o Rack (Ruby).

### CI/CD
*Integración Continua / Despliegue (o Entrega) Continuo*. Prácticas en las que cada cambio subido al repositorio se compila, se prueba automáticamente ([tests](#test)) y, si todo va bien, se despliega. Herramientas: GitHub Actions, GitLab CI, Jenkins.

### Clase
Plantilla que define los atributos (estado) y métodos (comportamiento) de los [objetos](#programación-orientada-a-objetos). Base de la programación orientada a objetos.

### Clave foránea
Columna de una tabla que referencia la [clave primaria](#clave-primaria) de otra, estableciendo una relación entre ellas y garantizando la **integridad referencial**.

### Clave primaria
Columna (o conjunto de columnas) que identifica de forma única cada fila de una tabla. No puede repetirse ni ser nula.

### CLI
*Command Line Interface*. Interfaz de línea de comandos. PHP puede ejecutarse desde la CLI (`php script.php`) además de desde el servidor web; muchas herramientas ([Composer](#composer), [Artisan](#artisan), `bin/console` de [Symfony](#symfony)) son CLI.

### Código de estado HTTP
Número de tres cifras con el que el servidor indica el resultado de una petición:
* **1xx** Informativos.
* **2xx** Éxito: `200 OK`, `201 Created`, `204 No Content`.
* **3xx** [Redirección](#redirección): `301 Moved Permanently`, `302 Found`, `304 Not Modified`.
* **4xx** Error del cliente: `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `405 Method Not Allowed`, `419/422` (validación en Laravel), `429 Too Many Requests`.
* **5xx** Error del servidor: `500 Internal Server Error`, `502 Bad Gateway`, `503 Service Unavailable`.

```php
http_response_code(404);
```

### Cola de trabajos
*Queue*. Mecanismo para ejecutar tareas lentas (enviar correos, procesar imágenes) en segundo plano: la petición encola el trabajo y responde enseguida, y un proceso **worker** lo ejecuta después. Herramientas: [Redis](#redis), RabbitMQ, Amazon SQS, colas de Laravel.

### CommonJS / ES Modules
**(Node.js)** Los dos sistemas de módulos de JavaScript en Node.js:
* **CommonJS** (el clásico de Node): `require()` y `module.exports`.
* **ES Modules** (el estándar del lenguaje): `import` y `export`. Se activa con `"type": "module"` en [package.json](#packagejson) o usando la extensión `.mjs`.
```js
// CommonJS
const express = require('express');
module.exports = router;

// ES Modules
import express from 'express';
export default router;
```

### Composer
Gestor de dependencias de PHP. Las dependencias se declaran en `composer.json`, se instalan en `vendor/` y las versiones exactas quedan fijadas en `composer.lock`. También genera la [autocarga](#autocarga). El repositorio público de paquetes es **Packagist**.
```bash
composer require monolog/monolog
```

### Consulta preparada
*Prepared statement*. Consulta SQL que se envía al SGBD con **marcadores** en lugar de valores; los valores se pasan aparte. Es la defensa principal contra la [inyección SQL](#inyección-sql).
```php
$stmt = $pdo->prepare('SELECT * FROM usuarios WHERE email = :email');
$stmt->execute(['email' => $email]);
$usuario = $stmt->fetch();
```

### Contenedor
Unidad que empaqueta una aplicación con todas sus dependencias y se ejecuta aislada sobre el núcleo del sistema anfitrión. Es más ligero que una máquina virtual. Ver [Docker](#docker).

### Contenedor de servicios
*Service container / IoC container*. Componente de un [framework](#framework) que sabe construir objetos y resolver sus dependencias automáticamente, aplicando la [inyección de dependencias](#inyección-de-dependencias). Existe en [Laravel](#laravel), [Symfony](#symfony), [NestJS](#nestjs) y, con el nombre de [ApplicationContext](#applicationcontext), en Spring.

### Controlador
En el patrón [MVC](#mvc), componente que recibe la petición, interactúa con el [modelo](#modelo) y elige la [vista](#vista) o respuesta a devolver. Ver [Enrutamiento](#enrutamiento).

### Cookie
Pequeño dato que el servidor envía al navegador (cabecera `Set-Cookie`) y que este devuelve en cada petición posterior al mismo dominio (cabecera `Cookie`). Se usa para [sesiones](#sesión), preferencias o seguimiento. Atributos importantes de seguridad: `HttpOnly`, `Secure`, `SameSite`, además de `Expires`/`Max-Age`, `Path` y `Domain`.
```php
setcookie('tema', 'oscuro', [
    'expires' => time() + 86400 * 30,
    'httponly' => true,
    'secure' => true,
    'samesite' => 'Lax',
]);
```

### CORS
*Cross-Origin Resource Sharing*. Mecanismo mediante el cual un servidor indica, con cabeceras como `Access-Control-Allow-Origin`, qué **orígenes** (esquema + dominio + puerto) distintos del suyo pueden leer sus respuestas desde JavaScript en el navegador. Relaja la **política del mismo origen**. Para peticiones no simples el navegador envía antes una petición `OPTIONS` de comprobación (*preflight*). En Express se configura con el paquete `cors` (`app.use(cors({ origin: 'https://miweb.com' }))`) y en Spring con `@CrossOrigin` o en la configuración de [Spring Security](#spring-security).

### Cron
Planificador de tareas de los sistemas Unix que ejecuta comandos periódicamente según una expresión (`minuto hora día mes día_semana`). Se usa para tareas programadas: copias de seguridad, limpieza, envío de informes.
```
0 3 * * * php /var/www/app/artisan schedule:run
```

### CRUD
*Create, Read, Update, Delete*. Las cuatro operaciones básicas sobre datos persistentes. Se corresponden con `INSERT`, `SELECT`, `UPDATE`, `DELETE` en [SQL](#sql) y con `POST`, `GET`, `PUT/PATCH`, `DELETE` en una [API REST](#api-rest).

### CSRF
*Cross-Site Request Forgery*. Ataque en el que una web maliciosa provoca que el navegador de la víctima envíe una petición a otra web en la que está autenticada (aprovechando sus [cookies](#cookie)). Se previene con un **token CSRF** aleatorio en cada formulario que el servidor verifica, y con el atributo `SameSite` de las cookies.

---

## D

### Despliegue
*Deploy*. Proceso de poner una versión de la aplicación en funcionamiento en un [entorno](#entorno) (normalmente producción): copiar el código, instalar dependencias, ejecutar [migraciones](#migración), limpiar cachés, reiniciar servicios. Ver [CI/CD](#cicd).

### Dirección IP
Identificador numérico de un equipo en una red: IPv4 (`192.168.1.10`) o IPv6 (`2001:db8::1`). En PHP la IP del cliente está en `$_SERVER['REMOTE_ADDR']`.

### DispatcherServlet
**(Spring MVC)** [Servlet](#servlet) que actúa como [front controller](#front-controller) de [Spring MVC](#spring-mvc): recibe todas las peticiones, las despacha al método del [controlador](#controlador) correspondiente, convierte los datos de entrada y salida (por ejemplo, de y hacia [JSON](#json)) y resuelve las [vistas](#vista).

### DNS
*Domain Name System*. Sistema que traduce nombres de [dominio](#dominio) (`ejemplo.com`) a [direcciones IP](#dirección-ip). Registros habituales: `A` (IPv4), `AAAA` (IPv6), `CNAME` (alias), `MX` (correo), `TXT`.

### Docker
Plataforma para crear y ejecutar [contenedores](#contenedor). Una **imagen** se define en un `Dockerfile` y a partir de ella se lanzan contenedores. Permite que el entorno de desarrollo sea idéntico al de producción.

### Docker Compose
Herramienta para definir y ejecutar aplicaciones de varios [contenedores](#contenedor) (por ejemplo, servidor web + PHP + base de datos) en un fichero `compose.yaml` ([YAML](#yaml)).
```bash
docker compose up -d
```

### Doctrine
[ORM](#orm) de PHP basado en el patrón *Data Mapper*, usado por defecto en [Symfony](#symfony). Las entidades son clases PHP simples y un *EntityManager* se encarga de persistirlas.

### Dominio
Nombre legible que identifica un sitio en Internet (`ejemplo.com`). Se compone de niveles: dominio de primer nivel (`.com`, `.es`), dominio y subdominios (`api.ejemplo.com`). Ver [DNS](#dns).

### dotenv
**(Node.js)** Paquete que carga las [variables de entorno](#variable-de-entorno) definidas en un fichero `.env` dentro de `process.env`. Desde Node.js 20.6 existe la alternativa nativa `node --env-file=.env app.js`.

### DTO
*Data Transfer Object*. Objeto sencillo, sin lógica, cuyo único propósito es transportar datos entre capas (por ejemplo, los datos validados de una petición).

---

## E

### EJS
**(Node.js)** *Embedded JavaScript*. Motor de [plantillas](#plantilla) que incrusta JavaScript en HTML: `<%= variable %>` imprime con [escape](#escape-de-salida) y `<% código %>` ejecuta lógica. En Express se configura con `app.set('view engine', 'ejs')` y se usa con `res.render()`.
```ejs
<ul>
  <% libros.forEach(libro => { %>
    <li><%= libro.titulo %></li>
  <% }) %>
</ul>
```

### Eloquent
[ORM](#orm) de [Laravel](#laravel), basado en el patrón *Active Record*: cada [modelo](#modelo) representa una tabla y cada instancia una fila.
```php
$libros = Libro::where('autor', 'Cervantes')->orderBy('titulo')->get();
```

### Endpoint
URL concreta de una [API](#api) junto con el método HTTP que acepta; cada uno corresponde a una operación (`GET /api/libros`).

### Enrutamiento
*Routing*. Mecanismo que asocia cada combinación de método HTTP + URL con el código ([controlador](#controlador)) que debe atenderla. Normalmente se implementa con un [front controller](#front-controller).
```php
// Laravel
Route::get('/libros/{id}', [LibroController::class, 'show']);
```
```java
// Spring Boot
@GetMapping("/libros/{id}")
public Libro ver(@PathVariable Long id) { ... }
```
```js
// Express
app.get('/libros/:id', (req, res) => { /* req.params.id */ });
```

### Entidad
**(JPA)** Clase Java anotada con `@Entity` que se mapea con una tabla de la base de datos. Cada instancia representa una fila. Ver [JPA](#jpa).
```java
@Entity
public class Libro {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String titulo;

    @ManyToOne
    private Autor autor;
}
```

### Entorno
Cada una de las instalaciones en las que se ejecuta una aplicación: **desarrollo** (local), **pruebas/staging** (réplica de producción) y **producción** (la que usan los usuarios). La configuración de cada uno se separa mediante [variables de entorno](#variable-de-entorno).

### Escalabilidad
Capacidad de un sistema para atender más carga. **Vertical**: máquina más potente. **Horizontal**: más máquinas detrás de un [balanceador de carga](#balanceador-de-carga), lo que exige que la aplicación sea [sin estado](#stateless).

### Escape de salida
Convertir los caracteres especiales de un dato al mostrarlo para que se interpreten como texto y no como código. En HTML se usa `htmlspecialchars()`. Es la defensa principal contra [XSS](#xss). Los motores de [plantillas](#plantilla) lo hacen automáticamente.
```php
echo htmlspecialchars($comentario, ENT_QUOTES, 'UTF-8');
```

### Event loop
**(Node.js)** *Bucle de eventos*. Mecanismo que permite a [Node.js](#nodejs) atender muchas conexiones con un único hilo. Las operaciones de entrada/salida (red, disco, base de datos) se delegan al sistema a través de la librería *libuv* y, cuando terminan, sus [callbacks](#callback) se encolan para que el bucle los ejecute. Por eso nunca se debe bloquear el hilo principal con cálculos pesados; para ellos existen los *worker threads*.

### Excepción
Mecanismo para señalar y gestionar errores: se lanza con `throw` y se captura con `try/catch`. En producción, las excepciones no capturadas deben registrarse en el [log](#log) y mostrar una página de error genérica, nunca la traza al usuario. En Spring se centraliza con `@RestControllerAdvice` y `@ExceptionHandler`; en Express, con un [middleware](#middleware) de errores de cuatro parámetros.
```php
try {
    $pdo = new PDO($dsn, $user, $pass);
} catch (PDOException $e) {
    error_log($e->getMessage());
}
```

### Express
**(Node.js)** [Framework](#framework) minimalista para aplicaciones web y APIs en [Node.js](#nodejs). Se basa en [rutas](#ruta), en una cadena de [middleware](#middleware) y en los objetos [req y res](#req-y-res). Al ser minimalista, funcionalidades como la seguridad ([Helmet](#helmet)), la autenticación ([Passport.js](#passportjs)) o el acceso a datos ([Mongoose](#mongoose), [Prisma](#prisma)) se añaden con paquetes de [npm](#npm). Las rutas se organizan en módulos con el [Router de Express](#router-de-express).
```js
import express from 'express';

const app = express();
app.use(express.json());              // parsea cuerpos JSON en req.body

app.get('/api/libros', async (req, res) => {
  res.json(await Libro.find());
});

app.post('/api/libros', async (req, res) => {
  const libro = await Libro.create(req.body);
  res.status(201).json(libro);
});

app.listen(3000, () => console.log('Escuchando en http://localhost:3000'));
```

---

## F

### Factory
1. Patrón de diseño que encapsula la creación de objetos.
2. En [Laravel](#laravel), clases que generan modelos con datos falsos para pruebas y para los [seeders](#seeder).

### Filtrado de entrada
Comprobar y limpiar todos los datos que llegan del exterior (`$_GET`, `$_POST`, cabeceras, ficheros, cookies) antes de usarlos. Regla de oro: **nunca confíes en los datos del usuario**. PHP ofrece `filter_input()` y `filter_var()`. Ver [Validación](#validación) y [Sanitización](#sanitización).
```php
$edad = filter_input(INPUT_POST, 'edad', FILTER_VALIDATE_INT);
```

### Flyway / Liquibase
**(Java)** Herramientas de [migraciones](#migración) de base de datos muy usadas con [Spring Boot](#spring-boot). Flyway aplica al arrancar la aplicación los scripts SQL versionados de `src/main/resources/db/migration` (`V1__crear_tablas.sql`, `V2__añadir_precio.sql`…) y anota en una tabla cuáles se han ejecutado ya.

### Framework
Conjunto de librerías, convenciones y estructura sobre el que se construye una aplicación, resolviendo tareas comunes (enrutamiento, ORM, plantillas, seguridad). Ejemplos de servidor: [Laravel](#laravel), [Symfony](#symfony) (PHP); Django, Flask (Python); [Express](#express), [NestJS](#nestjs) (Node.js); [Spring Boot](#spring-boot) (Java); Ruby on Rails; ASP.NET Core.

### Front controller
Patrón en el que **todas** las peticiones entran por un único punto (normalmente `public/index.php`), que inicializa la aplicación y delega en el [enrutador](#enrutamiento). Se configura reescribiendo las URL en el servidor web (`.htaccess`, `try_files` en Nginx).

### Frontend
Parte de la aplicación que se ejecuta en el navegador del usuario: HTML, CSS y JavaScript. Opuesto a [backend](#backend).

### Full stack
Desarrollador o pila tecnológica que abarca tanto [frontend](#frontend) como [backend](#backend).

---

## G

### GET
[Método HTTP](#métodos-http) para **obtener** un recurso. Sus parámetros viajan en la [query string](#query-string) de la URL, por lo que es visible, se guarda en el historial y se puede cachear. Debe ser [seguro e idempotente](#idempotencia): no debe modificar datos. En PHP: `$_GET`.

### Git
Sistema de control de versiones distribuido. Conceptos clave: repositorio, *commit*, rama (*branch*), *merge*, *pull request*, remoto (GitHub, GitLab).

### Gradle
**(Java)** Herramienta de construcción y gestión de dependencias, alternativa a [Maven](#maven). El proyecto se describe en `build.gradle` (Groovy) o `build.gradle.kts` (Kotlin) y se ejecuta con el *wrapper* incluido en el proyecto: `./gradlew bootRun`, `./gradlew test`, `./gradlew build`.

### GraphQL
Lenguaje de consulta para APIs en el que el cliente pide exactamente los campos que necesita a través de un único [endpoint](#endpoint). Alternativa a [REST](#api-rest).

---

## H

### Hash
Función que transforma un dato en una cadena de longitud fija de forma **irreversible**. Para contraseñas se usan algoritmos lentos y con [sal](#sal) ([bcrypt](#bcrypt), Argon2); nunca MD5 ni SHA-1. No confundir con **cifrado**, que sí es reversible con la clave.
```php
$hash = password_hash($password, PASSWORD_DEFAULT);
if (password_verify($intento, $hash)) { /* contraseña correcta */ }
```

### Helmet
**(Express)** [Middleware](#middleware) que añade de una vez varias [cabeceras HTTP](#cabeceras-http) de seguridad (`Content-Security-Policy`, `Strict-Transport-Security`, `X-Content-Type-Options`, `X-Frame-Options`…).
```js
import helmet from 'helmet';
app.use(helmet());
```

### Helper
Función de utilidad global que simplifica tareas comunes (`route()`, `asset()`, `config()` en [Laravel](#laravel)).

### Hibernate
**(Java)** [ORM](#orm) de Java e implementación de [JPA](#jpa) usada por defecto en [Spring Boot](#spring-boot). La propiedad `spring.jpa.hibernate.ddl-auto` (`none`, `validate`, `update`, `create`, `create-drop`) controla si genera el esquema de la base de datos a partir de las [entidades](#entidad). En producción conviene usar `validate` o `none` y gestionar el esquema con [Flyway](#flyway--liquibase).

### Host virtual
*Virtual host*. Configuración que permite a un mismo [servidor web](#servidor-web) servir varios sitios distintos según el dominio solicitado (cabecera `Host`), cada uno con su propia carpeta raíz (`DocumentRoot`).

### Hosting
Servicio de alojamiento de aplicaciones web. Tipos: **compartido**, [VPS](#vps), **dedicado**, **cloud** (AWS, Azure, Google Cloud) y **PaaS** (la plataforma gestiona el servidor y solo se sube el código).

### .htaccess
Fichero de configuración por directorio de [Apache](#apache-http-server). Se usa para reescribir URL (`mod_rewrite`), redirecciones, restringir accesos o configurar cabeceras.
```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [L]
```

### HTTP
*HyperText Transfer Protocol*. Protocolo de aplicación de la web, basado en [petición](#petición-http)-[respuesta](#respuesta-http) y [sin estado](#stateless). Versiones: HTTP/1.1, HTTP/2 (multiplexación) y HTTP/3 (sobre QUIC/UDP).

### HTTPS
[HTTP](#http) sobre [TLS](#ssl--tls): la comunicación va cifrada y se verifica la identidad del servidor mediante un **certificado**. Es imprescindible hoy en cualquier sitio. Certificados gratuitos: **Let's Encrypt**.

---

## I

### Idempotencia
Propiedad de una operación que produce el mismo resultado se ejecute una o varias veces. `GET`, `PUT` y `DELETE` son idempotentes; `POST` no. Un método es **seguro** si además no modifica nada (`GET`, `HEAD`, `OPTIONS`).

### include / require
Instrucciones de PHP para incorporar el contenido de otro fichero. `require` produce un error fatal si no existe; `include` solo un aviso. Las variantes `_once` evitan cargarlo dos veces. Ver [Autocarga](#autocarga).

### Índice
Estructura de una base de datos que acelera las búsquedas sobre una o varias columnas, a costa de espacio y de escrituras algo más lentas. Las [claves primarias](#clave-primaria) y las restricciones `UNIQUE` llevan índice automáticamente.

### Interfaz
Contrato que define qué métodos debe implementar una clase sin decir cómo. Permite programar contra abstracciones y reducir el [acoplamiento](#acoplamiento).

### Inversión de control
*IoC, Inversion of Control*. Principio según el cual es el framework, y no nuestro código, quien controla la creación de los objetos y el flujo de ejecución ("no nos llames, nosotros te llamaremos"). Su forma más habitual es la [inyección de dependencias](#inyección-de-dependencias). Ver [ApplicationContext](#applicationcontext).

### Inyección de dependencias
Técnica en la que un objeto **recibe** las dependencias que necesita (normalmente por el constructor) en lugar de crearlas él mismo. Facilita los [tests](#test) y reduce el [acoplamiento](#acoplamiento). Es la forma más habitual de [inversión de control](#inversión-de-control). Ver [Contenedor de servicios](#contenedor-de-servicios).
```php
// PHP
class PedidoService {
    public function __construct(private Mailer $mailer) {}
}
```
```java
// Spring: el ApplicationContext inyecta el bean Mailer por el constructor
@Service
public class PedidoService {
    private final Mailer mailer;
    public PedidoService(Mailer mailer) { this.mailer = mailer; }
}
```

### Inyección SQL
Ataque en el que el usuario introduce fragmentos de SQL en un dato que la aplicación concatena en una consulta, alterándola. Ejemplo: un login con `' OR '1'='1`. Se previene con [consultas preparadas](#consulta-preparada) o un [ORM](#orm). Nunca se debe concatenar entrada del usuario en SQL.

---

## J

### Jakarta EE
**(Java)** Conjunto de especificaciones para aplicaciones empresariales en Java, antes llamado *Java EE*: [Servlets](#servlet), [JPA](#jpa), [Bean Validation](#bean-validation), JAX-RS… Desde Spring Boot 3 los paquetes se llaman `jakarta.*` en lugar de `javax.*`.

### JAR / WAR
**(Java)** Formatos de empaquetado de aplicaciones Java. Un **JAR** (*Java ARchive*) contiene clases compiladas y recursos. Spring Boot genera un JAR ejecutable que lleva el servidor ([Tomcat](#tomcat)) embebido y se lanza con `java -jar app.jar`. Un **WAR** (*Web ARchive*) se despliega en un servidor de aplicaciones externo.

### Java
Lenguaje de programación orientado a objetos y fuertemente tipado que se compila a *bytecode* y se ejecuta en la [JVM](#jvm). Muy usado en backend empresarial, sobre todo con [Spring Boot](#spring-boot).

### JDBC
**(Java)** *Java Database Connectivity*. API de bajo nivel de Java para conectarse a bases de datos relacionales y ejecutar SQL (el equivalente a [PDO](#pdo) en PHP). Cada SGBD aporta su propio *driver*, y las URL de conexión tienen la forma `jdbc:mysql://host:3306/basedatos`. Spring ofrece `JdbcTemplate` para simplificar su uso, y [JPA](#jpa) trabaja por encima de JDBC.

### JOIN
Operación [SQL](#sql) que combina filas de varias tablas relacionadas. Tipos: `INNER JOIN` (solo coincidencias), `LEFT JOIN` (todas las de la izquierda), `RIGHT JOIN`, `CROSS JOIN`.

### JPA
**(Java)** *Jakarta Persistence API*. Especificación estándar de Java para el [mapeo objeto-relacional](#orm) mediante [anotaciones](#anotación) (`@Entity`, `@Id`, `@OneToMany`…). Define el `EntityManager`, que gestiona el ciclo de vida de las [entidades](#entidad), y el lenguaje de consultas orientado a objetos **JPQL**. Su implementación más usada es [Hibernate](#hibernate).

### JSON
*JavaScript Object Notation*. Formato de texto ligero para intercambiar datos, estándar de facto en las [APIs](#api). En PHP: `json_encode()` y `json_decode()`.
```php
header('Content-Type: application/json');
echo json_encode(['id' => 7, 'titulo' => 'El Quijote']);
```

### JVM
*Java Virtual Machine*. Máquina virtual que ejecuta el *bytecode* de Java (y de otros lenguajes como Kotlin o Scala) con independencia del sistema operativo. Para desarrollar se instala el **JDK** (*Java Development Kit*), que incluye el compilador y la JVM.

### JWT
*JSON Web Token*. [Token](#token) firmado formado por tres partes en Base64URL (cabecera.carga.firma) que contiene información (*claims*) sobre el usuario. Permite [autenticación](#autenticación) [sin estado](#stateless) en APIs: el cliente lo envía en `Authorization: Bearer <token>`. La carga **no está cifrada**, solo firmada.

---

## K

### Kubernetes
Plataforma de orquestación de [contenedores](#contenedor): despliega, escala y reinicia automáticamente aplicaciones formadas por muchos contenedores en un clúster de máquinas.

---

## L

### LAMP / LEMP
Pila clásica para aplicaciones web: **L**inux + **A**pache (o Nginx, la **E** de *Engine-X*) + **M**ySQL/MariaDB + **P**HP. Variantes: WAMP (Windows), MAMP (macOS), XAMPP (multiplataforma).

### Laravel
[Framework](#framework) PHP muy popular basado en [MVC](#mvc). Incluye [Eloquent](#eloquent), [Blade](#blade), [Artisan](#artisan), [migraciones](#migración), [colas](#cola-de-trabajos), autenticación y validación.

### Lenguaje de servidor
Lenguaje con el que se programa el [backend](#backend): PHP, Python, [Java](#java), JavaScript/[TypeScript](#typescript) ([Node.js](#nodejs)), C#, Ruby, Go… Se ejecuta en el servidor y el cliente solo recibe el resultado (HTML, JSON…).

### localhost
Nombre que hace referencia al propio equipo (IP `127.0.0.1` o `::1`). Se usa en desarrollo para acceder a los servidores locales.

### Log
Registro de eventos que genera una aplicación o servidor (errores, accesos, avisos), útil para depurar y auditar. Niveles habituales (PSR-3): `debug`, `info`, `notice`, `warning`, `error`, `critical`, `alert`, `emergency`. Librerías típicas: **Monolog** (PHP), **SLF4J** + **Logback** (Java/Spring Boot, por defecto), **pino**, **winston** y **morgan** (registro de peticiones HTTP) en Node.js.

### Lombok
**(Java)** Librería que genera código repetitivo durante la compilación a partir de anotaciones: `@Getter`, `@Setter`, `@NoArgsConstructor`, `@AllArgsConstructor`, `@RequiredArgsConstructor`, `@Builder`, `@Data`, `@Slf4j`. Los `record` de Java reducen su necesidad en los [DTO](#dto).

---

## M

### Maven
**(Java)** Herramienta de construcción y gestión de dependencias para Java. El proyecto se describe en el fichero `pom.xml` (dependencias, *plugins*, versión de Java) y las dependencias se descargan del repositorio **Maven Central**. Fases principales de su ciclo de vida: `compile`, `test`, `package`, `install`. Con Spring Boot: `./mvnw spring-boot:run`.

### Métodos HTTP
También llamados *verbos*. Indican la acción a realizar sobre el recurso:
* [`GET`](#get): obtener.
* [`POST`](#post): crear o enviar datos para su procesamiento.
* `PUT`: reemplazar completamente un recurso.
* `PATCH`: modificar parcialmente un recurso.
* `DELETE`: borrar.
* `HEAD`: como `GET` pero sin cuerpo.
* `OPTIONS`: consultar qué métodos admite (usado en [CORS](#cors)).

Los formularios HTML solo admiten `GET` y `POST`; los frameworks simulan el resto con un campo oculto `_method`.

### Microservicios
Arquitectura en la que la aplicación se divide en servicios pequeños e independientes, cada uno con su propia base de datos y [despliegue](#despliegue), que se comunican por red (HTTP, mensajería). Opuesto a [monolito](#monolito).

### Middleware
Capa que se ejecuta antes y/o después del [controlador](#controlador) para cada petición, formando una cadena. Se usa para [autenticación](#autenticación), [CSRF](#csrf), [CORS](#cors), [logs](#log), [limitación de peticiones](#rate-limiting), etc.

* En [Express](#express) todo es middleware: funciones `(req, res, next)` que llaman a `next()` para pasar al siguiente. Un middleware con **cuatro** parámetros `(err, req, res, next)` es un manejador de errores.
* En [Spring](#spring-framework) el papel lo cumplen los **filtros** de [Servlet](#servlet) (como la cadena de [Spring Security](#spring-security)) y los **interceptores** (`HandlerInterceptor`).
* En [Laravel](#laravel) son clases con un método `handle($request, $next)`.

```js
// Express: middleware de autenticación y de errores
function requiereLogin(req, res, next) {
  if (!req.session?.usuario) return res.status(401).json({ error: 'No autenticado' });
  next();
}
app.use('/admin', requiereLogin);

app.use((err, req, res, next) => {
  console.error(err);
  res.status(500).json({ error: 'Error interno' });
});
```

### Migración
Fichero de código que describe un cambio en el esquema de la base de datos (crear tabla, añadir columna…) y cómo deshacerlo. Permite versionar la base de datos junto al código.
```php
Schema::create('libros', function (Blueprint $table) {
    $table->id();
    $table->string('titulo');
    $table->timestamps();
});
```

### Modelo
En [MVC](#mvc), la capa que representa los datos y la lógica de negocio. En los [ORM](#orm), clase que se corresponde con una tabla.

### MongoDB
Base de datos [NoSQL](#nosql) orientada a documentos que almacena la información en documentos tipo JSON (BSON) agrupados en colecciones, sin esquema fijo.

### Mongoose
**(Node.js)** ODM (*Object Document Mapper*) para [MongoDB](#mongodb). Permite definir **esquemas** con tipos y validaciones, y **modelos** para operar con las colecciones.
```js
const libroSchema = new mongoose.Schema({
  titulo: { type: String, required: true },
  precio: { type: Number, min: 0 },
});
const Libro = mongoose.model('Libro', libroSchema);
```

### Monolito
Aplicación desplegada como una única unidad que contiene toda la funcionalidad. Más sencilla de desarrollar y desplegar que los [microservicios](#microservicios).

### MVC
*Modelo-Vista-Controlador*. Patrón de arquitectura que separa la aplicación en:
* [Modelo](#modelo): datos y lógica de negocio.
* [Vista](#vista): presentación.
* [Controlador](#controlador): recibe la petición y coordina modelo y vista.

Es la base de la mayoría de los [frameworks](#framework) de servidor.

### MySQL / MariaDB
SGBD [relacionales](#base-de-datos-relacional) de código abierto, los más usados junto a PHP. MariaDB es una bifurcación (*fork*) de MySQL compatible con él. Herramientas de administración: phpMyAdmin, MySQL Workbench, DBeaver, Adminer.

---

## N

### N+1 (problema)
Problema de rendimiento en el que se hace una consulta para obtener N registros y luego una consulta adicional por cada uno para cargar sus relaciones (N+1 consultas en total). Se soluciona con **carga ansiosa** (*eager loading*), por ejemplo `Libro::with('autor')->get()` en [Eloquent](#eloquent).

### Namespace
Espacio de nombres. Agrupa clases, funciones y constantes para evitar conflictos de nombres. En PHP se declara con `namespace` y se importa con `use`. Se relaciona con la estructura de carpetas mediante [PSR-4](#psr).
```php
namespace App\Controllers;
use App\Models\Libro;
```

### NestJS
**(Node.js)** [Framework](#framework) para Node.js escrito en [TypeScript](#typescript), con arquitectura modular, decoradores e [inyección de dependencias](#inyección-de-dependencias). Está muy inspirado en Angular y en Spring, y por debajo usa [Express](#express) (o Fastify).

### Nginx
[Servidor web](#servidor-web) y [proxy inverso](#proxy-inverso) de alto rendimiento, basado en eventos. Para ejecutar PHP delega en [PHP-FPM](#php-fpm) mediante FastCGI. No usa ficheros `.htaccess`.

### Node.js
Entorno de ejecución de JavaScript fuera del navegador, basado en el motor V8. Usa un modelo de E/S no bloqueante y [asíncrono](#asincronía) gestionado por el [event loop](#event-loop), con un único hilo principal. Su gestor de paquetes es [npm](#npm) y su framework web más popular, [Express](#express). Alternativas más recientes: **Deno** y **Bun**.

### node_modules
**(Node.js)** Carpeta en la que [npm](#npm) instala las dependencias del proyecto. No se sube al repositorio (se añade a `.gitignore`), porque se regenera con `npm install` a partir de [package.json](#packagejson) y `package-lock.json`.

### nodemon
**(Node.js)** Herramienta de desarrollo que reinicia automáticamente la aplicación cuando detecta cambios en los ficheros. Desde Node.js 18 existe la alternativa nativa `node --watch`.

### Normalización
Proceso de diseño de bases de datos [relacionales](#base-de-datos-relacional) que organiza las tablas para eliminar redundancias y anomalías, siguiendo las **formas normales** (1FN, 2FN, 3FN, FNBC…).

### NoSQL
Familia de bases de datos no relacionales, normalmente sin esquema fijo y pensadas para escalar horizontalmente. Tipos: documentales ([MongoDB](#mongodb)), clave-valor ([Redis](#redis)), columnares (Cassandra) y de grafos (Neo4j).

### npm
**(Node.js)** *Node Package Manager*. Gestor de paquetes de Node.js y registro público de paquetes. Comandos habituales: `npm init`, `npm install paquete` (con `-D` para dependencias de desarrollo), `npm run <script>` y `npm ci` (instalación exacta a partir del fichero *lock*). **npx** ejecuta un paquete sin instalarlo de forma global. Alternativas: **pnpm** y **Yarn**.

---

## O

### OAuth 2.0
Protocolo de [autorización](#autorización) delegada: permite que una aplicación acceda a recursos de un usuario en otro servicio sin conocer su contraseña, mediante un **token de acceso**. Es lo que hay detrás de "Iniciar sesión con Google/GitHub" (junto con [OpenID Connect](#openid-connect)).

### OPcache
Extensión de PHP que guarda en memoria el código ya compilado (*bytecode*) para no tener que analizar los scripts en cada petición. Mejora mucho el rendimiento en producción.

### OpenID Connect
Capa de [autenticación](#autenticación) construida sobre [OAuth 2.0](#oauth-20). Añade un *ID token* ([JWT](#jwt)) con la identidad del usuario.

### ORM
*Object-Relational Mapping*. Técnica y librería que permite trabajar con las tablas de una base de datos relacional como si fueran objetos del lenguaje, sin escribir SQL directamente. Ejemplos: [Eloquent](#eloquent), [Doctrine](#doctrine), [Hibernate](#hibernate)/[JPA](#jpa) y [Spring Data JPA](#spring-data-jpa) (Java), SQLAlchemy (Python), [Prisma](#prisma), Sequelize y TypeORM (Node.js). Para bases de datos documentales existen los ODM, como [Mongoose](#mongoose).

### OWASP
*Open Worldwide Application Security Project*. Fundación dedicada a la seguridad de las aplicaciones web. Su **OWASP Top 10** recoge los riesgos de seguridad más críticos (control de acceso roto, fallos criptográficos, inyección, configuración insegura…).

---

## P

### package.json
**(Node.js)** Fichero de manifiesto de un proyecto Node.js: nombre, versión, tipo de módulos, *scripts* y dependencias (`dependencies` y `devDependencies`) con rangos de [versionado semántico](#versionado-semántico). Las versiones exactas instaladas quedan fijadas en `package-lock.json`. Es el equivalente a `composer.json` en PHP o `pom.xml` en [Maven](#maven).
```json
{
  "name": "api-libros",
  "type": "module",
  "scripts": {
    "start": "node src/index.js",
    "dev": "node --watch src/index.js",
    "test": "vitest"
  },
  "dependencies": { "express": "^5.1.0" }
}
```

### Paginación
Dividir un listado grande de resultados en páginas. En SQL se implementa con `LIMIT` y `OFFSET` (o mediante cursores para grandes volúmenes).
```sql
SELECT * FROM libros ORDER BY id LIMIT 10 OFFSET 20; -- página 3
```

### Passport.js
**(Node.js)** [Middleware](#middleware) de [autenticación](#autenticación) para Express basado en **estrategias** intercambiables: local (usuario y contraseña), [JWT](#jwt), [OAuth 2.0](#oauth-20) con Google, GitHub, etc.

### Patrón de diseño
Solución general y reutilizable a un problema habitual de diseño de software. Ejemplos: Singleton, [Factory](#factory), Strategy, Observer, [Repositorio](#repositorio), [MVC](#mvc), [Front controller](#front-controller).

### Payload
Datos útiles que transporta una petición o un mensaje (por ejemplo, el JSON del [body](#body) o la carga de un [JWT](#jwt)).

### PDO
*PHP Data Objects*. Capa de abstracción de PHP para acceder a bases de datos con la misma interfaz independientemente del SGBD. Admite [consultas preparadas](#consulta-preparada) y [transacciones](#transacción).
```php
$pdo = new PDO('mysql:host=localhost;dbname=tienda;charset=utf8mb4', $user, $pass, [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
]);
```

### Perfil de Spring
**(Spring)** *Profile*. Mecanismo para activar una configuración y unos [beans](#bean) distintos según el [entorno](#entorno) (`dev`, `test`, `prod`). Se activa con `spring.profiles.active=prod` (o con la variable de entorno `SPRING_PROFILES_ACTIVE`) y hace que se cargue además el fichero `application-prod.properties`.

### Petición HTTP
*Request*. Mensaje que el cliente envía al servidor. Contiene: [método](#métodos-http), [URL](#url), versión del protocolo, [cabeceras](#cabeceras-http) y, opcionalmente, un [cuerpo](#body).
```
POST /login HTTP/1.1
Host: ejemplo.com
Content-Type: application/x-www-form-urlencoded

usuario=ana&password=secreto
```

### PHP
*PHP: Hypertext Preprocessor*. Lenguaje de programación interpretado, diseñado para el desarrollo web en servidor, que puede incrustarse en HTML. Ofrece [superglobales](#superglobales), [sesiones](#sesión), [PDO](#pdo), tipado opcional y orientación a objetos completa.

### PHP-FPM
*FastCGI Process Manager*. Gestor de procesos PHP que atiende las peticiones que le pasa el servidor web ([Nginx](#nginx) o [Apache](#apache-http-server)) por FastCGI. Es la forma habitual de ejecutar PHP en producción.

### PHPUnit
Framework de [tests](#test) unitarios estándar en PHP. Alternativa con sintaxis más expresiva: **Pest**.

### Plantilla
*Template*. Fichero que mezcla el HTML de la página con marcadores donde se insertan los datos, separando la presentación de la lógica. Motores: [Blade](#blade), [Twig](#twig), Smarty (PHP), [Thymeleaf](#thymeleaf) (Java), [EJS](#ejs) y [Pug](#pug) (Node.js), Jinja (Python). Ver [Vista](#vista).

### PM2
**(Node.js)** Gestor de procesos para Node.js en producción: mantiene la aplicación en ejecución, la reinicia si se cae, permite lanzar varias instancias (modo clúster) para aprovechar todos los núcleos y gestiona los [logs](#log).

### POST
[Método HTTP](#métodos-http) para enviar datos al servidor (crear recursos, enviar formularios). Los datos van en el [cuerpo](#body), no en la URL. No es [idempotente](#idempotencia). En PHP: `$_POST`. Tras procesar un formulario se recomienda el patrón **PRG** (*Post/Redirect/Get*) para evitar reenvíos al recargar.

### Prisma
**(Node.js)** [ORM](#orm) para Node.js y [TypeScript](#typescript). El modelo de datos se define en el fichero `schema.prisma`, a partir del cual genera un cliente con tipos y las [migraciones](#migración). Alternativas: **Sequelize**, **TypeORM** y **Drizzle**.

### Programación orientada a objetos
Paradigma basado en **objetos** (instancias de [clases](#clase)) que combinan datos y comportamiento. Principios: encapsulación, herencia, polimorfismo y abstracción. Ver [SOLID](#solid).

### Promesa
**(JavaScript)** *Promise*. Objeto que representa el resultado futuro de una operación [asíncrona](#asincronía). Puede estar *pendiente*, *cumplida* (`resolve`) o *rechazada* (`reject`). Se consume con `.then()` y `.catch()` o con [async/await](#async--await). `Promise.all()` espera a que se cumplan varias en paralelo.

### Proxy inverso
Servidor que se sitúa delante de uno o varios servidores de aplicaciones y recibe las peticiones de los clientes en su nombre. Se usa para [balancear carga](#balanceador-de-carga), terminar [TLS](#ssl--tls), [cachear](#caché) o servir ficheros estáticos. Ejemplos: [Nginx](#nginx), Traefik, Caddy.

### PSR
*PHP Standards Recommendations*. Recomendaciones del PHP-FIG para la interoperabilidad entre proyectos PHP. Destacan: **PSR-1/PSR-12** (estilo de código), **PSR-3** ([logging](#log)), **PSR-4** ([autocarga](#autocarga)), **PSR-7** (mensajes HTTP), **PSR-11** ([contenedor](#contenedor-de-servicios)), **PSR-15** ([middleware](#middleware)).

### Puerto
Número (0–65535) que identifica un servicio dentro de un equipo. Habituales: 80 (HTTP), 443 (HTTPS), 22 (SSH), 3306 (MySQL), 5432 (PostgreSQL), 6379 (Redis), 8000/8080 (servidores de desarrollo).

### Pug
**(Node.js)** Motor de [plantillas](#plantilla) para Express con una sintaxis basada en la indentación, sin etiquetas de cierre.

---

## Q

### Query builder
Constructor de consultas. API que permite crear consultas SQL encadenando métodos en lugar de escribir la cadena SQL a mano, con [consultas preparadas](#consulta-preparada) internamente.
```php
DB::table('libros')->where('precio', '<', 20)->orderBy('titulo')->get();
```

### Query string
Parte de la [URL](#url) tras el signo `?`, formada por pares `clave=valor` separados por `&`. En PHP se lee con `$_GET`.
```
https://ejemplo.com/buscar?q=php&pagina=2
```

---

## R

### Rate limiting
Limitación del número de peticiones que un cliente puede hacer en un periodo de tiempo, para proteger frente a abusos, fuerza bruta o denegación de servicio. Al superarlo se responde con `429 Too Many Requests`.

### Redirección
Respuesta que indica al cliente que debe ir a otra URL, mediante un [código 3xx](#código-de-estado-http) y la cabecera `Location`. Tras un `header('Location: ...')` en PHP conviene llamar a `exit`.
```php
header('Location: /panel');
exit;
```

### Redis
Almacén de datos clave-valor en memoria, muy rápido. Se usa como [caché](#caché), almacén de [sesiones](#sesión), [cola de trabajos](#cola-de-trabajos) o mensajería pub/sub.

### Repositorio
1. Almacén de código gestionado con [Git](#git).
2. Patrón de diseño que encapsula el acceso a datos tras una [interfaz](#interfaz) con métodos como `buscarPorId()` o `guardar()`, aislando la lógica de negocio de la tecnología de persistencia.

### req y res
**(Express)** Objetos que recibe cada manejador de ruta y [middleware](#middleware) de Express:
* `req` (petición): `req.params` (parámetros de la ruta), `req.query` ([query string](#query-string)), `req.body` (cuerpo; necesita `express.json()` o `express.urlencoded()`), `req.headers`, `req.cookies` (con el paquete `cookie-parser`).
* `res` (respuesta): `res.status(201)`, `res.json(objeto)`, `res.send(texto)`, `res.render('vista', datos)`, `res.redirect('/ruta')`, `res.set(cabecera, valor)`, `res.cookie(nombre, valor, opciones)`.

### ResponseEntity
**(Spring)** Clase que representa una [respuesta HTTP](#respuesta-http) completa: cuerpo, [código de estado](#código-de-estado-http) y [cabeceras](#cabeceras-http).
```java
@GetMapping("/{id}")
public ResponseEntity<Libro> ver(@PathVariable Long id) {
    return repo.findById(id)
        .map(ResponseEntity::ok)
        .orElse(ResponseEntity.notFound().build());
}
```

### Respuesta HTTP
*Response*. Mensaje que el servidor devuelve al cliente. Contiene: versión, [código de estado](#código-de-estado-http), [cabeceras](#cabeceras-http) y, opcionalmente, un [cuerpo](#body).
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>...
```

### REST
*REpresentational State Transfer*. Estilo de arquitectura para sistemas distribuidos con estos principios: cliente-servidor, [sin estado](#stateless), cacheable, interfaz uniforme (recursos identificados por URI y manipulados con métodos estándar), sistema en capas. Ver [API REST](#api-rest).

### Rollback
Deshacer una operación: los cambios de una [transacción](#transacción) no confirmada, una [migración](#migración) o un [despliegue](#despliegue) fallido.

### Router de Express
**(Express)** `express.Router()` crea un enrutador independiente con sus propias [rutas](#ruta) y [middleware](#middleware), que luego se monta bajo un prefijo. Sirve para organizar la aplicación en módulos.
```js
// routes/libros.js
const router = express.Router();
router.get('/', listar);
router.get('/:id', ver);
router.post('/', crear);
export default router;

// app.js
app.use('/api/libros', librosRouter);
```

### Ruta
Definición que asocia una URL (y un método) con el código que la atiende. Puede contener parámetros (`/libros/{id}`) y tener nombre para generar enlaces. Ver [Enrutamiento](#enrutamiento).

---

## S

### Sal
*Salt*. Valor aleatorio que se añade a una contraseña antes de calcular su [hash](#hash), para que dos contraseñas iguales den hashes distintos y no se puedan usar tablas precalculadas (*rainbow tables*). `password_hash()` la genera automáticamente.

### Sanitización
Limpiar o transformar un dato para eliminar caracteres no deseados o peligrosos (por ejemplo, quitar espacios o etiquetas). Complementa, pero no sustituye, a la [validación](#validación) y al [escape de salida](#escape-de-salida).

### Seeder
Clase o script que rellena la base de datos con datos iniciales o de prueba. Ver [Factory](#factory).
```bash
php artisan db:seed
```

### Serialización
Convertir un objeto o estructura de datos en un formato que se pueda almacenar o transmitir (JSON, XML, cadena serializada de PHP) y reconstruirlo después (*deserialización*). Deserializar datos que no son de confianza con `unserialize()` es peligroso.

### Servidor de aplicaciones
Servidor que ejecuta la lógica de la aplicación (por ejemplo [PHP-FPM](#php-fpm), [Tomcat](#tomcat), Gunicorn, el propio proceso de [Node.js](#nodejs)), normalmente detrás de un [servidor web](#servidor-web) o [proxy inverso](#proxy-inverso).

### Servidor web
Software que atiende las [peticiones HTTP](#petición-http): sirve ficheros estáticos y pasa las peticiones dinámicas al intérprete o [servidor de aplicaciones](#servidor-de-aplicaciones). Ejemplos: [Apache](#apache-http-server), [Nginx](#nginx), Caddy, LiteSpeed, IIS. PHP incluye uno para desarrollo: `php -S localhost:8000`.

### Servlet
**(Java)** Clase Java ([Jakarta EE](#jakarta-ee)) que atiende peticiones HTTP dentro de un contenedor de servlets como [Tomcat](#tomcat). Es la base sobre la que se construye [Spring MVC](#spring-mvc), a través del [DispatcherServlet](#dispatcherservlet).

### Sesión
Mecanismo para mantener información de un usuario entre peticiones, a pesar de que [HTTP](#http) no tiene estado. El servidor guarda los datos y el cliente solo conserva un identificador de sesión en una [cookie](#cookie) (`PHPSESSID`). Tras iniciar sesión hay que regenerar el identificador para evitar la **fijación de sesión**.
```php
session_start();
session_regenerate_id(true);
$_SESSION['usuario_id'] = $usuario['id'];
```

### SFTP / FTP
Protocolos de transferencia de ficheros. **FTP** no cifra las credenciales; **SFTP** funciona sobre [SSH](#ssh) y es el recomendado para subir ficheros a un servidor.

### Slug
Parte de una [URL](#url) que identifica un recurso de forma legible para personas y buscadores, normalmente generada a partir del título: en minúsculas, sin acentos ni caracteres especiales y con las palabras separadas por guiones.
En la URL `https://ejemplo.com/blog/introduccion-a-php`, el slug es `introduccion-a-php`. Mejora el SEO frente a URLs del tipo `post.php?id=42`.

### SOAP
*Simple Object Access Protocol*. Protocolo de servicios web basado en mensajes [XML](#xml) con un contrato formal descrito en WSDL. Más rígido y pesado que [REST](#api-rest); sigue presente en sistemas empresariales y administraciones.

### SOLID
Cinco principios de diseño orientado a objetos:
* **S**: Responsabilidad única: una clase debe tener un solo motivo para cambiar.
* **O**: Abierto/cerrado: abierto a extensión, cerrado a modificación.
* **L**: Sustitución de Liskov: las subclases deben poder usarse en lugar de su clase base.
* **I**: Segregación de interfaces: mejor varias interfaces específicas que una general.
* **D**: Inversión de dependencias: depender de abstracciones, no de implementaciones. Ver [Inyección de dependencias](#inyección-de-dependencias).

### Spring Boot
**(Java)** Proyecto de Spring que simplifica la creación de aplicaciones listas para producción. Aporta **autoconfiguración** según las dependencias presentes, [starters](#starter), servidor embebido ([Tomcat](#tomcat)), [Actuator](#actuator) y configuración externa en [application.properties](#applicationproperties--applicationyml). La aplicación arranca desde una clase anotada con `@SpringBootApplication`.
```java
@SpringBootApplication
public class TiendaApplication {
    public static void main(String[] args) {
        SpringApplication.run(TiendaApplication.class, args);
    }
}
```

### Spring Data JPA
**(Spring)** Módulo que genera automáticamente la implementación de los [repositorios](#repositorio) a partir de interfaces. Basta con extender `JpaRepository<Entidad, TipoDelId>` para obtener el [CRUD](#crud), la [paginación](#paginación) y la ordenación. Además, crea consultas a partir del nombre del método (*query methods*) o con `@Query`.
```java
public interface LibroRepository extends JpaRepository<Libro, Long> {
    List<Libro> findByAutorNombreOrderByTituloAsc(String nombre);

    @Query("SELECT l FROM Libro l WHERE l.precio < :max")
    List<Libro> baratos(@Param("max") BigDecimal max);
}
```

### Spring Framework
**(Java)** [Framework](#framework) de Java para aplicaciones empresariales, basado en la [inversión de control](#inversión-de-control) y la [inyección de dependencias](#inyección-de-dependencias). Está formado por módulos: Core, [Spring MVC](#spring-mvc), Spring WebFlux (programación reactiva), [Spring Data](#spring-data-jpa), [Spring Security](#spring-security)… [Spring Boot](#spring-boot) facilita su configuración.

### Spring Initializr
**(Spring)** Generador de proyectos Spring Boot (en start.spring.io y también integrado en los IDE). Permite elegir [Maven](#maven) o [Gradle](#gradle), la versión de Java y los [starters](#starter) que se quieren incluir.

### Spring MVC
**(Spring)** Módulo web de Spring basado en el patrón [MVC](#mvc) y en la API de [Servlets](#servlet). Los [controladores](#controlador) se definen con `@Controller`, si devuelven vistas (por ejemplo de [Thymeleaf](#thymeleaf)), o con `@RestController`, si devuelven datos que se serializan a [JSON](#json) con la librería Jackson.
```java
@RestController
@RequestMapping("/api/libros")
@RequiredArgsConstructor
public class LibroController {
    private final LibroService service;

    @GetMapping
    public List<Libro> listar() {
        return service.listar();
    }

    @PostMapping
    @ResponseStatus(HttpStatus.CREATED)
    public Libro crear(@Valid @RequestBody LibroDTO dto) {
        return service.crear(dto);
    }
}
```

### Spring Security
**(Spring)** Módulo de [autenticación](#autenticación) y [autorización](#autorización) de Spring. Funciona como una cadena de filtros (`SecurityFilterChain`) que se ejecuta antes de los controladores. Ofrece login por formulario, [autenticación básica](#autenticación-básica-http), [JWT](#jwt), [OAuth 2.0](#oauth-20), protección [CSRF](#csrf), codificación de contraseñas (`BCryptPasswordEncoder`, ver [bcrypt](#bcrypt)) y control de acceso por roles (`@PreAuthorize("hasRole('ADMIN')")`).

### SQL
*Structured Query Language*. Lenguaje estándar para gestionar bases de datos [relacionales](#base-de-datos-relacional). Se divide en DDL (`CREATE`, `ALTER`, `DROP`), DML (`SELECT`, `INSERT`, `UPDATE`, `DELETE`), DCL (`GRANT`, `REVOKE`) y control de transacciones (`COMMIT`, `ROLLBACK`).

### SSH
*Secure Shell*. Protocolo para conectarse de forma cifrada a un servidor remoto y ejecutar comandos. Admite autenticación con contraseña o, mejor, con par de claves pública/privada.

### SSL / TLS
Protocolos criptográficos que cifran la comunicación en red y autentican al servidor mediante certificados. SSL está obsoleto; hoy se usa **TLS** (1.2 y 1.3), aunque se siga diciendo "certificado SSL". Ver [HTTPS](#https).

### SSR
*Server-Side Rendering*. Generar el HTML completo de la página en el servidor y enviarlo al navegador. Es el modelo tradicional de PHP. Mejora el SEO y el tiempo de primera carga frente al renderizado solo en el cliente (CSR).

### Starter
**(Spring Boot)** Dependencia que agrupa todo lo necesario para una funcionalidad, con versiones compatibles entre sí: `spring-boot-starter-web`, `spring-boot-starter-data-jpa`, `spring-boot-starter-security`, `spring-boot-starter-validation`, `spring-boot-starter-thymeleaf`, `spring-boot-starter-test`…

### Stateless
*Sin estado*. Un sistema es *stateless* cuando cada petición contiene toda la información necesaria para procesarla y el servidor no recuerda nada de las anteriores. HTTP lo es; las [sesiones](#sesión) añaden estado. Las APIs con [JWT](#jwt) suelen ser *stateless*, lo que facilita la [escalabilidad](#escalabilidad) horizontal.

### Stream
1. **(Node.js)** Flujo de datos que se procesa por fragmentos (*chunks*) en lugar de cargarse entero en memoria. Los hay legibles, escribibles, dúplex y de transformación; `req` y `res` son streams. Resultan útiles para ficheros grandes, vídeo o descargas.
2. **(Java)** La *Stream API* es otra cosa: un conjunto de operaciones funcionales sobre colecciones (`filter`, `map`, `collect`…).

### Subida de ficheros
Envío de ficheros desde un formulario con `method="post"` y `enctype="multipart/form-data"`. En PHP llegan en `$_FILES` y se mueven con `move_uploaded_file()`. Precauciones: comprobar tamaño y tipo real (no fiarse de la extensión ni del tipo MIME enviado), renombrar el fichero y guardarlo fuera de la carpeta pública o sin permisos de ejecución. En Express se procesan con el middleware **multer**; en Spring, con un parámetro `MultipartFile`.

### Superglobales
Variables de PHP accesibles desde cualquier ámbito, que contienen la información de la petición y del entorno: `$_GET`, `$_POST`, `$_REQUEST`, `$_COOKIE`, `$_SESSION`, `$_FILES`, `$_SERVER`, `$_ENV` y `$GLOBALS`.

### Symfony
[Framework](#framework) PHP modular formado por componentes reutilizables (muchos de ellos usados también por [Laravel](#laravel) y otros proyectos). Usa [Twig](#twig) y [Doctrine](#doctrine) por defecto.

---

## T

### TCP/IP
Conjunto de protocolos en el que se basa Internet. **IP** se encarga del direccionamiento y encaminamiento de paquetes; **TCP** garantiza una entrega fiable y ordenada. HTTP/1.1 y HTTP/2 funcionan sobre TCP.

### Test
Prueba automatizada que verifica que el código funciona como se espera. Tipos:
* **Unitario**: prueba una unidad aislada (una clase o función).
* **De integración**: prueba varios componentes juntos (por ejemplo, con base de datos).
* **Funcional / end-to-end**: prueba la aplicación completa desde el punto de vista del usuario.

En TDD (*Test-Driven Development*) se escribe el test antes que el código. Herramientas: [PHPUnit](#phpunit) y Pest (PHP); **JUnit 5**, **Mockito** (dobles de prueba) y `@SpringBootTest`/`MockMvc` (Java/Spring); **Jest**, **Vitest**, el *test runner* nativo `node:test` y **Supertest** (peticiones HTTP a Express) en Node.js.

### Thymeleaf
**(Spring)** Motor de [plantillas](#plantilla) para Java integrado con [Spring MVC](#spring-mvc). Usa atributos HTML (`th:text`, `th:each`, `th:if`, `th:href="@{/libros}"`), por lo que las plantillas siguen siendo HTML válido que se puede abrir directamente en el navegador.
```html
<tr th:each="libro : ${libros}">
  <td th:text="${libro.titulo}">Título de ejemplo</td>
</tr>
```

### Token
Cadena que representa una credencial o un permiso. Ejemplos: el identificador de [sesión](#sesión), el token [CSRF](#csrf), un [JWT](#jwt), un token de acceso de [OAuth](#oauth-20), un enlace de recuperación de contraseña. Debe generarse con un generador aleatorio criptográficamente seguro (`random_bytes()` en PHP).

### Tomcat
**(Java)** Contenedor de [Servlets](#servlet) y [servidor web](#servidor-web) de la fundación Apache para aplicaciones Java. Spring Boot lo incluye embebido por defecto; las alternativas son Jetty y Undertow.

### Transacción
Conjunto de operaciones sobre la base de datos que se ejecutan como una unidad: o se confirman todas (`COMMIT`) o se deshacen todas (`ROLLBACK`). Cumplen las propiedades [ACID](#acid).
```php
$pdo->beginTransaction();
try {
    $pdo->prepare('UPDATE cuentas SET saldo = saldo - ? WHERE id = ?')->execute([100, 1]);
    $pdo->prepare('UPDATE cuentas SET saldo = saldo + ? WHERE id = ?')->execute([100, 2]);
    $pdo->commit();
} catch (Exception $e) {
    $pdo->rollBack();
}
```

### Twig
Motor de [plantillas](#plantilla) para PHP usado por [Symfony](#symfony). Sintaxis: `{{ variable }}` para imprimir (con escape automático) y `{% ... %}` para lógica.

### TypeScript
Superconjunto de JavaScript que añade tipado estático y se compila (*transpila*) a JavaScript. Muy usado en el backend con Node.js ([NestJS](#nestjs), [Prisma](#prisma)). Las versiones recientes de Node.js pueden ejecutar directamente ficheros `.ts` sencillos.

---

## U

### URI
*Uniform Resource Identifier*. Cadena que identifica un recurso. Una [URL](#url) es un tipo de URI que además indica cómo acceder a él.

### URL
*Uniform Resource Locator*. Dirección de un recurso en la web. Partes:
```
https://usuario@www.ejemplo.com:443/blog/articulo?id=7&lang=es#comentarios
\___/   \_____/ \_____________/ \_/\___________/ \____________/ \_________/
esquema usuario      host     puerto   ruta       query string   fragmento
```
El fragmento (`#...`) no se envía al servidor. Ver [Query string](#query-string) y [Slug](#slug).

### UTF-8
Codificación de caracteres Unicode, estándar en la web. Hay que usarla de forma coherente en todas las capas: ficheros fuente, cabecera `Content-Type`, `<meta charset>`, conexión a la base de datos (`utf8mb4` en MySQL) y funciones de cadena multibyte (`mb_*` en PHP).

---

## V

### Validación
Comprobar que los datos recibidos cumplen las reglas esperadas (obligatorio, tipo, longitud, formato, rango, unicidad…) antes de procesarlos. La validación en el cliente (HTML/JS) mejora la experiencia, pero **siempre** debe repetirse en el servidor, porque la del cliente se puede saltar. Ver [Filtrado de entrada](#filtrado-de-entrada). En Spring se usa [Bean Validation](#bean-validation); en Express, librerías como **express-validator**, **Zod** o **Joi**.
```php
$request->validate([
    'email' => 'required|email|unique:usuarios',
    'edad'  => 'required|integer|min:18',
]);
```

### Variable de entorno
Variable definida en el sistema operativo o en el proceso que configura la aplicación sin tocar el código: credenciales de la base de datos, claves de API, modo depuración… En desarrollo suelen guardarse en un fichero `.env`, que **nunca** debe subirse al repositorio. En PHP se leen con `getenv()`/`$_ENV`; en Node.js, con `process.env` (ver [dotenv](#dotenv)); en Spring, con `${VARIABLE}` en [application.properties](#applicationproperties--applicationyml) o `@Value`.
```
APP_ENV=local
DB_HOST=127.0.0.1
DB_PASSWORD=secreto
```

### Versionado de API
Estrategia para introducir cambios incompatibles en una [API](#api) sin romper a los clientes existentes: en la URL (`/api/v2/libros`), en una cabecera o en el tipo de contenido.

### Versionado semántico
*SemVer*. Convención de numeración `MAYOR.MENOR.PARCHE`: se incrementa MAYOR con cambios incompatibles, MENOR con funcionalidad nueva compatible y PARCHE con correcciones de errores. En [package.json](#packagejson) y en [Composer](#composer), `^1.4.2` admite actualizaciones menores y de parche (`<2.0.0`) y `~1.4.2` solo de parche (`<1.5.0`).

### Vista
En [MVC](#mvc), la capa de presentación: genera la salida (normalmente HTML) a partir de los datos que le pasa el [controlador](#controlador). Suele implementarse con [plantillas](#plantilla). No debe contener lógica de negocio.

### VPS
*Virtual Private Server*. Máquina virtual alquilada a un proveedor, con su propio sistema operativo y acceso de administrador (root). Ver [Hosting](#hosting).

---

## W

### WAF
*Web Application Firewall*. Cortafuegos que analiza el tráfico HTTP y bloquea ataques conocidos ([inyección SQL](#inyección-sql), [XSS](#xss)…). Ejemplos: ModSecurity, Cloudflare WAF.

### Webhook
Petición HTTP que un servicio envía automáticamente a una URL nuestra cuando ocurre un evento (un pago completado, un *push* en un repositorio). Es lo contrario de consultar periódicamente (*polling*). Se debe verificar su firma para comprobar el origen.

### WebSocket
Protocolo que establece un canal de comunicación **bidireccional y persistente** entre cliente y servidor sobre una única conexión TCP. Permite que el servidor envíe datos al cliente en tiempo real (chats, notificaciones, juegos). Alternativas: *long polling* y **Server-Sent Events** (SSE, solo servidor → cliente).

---

## X

### Xdebug
Extensión de PHP para depuración paso a paso (puntos de ruptura desde el IDE), *profiling* y análisis de cobertura de [tests](#test).

### XML
*eXtensible Markup Language*. Lenguaje de marcas para representar datos estructurados de forma jerárquica. Usado en [SOAP](#soap), RSS, ficheros de configuración y formatos documentales. En las APIs actuales ha sido desplazado en gran medida por [JSON](#json).

### XSS
*Cross-Site Scripting*. Ataque en el que se consigue inyectar JavaScript en una página que verán otros usuarios (por ejemplo, en un comentario), pudiendo robar cookies o actuar en su nombre. Tipos: **almacenado**, **reflejado** y **basado en DOM**. Se previene con el [escape de salida](#escape-de-salida), cookies `HttpOnly` y la cabecera **Content-Security-Policy** (CSP).

---

## Y

### YAML
*YAML Ain't Markup Language*. Formato de serialización de datos legible, basado en la indentación. Muy usado en ficheros de configuración ([Docker Compose](#docker-compose), [Symfony](#symfony), [CI/CD](#cicd)).
```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
```

---

## Z

### Zona horaria
Configuración que determina cómo se interpretan y muestran fechas y horas. Se recomienda almacenar las fechas en **UTC** en la base de datos y convertirlas a la zona del usuario al mostrarlas. En PHP: `date_default_timezone_set()` o la directiva `date.timezone` de `php.ini`.
