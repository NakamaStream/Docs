---
icon: webhook
---

# Uso de api

NakamaStream ofrece una serie de APIs públicas diseñadas para facilitar el acceso a la información de los animes disponibles en nuestra plataforma. Aunque el número de APIs disponibles es limitado, cada una de ellas ha sido desarrollada para cubrir funciones esenciales y garantizar que los usuarios puedan interactuar eficientemente con los datos que ofrecemos.

## Método Node.js

### Instalación:

Para instalar NakamaStream Lib, simplemente use npm:

```bash
$ npm install nakamastream-lib
```

### Módulos Actuales

Los siguientes módulos están actualmente disponibles en NakamaStream Lib:

```javascript
const AnimesRecent = require('./lib/AnimesRecent');
const AnimesAll = require('./lib/AnimesAll');
const CaptchaService = require('./lib/auth/CaptchaService');

module.exports = {
  AnimesRecent,
  AnimesAll,
  CaptchaService
};
```

## AnimesRecent

### Métodos

#### `fetchRecentAnimes()`

* **Descripción**: Realiza una solicitud GET a la API para recuperar una lista de animes recientes. Esta función se adhiere a un límite de velocidad definido, lo que garantiza que las solicitudes a la API no se realicen con más frecuencia de la permitida.
* **Devuelve**: una promesa que se resuelve en una serie de objetos que representan los animes recientes.
* **Errores**: arroja un error si se excede el límite de velocidad o si hay un problema al obtener los animes.
* **Test**:

```javascript
/**
 * Importa la clase AnimesRecent de la librería nakamastream-lib para interactuar con la API
 */
const { AnimesRecent } = require('nakamastream-lib');

/**
 * Función autoejecutable asíncrona que demuestra el uso de la clase AnimesRecent
 * para obtener y mostrar información sobre animes recientes.
 * 
 * Esta función:
 * 1. Crea una instancia de AnimesRecent
 * 2. Obtiene la lista de animes recientes
 * 3. Muestra el último anime cargado
 * 4. Maneja posibles errores durante la ejecución
 */
(async () => {
  // Crear una instancia de la clase AnimesRecent con configuración por defecto
  const animesRecent = new AnimesRecent();

  try {
    // Obtiene la lista de animes recientes desde la API
    const recentAnimes = await animesRecent.fetchRecentAnimes();

    // Muestra la lista completa de animes recientes
    console.log('Animes recientes:', recentAnimes);

    // Obtiene y muestra información sobre el anime más recientemente cargado
    const latestAnime = animesRecent.getMostRecentUploadedAnime();
    if (latestAnime) {
      console.log('Último anime cargado:', latestAnime);
    } else {
      console.log('No hay un nuevo anime cargado.');
    }
  } catch (error) {
    // Captura y muestra cualquier error que ocurra durante la ejecución
    console.error('Error al obtener animes recientes:', error.message);
  }
})();
```

#### `getMostRecentUploadedAnime()`

* D**escripción**: Recupera información sobre el último anime subido, si ha habido uno nuevo desde la última búsqueda.
* **Devuelve**: Un objeto que contiene información sobre el último anime subido o nulo si no hay animes nuevos.
* **Test**:

```javascript
/**
 * Script para obtener y mostrar el último anime agregado usando la librería nakamastream-lib
 * 
 * Este script crea una instancia de AnimesRecent, obtiene la lista de animes recientes
 * y muestra el último anime agregado. Si hay errores durante el proceso, los maneja
 * apropiadamente.
 * 
 * @requires nakamastream-lib
 */

const { AnimesRecent } = require('nakamastream-lib'); // Asegúrate de que el archivo se llame AnimesRecent.js

/**
 * Función autoejecutable asíncrona que maneja la lógica principal
 * 
 * Esta función realiza los siguientes pasos:
 * 1. Crea una instancia de AnimesRecent
 * 2. Obtiene la lista de animes recientes
 * 3. Obtiene y muestra el último anime agregado
 * 4. Maneja cualquier error que pueda ocurrir durante el proceso
 */
(async () => {
  // Crear una instancia de la clase AnimesRecent
  const animesRecent = new AnimesRecent();

  try {
    // Llamar a fetchRecentAnimes para actualizar la lista de animes recientes
    await animesRecent.fetchRecentAnimes();

    // Llamar a getMostRecentUploadedAnime para obtener el último anime cargado
    const latestAnime = animesRecent.getMostRecentUploadedAnime();

    if (latestAnime) {
      console.log('Último anime cargado:', latestAnime);
    } else {
      console.log('No hay un nuevo anime cargado o no se ha actualizado la lista.');
    }
  } catch (error) {
    // Manejar errores
    console.error('Error al obtener el último anime cargado:', error.message);
  }
})();
```

