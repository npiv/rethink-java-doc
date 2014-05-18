#####
Notes
#####

------------------
Java 8 or Previous
------------------
The library is compatibly with java 1.6 and up. All the examples with regards to lambdas use the new java 8 syntax.

for example in Java 8 one can write:

.. code-block:: java

	r.table("heros").filter(
		r.lambda(row->row.field("age").gt(20)) 
	).run(con);

Pre java 1.8 this would need to be invoked with an anonymous inner class.

.. code-block:: java

    r.table("heros").filter(r.lambda(new DBLambda() {
          @Override
          public RTFluentRow apply(RTFluentRow row) {
              return row.field("age").gt(20);
          }
    })).run(con);


.. note::
	Both will work, but the documentation will stick to the java 8 syntax. It's up to the end user to convert the example to an anonymous inner class where needed


----------
Milestones
----------
 * Implement cursors 
 * Implement Date functions
 * ORM Mapping
 * Spring data integration
 * DB connection pooling

----------
Contribute
----------
Fork, submit an issue, contact me on github, or send me a mail at nick.verlinde on the google mail.


