# MySQL to Postgres Migrator

Sample project with basic docker-compose commands to migrate a mysql db to postgres db.

Put `.sql` files to `./data/mysql` for initialization.

Also postgres `.sql` files can be added to `./data/postgres` for postgres db initialization if needed.

## Initializating

```sh
docker-compose up -d mysqldb phpmyadmin postgresdb pgadmin
```

or

```sh
docker-compose up -d mysqldb postgresdb
```

## Migrating

Run after initializations are **complete**.

```sh
docker-compose run --rm pgloader pgloader mysql://root:admin@mysqldb/public postgresql://root:admin@postgresdb/bar
```

## Exporting

```sh
docker-compose exec postgresdb bash -c "pg_dump -U root bar > /output/bar.sql"
```
