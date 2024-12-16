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
// Se llama a la función `fetchRecentAnimes` del objeto `animesRecent`.
// Esta función probablemente realiza una solicitud (Con Nuestra Api) para obtener los animes recientes.
// La palabra clave `await` indica que esta función es asíncrona y que el código esperará
// a que se complete la operación antes de continuar.
const recentAnimes = await animesRecent.fetchRecentAnimes();

// Una vez que los animes recientes han sido obtenidos y almacenados en la variable `recentAnimes`,
// se imprimen en la consola del desarrollador para ver el contenido.
console.log(recentAnimes);
```

#### `getMostRecentUploadedAnime()`

* D**escripción**: Recupera información sobre el último anime subido, si ha habido uno nuevo desde la última búsqueda.
* **Devuelve**: Un objeto que contiene información sobre el último anime subido o nulo si no hay animes nuevos.
* **Test**:

```javascript
// Se llama al método `getMostRecentUploadedAnime` del objeto `animesRecent`.
// Este método probablemente devuelve el anime más reciente que fue subido.
// Dado que no se usa `await`, asumimos que el método es sincrónico y no devuelve una promesa.
const lastAnime = animesRecent.getMostRecentUploadedAnime();

// Imprime en la consola el contenido de `lastAnime`.
// Esto permite ver los detalles del anime más reciente subido (por ejemplo, nombre, episodio, fecha de subida, etc.).
console.log(lastAnime);
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
*

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