## AnimesAll

### Métodos

#### `fetchAllAnimes()`

* **Descripción**: Realiza una solicitud GET a la API para recuperar la lista completa de animes. Este método se adhiere a un límite de velocidad definido para evitar solicitudes demasiado frecuentes a la API.
* **Devuelve**: una promesa que se resuelve en una serie de objetos que representan todos los animes.
* **Errores**: arroja un error si se excede el límite de velocidad o si hay un problema al obtener los animes.
* **Test:**

```javascript
try {
  // Se intenta ejecutar la función `fetchAllAnimes` del objeto `animesAll`.
  // Esta función realiza una solicitud para obtener una lista completa de animes.
  // La palabra clave `await` indica que este es un proceso asíncrono y se esperará su resultado.
  const allAnimes = await animesAll.fetchAllAnimes();

  // Si la operación anterior es exitosa, se imprime en la consola la lista de todos los animes obtenidos.
  console.log(allAnimes);
} catch (error) {
  // Si ocurre un error durante la ejecución de `fetchAllAnimes` (por ejemplo, un problema de red o
  // una respuesta de error del servidor), el programa captura el error aquí.
  // `error.message` imprime el mensaje de error específico para que sea más fácil de depurar.
  console.error(error.message);
}

```

#### `searchAnimes(query)`

* **Descripción**: Busca animes por título en los datos almacenados en caché.
**Parámetros**:
* `query` (string): El término de búsqueda para filtrar animes por título.
* **Devuelve**: una serie de objetos de anime que coinciden con el término de búsqueda. Devuelve una matriz vacía si no hay caché disponible.
* **Test:**

```javascript
// Se llama al método `searchAnimes` del objeto `animesAll`.
// Este método realiza una búsqueda en una lista o base de datos de animes,
// utilizando el término 'Death Note' como criterio.
// Dado que no se usa `await`, asumimos que el método es sincrónico y devuelve los resultados de inmediato.
const results = animesAll.searchAnimes('Death Note');

// Se imprimen los resultados de la búsqueda en la consola.
// Esto permite al desarrollador inspeccionar el contenido devuelto por `searchAnimes`.
console.log(results);
```

#### `getCachedAnimes()`

* **Descripción**: recupera los datos de anime almacenados en caché sin realizar una nueva solicitud de API.
* **Devuelve**: la matriz almacenada en caché de objetos de anime o nula si no existe caché.
* **Test**:

```javascript
// Se llama al método `getCachedAnimes` del objeto `animesAll`.
// Este método probablemente obtiene los animes almacenados en caché, es decir, datos que han sido previamente guardados
// para evitar hacer solicitudes repetitivas a la base de datos o API. El resultado se guarda en la variable `cachedData`.
const cachedData = animesAll.getCachedAnimes();

// Se verifica si `cachedData` tiene algún valor.
// Si la caché contiene datos (es decir, no es `null` o `undefined`), se ejecuta el bloque de código dentro del `if`.
if (cachedData) {
  // Si hay datos en caché, se imprimen en la consola con un mensaje indicando que se están usando datos almacenados.
  console.log('Using cached data:', cachedData);
}

```

## CaptchaService

### Métodos

#### `getNewCaptcha()`

Obtiene un nuevo captcha de la API.

* **Devuelve:** `Promise`: una promesa que se resuelve en los datos captcha.
* **Test**:

```javascript
try {
    // Se llama al método `getNewCaptcha` del objeto `captchaService`.
    // Este método realiza una solicitud asíncrona (a nuestra Api) para obtener un nuevo captcha.
    // La palabra clave `await` indica que el código esperará hasta que el captcha sea obtenido antes de continuar.
    const captcha = await captchaService.getNewCaptcha();

    // Si la solicitud para obtener el captcha es exitosa, se imprime en la consola el objeto `captcha`.
    // El mensaje indica que el captcha fue obtenido correctamente.
    console.log('Captcha obtained:', captcha);
} catch (error) {
    // Si ocurre un error durante la ejecución del código dentro del bloque `try`, el flujo de ejecución se mueve al bloque `catch`.
    // Aquí se captura el error y se muestra un mensaje en la consola con la descripción del problema.
    console.error('Error fetching captcha:', error.message);
}

```

#### `handleApiError(error)`

Maneja errores de solicitudes de API.

* **Parámetros**:&#x20;
* \- `error` `(Error)`: El objeto de error lanzado durante la solicitud. - **Lanza:** Lanza un error más descriptivo según la respuesta.
* **Test:**

Este método se llama internamente dentro de `getNewCaptcha()` y no es necesario llamarlo directamente.
