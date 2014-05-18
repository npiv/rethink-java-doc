###############
Transformations
###############


---
map
---
Transform each element of the sequence by applying the given mapping function.

Example: Construct a sequence of hero power ratings.

.. code-block:: java
	
	List<Double> res = r.table("marvel").map(hero ->
		hero.field("combatPower").add(hero.field("compassionPower").mul(2));
	).runTyped(conn);

----------
withFields
----------
Takes a sequence of objects and a list of fields. If any objects in the sequence don"t have all of the specified fields, they"re dropped from the sequence. The remaining objects have the specified fields plucked out. (This is identical to has_fields followed by pluck on a sequence.)

Example: Get a list of heroes and their nemeses, excluding any heroes that lack one.

.. code-block:: java
	
	r.table("marvel").withFields("id", "nemesis").run(c);

---------
concatMap
---------
Flattens a sequence of arrays returned by the mappingFunction into a single sequence.

Example: Construct a sequence of all monsters defeated by Marvel heroes. Here the field "defeatedMonsters" is a list that is concatenated to the sequence.

.. code-block:: java
	
	r.table("marvel").concatMap(h->h.field("defeatedMonsters")).run(c);



-------
orderBy
-------
Sort the sequence by document values of the given key(s). To specify the ordering, wrap the attribute with either r.asc or r.desc (defaults to ascending).

Sorting without an index requires the server to hold the sequence in memory, and is limited to 100,000 documents. Sorting with an index can be done on arbitrarily large tables, or after a between command using the same index.

Example: Order all the posts using the index date.

.. code-block:: java
	
	r.table("posts").orderByIndex("date").run(conn);

The index must have been previously created with indexCreate.

.. code-block:: java
	
	r.table("posts").indexCreate("date").run(conn);

You can also select a descending ordering

.. code-block:: java
	
	r.table("posts").orderBy(r.desc("date")).run(conn);

Example: If you have a sequence with less than 100,000 documents, you can order it without an index.

.. code-block:: java
	
	r.table("posts").get(1).field("comments").orderByField("date");

Example: If you have a sequence with less than 100,000 documents, you can order it with an arbitrary function directly.

.. code-block:: java

	r.table("small_table").orderBy(doc ->
		doc.field("upvotes").minus(doc.field("downvotes"));
	);

Signatures:

.. code-block:: java

	public OrderBy orderBy(RqlFunction function);
	public OrderBy orderBy(List<String> fields, String index);
	public OrderBy orderBy(List<String> fields);
	public OrderBy orderByIndex(String index);
	public OrderBy orderByField(String field);

----
Skip
----

Skip a number of elements from the head of the sequence.

Example: Here in conjunction with order_by we choose to ignore the most successful heroes.

.. code-block:: java

	r.table("marvel").orderBy("successMetric").skip(10).run(conn);


-----
limit
-----

End the sequence after the given number of elements.

Example: Only so many can fit in our Pantheon of heroes.

.. code-block:: java

	r.table("marvel").orderBy("belovedness").limit(10).run(conn);


---------
IndexesOf
---------

Get the indexes of an element in a sequence. If the argument is a predicate, get the indexes of all elements matching it.

Example: Find the position of the letter "c".

.. code-block:: java

	r.expr(["a","b","c"]).indexesOf("c").run(conn);

Example: Find the popularity ranking of invisible heroes.

.. code-block:: java

	r.table("marvel").union(r.table("dc")).orderBy("popularity").indexesOf(
		r.row.field("superpowers").contains("invisibility")
	).run(conn);

-------
isEmpty
-------
Test if a sequence is empty.

Example: Are there any documents in the marvel table?

.. code-block:: java

	Boolean answer = r.table("marvel").isEmpty().run(conn)

-----
Union
-----
Concatenate two sequences.

Example: Construct a stream of all heroes.

.. code-block:: java

	r.table("marvel").union(r.table("dc")).run(conn);


------
Sample
------
Select a given number of elements from a sequence with uniform random distribution. Selection is done without replacement.

Example: Select 3 random heroes.

.. code-block:: java

	r.table("marvel").sample(3).run(conn);