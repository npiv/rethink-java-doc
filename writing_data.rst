############
Writing Data
############

------
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

---
get
---
Get a document by primary key.

Example: Find a document with the primary key 'superman'.

.. code-block:: java
	
	DBObject result = r.get("superman").run(con);

------
getAll
------
Get all documents where the given value matches the value of the requested index.

Possible Signatures: :java:ref:`RTFluentQuery.getAll`

Example: Secondary index keys are not guaranteed to be unique so we cannot query via "get" when using a secondary index.

.. code-block:: java
	
	List<DBObject> results = r.get("superman","spiderman").run(con);

------
between
-------
TODO: implement

------
filter
------
TODO: implement

