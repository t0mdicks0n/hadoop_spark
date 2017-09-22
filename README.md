Build by:
 ```
 docker build -t <name> .
 ```
Run and SSH into the container by:
 ```
 docker run -it <name> /etc/bootstrap.sh -bash
 ```
Run example MapReduce Job:
```
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.4.jar grep input output 'dfs[a-z.]+'
```

