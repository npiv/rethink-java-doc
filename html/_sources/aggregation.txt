###########
Aggregation
###########


-----
group
-----
Takes a stream and partitions it into multiple groups based on the fields or functions provided. Commands chained after group will be called on each of these grouped sub-streams, producing grouped data.

Example: What is each player"s best game?

.. code-block:: java

	r.table("games").group("player").max("points").run(conn);

.. note:: 

	by default RethinkDB returns a quite unwieldy data result that looks like

.. code-block:: javascript

	{
	data=
		[
			[Alice, [{id=5.0, type=free, points=7.0, player=Alice}, 
					{id=12.0, type=free, points=2.0, player=Alice}]], 
			[Bob, 	[{id=2.0, type=ranked, points=15.0, player=Bob}, 
					{id=11.0, type=free, points=10.0, player=Bob}]]
		], 
	$reql_type$=GROUPED_DATA
	}

If you know you are expecting GROUPED DATA you can circumvent this and let the driver convert it for you by running:

.. code-block:: java

	r.table("games").group("player").max("points").runForGroup(conn);

Which would give you

.. code-block:: javascript

	{
	Bob=[
		{id=2.0, type=ranked, points=15.0, player=Bob}, 
		{id=11.0, type=free, points=10.0, player=Bob}], 
	Alice=[
		{id=5.0, type=free, points=7.0, player=Alice}, 
		{id=12.0, type=free, points=2.0, player=Alice}]
	}

You can also group by a function if you are interested in more than one field:

.. code-block:: java

	r.table(tableName).group(row->
			return row.pluck(Lists.newArrayList("player","points"));
	).max("points").field("points").runForGroup(con));


-------
ungroup
-------
Takes a grouped stream or grouped data and turns it into an array of objects representing the groups. Any commands chained after ungroup will operate on this array, rather than operating on each group individually. This is useful if you want to e.g. order the groups by the value of their reduction.

The format of the array returned by ungroup is the same as the default native format of grouped data in the javascript driver and data explorer.

Example: What is the maximum number of points scored by each player, with the highest scorers first?

.. code-block:: java

	r.table("games")
    	.group("player").max("points").field("points")
    	.ungroup().orderBy(r.desc("reduction")).run(conn)


------
reduce
------

Produce a single value from a sequence through repeated application of a reduction function.

Example: Return the number of documents in the table posts.

.. code-block:: java

	double result = r.table("posts")
		.map(post -> r.expr(1))
		.reduce((l,r) -> l.add(r))
		.run(con);                     


-----
count
-----
Count the number of elements in the sequence. With a single argument, count the number of elements equal to it. If the argument is a function, it is equivalent to calling filter before count.

Example: Just how many super heroes are there?

.. code-block:: java

	(r.table("marvel").count().add(r.table("dc").count()).run(conn);


---
sum
---
Sums all the elements of a sequence. If called with a field name, sums all the values of that field in the sequence, skipping elements of the sequence that lack that field. If called with a function, calls that function on every element of the sequence and sums the results, skipping elements of the sequence where that function returns None or a non-existence error.

Example: What"s 3 + 5 + 7?

.. code-block:: java

	double sum = r.expr(Lists.newArrayList(3, 5, 7)).sum().run(conn);


---
avg
---
Averages all the elements of a sequence. If called with a field name, averages all the values of that field in the sequence, skipping elements of the sequence that lack that field. If called with a function, calls that function on every element of the sequence and averages the results, skipping elements of the sequence where that function returns None or a non-existence error.

Example: What"s the average of 3, 5, and 7?

.. code-block:: java

	double avg = r.expr(Lists.newArrayList(3, 5, 7)).avg().run(conn)

---
min
---
Finds the minimum of a sequence. If called with a field name, finds the element of that sequence with the smallest value in that field. If called with a function, calls that function on every element of the sequence and returns the element which produced the smallest value, ignoring any elements where the function returns None or produces a non-existence error.

Example: What"s the minimum of 3, 5, and 7?

.. code-block:: java

	double min = r.expr(Lists.newArrayList(3, 5, 7)).min().run(conn)

---
max
---
Finds the maximum of a sequence. If called with a field name, finds the element of that sequence with the largest value in that field. If called with a function, calls that function on every element of the sequence and returns the element which produced the largest value, ignoring any elements where the function returns None or produces a non-existence error.

Example: What"s the maximum of 3, 5, and 7?

.. code-block:: java

	double max = r.expr(Lists.newArrayList(3, 5, 7)).max().run(conn)

--------
distinct
--------
Remove duplicate elements from the sequence.

Example: Which unique villains have been vanquished by marvel heroes?

.. code-block:: java
	
	r.table("marvel").concat_map(hero -> hero.field("villainList").distinct().run(conn);

--------
contains
--------
Returns whether or not a sequence contains all the specified values, or if functions are provided instead, returns whether or not a sequence contains values matching all the specified functions.

Example: Has Iron Man ever fought Superman?

.. code-block:: java
	
	r.table("marvel").get("ironman").field("opponents").contains("superman").run(conn);