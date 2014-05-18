##############
Math And Logic
##############

---
add
---
add 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").add(22))).run(con);

---
sub
---
sub 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").sub(22))).run(con);

---
mul
---
mul 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").mul(22))).run(con);

---
div
---
div 2 numbers

.. code-block:: java

	r.table("heros").map(r.lambda(x.field("age").div(22))).run(con);

---
mod
---
get the modulus of 2 numbers

.. code-block:: java

	r.table("heros").filter(r.lambda(x.field("age").mod(2))).run(con); // get the even ages

---
and
---
Create an and clause.

.. code-block:: java

	r.table("heros").filter(row->
		r.and(
			row.field("name").eq("Adam")
			row.field("id").eq(1)
		)
	).run(con);


---
or
---
Create an or clause.

.. code-block:: java

	r.table("heros").filter(row->
		r.and(
			row.field("name").eq("Adam")
			row.field("name").eq("Eve")
		)
	).run(con);


---
eq
---
Specifiy an equals condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("name").eq("John")).run(con); // All the Johns	


---
ne
---
Specifiy a not equal condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("name").ne("John")).run(con); // everyone but John

---
gt
---
Specifiy a greater than condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").gt(10)).run(con); // everyone older than 10


---
ge
---
Specifiy a greater than or equal condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").ge(10)).run(con); // everyone older than or equal to 10

---
lt
---
Specifiy a less than condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").lt(10)).run(con); // everyone younger than 10

---
le
---
Specifiy a less than or equal condition

.. code-block:: java

	r.table("heros").filter(row-> row.field("age").le(10)).run(con); // everyone younger than or equal to 10


---
not
---
todo: doc and test

