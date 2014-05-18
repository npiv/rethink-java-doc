##############
Accessing REQL
##############

--
r
--

The top-level ReQL namespace.

Example: Set up your top-level namespace.

.. code-block:: java

	private RethinkDB r = RethinkDB.r;


-------
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


-----
close
-----
Close an open connection.

Example: Close an open connection

.. code-block:: java
	
	conn.close();



---------
reconnect
---------
Close and reopen a connection. 

Example: 

.. code-block:: java
	
	conn.reconnect();



---
use
---
Change the default database on this connection.

Example: Change the default database so that we don't need to specify the database when referencing a table.

.. code-block:: java

	conn.use("marvel");
	r.table("heroes").run(conn); // refers to r.db("marvel").table("heroes")


---
run
---

Run a query on a connection, returning either a single JSON result or a cursor, depending on the query.

Example:

.. code-block:: java

	List<DBObject> results = r.table("mystuff").run(connection);

