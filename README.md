Build by:
 ```
 docker build -t hadoop .
 ```
Run and SSH into the container by:
 ```
 docker run -it -p 50070:50070 hadoop /etc/bootstrap.sh -bash
 ```
Go to http://127.0.0.1:50070/ in your browser and see that Hadoop is working by executing the following inside the Docker image:
```
hadoop version
```
Create a file and write whatever you want
```
vi /tmp/test.txt
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






Make the directory /user/hduser on HDFS:
```
hdfs dfs -mkdir -p /user/hduser
```


