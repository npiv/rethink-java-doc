#####################
Document Manipulation
#####################

***
row
***
Returns the currently visited document.

Example: Get all users whose age is greater than 5.

.. code-block:: java

	r.table("users").filter(r.row.field("age").gt(5)).run(conn);

*****
pluck
*****
Plucks out one or more attributes from either an object or a sequence of objects (projection).

Example: We just need information about IronMan"s reactor and not the rest of the document.

.. code-block:: java

	r.table("marvel").get("IronMan").pluck("reactorState", "reactorPower").run(conn);

*******
without
*******
The opposite of pluck; takes an object or a sequence of objects, and returns them with the specified paths removed.

Example: Since we don"t need it for this computation we"ll save bandwidth and leave out the list of IronMan"s romantic conquests.

.. code-block:: java

	r.table("marvel").get("IronMan").without("personalVictoriesList").run(conn)

*****
merge
*****

Merge two objects together to construct a new object with properties from both. Gives preference to attributes from other when there is a conflict.

Example: Equip IronMan for battle.

.. code-block:: java

	r.table("marvel").get("IronMan").merge(
		r.table("loadouts").get("alienInvasionKit")
	).run(conn);


******
append
******
Append a value to an array.

Example: Retrieve Iron Man"s equipment list with the addition of some new boots.

.. code-block:: java

	r.table("marvel").get("IronMan").field("equipment").append("newBoots").run(conn);

*******
prepend
*******
Prepend a value to an array.

Example: Retrieve Iron Man"s equipment list with the addition of some new boots.

.. code-block:: java
	
	r.table("marvel").get("IronMan").field("equipment").prepend("newBoots").run(conn);

**********
difference
**********
Remove the elements of one array from another array.

Example: Retrieve Iron Man"s equipment list without boots.

.. code-block:: java
	
	r.table("marvel").get("IronMan").field("equipment")
		.difference(Lists.newArrayList("Boots")).run(conn);

*********
setInsert
*********
Add a value to an array and return it as a set (an array with distinct values).

Example: Retrieve Iron Man"s equipment list with the addition of some new boots.

.. code-block:: java

	r.table("marvel").get("IronMan").field("equipment")
		.setInsert(Lists.newArrayList("boots")).run(conn);

********
setUnion
********
Add a several values to an array and return it as a set (an array with distinct values).

Example: Retrieve Iron Man"s equipment list with the addition of some new boots and an arc reactor.

.. code-block:: java

	r.table("marvel").get("IronMan").field("equipment")
		.setUnion(Lists.newArrayList("boots","arcReactor")).run(conn);

***************
setIntersection
***************
Intersect two arrays returning values that occur in both of them as a set (an array with distinct values).

Example: Check which pieces of equipment Iron Man has from a fixed list.

.. code-block:: java

	r.table("marvel").get("IronMan").field("equipment")
		.setIntersection(Lists.newArrayList("newBoots")).run(conn);

*************
setDifference
*************
Remove the elements of one array from another and return them as a set (an array with distinct values).

Example: Check which pieces of equipment Iron Man has, excluding a fixed list.

.. code-block:: java

	r.table("marvel").get("IronMan").field("equipment")
		.setDifference(Lists.newArrayList("newBoots", "arc_reactor")).run(conn);

*****
field
*****
Get a single field from an object. If called on a sequence, gets that field from every object in the sequence, skipping objects that lack it.

Example: What was Iron Man"s first appearance in a comic?

.. code-block:: java

	r.table("marvel").get("IronMan").field("firstAppearance").run(conn);

*********
hasFields
*********
Filter if an object has all of the specified fields. An object has a field if it has the specified key and that key maps to a non-None value. For instance, the object {"a":1,"b":2,"c": None} has the fields a and b.

Example: Which heroes are married?

.. code-block:: java

	r.table("marvel").hasFields("spouse").run(conn);

********
insertAt
********
Insert a value in to an array at a given index. Returns the modified array.

Example: Hulk decides to join the avengers.

.. code-block:: java

	r.expr(Lists.newArrayList("Iron Man", "Spider-Man")).insertAt(1, "Hulk").run(conn);

********
spliceAt
********
Insert several values in to an array at a given index. Returns the modified array.

Example: Hulk and Thor decide to join the avengers.

.. code-block:: java

	r.expr(Lists.newArrayList("Iron Man", "Spider-Man"))
		.insertAt(1, Lists.newArrayList("Hulk", "Thor")).run(conn);	

********
deleteAt
********
Remove an element from an array at a given index. Returns the modified array.

Example: Hulk decides to leave the avengers.

.. code-block:: java

	r.expr(Lists.newArrayList("Iron Man", "Spider-Man")).deleteAt(1).run(conn);

or delete within a range

.. code-block:: java

	r.expr(Lists.newArrayList("Iron Man", "Spider-Man")).deleteAt(0,2).run(conn);


******
change
******
Change a value in an array at a given index. Returns the modified array.

Example: Bruce Banner hulks out.

.. code-block:: java

	r.expr(Lists.newArrayList("Iron Man", "Bruce", "Spider-Man")).changeAt(1, "Hulk").run(conn)

****
keys
****
Return an array containing all of the object"s keys.

Example: Get all the keys of a row.

.. code-block:: java

	r.table("marvel").get("ironman").keys().run(conn);
