# Proyecto de Despliegue de Contenedores Multi-Entorno con Flask y PostgreSQL

<div align="center">

[![Estado](https://img.shields.io/badge/estado-activo-success.svg)]()
[![Licencia](https://img.shields.io/badge/licencia-MIT-blue.svg)](/LICENSE)

</div>

---

## 📝 Tabla de Contenidos

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

## 🧐 Acerca del Proyecto <a name = "acerca-del-proyecto"></a>

Este proyecto es una aplicación web desarrollada con Flask que demuestra el despliegue de contenedores multi-entorno utilizando Docker. La aplicación se conecta a una base de datos PostgreSQL y utiliza Redis como sistema de caché. El objetivo es practicar y mostrar cómo configurar y ejecutar una aplicación en entornos de desarrollo y producción, asegurando la correcta interacción entre los servicios.

## 🏁 Comenzando <a name = "comenzando"></a>

Estas instrucciones te guiarán para obtener una copia del proyecto y ejecutarlo en tu máquina local para propósitos de desarrollo y pruebas.

### Prerequisitos

Asegúrate de tener instalados los siguientes componentes en tu sistema:

- **Docker**: Para crear y administrar contenedores.
- **Docker Compose**: Para orquestar los contenedores de Docker.
- **Python 3.8 o superior**: Para ejecutar scripts si es necesario.
- **Cliente de PostgreSQL (`psql`)**: Para interactuar con la base de datos.
- **Cliente de Redis (`redis-cli`)**: Para interactuar con Redis.

#### Instalación de Prerequisitos en Mac

**Instalar Docker Desktop:**

Descarga e instala Docker Desktop para Mac desde [Docker Desktop](https://www.docker.com/products/docker-desktop).

**Instalar Cliente de PostgreSQL:**

```bash
brew install postgresql
