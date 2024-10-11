# Proyecto de Despliegue de Contenedores Multi-Entorno con Flask y PostgreSQL

---

## 📝 Índice de Contenidos

- [Acerca del Proyecto](#acerca-del-proyecto)
- [Comenzando](#comenzando)
  - [Prerequisitos](#prerequisitos)
  - [Instalación](#instalación)
- [Uso](#uso)
- [Despliegue](#despliegue)
- [Componentes del Proyecto y Arquitectura](#componentes-del-proyecto-y-arquitectura)
- [Pruebas Realizadas y Resultados](#pruebas-realizadas-y-resultados)
- [Construido con](#construido-con)
- [Autores](#autores)
- [Agradecimientos](#agradecimientos)

## 🧐 Acerca del Proyecto <a name="acerca-del-proyecto"></a>

Este proyecto es una aplicación web desarrollada con Flask que demuestra el despliegue de contenedores multi-entorno utilizando Docker. La aplicación se conecta a una base de datos PostgreSQL y utiliza Redis como sistema de caché. El objetivo es practicar y mostrar cómo configurar y ejecutar una aplicación en entornos de desarrollo y producción, asegurando la correcta interacción entre los servicios.

## 🏁 Comenzando <a name="comenzando"></a>

Estas instrucciones te guiarán para obtener una copia del proyecto y ejecutarlo en tu máquina local para propósitos de desarrollo y pruebas.

### Prerequisitos

Asegúrate de tener instalados los siguientes componentes en tu sistema:

Docker: Para crear y administrar contenedores.
Docker Compose: Para orquestar los contenedores de Docker.
Python 3.8 o superior: Para ejecutar scripts si es necesario.
Cliente de PostgreSQL (psql): Para interactuar con la base de datos.
Cliente de Redis (redis-cli): Para interactuar con Redis.

#### Instalación de Prerequisitos en Mac

En primer lugar, se asume que se tiene el gestor de paquetes Homebrew instalado, en caso contrario, instalarlo mediante el siguiente comando

```bash
 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Instalar Docker Desktop:**

Descarga e instala Docker Desktop para Mac desde la web de Docker Desktop.

**Instalar Cliente de PostgreSQL:**

```bash
 brew install postgresql
```

**Instalar Cliente de Redis:**

```bash
 brew install redis
```


### Instalación

Sigue estos pasos para configurar y ejecutar el proyecto:

1. **Clona este repositorio:**

```bash
 git clone https://github.com/tu_usuario/tu_repositorio.git
 cd tu_repositorio
```


2. **Construye y ejecuta los contenedores con Docker Compose:**

   - **Entorno de Desarrollo:**

     ```bash
     docker-compose -f docker-compose.dev.yml up --build
     ```

   - **Entorno de Producción:**

     ```bash
     docker-compose up --build
     ```

3. **Configura la base de datos:**

Conéctate al contenedor de PostgreSQL y crea la tabla necesaria:

```bash
 psql -h localhost -p 5432 -U edu -d usuarios
```

Ingresa la contraseña 0000 cuando se te solicite.

En el prompt de psql, ejecuta:

```sql
 CREATE TABLE usuarios (
     id SERIAL PRIMARY KEY,
     nombre VARCHAR(50) NOT NULL,
     email VARCHAR(100) NOT NULL,
     contraseña VARCHAR(100) NOT NULL
 );
```

4. **Inserta datos iniciales en la base de datos (opcional):**

```sql
 INSERT INTO usuarios (nombre, email, contraseña) VALUES ('Juan Pérez', 'juan.perez@example.com', 'password123');
```


5. **Establece mensajes en Redis (opcional):**

Conéctate a Redis:

```bash
 redis-cli -h localhost -p 6379
```
Establece un mensaje:

```bash
 set mensaje "Hola desde Redis"
```


## 🎈 Uso <a name="uso"></a>

Una vez que los contenedores estén en funcionamiento, puedes acceder a la aplicación web desde tu navegador en http://localhost:5000.

La aplicación mostrará:

Estado de la conexión a la base de datos.
Estado de la conexión a Redis.
Datos almacenados en la tabla usuarios.
Mensaje obtenido desde Redis.

## 🚀 Despliegue <a name="despliegue"></a>

Para desplegar este proyecto en un entorno en vivo, asegúrate de:

Configurar variables de entorno adecuadas para producción.
Utilizar métodos seguros para manejar credenciales y secretos.
Implementar prácticas de seguridad recomendadas para Docker y tus servicios.

## 📂 Componentes del Proyecto y Arquitectura <a name="componentes-del-proyecto-y-arquitectura"></a>

El proyecto consta de los siguientes componentes:

Aplicación Flask (app.py): Aplicación web que maneja las rutas y la lógica de negocio.
Base de Datos PostgreSQL: Almacena los datos de la aplicación.
Redis: Sistema de caché utilizado para almacenar datos temporales.
Docker: Utilizado para contenerizar la aplicación y sus servicios.
Docker Compose: Orquesta los diferentes contenedores y configura las redes y volúmenes necesarios.

### Diagrama de Arquitectura

texto


## 🔧 Pruebas Realizadas y Resultados <a name="pruebas-realizadas-y-resultados"></a>

### Prueba de Conexión a la Base de Datos

Descripción: Verificar que la aplicación puede conectarse a la base de datos y recuperar datos.
Procedimiento: Iniciar la aplicación y acceder a la ruta principal.
Resultado Esperado: Mostrar "Connected" para la base de datos y listar los datos de la tabla usuarios.
Resultado Obtenido: Conexión exitosa y datos mostrados correctamente.

### Prueba de Conexión a Redis

Descripción: Verificar que la aplicación puede conectarse a Redis y obtener valores almacenados.
Procedimiento: Establecer un valor en Redis y acceder a la ruta principal.
Resultado Esperado: Mostrar "Connected" para Redis y mostrar el mensaje almacenado.
Resultado Obtenido: Conexión exitosa y mensaje mostrado correctamente.

### Prueba de Inserción de Datos en Redis desde Consola

Descripción: Validar que los datos insertados en Redis desde la consola se reflejan en la aplicación.
Procedimiento: Utilizar redis-cli para establecer nuevos valores y actualizar la página web.
Resultado Esperado: Los nuevos valores aparecen en la sección correspondiente de la aplicación.
Resultado Obtenido: Los datos se muestran correctamente en la aplicación.

## ⛏️ Construido con <a name="construido-con"></a>

- Flask - Microframework web
- PostgreSQL - Base de datos relacional
- Redis - Sistema de caché en memoria
- Docker - Contenedores
- Docker Compose - Orquestación de contenedores
- Gunicorn - Servidor WSGI para aplicaciones Python

## ✍️ Autores <a name="autores"></a>

- Eduardo Bonnín Narváez - Desarrollo y documentación - TuGitHub

## 🎉 Agradecimientos <a name="agradecimientos"></a>

- A la comunidad de código abierto por su apoyo y contribuciones.