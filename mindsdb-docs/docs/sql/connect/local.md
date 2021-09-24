# MindsDB as a SQL Database

MindsDB provides a powerful MySQL API that allows to the users to connect to it using the [MySQL Command-Line Client](https://dev.mysql.com/doc/refman/8.0/en/mysql.html) or [DBeaver](https://dbeaver.io/). By default, MindsDB Server will start the HTTP and MySQL APIs. If you want to run only the MySQL API provide that as a parameter on the server start:

```
python3 -m mindsdb --api=mysql
```

This will start MySQL API on a `127.0.0.1:47335` with the `mindsdb` as a default user and create a `mindsdb` database. To change the deafult parameters you need to extend the MindsDBs `config.json` or create another config and send it as a parameter to the serve start command as:

```
python3 -m mindsdb --api=mysql --config=config.json
```

In case you are using Docker, visit the [Docker extend config docs](/deployment/docker/#extend-configjson).
To read more about avaiable config.json options check the [configuration docs](/datasources/configuration/#extending-default-configuration).

## Connect

Connecting to MySQL API is the same as connecting to MySQL database. The required parameters are:

* -h, --host: Host on which MySQL API is located(default 127.0.0.1)	
* --port: TCP/IP port number for connection(default 3306)	
* -u, --user: MySQL user name to use when connecting(default mindsdb)	
* -p, --password: Password to use when connecting(default no password)	

Open mysql-client and run:

```
mysql -h 127.0.0.1 --port 3306 -u mindsdb -p 
```

![Connect](/assets/sql/mysql-client.gif)


Or, if you are using another database manager interface make sure to select Driver for MySQL 8 and later.

![Connect](/assets/sql/connectdb.png)

## MindsDB Database

On the start mindsdb database will contain 2 tables `predictors` and `commands`. 

![Connect](/assets/sql/show.png)

All of the new trained machine learning models will be vissible as a new record inside the `predictors` table. The `predictors` columns contains information about each model as:

* name - The name of the model.
* status - Training stauts(training, complete, error).
* accuracy - The model accuracy.
* predict - The name of the target varaibale.
* select_data_query - SQL select query to create the datasource.
* external_datasource - Name of the pre existing datasource created from GUI.
* training options - Additional training parameters. The full list can be found at [PredictorInterface docs](/PredictorInterface/#learn).