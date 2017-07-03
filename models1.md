### Introduction to Models

*Also: see the [cheat sheet](console_crud.md) for how to manipulate the database.*

A _model_ is something that is a virtual representation of something else.  In a web application, a model is software represenation
of a real-world thing.

In Rails, a model is a simple Ruby class that happens to live under
`app/models`.  Methods and data members of the class are designed to
embody the rules, behavior, and policies of the real-world objects
they represent. For example,
to build the website for United Airlines, we would need represent
many real-world things: passengers, airplanes, reservations, flights,
airports, baggage, and boarding passes. Each of these real-world
entities would be represented by a model.

Most models also act as a source of data. A _Flight_ class would
not only provide an interface to learn about the origin, destination,
and list of passengers, but would also have the capability to
persist this information to a database.

In Rails, a model that wants to persist its data to a database
simply derives from a base class named `ApplicationRecord`.  

A naming convention is used to automatically associate a model
class to its underlying table in the database:

* Model class names are _singular nouns_
* Table names are the _plural_ version of the class name

```
Model Class Name            Database Table Name
------------------          -------------------
Flight                      flights
Person                      people
Product                     products
Movie                       movies
Octopus                     octopi
Mouse                       mice
```