.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTTopLevelQueryTypes.DMLResult
==============================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class DMLResult extends RTTopLevelQuery
   :outertype: RTTopLevelQueryTypes

Constructors
------------
DMLResult
^^^^^^^^^

.. java:constructor:: public DMLResult(RTTreeKeeper treeKeeper)
   :outertype: RTTopLevelQueryTypes.DMLResult

Methods
-------
run
^^^

.. java:method:: @Override public com.rethinkdb.response.model.DMLResult run(RethinkDBConnection connection)
   :outertype: RTTopLevelQueryTypes.DMLResult

