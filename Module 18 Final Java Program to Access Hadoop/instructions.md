In this assignment, you will practice performing data storage in Hadoop using data that contains information about product sales transactions. In the first part of the assignment, you will be challenged to build a Hadoop Docker container and ingest data into Hadoop data storage. In the second part of the assignment, you will explain what each Java program does and then apply the MapReduce framework to an input file to calculate aggregate sales by country.

Prior to beginning this activity, review the submission instructions below to ensure that you collect the required screenshots as you progress through the activity.

Reference

Taylor, David. “Hadoop & MapReduce Examples: Create First Program in Java.” Guru99. 2021. https://www.guru99.com/create-your-first-hadoop-program.html.Links to an external site.

To complete this assignment, follow these steps:

Before you begin the steps of the activity below, be sure that you have the Hadoop containers that you created in Activity 18.1 running within Docker.

Navigate to the [Big Data Europe Project](https://github.com/big-data-europe/docker-hadoop).GitHub repository and download the Docker Hadoop image on your local machine. Provide a screenshot to show that you successfully cloned the Big Data Europe Project GitHub repository.
The Big Data Europe Project GitHub repository contains a docker-compose.yml file that is ready to be deployed to the Docker containers. Provide a screenshot to show that you are able to find the docker-compose.yml file using the command line interface.

From the top level of your repository, run the following command to create the containers:
`docker-compose up -d`

Note: The -d flag will set the container to run in a detachable model, i.e., in the background. Provide a screenshot to show that you successfully ran the Docker command to create the containers.

Check the Hadoop containers that were created from the Hadoop images, and make sure that each container displays the (healthy) STATUS.
Provide a screenshot to show that you have all of the Hadoop containers running in the (healthy) STATUS.

Review whether the Hadoop server is active by navigating to http://localhost:9870. Provide a screenshot to show that you are able to open a Hadoop web browser link.

Part 1: Ingesting Data into the HDFS

For the first part of this assignment, you will ingest the SalesData.csv file into Hadoop data storage.

Download and extract the testprogram.zip file on your machine. Open the command line interface on your machine and navigate to the extracted folder. Provide a screenshot to show that you unzipped the testprogram.zip file.
Change the directory to the parent of the testprogram and perform the Docker copy command to copy the testprogram folder into the home directory of the Hadoop namenode.
`docker cp testprogram/ namenode:/home`

Provide a screenshot to show that you copied the testprogram folder into the home directory of the Hadoop namenode.
Open the namenode CLI in Docker. Inside the home directory, use the HDFS command below to create an input folder called inputMapReduce.
`hdfs dfs -mkdir /inputMapReduce`

Navigate to the home directory of the testprogram folder. Use the command below to perform an HDFS copy of the SalesData.csv file into the Hadoop data storage.

`hdfs dfs -copyFromLocal SalesData.csv /inputMapReduce`

Provide a screenshot to show that you successfully copied the SalesData.csv file into the inputMapReduce folder.
Review the copied file using the HDFS cat command.
`hdfs dfs -cat /inputMapReduce/SalesData.csv`

Provide a screenshot to show that the file has been copied using the HDFS cat command.

## Part 2: Performing MapReduce: Aggregation Sales by Country

For the second part of this assignment, you will use the code files under the testprogram folder on the namenode using the Docker CLI.

Navigate and review the source code in the testprogram folder and describe the functions within each file listed below:
SalesCountryDriver.java
SalesMapper.java
SalesCountryReducer.java
In your submission file, provide a description of each of the three Java files listed above that are used to apply the MapReduce framework on the Hadoop database.
In the namenode CLI, run the commands below to set up an executable path in your system environment:
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre/
export CLASSPATH="$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-core-3.2.1.jar:$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-common-3.2.1.jar:$HADOOP_HOME/share/hadoop/common/hadoop-common-3.2.1.jar:~/testprogram/SalesCountry/*:$HADOOP_HOME/lib/*"
export HDFS_NAMENODE_USER="root"
export HDFS_DATANODE_USER="root"
export HDFS_SECONDARYNAMENODE_USER="root"
export YARN_RESOURCEMANAGER_USER="root"
export YARN_NODEMANAGER_USER="root"

Once you have completed this, run the command below to confirm that you have correctly defined the environment variables.

`printenv`

Provide a screenshot to show that you have successfully defined the environment variables in the namenode CLI.
Navigate to the /home/testprogram folder in the namenode CLI and compile a Java program using the command below. This will create a SalesCountry folder with class files within it.
`javac -d . SalesMapper.java SalesCountryReducer.java SalesCountryDriver.java`

Provide a screenshot to show that you successfully compiled the Java files in the SalesCountry folder.
From the testprogram folder, create a jar file from the Java code compiled in the previous step. To achieve this, run the command below:
`jar cfm ProductSalePerCountry.jar Manifest.txt SalesCountry/*.class`

Provide a screenshot to show that you successfully created a jar file from the compiled Java code.
Perform a MapReduce operation using the command below:
`$HADOOP_HOME/bin/hadoop jar ProductSalePerCountry.jar /inputMapReduce /mapreduce_output_sales`

Provide a screenshot to show that you successfully ran the MapReduce operation to distribute the analysis of the data.
Review the SalesCountry data output in the part-00000 file by running the command below:
`$HADOOP_HOME/bin/hdfs dfs -cat /mapreduce_output_sales/part-00000`

Provide a screenshot to show that you successfully visualized the content of the part-00000 file inside the mapreduce_output_sales folder.