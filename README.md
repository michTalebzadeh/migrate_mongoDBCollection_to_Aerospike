# migrate_mongoDBCollection_to_Aerospike
Example of migrating a mongoDB collection documents to Aerospike Set using Spark as ETL tool
You will need the jar files as follows (at time of writing)
aerospike-spark-assembly-1.1.2.jar
mongo-spark-connector_2.11-2.3.0.jar
mongo-java-driver-3.8.1.jar 
In Addition, you will need the following mongoDB packages
org.mongodb.spark:mongo-spark-connector_2.11:2.3.0

Spark’s shell provides a simple tool to analyze data interactively. It is available in either Scala (which runs on the Java VM and is thus a good way to use existing Java libraries) or Python. Start it by running the following:
$SPARK_HOME/bin/spark-shell
However, if you choose this way you will need tp pass the jar file and packages. Example as below
$SPARK_HOME/bin/spark-shell --jars /home/hduser/jars/aerospike-spark-assembly-1.1.2.jar,/home/hduser/jars/mongo-spark-connector_2.11-2.3.0.jar,/home/hduser/jars/mongo-java-driver-3.8.1.jar --packages org.mongodb.spark:mongo-spark-connector_2.11:2.3.0
Also as there is a bug in Mongo, if you choose this approach, you will need to pass MongoDB credentials to spark-shell as well!
$SPARK_HOME/bin/spark-shell --jars /home/hduser/jars/aerospike-spark-assembly-1.1.2.jar,/home/hduser/jars/mongo-spark-connector_2.11-2.3.0.jar,/home/hduser/jars/mongo-java-driver-3.8.1.jar --packages org.mongodb.spark:mongo-spark-connector_2.11:2.3.0 --conf "spark.mongodb.input.uri=mongodb://<DB_USER>:<DB_PASSWORD>@<HOST_NAME>:<MONGO_PORT>/<DB_NAME>.<COLLECTION_NAME>
If you use SBT to create a Uber or Fat Jar file, you will not need this.
Note that example here uses Aerospike with user authentication. Both the Aerospike-Spark connector and user authentication are part of Aerospike Enterprise edition and are licensed product.
