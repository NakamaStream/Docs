---
icon: github-alt
cover: ../.gitbook/assets/NakamaStream.png
coverY: 42.495652173913044
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# OpenSource

NakamaStream es un proyecto OpenSource, lo que significa que está disponible de forma gratuita para todo el mundo. El código fuente se encuentra alojado en nuestro [repositorio oficial de GitHub](https://github.com/NakamaStream/NakamaStream), permitiendo que cualquier persona pueda crear su propia versión de NakamaStream sin infringir derechos legales. Sin embargo, es importante aclarar que no asumimos responsabilidad alguna sobre el uso que se haga del código.

**contribuyentes**

![](https://contrib.rocks/image?repo=NakamaStream/NakamaStream)

### Instalación y Desarrollo Local

#### 1. Clona este repositorio usando

```bash
$ git clone https://github.com/NakamaStream/NakamaStream.git
```

```bash
$ cd NakamaStream
```

#### 2. Instalación

#### Requisitos básicos

{% hint style="success" %}
Esta plataforma está construida sobre [Node.js](https://nodejs.org/) y utiliza [Express](https://expressjs.com/) para asegurar los tiempos de respuesta más rápidos posibles.
{% endhint %}

#### Instalar Express

```bash
$ npm list -g express
```

```bash
$ npm list express
```

#### Verificar instalaciones

* Verifique que tanto Node.js como Express estén instalados correctamente ejecutando.

```bash
$ node -v
$ npx express --version
```

#### Instalar Dependencias

* Puedes usar `npm` para instalar dependencias rápidamente para instalar todas las dependencias del proyecto.

```bash
$ npm install
```

#### 3. Iniciar proyecto en local host

* Ejecutar en modo de desarrollo

```bash
$ npm run dev
```

#### 4.  Configuracion

## captcha.yml <a href="#file-name-id" id="file-name-id"></a>

```yaml
# Dejas el archivo como esta al clonar el repositorio
```

## database.yml

Esta es la configuración principal de la web; para poder iniciar la base de datos, debe de ser del tipo [mysql](https://www.mysql.com/) para que funcione.

```yaml
# Configuración de conexión a la base de datos

# Esta sección contiene los parámetros necesarios para establecer una conexión 
#segura y exitosa con la base de datos.

# Dirección del host donde se encuentra alojada la base de datos.
host: 'Tu Host/Your Host'

# El nombre de usuario utilizado para autenticarse y acceder a la base de datos.
user: 'Tu usuario/Your Username'

# La contraseña asociada al usuario de la base de datos. Se recomienda encarecidamente 
# mantener esta información segura y confidencial.
password: 'Tu contraseña/Your password'

# El nombre de la base de datos a la que se desea conectar. Este nombre debe coincidir exactamente con el nombre 
# de la base de datos que se desea utilizar.
name: 'Nombre de la base de datos/Database name'
```

## email.yml

Esta configuración es para que el servicio de email funcione, así que es necesario configurar este archivo si quieres poder enviar email.

```yaml
nodemailer:
  # Especifica el servicio de correo electrónico que se utilizará.
  # En este caso, se utiliza Gmail para enviar correos.
  service: "gmail"

  # El nombre de usuario de la cuenta de correo electrónico que se utilizará para autenticar el envío de correos.
  # Debe ser la dirección de correo electrónico completa.
  user: "tucorreo/yourmail"

  # La contraseña de la cuenta de correo electrónico.
  # Se recomienda usar un "App Password" de Gmail en lugar de la contraseña de la cuenta para mayor seguridad.
  pass: "yourpass/tucontraseña"


resetPasswordBaseURL: "http://localhost:3000" # Dominio que usas para la web
resetPasswordSubject: "Restablecimiento de contraseña"
resetPasswordMessage: "Hola, por favor usa el siguiente enlace para restablecer tu contraseña: {link}. Este enlace expira en 1 hora."
```

## hcaptcha.yml

Este archivo es muy importante como  base de datos; para poder configurarlo, necesita tener creado CAPTCHA en la página oficial de ([hCaptcha](https://www.hcaptcha.com/))

```yaml
# Configuración de claves para integrar hCaptcha en los entornos de desarrollo y producción.
# hCaptcha es un servicio que ayuda a proteger tus aplicaciones contra bots.
# Asegúrate de reemplazar los valores con las claves proporcionadas por hCaptcha.

development:
  # Claves para el entorno de desarrollo (local o pruebas).
  # Reemplaza "TU_SITE_KEY" con tu clave pública de hCaptcha para desarrollo.
  site_key: "TU_SITE_KEY"
  
  # Reemplaza "TU_SECRET_KEY" con tu clave secreta de hCaptcha para desarrollo.
  # La clave secreta es confidencial. No la compartas ni la publiques.
  secret_key: "TU_SECRET_KEY"

production:
  # Claves para el entorno de producción (en vivo).
  # Reemplaza "TU_SITE_KEY" con tu clave pública de hCaptcha para producción.
  site_key: "TU_SITE_KEY"
  
  # Reemplaza "TU_SECRET_KEY" con tu clave secreta de hCaptcha para producción.
  # La clave secreta es confidencial. Asegúrate de mantenerla segura.
  secret_key: "TU_SECRET_KEY"

# Notas importantes:
# - "site_key" (clave pública) se usa en el frontend para inicializar el widget de hCaptcha.
# - "secret_key" (clave privada) se usa en el backend para verificar los tokens enviados por el cliente.
# - El entorno "development" es ideal para pruebas locales y no debería compartirse.
# - Asegúrate de mantener las claves de "production" fuera del alcance público.
# - No incluyas este archivo en repositorios públicos.
```

### Avertencia

{% hint style="warning" %}
> **Advertencia sobre el Uso de Contenido de Anime**
>
> Este proyecto puede involucrar el uso de contenido de anime que podría estar protegido por derechos de autor. Toma en cuenta lo siguiente:
>
> * **Riesgos Legales**: Las distribuidoras y propietarios de derechos de autor pueden tomar acciones legales contra el uso no autorizado de su contenido. Esto puede incluir demandas por infracción de copyright o la eliminación de tu sitio web o servicio.
> * **Alojamiento de Archivos Externos**: Si tu plataforma utiliza servicios de alojamiento de archivos externos para los animes, asegúrate de que el contenido que estás compartiendo cumpla con las leyes de derechos de autor y las políticas del servicio de alojamiento.
>
> Es tu responsabilidad asegurarte de que el contenido que utilizas no infrinja los derechos de los creadores y distribuidores. El incumplimiento puede resultar en consecuencias legales y la eliminación de tu plataforma.
{% endhint %}

### Licencia 📝

Este proyecto, denominado **NakamaStream**, ha sido desarrollado por un equipo pequeño y está bajo la licencia MIT. NakamaStream es un proyecto de código abierto, lo que significa que puedes utilizar, modificar y distribuir el código fuente de acuerdo con los términos de la licencia MIT.

#### Condiciones de Uso

1. **Permisos**:
   * Uso personal y comercial
   * Modificación
   * Distribución
   * Sublicencia
   * Uso privado
2. **Condiciones**:
   * Incluir una copia de esta licencia y el aviso de copyright en todas las copias o partes sustanciales del software.
3. **Limitaciones**:
   * El software se proporciona "tal cual", sin garantía de ningún tipo, expresa o implícita, incluyendo pero no limitándose a las garantías de comerciabilidad, idoneidad para un propósito particular y no infracción. En ningún caso los autores o titulares de derechos de autor serán responsables de cualquier reclamo, daño o responsabilidad, ya sea en una acción de contrato, agravio o de otro tipo, que surja de, o en conexión con el software o el uso u otros tratos en el software.

#### Responsabilidad

El uso que se le dé a nuestro código es bajo tu propia responsabilidad. El equipo de NakamaStream no se hace responsable de cualquier uso indebido o ilegal del código fuente proporcionado. Cualquier consecuencia derivada del uso de este software es exclusiva responsabilidad del usuario.
