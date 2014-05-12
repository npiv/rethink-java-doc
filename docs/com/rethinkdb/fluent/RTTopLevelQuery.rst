.. java:import:: com.rethinkdb RethinkDBConnection

.. java:import:: com.rethinkdb.ast RTOperationConverter

.. java:import:: com.rethinkdb.ast RTTreeKeeper

.. java:import:: org.slf4j Logger

.. java:import:: org.slf4j LoggerFactory

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

treeKeeper
^^^^^^^^^^

.. java:field:: public RTTreeKeeper treeKeeper
   :outertype: RTTopLevelQuery

Constructors
------------
RTTopLevelQuery
^^^^^^^^^^^^^^^

.. java:constructor:: protected RTTopLevelQuery(RTTreeKeeper treeKeeper)
   :outertype: RTTopLevelQuery

RTTopLevelQuery
^^^^^^^^^^^^^^^

.. java:constructor:: protected RTTopLevelQuery()
   :outertype: RTTopLevelQuery

Methods
-------
run
^^^

.. java:method:: public Object run(RethinkDBConnection connection)
   :outertype: RTTopLevelQuery

