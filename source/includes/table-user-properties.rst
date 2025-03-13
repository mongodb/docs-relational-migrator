.. list-table:: 
   :header-rows: 1
   :width: 60 30 10

   * - Property Name
     - Description 
     - Default 

   * - ``spring.profiles.active``
     - Relational Migrator can be run in the following profile: 

       - ``kafka``: Remote server using embedded server deployment.
       - ``confluent``: Remote server using Confluent Cloud for managed Kafka

       Set the profile value to ``kafka``. 
     - ``local``

   * - ``server.port``
     - The port the Relation Migrator application runs on.
     - ``8278``

   * - ``migrator.kafka.bootstrap.servers``
     - This is a list of ``host:port`` pairs of your pre-existing kafka cluster. 

       For more information, see `Worker Configuration Properties 
       <https://docs.confluent.io/platform/current/connect/userguide.html#worker-configuration-properties-file>`__. 
     - No default

   * - ``migrator.kafka.connect.url``
     - The Kafka Connect host url using the ``{host}:{port}`` format.
     - No default  

   * - ``migrator.kafka.connect.metrics.jmx.service.url``
     - The Kafka Connect Java Management Extensions (JMX) url. 

       For example: ``service:jmx:rmi:///jndi/rmi://localhost:9876/jmxrmi``
     - No default

   * - ``migrator.kafka.connect.metrics.jmx.ssl``
     - Set to ``true`` if SSL is enabled.

       You can add additonal remote Java Management Extensions (JMX) for SSL 
       configurations by prefixing them with ``migrator.kafka.connect.metrics.jmx.properties``.
     - ``false``

   * - ``migrator.kafka.enable.topic.cleanup``
     -  Cleans up the topics created during the last migration job.
     -  ``false``

   * - ``migrator.connector.source.common.errors.max.retries``
     - For the source connector, it specifies the maximum number of retries on a 
       retriable failure. Relational Migrator attempts recovery from source database 
       retriable failures up to a set limit before the job fails.
     - ``5``

   * - ``migrator.connector.source.common.errors.retry.initial.max.ms``
     - For the source connector, it specifies the delay in milliseconds to start 
       again after a retriable failure. The value is doubled after every retry but 
       does not exceed ``migrator.connector.source.common.errors.retry.delay.max.ms``.
     - ``30000``

   * - ``migrator.connector.source.common.errors.retry.delay.max.ms``
     - For the source connector, it specifies the maximum delay in milliseconds 
       between retries after a retriable failure.
     - ``60000``

   * - ``migrator.connector.sink.common.errors.max.retries``
     - For the sink connector, it specifies the maximum number of retries on a 
       retriable failure. Relational Migrator attempts recovery from source database 
       retriable failures up to a set limit before the job fails.
     - ``5``    

   * - ``migrator.connector.sink.common.errors.retry.initial.max.ms``
     - For the sink connector, it specifies the delay in milliseconds to start again 
       after a retriable failure. The value is doubled after every retry but does not exceed 
       ``migrator.connector.sink.common.errors.retry.delay.max.ms``.
     - ``30000``

   * - ``migrator.connector.sink.common.errors.retry.delay.max.ms``
     - For the sink connector, it specifies the maximum delay in milliseconds 
       between retries after a retriable failure.
     - ``60000``