In this activity, you will be utilizing the word count program from Mini-Lesson 18.4 on a larger text file that you will download from Project Gutenberg Links to an external site..

An alternate site for downloading the required .zip file is the Internet Archive Links to an external site.. If you have any difficulty accessing Project Gutenberg, please try downloading the .zip file from the Internet Archive Links to an external site.instead.

Reference

Project Gutenberg. “Welcome to Project Gutenberg.” Project Gutenberg. Accessed December 21, 2021. https://gutenberg.org/Links to an external site.

Prior to beginning this activity, review the submission instructions below to ensure that you collect the required screenshots as you progress through the activity.

Make sure that you have installed Hadoop in Docker and that all of the containers are running.
Provide a screenshot of your Docker desktop to show all of the Hadoop containers running.
Open your browser to Project Gutenberg Links to an external site.and look for Moby Dick by Herman Melville. Download the .zip file containing the book as a text (.txt) file to your local machine. Unzip the file to your local machine. Provide a screenshot of your local machine to show that you successfully downloaded the Moby Dick .zip file and unzipped its contents to your local machine. (If you have any difficulty accessing Project Gutenberg, please try downloading the .zip file from the Internet Archive Links to an external site.instead.)
From your Docker desktop, select <CLI> from the namenode container. From the bash window, create a folder in the namenode container and call it input. Provide a screenshot to show that you successfully created the input folder in the namenode container.
From your local machine, run a Docker cp command to copy the .txt file you downloaded from Project Gutenberg or the Internet Archive to the namenode input container. 
`docker cp ./mobydick/. namenode:/input`
Provide a screenshot to show that you successfully copied the .txt file to the namenode container.
From the bash window, run a HDFS command to create a folder named input. Provide a screenshot to show that you successfully created an input folder.
`hadoop fs -mkdir -p input`
From the bash window, run a HDFS command to copy the contents of the local input folder to the HDFS input 
`hdfs dfs -put ./input/* input`
Provide a screenshot to show that you successfully ran the HDFS command to copy the contents of the local input folder to the HDFS input folder.
From the bash window, run the curl command to download the hadoop-mapreduce-examples-2.7.1-sources.jar jar file to the current directory. `curl -L https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/hadoop-mapreduce-examples-2.7.1-sources.jar --output hadoop-mapreduce-examples-2.7.1-sources.jar`

Provide a screenshot to show that you successfully ran the curl command to download the jar file.
From the bash window, run the word count program. 
`hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount input output`

Provide a screenshot to show that you successfully ran the word count program. For this step, ensure that the output directory does not exist already. If it does, you can delete it before completing this step by running the command rm -r output.
From the bash window, run the cat command on the HDFS output directory to display the contents of the file. 
`hdfs dfs -cat output/part-r-00000`
Provide a screenshot to show that you successfully executed the cat command to display the contents of the file.
In this activity, you ran a word count program to illustrate Hadoop’s MapReduce architecture. You also manipulated the HDFS so that Hadoop could process files.