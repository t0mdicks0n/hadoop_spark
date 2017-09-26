Build by:
 ```
docker build -t hadoop .
 ```
Run and SSH into the container by:
 ```
docker run -it -p 50070:50070 -p 8088:8088 hadoop /etc/bootstrap.sh -bash
 ```
Go to localhost:50070 & localhost:8088 in your browser and see that Hadoop is working by executing the following inside the Docker image:
```
hadoop version
```
Create a file and write whatever you want
```
echo "hello world hello Hello" > /tmp/test.txt
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
hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.4.jar wordcount test.txt output
```




echo "hello world hello Hello" > /tmp/test.txt && hadoop dfsadmin -safemode leave && hadoop fs -copyFromLocal /tmp/test.txt test.txt && cd $HADOOP_HOME && hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.4.jar wordcount test.txt output



Make the directory /user/hduser on HDFS:
```
hdfs dfs -mkdir -p /user/hduser
```


