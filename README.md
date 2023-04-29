# PostgreSQL with PostGIS in Docker Compose

This repository contains a `docker-compose.yml` file for setting up a development environment with PostGIS, Adminer, and pgAdmin4. The configuration allows you to create, manage, and visualize your spatial data with ease.

## Prerequisites

- Docker: Install [Docker](https://www.docker.com/get-started) on your machine.
- Docker Compose: Install [Docker Compose](https://docs.docker.com/compose/install/) on your machine.

## Services

The `docker-compose.yml` file defines the following services:

1. **db**: A PostgreSQL database with PostGIS extension.
2. **adminer**: A lightweight web-based database administration tool.
3. **pgadmin**: A more advanced web-based database administration tool specifically designed for PostgreSQL.

## Usage

1. Clone this repository:

   ```
   git clone https://github.com/Roman-Blinkov/postgis-in-docker-compose.git
   cd postgis-in-docker-compose
   ```

2. Create a `.env` file in the root directory of the project with the following content:

   ```
   POSTGRES_USER=myuser
   POSTGRES_PASSWORD=mystrongpassword
   POSTGRES_DB=mydb
   POSTGRES_PORT=5432
   ADMINER_PORT=18088
   PGADMIN_DEFAULT_EMAIL=example@example.com
   PGADMIN_DEFAULT_PASSWORD=admin
   PGADMIN_PORT=5050
   ```

   Replace the values in the `.env` file with your desired configuration.

3. Run the following command in your terminal:

   ```
   docker-compose up -d
   ```

   This will download and run the necessary Docker images and create the containers.

4. Access the Adminer interface at `http://localhost:<ADMINER_PORT>` (e.g. `http://localhost:18088`). Log in using the following credentials:

   - System: PostgreSQL
   - Server: db
   - Username: `<POSTGRES_USER>` (from the `.env` file)
   - Password: `<POSTGRES_PASSWORD>` (from the `.env` file)

5. Access the pgAdmin4 interface at `http://localhost:<PGADMIN_PORT>` (e.g. `http://localhost:5050`). Log in using the following credentials:

   - Email: `<PGADMIN_DEFAULT_EMAIL>` (from the `.env` file)
   - Password: `<PGADMIN_DEFAULT_PASSWORD>` (from the `.env` file)

## Volumes

The following volumes are defined in the `docker-compose.yml` file:

- **./postgisdata**: Stores the PostgreSQL database files with PostGIS extension.
- **./pgadmin**: Stores the pgAdmin4 configuration and session files.

These volumes persist the data on your local machine, so you can safely stop and remove the containers without losing your data.

## Ports

The following ports are exposed by the containers and can be customized through the `.env` file:

- **db**: `${POSTGRES_PORT:-5432}` (PostgreSQL)
- **adminer**: `${ADMINER_PORT:-18088}` (Adminer)
- **pgadmin**: `${PGADMIN_PORT:-5050}` (pgAdmin4)

## License

This project is licensed under the MIT License.
