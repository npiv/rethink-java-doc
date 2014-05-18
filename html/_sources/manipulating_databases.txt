######################
Manipulating Databases
######################

--------
dbCreate
--------
Create a database. A RethinkDB database is a collection of tables, similar to relational databases.

If successful, the operation returns a :java:ref:`DDLResult` {created=1}. If a database with the same name already exists the operation throws :java:ref:`RethinkDBException`.

Note: that you can only use alphanumeric characters and underscores for the database name.

Example:

.. code-block:: java
    
     DDLResult result = r.dbCreate("db").run(connection);

------
dbDrop
------
Drop a database. The database, all its tables, and corresponding data will be deleted.

If successful, the operation returns the object :java:ref:`DDLResult` {dropped=1}. If the specified database doesn't exist a :java:ref:`RethinkDBException` is thrown.

Example: Drop a database named 'superheroes'.

.. code-block:: java
    
     DDLResult result = r.dbDrop("db").run(connection);

------
dbList
------
List all database names in the system. The result is a list of strings.

Example: 

.. code-block:: java
    
     List<String> result = r.dbList().run(connection);

