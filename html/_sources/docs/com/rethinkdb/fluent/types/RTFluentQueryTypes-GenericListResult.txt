.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTFluentQuery

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.response DBResponseMapper

.. java:import:: com.rethinkdb.response.model DDLResult

.. java:import:: com.rethinkdb.response.model DMLResult

.. java:import:: java.util List

RTFluentQueryTypes.GenericListResult
====================================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public static class GenericListResult extends RTFluentQuery
   :outertype: RTFluentQueryTypes

Constructors
------------
GenericListResult
^^^^^^^^^^^^^^^^^

.. java:constructor:: public GenericListResult(RTTreeKeeper treeKeeper)
   :outertype: RTFluentQueryTypes.GenericListResult

Methods
-------
run
^^^

.. java:method:: @SuppressWarnings public List run(RethinkDBConnection connection)
   :outertype: RTFluentQueryTypes.GenericListResult

