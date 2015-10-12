======
spark
======

An additinal state for the Salt Stack `hadoop-formula
<https://github.com/saltstack-formulas/hadoop-formula>`_
, which installs apache spark on the hadoop_master 

Relies on hadoop-formula/hadoop/settings.sls. 
This is intended to be added to the formula directory like so:
::

    git clone https://github.com/mraymond77/spark-formula
    cd spark-formula
    mv spark /srv/salt/formulas/hadoop-formula/hadoop/

hadoop.spark will then be available as a state.

``hadoop.spark``
---------------

Installs a prebuilt spark directory and creates a link to ``/usr/lib/spark``  
Spark is installed on the hadoop_master only, and no further configuration is needed. `Spark in yarn mode <http://spark.apache.org/docs/latest/running-on-yarn.html>`_ uses hadoop configuration files to identify cluster members.
For other modes, see the `spark documentation <http://spark.apache.org/docs/latest/cluster-overview.html>`_.

Similar to the hadoop.hdfs state, this requires the hadoop roles be defined in ``/etc/salt/grains``
::

    roles:
      - hadoop_slave

and
::

    roles:
      - hadoop_master


Version settings in the hadoop pillar
====================================
A key for spark should be added to the hadoop pillar to specify a version. Otherwise, it defaults to spark-1.5.1-bin-hadoop2.6

::

    spark:
      version: 1.5.1-bin-hadoop2.6


