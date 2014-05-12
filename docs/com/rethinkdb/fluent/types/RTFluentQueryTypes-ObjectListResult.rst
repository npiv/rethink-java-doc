.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentQueryTypes.ObjectListResult
===================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class ObjectListResult extends RTFluentQuery
   :outertype: RTFluentQueryTypes

Constructors
------------
ObjectListResult
^^^^^^^^^^^^^^^^

.. java:constructor:: public ObjectListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQueryTypes.ObjectListResult

Methods
-------
run
^^^

.. java:method:: @Override @SuppressWarnings public List<com.rethinkdb.model.DBObject> run(RethinkDBConnection connection)
   :outertype: RTFluentQueryTypes.ObjectListResult

