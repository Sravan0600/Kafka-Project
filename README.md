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

We create producers and consumers running on our kafka server and the data given by the producer is recieved by the consumer.
We connect to the kafka server from our local machine using the public IP and send data using python and the consumer will recieve it.
Now, importing simialar packages for the consumer, and we decode it as the producer encodes it when he sends it to the kafka server and you can loop through the data.
We will be uing a dataset for this project and we go through it using pandas and we converst this data into json format and we send this data through the producer code.
The server might break but you can restart your zoo keeper and kafka server and the consumer will be recieving data again in real time.
We can flush out the old data and send in the new data using the command producer.flush().
Next we create an amazon S3 bucket.
Configure AWS account to your local machine and have aws CLI installed. 
In the consumer code, you can make changes to save the data into our S3 bucket.
Once we have both our codes running, we have some amount of data saved on our S3 bucket. If we download one of the files saved on S3 bucket and open it, we have one single event saved in the file.
We use crawler form AWS glue to go through the schema of data present in our S3 bucket as we can query it using Athena.
We give S3 bucket as the data source for the crawler. We need to give IAM role to glue for it to be able to access S3 just as how we configured our local machine to write data to the S3 bucket. 
We create a new database on Glue and once we finish, our crawler is created and running and once it is finisher we get to the next step.
We can preview the table using AWS athena and perform queries on it. 
We can add time delay on our producer data and the consumer data consumes the data and sends it to S3. 
We are now sending data in real time and the data is sent through kafka and to S3, crawler, glue and athena and we can verify it refreshing and checking the row count.
