#####
Joins
#####

---------
innerJoin
---------
Returns the inner product of two sequences (e.g. a table, a filter result) filtered by the predicate. The query compares each row of the left sequence with each row of the right sequence to find all pairs of rows which satisfy the predicate. When the predicate is satisfied, each matched pair of rows of both sequences are combined into a result row.

Example: Construct a sequence of documents containing all cross-universe matchups where a marvel hero would lose.

.. code-block:: java
    
     List<JoinResult> res = r.table("marvel").inner_join(r.table("dc"), 
     	(marvelRow, dcRow) -> marvelRow.field("strength").lt(dcRow.field("strength"))
     ).run(con);    


---------
outerJoin
---------
Computes a left outer join by retaining each row in the left table even if no match was found in the right table.

Example: Construct a sequence of documents containing all cross-universe matchups where a marvel hero would lose, but keep marvel heroes who would never lose a matchup in the sequence.

.. code-block:: java
    
     List<JoinResult> res = r.table("marvel").outerJoin(r.table("dc"), 
     	(marvelRow, dcRow) -> marvelRow.field("strength").lt(dcRow.field("strength"))
     ).run(con);    

------
eqJoin
------
An efficient join that looks up elements in the right table by primary key.

Example: Let our heroes join forces to battle evil!

.. code-block:: java
    
     List<JoinResult> res = r.table("marvel").eqJoin(
     	"main_dc_collaborator", r.table("dc")
     ).run(con);     	

---
zip
---
Used to 'zip' up the result of a join by merging the 'right' fields into 'left' fields of each member of the sequence.

Example: 'zips up' the sequence by merging the left and right fields produced by a join.

.. code-block:: java
    
     List<Map<String,Object>> res = r.table("marvel").eqJoin(
     	"main_dc_collaborator", r.table("dc")
	).zip().run(con);     	    