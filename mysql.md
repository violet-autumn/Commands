### MYSQL Commands

##### Connecting to a MySQL instance from gcloud
```
gcloud sql connect <instance-name> --user=root --quiet
```

##### Show all databases and select a database
```
SHOW DATABASES;
USE <database-name>;
```

##### Store database name in a variable 
```
SELECT @dbname:='<database-name>';
```

##### Show the total size of a database
```
SELECT
  SUM(ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024)) AS `Size (MB)`
FROM
  information_schema.TABLES
WHERE 
  TABLE_SCHEMA = @dbname;
```

##### Show all tables in the database
```
SHOW TABLES;
```

##### Show the name and size of all the tables (in MB) in the database
```
SELECT
  TABLE_SCHEMA AS `Database`,
  TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM
  information_schema.TABLES
WHERE 
  TABLE_SCHEMA = @dbname;
```

##### Show the DDL of a specific table
```
SHOW CREATE TABLE <table-name>;
```


