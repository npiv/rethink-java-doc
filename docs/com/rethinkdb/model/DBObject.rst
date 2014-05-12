.. java:import:: java.util Collections

.. java:import:: java.util HashMap

.. java:import:: java.util Map

DBObject
========

.. java:package:: com.rethinkdb.model
   :noindex:

.. java:type:: @SuppressWarnings public class DBObject

   A low level representation of an Object that is stored or read from the database. This is a more convenient interface than a raw map, but ultimately just stores a list of key values.

Fields
------
map
^^^

.. java:field:: protected Map<String, Object> map
   :outertype: DBObject

Constructors
------------
DBObject
^^^^^^^^

.. java:constructor:: protected DBObject()
   :outertype: DBObject

DBObject
^^^^^^^^

.. java:constructor:: protected DBObject(Map<String, Object> map)
   :outertype: DBObject

Methods
-------
get
^^^

.. java:method:: public <T> T get(String key)
   :outertype: DBObject

getAsMap
^^^^^^^^

.. java:method:: public Map<String, Object> getAsMap()
   :outertype: DBObject

toString
^^^^^^^^

.. java:method:: @Override public String toString()
   :outertype: DBObject

