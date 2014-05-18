###################
Rethink Java Driver
###################

Introduction
============

The Rethink Java Driver aims to closely mirror the existing ruby/python/js implementations. Due to limitations of java being a typed language some inspiration will be sought from existing java big data drivers like mongo to make the api as fluent as possible for the end user.

At the same time with java 8 lambda syntax we should be able to get pretty close. The driver itself expects a minimum of java 1.6. But users using java 1.8 can do funky stuff like:

.. code-block:: java

	r.table("heros").filter(
		r.lambda(row->row.field("age").gt(20)) // this is executed remotely!
	).run(con);

Which pre java 1.8 would need to be invoked with an anonymous inner class like

.. code-block:: java

    r.table("heros").filter(r.lambda(new DBLambda() {
          @Override
          public RTFluentRow apply(RTFluentRow row) {
              return row.field("age").gt(20);
          }
    })).run(con);

Of course you can still choose to create concrete FunctionClasses in pre java 8 code and have it look something like:

.. code-block:: java

    r.table("heros").filter(new AgeGTCondition(20)).run(con);


.. note::
	For the remainder of the documentation all the examples will use the Java 8 Lambda syntax where possible. Just make note that java 1.6+ is supported, albeit in a slightly more limited form.


Milestones
==========
 * complete implementation + documentation of core methods in the `python api <http://rethinkdb.com/api/python/>`_ See the left hand menu for what's there already 
 * ORM module
 * Spring data integration
 * DB connection pooling


Contribute
==========
Fork, submit an issue, contact me on github, or send me a mail at nick.verlinde on the google mail. I should be able to respond to any of those mediums within 24 hours.


User Documentation
------------------

.. toctree::
    :maxdepth: 2

    index
    accessing_reql
    manipulating_databases
    manipulating_tables
    writing_data
    math_logic

