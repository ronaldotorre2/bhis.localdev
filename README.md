## Next Local Development
This project provides a local development environment for Next bank applications, using docker compose to orchestrate services.


## Serviços utilizados

### POSTGRESQL

A relational database used to persist application data. The Postgres container is configured for local use, facilitating development and testing without the need for an external database.


### PGADMIN
Para acessar o banco de dados devem olhar no fonte que temos o .env_exemple, devem criar um arquivo local .env com o as informações do seu usuário localhost

```
.env
```

To access pgadmin use this url.

```
http://localhost:15433/login?next=/
```

### PRISMA
Prisma is a database versioning and migration automation tool. It executes versioned SQL scripts, applying changes to the database and maintaining a history of previous migrations. This ensures that all environments can evolve the database in a controlled and reproducible manner.

To rotate the prism, hold the commands
```
npx prisma migrate dev
```

For more information about the prism, access the official documentation

```
https://www.prisma.io/docs/
```



## Scripts de Migration
Prisma migration scripts should be placed in the folder:


```
migrations/sql/
```

Each script must follow the prism naming pattern, which is composed of year, month, date and 6 numbers, which can have 5 leading zeros and 1 number from 1 to 9. Here is an example:

```
20250530204913-CreatePerson
```

- The numbered composition becomes the version and migration number.
- The number represents the incremental execution order.
- After the numbers, a brief description of the migration.


Prisma executes scripts in order and maintains a history of applied migrations in the database itself, ensuring traceability and change control.


## How to use
1. Make sure the migration scripts are in`
/migrations/sql/`.
2. Bring up the environment with `docker compose up` to create the database container.


--- 

*The first time you run the container after pulling, it is recommended to access the container.


```
docker exec -it postgre sh
```

* Acess o postgre

```
postgre -u root -p
```

It is recommended to check first if it is logging in and working, if not, create the esys user and inform the privilege.

To exit, press \e then type the command exit;

---

For questions or problems, consult the official documentation for each tool or open an issue in this repository.


## Mandatory requirements

### Verify installation
1. Docker
2. Docker Compose


### Comands of docker

To upload localdev follow these steps:

```
docker compose up
```
This command searches for and downloads the respective images the first time it is run, builds the containers, and binds them for local use.

To kill localdev, proceed as follows:


```
docker compose down
```
This command checks the containers in this package and deletes them.

To close or pause without killing the containers:

```
In your terminal press ctrl + c
```

For more information about docker, see the material available at <https://www.docker.com/>
