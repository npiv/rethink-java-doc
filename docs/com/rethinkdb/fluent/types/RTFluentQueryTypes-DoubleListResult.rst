.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentQueryTypes.DoubleListResult
===================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class DoubleListResult extends RTFluentQuery
   :outertype: RTFluentQueryTypes

Constructors
------------
DoubleListResult
^^^^^^^^^^^^^^^^

.. java:constructor:: public DoubleListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQueryTypes.DoubleListResult

Methods
-------
run
^^^

.. java:method:: @Override @SuppressWarnings public List<Double> run(RethinkDBConnection connection)
   :outertype: RTFluentQueryTypes.DoubleListResult

