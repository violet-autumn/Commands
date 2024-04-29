### MYSQL Commands

##### Connecting to a CloudSQL instance from gcloud
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
SET @dbname:='<database-name>';
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

##### Show all tables in the database along with their primary keys
```
SELECT
  TABLE_NAME as `Table`,
  COLUMN_NAME as `Primary Key(s)`
FROM
  information_schema.COLUMNS
WHERE
  COLUMN_KEY='PRI' and TABLE_SCHEMA=@dbname;
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
  TABLE_SCHEMA = @dbname
ORDER BY
  (DATA_LENGTH + INDEX_LENGTH)
DESC;
```

##### Show the DDL of a specific table
```
SHOW CREATE TABLE <table-name>;
```

##### Create a new table
```
CREATE TABLE <table-name> (
<column-1> <datatype-of-column-1>,
<column-1> <datatype-of-column-1>,
PRIMARY KEY (<column-name>)
);
```

##### Insert data in a table
```
INSERT INTO <table-name> (<column-1>, <column-2>)
VALUES (<data-1>, <data-2>);
```
