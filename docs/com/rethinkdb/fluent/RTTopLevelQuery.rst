.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb RethinkDBException

.. java:import:: com.rethinkdb.ast RTOperationConverter

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: com.rethinkdb.mapper DBObjectMapper

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: org.slf4j Logger

.. java:import:: org.slf4j LoggerFactory

.. java:import:: java.util List

RTTopLevelQuery
===============

.. java:package:: com.rethinkdb.fluent
   :noindex:

.. java:type:: public class RTTopLevelQuery<T>

Fields
------
logger
^^^^^^

.. java:field:: protected static final Logger logger
   :outertype: RTTopLevelQuery

sampleClass
^^^^^^^^^^^

.. java:field:: protected Class<T> sampleClass
   :outertype: RTTopLevelQuery

treeKeeper
^^^^^^^^^^

.. java:field:: protected RTTreeKeeper treeKeeper
   :outertype: RTTopLevelQuery

Constructors
------------
RTTopLevelQuery
^^^^^^^^^^^^^^^

.. java:constructor:: protected RTTopLevelQuery(RTTreeKeeper treeKeeper, Class<T> sampleClass)
   :outertype: RTTopLevelQuery

RTTopLevelQuery
^^^^^^^^^^^^^^^

.. java:constructor:: protected RTTopLevelQuery()
   :outertype: RTTopLevelQuery

Methods
-------
run
^^^

.. java:method:: public T run(RethinkDBConnection connection)
   :outertype: RTTopLevelQuery

