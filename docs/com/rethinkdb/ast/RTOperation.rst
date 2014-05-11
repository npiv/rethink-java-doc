.. java:import:: com.google.common.collect Lists

.. java:import:: com.google.common.collect Maps

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.util Arrays

.. java:import:: java.util List

.. java:import:: java.util Map

RTOperation
===========

.. java:package:: com.rethinkdb.ast
   :noindex:

.. java:type:: public class RTOperation

Constructors
------------
RTOperation
^^^^^^^^^^^

.. java:constructor:: public RTOperation(Q2L.Term.TermType termType)
   :outertype: RTOperation

Methods
-------
db
^^

.. java:method:: public static RTOperation db(String dbname)
   :outertype: RTOperation

getArgs
^^^^^^^

.. java:method:: public List<Object> getArgs()
   :outertype: RTOperation

getOptionalArgs
^^^^^^^^^^^^^^^

.. java:method:: public Map<String, Object> getOptionalArgs()
   :outertype: RTOperation

getTermType
^^^^^^^^^^^

.. java:method:: public Q2L.Term.TermType getTermType()
   :outertype: RTOperation

pushArg
^^^^^^^

.. java:method:: protected RTOperation pushArg(Object arg)
   :outertype: RTOperation

toString
^^^^^^^^

.. java:method:: @Override public String toString()
   :outertype: RTOperation

withArgs
^^^^^^^^

.. java:method:: public RTOperation withArgs(Object... args)
   :outertype: RTOperation

withOptionalArg
^^^^^^^^^^^^^^^

.. java:method:: public RTOperation withOptionalArg(String key, Object value)
   :outertype: RTOperation

