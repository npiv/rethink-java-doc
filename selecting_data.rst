##############
Selecting Data
##############

--
db
--
Reference a database.

Example: Before we can query a table we have to select the correct database.

.. code-block:: java
	
	r.db("heroes").table("marvel").run(conn)

-----
table
-----
Select all documents in a table. This command can be chained with other commands to do further processing on the data.

Example: Return all documents in the table "marvel" of the default database.

.. code-block:: java
	
	r.table("marvel").run(conn)

---
get
---
Get a document by primary key.

Example: Find a document with the primary key "superman".

.. code-block:: java
	
	Map<String,Object> result = r.get("superman").run(con);

------
getAll
------
Get all documents where the given value matches the value of the requested index.

Example: Secondary index keys are not guaranteed to be unique so we cannot query via "get" when using a secondary index.

.. code-block:: java
	
	List<Map<String,Object>> results = r.getAll(
		Lists.newArrayList("man_of_steel"),"code_name"
	).run(con);

Example: Without an index argument, we default to the primary index. While get will either return the document or None when no document with such a primary key value exists, this will return either a one or zero length stream.

.. code-block:: java
	
	List<Map<String,Object>> results = r.getAll(
		Lists.newArrayList("man_of_steel")
	).run(con);

Example: You can get multiple documents in a single call to get_all.

.. code-block:: java

	List<Map<String,Object>> results = r.getAll(
		Lists.newArrayList("superman", "spiderman")
	).run(con);


------
filter
------
Get all the documents for which the given predicate is true.

filter can be called on a sequence, selection, or a field containing an array of elements. The return type is the same as the type on which the function was called on.

The body of every filter is wrapped in an implicit .default(False), which means that if a non-existence errors is thrown (when you try to access a field that does not exist in a document), RethinkDB will just ignore the document. The default value can be changed by passing the named argument default. Setting this optional argument to r.error() will cause any non-existence errors to return a RqlRuntimeError.

Example: Get all the users that are 30 years old.

.. code-block:: java

	List<Map<String,Object>> results = r.table("users").filter(
		r.row("age").eq(30)
	).run(c);

A more general way to write the same query is to use a lambda function. 

.. code-block:: java

	r.table("users").filter(
		user -> user.field("age").eq(30)
	).run(c);