############
Writing Data
############

------
insert
------

Insert documents into a table. Accepts a single document or an array of documents.

The optional arguments are:

* durability: possible values are hard and soft. This option will override the table or query"s durability setting (set in run). In soft durability mode RethinkDB will acknowledge the write immediately after receiving it, but before the write has been committed to disk.
* return_vals: if set to True and in case of a single insert/upsert, the inserted/updated document will be returned.
* upsert: when set to True, performs a replace if a document with the same primary key exists.
Insert returns an object that contains the following attributes:

See the doc of the returned :java:ref:`DMLResult` for a description of the attributes returned.

see `Python Doc <http://rethinkdb.com/api/python/insert/>`_ for full capabilites

.. code-block:: java

	DMLResult result = r.rable("test").insert(
					   new MapObject().with("name", "Jack"),
					   new MapObject().with("name", "Jill")
			      ).run(connection);

	result.getInserted() // = 2	


signatures:

.. code-block:: java

	public Insert insert(Map<String,Object> dbObject, Durability durability, Boolean returnVals, Boolean upsert);
	public Insert insert(Map<String,Object>... dbObject);
	public Insert insert(List<Map<String,Object>> dbObjects);
	public Insert insert(List<Map<String,Object>> dbObjects, Durability durability, Boolean returnVals, Boolean upsert);    

------
update
------
Update JSON documents in a table. Accepts a JSON document, a ReQL expression, or a combination of the two.

Example: Update the status of the post with id of 1 to published.

.. code-block:: java

	r.table("posts").get(1).update(new MapObject().with("published", true)).run(conn)

Example: Update the status of all posts to published.

.. code-block:: java
	
	r.table("posts").update(new MapObject().with("published", true)).run(conn);

Example: Update the status of all the post written by William.

.. code-block:: java
	
	r.table("posts").filter(...).update(new MapObject().with("published", true)).run(conn);

Example: Increment the field view with id of 1. This query will throw an error if the field views doesn"t exist.

.. code-block:: java

	r.table("posts").get(1).update(
		new MapObject().with("views", r.row.field("views").add(1)    	
	}).run(conn);

Example: Increment the field view of the post with id of 1. If the field views does not exist, it will be set to 0.

.. code-block:: java

	r.table("posts").update({
    	new MapObject().with("views", (r.row.field("views").add(1)).default(1) )  
	}).run(conn);

Example: Perform a conditional update.

If the post has more than 100 views, set the type of a post to hot, else set it to normal.

.. code-block:: java

	r.table("posts").get(1).update(post ->
    	r.branch(
        	post.field("views").gt(100),
        	new MapObject().with("type", "hot"),
        	new MapObject().with("type", "normal")
    	)
	).run(conn);


-------
replace
-------
Replace documents in a table. Accepts a JSON document or a ReQL expression, and replaces the original document with the new one. The new document must have the same primary key as the original document.

Example: Replace the document with the primary key 1.

.. code-block:: java

	r.table("posts").get(1).replace(
		new MapObject().with(...)
	).run(conn);


------
delete
------
Delete one or more documents from a table.

Example: Delete a single document from the table comments.

.. code-block:: java

	r.table("comments").get("7eab9e63-73f1-4f33-8ce4-95cbea626f59").delete().run(conn)

----
sync
----
sync ensures that writes on a given table are written to permanent storage. Queries that specify soft durability (durability="soft") do not give such guarantees, so sync can be used to ensure the state of these queries. A call to sync does not return until all previous writes to the table are persisted.

Example: After having updated multiple heroes with soft durability, we now want to wait until these changes are persisted.

.. code-block:: java
	
	r.table("marvel").sync().run(conn)