# Plugin de Moodle para reconocimiento de emciones

Plugin de bloque para Moodle que utiliza el servicio de `Amazon Rekognition` para hacer análisis de sentimientos de estudiantes en Moodle.

## Instalación del plugin

En su instalación de moodle, dentro de la carpeta `blocks` ejecute el siguiente comando.

```bash
git clone https://github.com/Gian12315/refactored-robot.git simplecamera
```

## Instalación de librerías PHP

```bash
composer require aws-project/stormwind:dev-dev
```

## Buildear los cambios al código Javascript en la carpeta amd.

El plugin utiliza lógica construida en Javascript, por lo que los cambios hecho a dicho código tendrán que ser buildeados para que el plugin pueda utilizarlo correctamente (ver más en: https://moodledev.io/docs/guides/javascript/modules), para esto se utiliza la herramienta `grunt`.

#### Instalar grunt.

```bash
npm install -g grunt-cli
```

> [!IMPORTANT] 
> Es necesario tener una versión de Node.js igual o mayor que 16 y menor o igual que 17 para instalar grunt.

#### Buildear el código.
```bash
npx grunt amd
```

O en caso de que vaya a estar haciendo cambios de manera frecuente:

```bash
npx grunt watch
```

Este último comando requiere la instalación de `Watchman`, en caso de que no lo tenga instalado, ejecute el siguiente comando:

#### Windows
```bash
scoop install watchman
```

#### MacOS
```bash
brew install watchman
```

#### Linux
En caso de que este ejecutando el proyecto en una distribución de Linux puede consultar la documentación de Watchman: https://facebook.github.io/watchman/docs/install.html

## Configuración de las variables de entorno

Como el plugin utiliza servicios de AWS y accede a la base de datos de Moodle, se requiere configurara un archivo `.env` con la siguiente estructura en la carpeta raiz del plugin:

```.env
AWS_REGION = your-aws-region
AWS_PUBLIC_KEY = your-public-key
AWS_SECRET_KEY = your-secret-key
DB_DIALECT = mysql | mariadb
DB_HOST = your-host
DB_NAME = moodle # Este es el nombre de la db de Moodle
DB_USER = your-user
DB_PASSWORD = your-password
```