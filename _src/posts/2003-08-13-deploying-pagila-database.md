    Title: deploying pagila database
    Date: 2003-08-13T16:11:29
    Tags: postgres, postgresql, database, pagila

_*pagila* is a popular postgres tutorial database._

<!-- more -->

* make sure superuser _postgres_ existing, or:

```bash
# create role postgres superuser password '888';
```

* create database _pagila_:

```bash
# create database pagila with owner postgres encoding 'UTF8';
```

* create _pagila_ schema:

```bash
$ psql -U postgres -f /xi/pagila-schema.sql pagila
```

* import data:

```bash
$ psql -U postgres -f /xi/pagila-data.sql pagila
```
