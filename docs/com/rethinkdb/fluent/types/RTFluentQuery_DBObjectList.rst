.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: java.util List

RTFluentQuery_DBObjectList
==========================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public class RTFluentQuery_DBObjectList extends RTFluentQuery<List>

Constructors
------------
RTFluentQuery_DBObjectList
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RTFluentQuery_DBObjectList(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQuery_DBObjectList

Methods
-------
run
^^^

.. java:method:: @Override public List<DBObject> run(RethinkDBConnection connection)
   :outertype: RTFluentQuery_DBObjectList

