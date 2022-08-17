### Swith database

```
\c db_name
```

### Delete a range of rows from ids

```
DELETE FROM your_table WHERE id BETWEEN bottom_value AND top_value;
```
### Count num of rows in a table

```
SELECT COUNT(*) FROM db_name;
```
### POSTGRES TO JSON
[DBA EXCHANGE](https://dba.stackexchange.com/questions/90482/export-postgres-table-as-json)

### Script to drop all tables in a specific database
```
DO $$ 
  DECLARE 
    r RECORD;
BEGIN
  FOR r IN 
    (
      SELECT table_name 
      FROM information_schema.tables 
      WHERE table_schema=current_schema()
    ) 
  LOOP
     EXECUTE 'DROP TABLE IF EXISTS ' || quote_ident(r.table_name) || ' CASCADE';
  END LOOP;
END $$ ;
```
### Restore with psql
```
psql -U username -d db_name -f path_to_backupfile
```
