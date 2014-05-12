.. java:import:: java.util List

.. java:import:: java.util Map

DBObjectBuilder
===============

.. java:package:: com.rethinkdb.model
   :noindex:

.. java:type:: public class DBObjectBuilder

   A fluent builder for DBObjects

Constructors
------------
DBObjectBuilder
^^^^^^^^^^^^^^^

.. java:constructor:: public DBObjectBuilder()
   :outertype: DBObjectBuilder

Methods
-------
build
^^^^^

.. java:method:: public DBObject build()
   :outertype: DBObjectBuilder

buildFromMap
^^^^^^^^^^^^

.. java:method:: public static DBObject buildFromMap(Map<String, Object> map)
   :outertype: DBObjectBuilder

with
^^^^

.. java:method:: public DBObjectBuilder with(String key, Number value)
   :outertype: DBObjectBuilder

with
^^^^

.. java:method:: public DBObjectBuilder with(String key, String value)
   :outertype: DBObjectBuilder

with
^^^^

.. java:method:: public DBObjectBuilder with(String key, Object value)
   :outertype: DBObjectBuilder

with
^^^^

.. java:method:: public <T> DBObjectBuilder with(String key, List<T> value)
   :outertype: DBObjectBuilder

