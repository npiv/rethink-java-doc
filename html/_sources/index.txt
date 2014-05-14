###################
Rethink Java Driver
###################

Introduction
============

The Rethink Java Driver aims to closely mirror the existing ruby/python/js implementations. Due to limitations of java being a typed language some inspiration will be sought from existing java big data drivers like mongo to make the api as fluent as possible for the end user.

At the same time with java 8 lambda syntax we should be able to get pretty close. The driver itself expects a minimum of java 1.6. But users using java 1.8 can do funky stuff like:

.. code-block:: java

	r.table("heros").filter(
		r.lambda(row->row.field("age").gt(20))
	).run(con);

Which pre java 1.8 would need to be invoked with an anonymous inner class like

	r.table("heros").filter(
		r.lambda(new DBLambda() {
              @Override
              public RTFluentRow apply(RTFluentRow row) {
              	  return row.field("age").gt(20);
              }
        })
	).run(con);

	// Alternatively you can create the class concretely to clean up your code. AdderLambda for example

	r.table("heros").filter(new AdderLambda(20)).run(con);

Both work. 

.. note::
	For the remainder of the documentation all the examples will use the Java 8 Lambda syntax where possible. If you are using a 1.6 library then all you have to do is convert it to the Anonymous inner class example. Or create a concrete class that implements :java:ref:`DBLambda`


Milestones
==========
 * complete implementation + documentation of core methods in the `python api <http://rethinkdb.com/api/python/>`_ See the left hand menu for what's there already 
 * ORM module
 * Spring data integration
 * DB connection pooling


Contribute
==========
Fork, submit an issue, contact me on github, or send me a mail at nick.verlinde on the google mail. I should be able to respond to any of those mediums within 24 hours.


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

If the connection cannot be established, a RqlDriverError exception will be thrown.

Possible Signatures see: :java:ref:`RethinkDB.connect`

Example: Opens a new connection to the database.

.. code-block:: java
	
	RethinkDBConnection connection = r.connect();


close
-----
Close an open connection.

Example: Close an open connection

.. code-block:: java
	
	conn.close();



reconnect
---------
Close and reopen a connection. 

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

.. note: 
	you can only use alphanumeric characters and underscores for the table name.

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


Math And Logic
==============

add
---
add 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").add(22)));

sub
---
sub 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").sub(22)));

mul
---
mul 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").mul(22)));

div
---
div 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").div(22)));

mod
---
get the modulus of 2 numbers

.. code-block:: java

	r.table("heros").filter(r.lambda(x.field("age").mod(2))); // get the even ages

and
---
Create an and clause.

.. code-block:: java

	r.table("heros").filter(row->
		r.and(
			row.field("name").eq("Adam")
			row.field("id").eq(1)
		)
	);


or
---
Create an or clause.

.. code-block:: java

	r.table("heros").filter(row->
		r.and(
			row.field("name").eq("Adam")
			row.field("name").eq("Eve")
		)
	);


eq
---
Specifiy an equals condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("name").eq("John")); // All the Johns	


ne
---
Specifiy a not equal condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("name").ne("John")); // everyone but John

gt
---
Specifiy a greater than condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").gt(10)); // everyone older than 10


ge
---
Specifiy a greater than or equal condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").ge(10)); // everyone older than or equal to 10

lt
---
Specifiy a less than condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").lt(10)); // everyone younger than 10

le
---
Specifiy a less than or equal condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").le(10)); // everyone younger than or equal to 10


not
---
todo: doc and test

