.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb RethinkDBException

.. java:import:: com.rethinkdb.ast RTOperationConverter

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.fluent RTTopLevelQuery

.. java:import:: com.rethinkdb.mapper DBObjectMapper

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: org.slf4j Logger

.. java:import:: org.slf4j LoggerFactory

.. java:import:: java.util List

RTTopLevelQuery_StringList
==========================

.. java:package:: com.rethinkdb.fluent.types
   :noindex:

.. java:type:: public class RTTopLevelQuery_StringList extends RTTopLevelQuery<List>

Constructors
------------
RTTopLevelQuery_StringList
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public RTTopLevelQuery_StringList(RTTreeKeeper treeKeeper)
   :outertype: RTTopLevelQuery_StringList

Methods
-------
run
^^^

.. java:method:: @Override public List<String> run(RethinkDBConnection connection)
   :outertype: RTTopLevelQuery_StringList

