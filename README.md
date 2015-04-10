#javaMapReduce_w_maven
#simple java map reduce project using maven

-- settings.xml in root dir of this repo is need to specify cloudera hadoop repository for maven, need to be copied or moved to ${HOME}/.m2/ directory

-- in order to run this program and build the jar, need to use maven clean install (or maven packate)

-- For executing the map reduce job, a fully functional hadoop cluster with HDFS/namenode/datanode etc. is required.

1. hadoop fs -mkdir -p /user/hduser/ # create directory on HDFS

2. hadoop fs -ls # take a look

3. sudo chown hduser:hadoop inputFile # input file must be owned by hduser

4. sudo chown hduser:hadoop MapReduce-0.0.1-SNAPSHOT.jar # jar file must be owned by hduser

5. hadoop dfs -copyFromLocal /home/hduser/input /user/hduser/ # input file need to be on HDFS, jar file don't need to be

6. hadoop jar /home/hduser/MapReduce-0.0.1-SNAPSHOT.jar com.hduser.hadoop.MapReduce.WordCount /user/hduser/input /user/hduser/output1 
  -a. MapReduce-0.0.1-SNAPSHOP.jar was build by maven from eclipse
  -b. com.hduser.hadoop.MapReduce.WordCount is where the main function is for the java MR project (main class). It needs to be specified for hadoop command line when running the job.
  -c. input file and output directory should also be specified

7. hadoop fs -ls # take a look again, output directory is generated

8. hadoop fs -copyToLocal /user/hduser/output1 /home/hduser # from HDFS to local
