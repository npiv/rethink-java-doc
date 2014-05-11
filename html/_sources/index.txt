###################
Rethink Java Driver
###################

Introduction
============

The Rethink Java Driver aims to closely mirror the existing ruby/python/js implementations. Due to limitations of java being a typed language some inspiration will be sought from existing java big data drivers like mongo to make the api as fluent as possible for the end user.

Milestones
==========
 * complete implementation of all methods in the `python api <http://rethinkdb.com/api/python/>`_
 * complete integration test of all methods. (these should grow together)
 * ORM module 
 * Spring data integration
 * DB connection pooling

Get involved
============
Development has only started recently. And whilst the first milestone should be hit within the next 2 weeks, there is still plenty to do. contact me on github, or send me a mail at nick.verlinde on the google mail.


########
Java API
########

Accessing REQL
==============

Placeholder


Manipulating Databases
======================

dbCreate
--------
Create a database. A RethinkDB database is a collection of tables, similar to relational databases.

If successful, the operation returns a :java:ref:`DMLResult` {created=1}. If a database with the same name already exists the operation throws :java:ref:`RethinkDBException`.

Note: that you can only use alphanumeric characters and underscores for the database name.

Example:

.. code-block:: java
    
     DMLResult result = r.dbCreate("db").run(connection);

dbDrop
------
Drop a database. The database, all its tables, and corresponding data will be deleted.

If successful, the operation returns the object :java:ref:`DMLResult` {dropped=1}. If the specified database doesn't exist a :java:ref:`RethinkDBException` is thrown.

Example: Drop a database named 'superheroes'.

.. code-block:: java
    
     DMLResult result = r.dbDrop("db").run(connection);

dbList
------
List all database names in the system. The result is a list of strings.

Example: 

.. code-block:: java
    
     List<String> result = r.dbList().run(connection);


Manipulating Tables
===================

tableCreate
-----------
Create a table. A RethinkDB table is a collection of JSON documents.

If successful, the operation returns a :java:ref:`DMLResult` {created=1}. If a table with the same name already exists, the operation throws :java:ref:`RethinkDBException`.

Note: that you can only use alphanumeric characters and underscores for the table name.

When creating a table you can specify the following options:

* primaryKey: the name of the primary key. The default primary key is id;
* durability: if set to 'soft', this enables soft durability on this table: writes will be 
* acknowledged by the server immediately and flushed to disk in the background. Default is 'hard' (acknowledgement of writes happens after data has been written to disk);
* datacenter: the name of the datacenter this table should be assigned to.

Example: Create a table named 'dc_universe' with the default settings.

.. code-block:: java
    
     DMLResult result = r.tableCreate("dc_universe").run(connection);

Possible Signatures: :java:ref:`RethinkQueryBuilder.tableCreate`

.. java:method:: public DMLResult tableCreate(String tableName) 

.. java:method:: public DMLResult tableCreate(String tableName, String pk, Durability durability, String datacenter) 

tableDrop
---------

tableList
---------