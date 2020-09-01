# Database design

### Primary Key
* Uniquely identify a particular record
* Must be unique within the table
* Can be any data type (always use Integers)
* Best PK don't have intrinsic relationship with the data
* Primary key stored in another table is called a Foreign Key
* PK and the FK MUST be the same data type


### Naming Conventions
* lowercase, snake_case
* Table names should lways be plural (users, posts, tweets)
* If no plural, just add lists at the end
* PK: id
* FK: singular table name + `_id` (user_id, post_id, tweet_id)

### Data Type (KAGGLE)
* varchar, text, integer, boolean, JSON(store an entire object?)
* phone number: varchar
* postal codes: 90210, 00215 (varchar) Otherwise get truncated
* URL varchar
* AWS S3 buket  Safe Secure Storage (you store the images, and keep the url)

### Relationships
* One to One: 1 record in the first table is related to 1 record in the 2nd table (1 could be zero)
* One to many: 1 record in the 1st table is related to 0/more records in the 2nd table
* Many to many: 1 or more records in the 1st table is related to 1 or more records in the 2nd table ( usually you have a 3rd table as the middle man)

### Dos and Don'ts
* Make fields required based on the initial save state of the record (NOT NULL)
* What data do you need to initialize the record (login, password, img? job?)
* Intelligent default values! (build-in functions) created_at timestamps NOW(), active boolean default to true
* Calculated fields! Don't use them! order total? age? full name?
* Customs functions are awesome!
* Try not to delete anything! regulate body want so check! record retention!

### ERD Entity Relationship Diagram (app.diagrams.net)
DBeaver - anlysis the DB and give you an ERD
