# Docker-practical
Practical guide with Docker.
# Ejercicio: Instalar Docker y Ejecutar PostgreSQL en un Contenedor

## Paso 1: Instalar Docker

### En Ubuntu

1. **Actualizar el índice de paquetes:**

    ```sh
    sudo apt-get update
    ```

2. **Instalar paquetes necesarios para usar el repositorio de Docker a través de HTTPS:**

    ```sh
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    ```

3. **Agregar la clave GPG oficial de Docker:**

    ```sh
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```

4. **Configurar el repositorio estable de Docker:**

    ```sh
    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

5. **Instalar Docker Engine:**

    ```sh
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```

6. **Verificar la instalación de Docker:**

    ```sh
    sudo docker run hello-world
    ```

### En macOS

1. **Descargar e instalar Docker para Mac desde [Docker Desktop for Mac](https://www.docker.com/products/docker-desktop)**.

2. **Abrir Docker Desktop para Mac** y seguir las instrucciones para completar la instalación.

### En Windows

1. **Descargar e instalar Docker para Windows desde [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop)**.

2. **Abrir Docker Desktop para Windows** y seguir las instrucciones para completar la instalación.

## Paso 2: Descargar la Imagen de PostgreSQL

1. **Usar Docker para hacer pull de la imagen oficial de PostgreSQL:**

    ```sh
    docker pull postgres
    ```

## Paso 3: Lanzar un Contenedor de PostgreSQL en el Puerto 5432

1. **Ejecutar el contenedor de PostgreSQL en el puerto 5432:**

    ```sh
    docker run --name postgresdb -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
    ```

    - `--name my_postgres`:postgresdb #Nombre del contenedor.
    - `-e POSTGRES_PASSWORD=mysecretpassword`: Establece la contraseña del usuario `postgres`.
    - `-p 3032:5432`: Mapea el puerto 3032 del host al puerto 5432 del contenedor.
    - `-d`: Ejecuta el contenedor en segundo plano (detached mode).
    - `postgres`: Imagen de Docker a usar.

2. **Verificar que el contenedor esté corriendo:**

    ```sh
    docker ps
    ```

3. **Conectar a la base de datos PostgreSQL:**

    Puedes usar `psql`, pgAdmin o cualquier cliente de PostgreSQL para conectarte a la base de datos en `localhost:3032` usando las credenciales definidas (`postgres` y `mysecretpassword`).

## Resumen

Este ejercicio cubre cómo instalar Docker en varias plataformas, descargar una imagen de PostgreSQL y ejecutar un contenedor en un puerto específico. Estos pasos son fundamentales para empezar a trabajar con bases de datos en contenedores Docker.

