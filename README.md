# Kafka-Project

-> Created an EC2 instance on AWS 
-> Installed latest version of Kafka on it using the terminal.
   (wget https://downloads.apache.org/kafka/3.8.0/kafka_2.12-3.8.0.tgz)
-> Decompressed it using this command (tar -xvf kafka_2.12-3.8.0.tgz)
-> Install Java on to your EC2 instance. 
We need to access the folder where we have kafka on our EC2 instance and start Zoo Keeper. 
Once we have zookeeper up and running in one terminal, we need to launch kafka using new window of another terminal.
We need to allocate some amount of memory to our Kafka server. 
We need to change the configuration to be able to access our EC2 instance since it wouldn't be possibe as we are not on the same private IP address. 
Once we make the necessary changes, our kafka server should run on our public IP address. 
We will be having three terminal windows running on which we have zoo keeper, kafka running in the first 2 windows and 3rd one we use for creating topcics, producers and consumers of the data.

