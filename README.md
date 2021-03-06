# Big-Data-Sort-using-Hadoop 
## CSC 550 1 Big Data - Final Project

This project implements Hadoop MapReduce to sort 10 GB of data in HDFS using GraySort. The output of MapReduce is a sequence of files comprising the final sorted dataset. GraySort consists of three parts: teragen, terasort and teravalidate. Teragen is used to generate the data. Terasort is used to submit a MapReduce job that sorts the data. Teravalidate is used to validate if the data has been sorted.

### Install Hadoop and start Hadoop using the command:
$ /usr/local/Cellar/hadoop/2.8.1/sbin/start-dfs.sh;<br />
/usr/local/Cellar/hadoop/2.8.1/sbin/start-yarn.sh<br />
### Using jps command check if all hadoop daemons are running or not.
$ jps<br />
16499 Jps<br />
73829 NodeManager<br />
24344 SecondaryNameNode<br />
24045 DataNode<br />
23822 NameNode<br />
73647 ResourceManager
### Create jar file from the project directory.
Jar file can also be created from terminal by using the command:<br />
$ jar -cvf hadoop-mapreduce-graysort.jar *.*
### Browse HDFS directory
http://localhost:50070/explorer.html#/<br />
### Generate 10 GB data using TeraGen
hadoop jar hadoop-mapreduce-graysort.jar teragen 100000000 /DataGen
### Sort data using TeraSort
hadoop jar hadoop-mapreduce-graysort.jar terasort  /DataGen /DataSort
### Validate the output using TeraValidate
hadoop jar hadoop-mapreduce-graysort.jar teravalidate -D mapped.reduce.tasks=8 /DataSort /DataValidate
### The output can be viewed by browsing HDFS directory at:
http://localhost:50070/explorer.html#/
