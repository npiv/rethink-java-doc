.. java:import:: java.util List

ProtoUtil
=========

.. java:package:: com.rethinkdb.proto
   :noindex:

.. java:type:: public class ProtoUtil

   Utilities to make traversing ProtoBuf objects easier

Methods
-------
hasKey
^^^^^^

.. java:method:: public static boolean hasKey(List<Q2L.Query.AssocPair> pairs, String key)
   :outertype: ProtoUtil

   Checks is a list of Protobuf AssocPairs contains a certain key

   :param pairs: pairs to check
   :param key: key to find
   :return: if key was present

