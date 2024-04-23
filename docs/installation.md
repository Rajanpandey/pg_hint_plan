# Installation

This section describes the installation steps.

## Building binary module

Simply run `make` at the top of the source tree, then `make install` as an
appropriate user. The `PATH` environment variable should be set properly
to point to a PostgreSQL set of binaries:

    $ tar xzvf pg_hint_plan-1.x.x.tar.gz
    $ cd pg_hint_plan-1.x.x
    $ make
    $ su
    $ make install

## Loading `pg_hint_plan`

`pg_hint_plan` does not require `CREATE EXTENSION`.  Loading it with a `LOAD`
command will activate it and of course you can load it globally by setting
`shared_preload_libraries` in `postgresql.conf`.  Or you might be
interested in `ALTER USER SET`/`ALTER DATABASE SET` for automatic loading in
specific sessions.

```sql
postgres=# LOAD 'pg_hint_plan';
LOAD
```

If you are planning to use the hint table, run:
    CREATE EXTENSION pg_hint_plan;
    SET pg_hint_plan.enable_hint_table TO on;
