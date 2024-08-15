In this activity, you will apply what you have learned in this section to create a Hadoop Docker environment from scratch and test it to make sure that it is working.

Prior to beginning this activity, review the submission instructions below to ensure that you collect the required screenshots as you progress through the activity.

To complete this activity, follow these steps:

Review the existing list of containers running on your machine by running the command below:
`docker ps`

Provide a screenshot to show that you successfully reviewed the list of Docker containers running on your machine using the docker ps command.

Navigate to the [Big Data Europe Project](https://github.com/big-data-europe/docker-hadoop).GitHub repository and download the Docker Hadoop image on your local machine. Provide a screenshot to show that you successfully cloned the Big Data Europe Project GitHub repository.
The Big Data Europe Project GitHub repository contains a docker-compose.yml file that is ready to be deployed to the Docker containers. Provide a screenshot to show that you are able to find the docker-compose.yml file using the command line interface.

From the top level of your repository, run the following command to create the containers:
`docker-compose up -d`

Note: The -d flag will set the container to run in a detachable model, i.e., in the background. Provide a screenshot to show that you successfully ran the Docker command to create the containers.

Check the Hadoop containers that were created from the Hadoop images, and make sure that each container displays the (healthy) STATUS.
Provide a screenshot to show that you have all of the Hadoop containers running in the (healthy) STATUS.

Review whether the Hadoop server is active by navigating to http://localhost:9870. Provide a screenshot to show that you are able to open a Hadoop web browser link.