# RDBMS - Relational DataBase Management System
* A server(database) that we can talk to with RDBMS
* psql is the RDBMS in vagrant
* the server can be hosted in cloud too

### Tabular Data
* Rows and columns (table like)
* Table === collection of related information
* Rows === records / one record is a single entity
* Columns === fields / adjustives, descript the entity that is stored

### Relational Databases
* Databases = collections of tables
* Relational DB === tables are all related to one another in some fashion

### SELECT Challenges
* Like GET, only retreive information
* No editing
* Aggregation - turn a bunch of records into a single value

> ```SQL
> SELECT COUNT(*) FROM users; //or// SELECT COUNT(id) FROM users;
> ```

* Capitalize the SQL command to improve readibility
* Separate the claues to different lines

2/ List users who are over age of 18
```SQL
SELECT *
FROM users; -- start with the backbone, and keep changes until you have it
WHERE age > 19 -- WHERE = filter for records return true
```

3/ List user who are over age of 18 and with last name "Barrows"
```SQL
SELECT *
FROM users
-- AND = && / " double quote are reserved for table name / field name
WHERE age > 19 AND lastname = 'Barrows';
-- String match is capital sensitive
```
* If error column doesn't exist, maybe typo, maybe double quote used by mistake

* 4/ List user who are over age of 18 and from Canada, and sorted by age from oldest to youngest, and ascending by last name
```SQL
SELECT *
FROM users
WHERE age > 18 AND counter = 'Canada';
-- default is ASC/ ORDER BY is like sort by
ORDER BY age DESC, last_name ASC -- chain ORDER BY request with comma ','
```

* 5/ List user who live in Canada and whose accounts are overdue (YYYYMMDD)
* If we need to change the time zone, we can do it on client side with moment
```SQL
SELECT *
FROM users
-- NOW() give dynamic date
WHERE counter = 'Canada' AND payment_due_date < NOW()
```

* 6/ List of user country with no duplicate

```SQL
-- DISTINCT only keep 1 instance
SELECT DISTINCT country
FROM users
ORDER BY country;
```

### 2 tables system
* SELECT create a new table that is readible for human

* 6/ List all of the albums with their song
* SELECT * is consider very poor practice, cause dev don't know what is in '*'
* Be specific and explicit with SELECT field

```SQL
SELECT album_name, artist_name, track_number, song_name
-- parent table as the first in JOIN/ one to many (preference)
  FROM albums
  -- if just id = album_id, ambigous error , there are two ids! which one?
  JOIN songs ON albums.id = album_id;
```
