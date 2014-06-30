##################
Control Structures
##################

******
branch
******

If the test expression returns False or None, the false_branch will be evaluated. Otherwise, the true_branch will be evaluated.

The branch command is effectively an if renamed due to language constraints.

Example: Return heroes and superheroes.

.. code-block:: java

	r.table("marvel").map(
	    r.branch(
	        r.row().field("victories").gt(100),
	        r.row().field("name").add(" is a superhero"),
	        r.row().field("name").add(" is a hero")
	    )
	).run(conn)