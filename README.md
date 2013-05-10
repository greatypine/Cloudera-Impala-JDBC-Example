Cloudera Impala JDBC Example
============================

This example shows how to build and run a maven-based project that executes SQL queries on Cloudera Impala using JDBC. 
Cloudera Impala is a native Massive Parallel Processing (MPP) query engine which enables users to perform interactive analysis of data stored in HBase or HDFS. 

Here are links to more information on Cloudera Impala:

- [Cloudera Enterprise RTQ](http://www.cloudera.com/content/cloudera/en/products/cloudera-enterprise-core/cloudera-enterprise-RTQ.html) 

- [Cloudera Impala Documentation](http://www.cloudera.com/content/support/en/documentation/cloudera-impala/cloudera-impala-documentation-v1-latest.html)

- [Cloudera Impala JDBC Documentation](http://www.cloudera.com/content/cloudera-content/cloudera-docs/Impala/latest/Installing-and-Using-Impala/ciiu_impala_jdbc.html)

- [Impala-User Google Group](https://groups.google.com/a/cloudera.org/forum/?fromgroups#!forum/impala-user)

 
 
To use the Cloudera Impala JDBC driver in your own maven-based project you can copy the `<dependency>` and `<repository>` elements from this project's pom to your own instead of manually downloading the JDBC driver jars.




###Dependencies
To build the project you must have Maven 2.x or higher installed.  Maven info is [here](http://maven.apache.org).

To run the project you must have access to a Hadoop cluster running Cloudera Impala with at least one populated table defined in the Hive Metastore.


###Configure the example
To configure the example you must:

- Select or create the table(s) to query against.
- Set the query and impalad host in the example source file

These steps are described in more detail below.





###Select or create the table(s) to run the example with
For this example I will use one of the Hue Beeswax sample tables.  I can see the tables using [Hue](http://gethue.com) as in the screenshot below:  


![Hue Table List](images/HueTableList.jpg)

###Set the query and impalad host
Edit these two setting in the ClouderaImpalaJdbcExample source file:

- Set the SQL Statement

`private static final String SQL_STATEMENT = "SELECT description FROM sample_07 limit 10";`
	
- Set the host for the impalad you want to connect to: 

`private static final String IMPALAD_HOST = "MyImpaladHost";`


###Building the project
To build the project, run the command `mvn clean compile` from the root of the project directory.   There is a build.sh script for your convenience.

###Running the example
To run the example, use the command `mvn exec:java -Dexec.mainClass=com.cloudera.example.ClouderaImpalaJdbcExample` from the root of the project directory.  There is a run.sh script for your convinience.

###Sample output
Here is sample output from running the example:

`mbrooks-MBP:Cloudera-Impala-JDBC-Example mbrooks$ ./run.sh

Cloudera Impala JDBC Example
Using Connection URL: jdbc:hive2://192.168.171.100:21050/;auth=noSasl
Running Query: SELECT description FROM sample_07 limit 10

== Begin Query Results ======================
All Occupations
Management occupations
Chief executives
General and operations managers
Legislators
Advertising and promotions managers
Marketing managers
Sales managers
Public relations managers
Administrative services managers
== End Query Results =======================


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 2.042s
[INFO] Finished at: Fri May 10 12:07:47 PDT 2013
[INFO] Final Memory: 7M/81M
[INFO] ------------------------------------------------------------------------
`
