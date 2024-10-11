# Práctica de Despliegue de Contenedores Multi-Entorno

---

## 📝 Índice

- [Acerca del Proyecto](#acerca-del-proyecto)
- [Set Up](#set-up)
- [Uso](#uso)
- [Componentes](#componentes)
- [Pruebas Realizadas y Resultados](#pruebas-realizadas-y-resultados)
- [Autores](#autores)

## 🧐 Acerca del Proyecto <a name="acerca-del-proyecto"></a>

Este proyecto es una práctica de la asignatura Redes Avanzadas que consiste en una aplicación web que muestra el despliegue de contenedores multi-entorno utilizando Docker. La aplicación se conecta a una base de datos PostgreSQL y utiliza Redis como sistema de caché. El objetivo es practicar y mostrar cómo configurar y ejecutar una aplicación en entornos de desarrollo y producción, asegurando la correcta interacción entre los servicios.

## 🏁 Set Up <a name="set-up"></a>

### Prerequisitos

- Docker: Para crear y administrar contenedores.
- Docker Compose: Para orquestar los contenedores de Docker.
- Python 3.8 o superior: Para ejecutar scripts si es necesario.
- Cliente de PostgreSQL (psql): Para interactuar con la base de datos.
- Cliente de Redis (redis-cli): Para interactuar con Redis.

#### Instalación de Prerequisitos en Mac

En primer lugar, se asume que se tiene el gestor de paquetes Homebrew instalado, en caso contrario, instalarlo mediante el siguiente comando

```bash
 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Instalar Docker Desktop:**

Descarga [Docker Desktop](https://www.docker.com/)

**Instalar Cliente de PostgreSQL:**

```bash
 brew install postgresql
```

**Instalar Cliente de Redis:**

```bash
 brew install redis
```

### Instalación

1. **Clona este repositorio:**

```bash
 git clone https://github.com/edubonnin/multi-environment-deployment-practice.git
 cd tu_repositorio
```

2. **Construye y ejecuta los contenedores con Docker Compose:**

   - **Entorno de Desarrollo:**

     ```bash
     docker-compose up --build
     ```

   - **Entorno de Producción:**

     ```bash
     docker-compose -f docker-compose.prod.yml up --build
     ```

3. **Configura la base de datos:**

Conéctate al contenedor de PostgreSQL:

```bash
 psql -h localhost -p 5432 -U edu -d usuarios
```

Ingresa la contraseña 0000 cuando se te solicite.

Crea la tabla necesaria en el prompt de psql:

```sql
 CREATE TABLE usuarios (
     id SERIAL PRIMARY KEY,
     nombre VARCHAR(50) NOT NULL,
     email VARCHAR(100) NOT NULL,
     contraseña VARCHAR(100) NOT NULL
 );
```

4. **Inserta datos iniciales en la base de datos:**

```sql
 INSERT INTO usuarios (nombre, email, contraseña) VALUES ('Juan Pérez', 'juan.perez@example.com', 'password123');
```

5. **Establece mensajes en Redis:**

Conéctate a Redis:

```bash
 redis-cli -h localhost -p 6379
```

Establece un mensaje:

```bash
 set mensaje "Hola desde Redis"
```

## 🎈 Uso <a name="uso"></a>

Una vez que los contenedores estén en funcionamiento, puedes acceder a la aplicación web desde tu navegador en http://localhost:5000

La aplicación muestra:

- Estado de la conexión a la base de datos
- Estado de la conexión a Redis
- Datos almacenados en la tabla usuarios
- Mensaje obtenido desde Redis

## 📂 Componentes <a name="componentes"></a>

- Aplicación Flask (app.py): Aplicación web que maneja las rutas y la lógica.
- index.html: Estructura básica del HTML.
- Base de Datos PostgreSQL: Almacena los datos de la aplicación.
- Redis: Sistema de caché que almacena datos temporales.
- Docker: Utilizado para contenerizar la aplicación y sus servicios.
- Docker Compose: Orquesta los diferentes contenedores y configura las redes y volúmenes necesarios.

## 🔧 Pruebas Realizadas y Resultados <a name="pruebas-realizadas-y-resultados"></a>

### Prueba de Conexión a la Base de Datos

- Descripción: Verificar que la aplicación puede conectarse a la base de datos y recuperar datos.
- Procedimiento: Iniciar la aplicación y acceder a la ruta principal.
- Resultado Esperado: Mostrar "Connected" para la base de datos y listar los datos de la tabla usuarios.
- Resultado Obtenido: Conexión exitosa y datos mostrados correctamente.

### Prueba de Conexión a Redis

- Descripción: Verificar que la aplicación puede conectarse a Redis y obtener valores almacenados.
- Procedimiento: Establecer un valor en Redis y acceder a la ruta principal.
- Resultado Esperado: Mostrar "Connected" para Redis y mostrar el mensaje almacenado.
- Resultado Obtenido: Conexión exitosa y mensaje mostrado correctamente.

### Prueba de Inserción de Datos en Redis desde Consola

- Descripción: Validar que los datos insertados en Redis desde la consola se reflejan en la aplicación.
- Procedimiento: Utilizar redis-cli para establecer nuevos valores y actualizar la página web.
- Resultado Esperado: Los nuevos valores aparecen en la sección correspondiente de la aplicación.
- Resultado Obtenido: Los datos se muestran correctamente en la aplicación.

## ✍️ Autores <a name="autores"></a>

Eduardo Bonnín Narváez - [GitHub](https://github.com/edubonnin)