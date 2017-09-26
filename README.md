## Build the image
Build by:
 ```
docker build -t hadoop .
 ```
Run and SSH into the container by:
 ```
docker run -it -p 50070:50070 -p 8088:8088 -p 8042:8042 -p 4040:4040 -h sandbox hadoop bash
 ```
Go to localhost:50070 & localhost:8088 in your browser and see that Hadoop is working by executing the following inside the Docker image:
```
hadoop version
```
## Execute Hadoop wordcount example
Create a file and write whatever you want
```
echo "Toms hello world hello Hello" > /tmp/test.txt
```
Exit safe mode
```
hadoop dfsadmin -safemode leave
```
Save the file to HDFS:
```
hadoop fs -copyFromLocal /tmp/test.txt test.txt
```
Execute the built in given example MapReduce-job "wordcount" on your newly created test.txt by writing the following in the terminal:
```
cd $HADOOP_HOME
```
and then:
```
hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.6.0.jar wordcount test.txt output
```
See the result by executing:
```
hdfs dfs -cat output/part-r-00000/
```
Or do it all in one command:
```
echo "hello world hello Hello" > /tmp/test3.txt && hadoop dfsadmin -safemode leave && hadoop fs -copyFromLocal /tmp/test3.txt test3.txt && cd $HADOOP_HOME && hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.6.0.jar wordcount test3.txt output && hdfs dfs -cat output/part-r-00000/
```
## Execute Spark Scala example (does not work at the moment)
Run the spark shell by executing:
```
spark-shell \
--master yarn-client \
--driver-memory 1g \
--executor-memory 1g \
--executor-cores 1
```
Execute this classic hello world command that should return 1000
```
sc.parallelize(1 to 1000).count()
```


