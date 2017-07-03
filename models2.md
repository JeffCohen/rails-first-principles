# Rails Models, Part 2

Thanks to the `ez` gem, you can get your database up and running quickly, skipping the more formal `Migrations` functionality in Rails.

### Database Schema

Your database schema will be generated automatically based on a description of your domain models.

Each domain model is translated into two physical artifacts:

1. A Ruby class derived from `ApplicationRecord`
2. A table in a relational database

By default, Rails will take care of constructing a SQLite3 database file for you, named `db/development.sqlite3`.  All of your
tables will live inside of this file.

You will never touch this file directly.  Modifying the schema (tables and columns) and managing the data (rows) is all 
done from Ruby.  

### 3-Step Recipe For Defining A Database-Backed Model

1. If you don't have a file named `db/models.yml`, run `rails db:migrate` to generate it.
2. Add the model definition to the `db/models.yml` file.
3. Run `rails db:migrate` to apply your specification to the database and to generate Ruby model classes, 
if necessary (see below).

Whenever you change `db/models.yml`, be sure to `rails db:migrate` to update your database.

Here's an example of how all of these things relate to each other:

```
# db/models.yml
Flight
  origin: text
  departure_time: time
  destination: text
  flight_number: text
  miles_earned: integer
```

```
# app/models/flight.rb
class Flight < ApplicationRecord`
end
```
TABLE: **flights**

|id|origin|departure_time|destination|flight_number|miles_earned|
|--|------|--------------|-----------|-------------|------------|
|14|ORD|9:40 am|JFK|133|705|
|15|LAX|12:19 pm|STL|501|1104|
|16|SEA|7:53 pm|SFO|242|489|
### Ruby Model Classes

Rails provides a component called _ActiveRecord_ to provide easy database acccess.  ActiveRecord adheres to a particular
pattern in computer science called an _object-relational mapper_ (ORM): it connects an object-oriented programming language (like Ruby)
to a relational database system (like SQLite3, Micosoft SQLServer, MySQL, Postgresql, Oracle, DB2, and more).

* _Models_ are simply Ruby classes that represent real-world things.
* In Rails, model files are expected to be in the `/app/models` folder.
* Database-backed models must derive from ApplicationRecord:  `class Flight < ApplicationRecord`.
* Model objects (instances) map to specific rows in the table, and object attributes map to specific column (cell) values.
* Use `rails console` to interact with your models and the live database.
* Learn how to "CRUD" data with model methods: `.create`, `.find_by`, `.where`, `.update`, and `.delete`
* Creating a new row can also be performed as a multi-step process: `.new` and then `.save`
