# Configuración de PrestaShop con Docker

Este proyecto te permite ejecutar PrestaShop utilizando Docker y Docker Compose. A continuación, se describen los pasos necesarios para configurar tu entorno.

## Requisitos

Necesitas ener Docker y Docker Compose instalados:

Los cescargué en estos enlaces:
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://github.com/docker/compose/releases)

## Pasos para ejecutar PrestaShop

### Paso 1: Creo directorio para el examen

Creo un directorio llamado examen_sxe

```bash
$ mkdir examen_sxe
$ cd examen_sxe

Paso 2: Crear el archivo docker-compose.yml
Dentro del directorio de mi proyecto, creo un archivo llamado docker-compose.yml y pego el contenido de este archivo:

version: '3'
services:
  mysql:
    image: mysql:5.7
    container_name: some-mysql
    environment:
      MYSQL_ROOT_PASSWORD: admin
    ports:
      - "3307:3306"
    networks:
      - prestashop-net

  prestashop:
    image: prestashop/prestashop
    container_name: some-prestashop
    environment:
      DB_SERVER: some-mysql
    ports:
      - "10.0.9.21"
    networks:
      - prestashop-net

networks:
  prestashop-net:

Explicación del docker-compose.yml

El archivo docker-compose.yml es un archivo que configura cómo se vana ejecutar los contenedores. 

Tiene dos servicios: mysql y prestashop.
Configuración para cada servicio, como la imagen a utilizar, el nombre del contenedor y las conexiones de red.
La versión de Docker Compose (3 en este caso).

Paso 3. Ejecutar contendedores

En la terminal de visual studio estando situado dentro de la carpeta del examen ejecuto el siguiente comando:
docker-compose up -d
El comando ejecutara contenedores según la configuración que puse en el docker compose. 

Paso 4: Acceder a PrestaShop en el navegador
Abro el navegador y pego lo siguiente:
En este caso es así ya que está es mi ip, variaría según el equipo.

http://10.0.9.21:8080

# ex_sxe
