# DROP statement

The `DROP` statement is used to delete an existing model table or delete datasource integration.



## DROP TABLE statement

The `DROP TABLE` statement is used to delete the model table:

```
DROP TABLE table_name;
```

### DROP TABLE example

The following SQL statement drops the model table called `home_rentals_model`:

```
DROP TABLE home_rentals_model;
```

## DROP DATABASE statement

The `DROP DATABASE` statement is used to delete datasource integration database:

```
DROP DATABSE integration_name
```

### DROP DATABASE example

The following SQL statement drops the integration database called `psql_rentals`:

```
DROP TABLE psql_rentals;
```