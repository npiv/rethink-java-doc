.. java:import:: com.rethinkdb RethinkDBException

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.model DBObjectBuilder

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.lang.reflect Field

.. java:import:: java.util ArrayList

.. java:import:: java.util HashMap

.. java:import:: java.util List

.. java:import:: java.util Map

DBObjectMapper
==============

.. java:package:: com.rethinkdb.mapper
   :noindex:

.. java:type:: public class DBObjectMapper

Methods
-------
fromDatumObject
^^^^^^^^^^^^^^^

.. java:method:: public static DBObject fromDatumObject(Q2L.Datum datum)
   :outertype: DBObjectMapper

   Maps a ProtoBuf Datum object to a DBObject

   :param datum: datum
   :return: DBObject

fromDatumObjects
^^^^^^^^^^^^^^^^

.. java:method:: public static DBObject fromDatumObjects(List<Q2L.Datum> datums)
   :outertype: DBObjectMapper

   Maps a list of Datum Objects to a DBObject

   :param datums: datum objects
   :return: DBObject

populateList
^^^^^^^^^^^^

.. java:method:: public static <T> T populateList(DBObject dbObject)
   :outertype: DBObjectMapper

populateObject
^^^^^^^^^^^^^^

.. java:method:: public static <T> T populateObject(T to, DBObject from)
   :outertype: DBObjectMapper

   Populates the fields in to based on values out of from

   :param to: the object to map into
   :param from: the object to map from
   :param <T>: the type of the into object
   :return: the into object

