.. java:import:: com.rethinkdb RethinkDBException

.. java:import:: com.rethinkdb.model DBObject

.. java:import:: com.rethinkdb.model DBObjectBuilder

.. java:import:: com.rethinkdb.proto Q2L

.. java:import:: java.lang.reflect Field

.. java:import:: java.util ArrayList

.. java:import:: java.util HashMap

.. java:import:: java.util List

.. java:import:: java.util Map

DBResponseMapper
================

.. java:package:: com.rethinkdb.response
   :noindex:

.. java:type:: public class DBResponseMapper

Methods
-------
fromDatumObject
^^^^^^^^^^^^^^^

.. java:method:: public static <T> T fromDatumObject(Q2L.Datum datum)
   :outertype: DBResponseMapper

   Maps a ProtoBuf Datum object to a java object

   :param datum: datum
   :return: DBObject

fromDatumObjectList
^^^^^^^^^^^^^^^^^^^

.. java:method:: public static <T> List<T> fromDatumObjectList(List<Q2L.Datum> datums)
   :outertype: DBResponseMapper

   Maps a list of Datum Objects to a list of java objects

   :param datums: datum objects
   :return: DBObject

populateObject
^^^^^^^^^^^^^^

.. java:method:: public static <T> T populateObject(T to, DBObject from)
   :outertype: DBResponseMapper

   Populates the fields in to based on values out of from

   :param to: the object to map into
   :param from: the object to map from
   :param <T>: the type of the into object
   :return: the into object

