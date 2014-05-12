.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentLevelQuery_Types.T_DoubleListResult
===========================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class T_DoubleListResult extends RTFluentQuery
   :outertype: RTFluentLevelQuery_Types

Constructors
------------
T_DoubleListResult
^^^^^^^^^^^^^^^^^^

.. java:constructor:: public T_DoubleListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentLevelQuery_Types.T_DoubleListResult

Methods
-------
run
^^^

.. java:method:: @Override @SuppressWarnings public List<Double> run(RethinkDBConnection connection)
   :outertype: RTFluentLevelQuery_Types.T_DoubleListResult

