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

r
-
The top-level ReQL namespace.

Example: Set up your top-level namespace.

.. code-block:: java

	private RethinkDB r = RethinkDB.r;


connect
-------
Create a new connection to the database server. The keyword arguments are:

* host: host of the RethinkDB instance. The default value is localhost.
* port: the driver port, by default 28015.
* db: the database used if not explicitly specified in a query, by default test.
* auth_key: the authentification key, by default the empty string.
* timeout: timeout period for the connection to be opened, by default 20 (seconds).

If the connection cannot be established, a RqlDriverError exception will be thrown.

Possible Signatures see: :java:ref:`RethinkDB.connect`

Example: Opens a new connection to the database.

.. code-block:: java
	
	RethinkDBConnection connection = r.connect();


close
-----
Close an open connection. Closing a connection waits until all outstanding requests have finished and then frees any open resources associated with the connection. 

TODO: implement noreply wait option

Example: Close an open connection

.. code-block:: java
	
	conn.close();


reconnect
---------
Close and reopen a connection. 

TODO: implement noreply wait option

Example: 

.. code-block:: java
	
	conn.reconnect();



use
---
Change the default database on this connection.

Example: Change the default database so that we don't need to specify the database when referencing a table.

.. code-block:: java

	conn.use("marvel");
	r.table("heroes").run(conn); // refers to r.db("marvel").table("heroes")


run
---

Run a query on a connection, returning either a single JSON result or a cursor, depending on the query.

TODO: implement additional options (use_outdated, time_format, profile and durability)

Example:

.. code-block:: java

	List<DBObject> results = r.table("mystuff").run(connection);


Manipulating Databases
======================

dbCreate
--------
Create a database. A RethinkDB database is a collection of tables, similar to relational databases.

If successful, the operation returns a :java:ref:`DDLResult` {created=1}. If a database with the same name already exists the operation throws :java:ref:`RethinkDBException`.

Note: that you can only use alphanumeric characters and underscores for the database name.

Example:

.. code-block:: java
    
     DDLResult result = r.dbCreate("db").run(connection);

dbDrop
------
Drop a database. The database, all its tables, and corresponding data will be deleted.

If successful, the operation returns the object :java:ref:`DDLResult` {dropped=1}. If the specified database doesn't exist a :java:ref:`RethinkDBException` is thrown.

Example: Drop a database named 'superheroes'.

.. code-block:: java
    
     DDLResult result = r.dbDrop("db").run(connection);

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

If successful, the operation returns a :java:ref:`DDLResult` {created=1}. If a table with the same name already exists, the operation throws :java:ref:`RethinkDBException`.

Note: that you can only use alphanumeric characters and underscores for the table name.

When creating a table you can specify the following options:

* primaryKey: the name of the primary key. The default primary key is id;
* durability: if set to 'soft', this enables soft durability on this table: writes will be 
* acknowledged by the server immediately and flushed to disk in the background. Default is 'hard' (acknowledgement of writes happens after data has been written to disk);
* datacenter: the name of the datacenter this table should be assigned to.

Example: Create a table named 'dc_universe' with the default settings.

.. code-block:: java
    
     DDLResult result = r.tableCreate("dc_universe").run(connection);

Possible Signatures: :java:ref:`RTDBQuery.tableCreate`

tableDrop
---------
Drop a table. The table and all its data will be deleted.

If succesful, the operation returns a :java:ref:`DDLResult` {"dropped": 1}. If the specified table doesn't exist a :java:ref:`RethinkDBException` is thrown.

Example: Drop a table named 'dc_universe'.

.. code-block:: java
	
	DDLResult result = r.tableDrop("dv_universe").run(connection);

tableList
---------

List all table names in a database. The result is a list of strings.

Example: List all tables of the 'test' database.

.. code-block:: java

	List<String> result = r.tableList().run(connection);


Writing Data
============

insert
------

Insert documents into a table. Accepts a single document or an array of documents.

The optional arguments are:

* durability: possible values are hard and soft. This option will override the table or query's durability setting (set in run). In soft durability mode RethinkDB will acknowledge the write immediately after receiving it, but before the write has been committed to disk.
* return_vals: if set to True and in case of a single insert/upsert, the inserted/updated document will be returned.
* upsert: when set to True, performs a replace if a document with the same primary key exists.
Insert returns an object that contains the following attributes:

See the doc of the returned :java:ref:`DMLResult` for a description of the attributes returned.

Possible Signatures: :java:ref:`RTFluentQuery.insert`

.. code-block:: java

	DMLResult result = r.rable("test").insert(
					   new DBObjectBuilder().with("name", "Jack").build(),
					   new DBObjectBuilder().with("name", "Jill").build()
			      ).run(connection);

	result.getInserted() // = 2	


get
---
Get a document by primary key.

Example: Find a document with the primary key 'superman'.

.. code-block:: java
	
	DBObject result = r.get("superman").run(con);


getAll
------
Get all documents where the given value matches the value of the requested index.

Possible Signatures: :java:ref:`RTFluentQuery.getAll`

Example: Secondary index keys are not guaranteed to be unique so we cannot query via "get" when using a secondary index.

.. code-block:: java
	
	List<DBObject> results = r.get("superman","spiderman").run(con);

between
-------
TODO: implement

filter
------
TODO: implement
