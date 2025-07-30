***Remark: before starting make sure that kafka  is installed on your ssh ec2 machine as well as java-1.8.0-openjdk , extract  it.***

        ***you have aws account***

          ***in aws create roles , polices ,buckets , ec2 etc***  



1.> **Start Zoo-keeper on ec2 machine:**



bin/zookeeper-server-start.sh config/zookeeper.properties



2.> **Start Kafka-server on ec2 machine:**



* &nbsp;  Then allocate some space to the machine
* &nbsp;  export KAFKA\_HEAP\_OPTS="-Xmx256M -Xms128M"
* &nbsp;  cd kafka\_2.12-3.3.1
* &nbsp;  start the server on the ec2 machine : bin/kafka-server-start.sh config/server.properties



|----------------------------------------------------------------------------------------------------------------------------------------|

*|**NOTE : look for advertised listener if it's not showing the ec2 instance public ip address ; then change the properties in the terminal |*** 

***|                                                                                                                                        |***

***|         "sudo nano config/server.properties" - change ADVERTISED\_LISTENERS to public ip of the EC2 instance***                            |

|----------------------------------------------------------------------------------------------------------------------------------------|



3.> Now that everything's set, open another terminal duplicate the session like performing ssh to to your ec2 machine as done above



--> then Create the topic:

* &nbsp;   cd kafka\_2.12-3.3.1
* &nbsp;   bin/kafka-topics.sh --create --topic test\_topic --bootstrap-server {your public ec2 ip address}:9092 --replication-factor 1 --         partitions 1



AND ON THE SAME TERMINAL WHERE CREATION OF TOPIC WAS DONE , START THE PRODUCER TOO ON THE SAME TERMINAL



-->Start Producer:

&nbsp;  bin/kafka-console-producer.sh --topic test\_topic --bootstrap-server {your public ec2 ip address}:9092 



--> Open another terminal duplicate the session like performing ssh to to your ec2 machine as done above

Start Consumer:

* cd kafka\_2.12-3.3.1
* bin/kafka-console-consumer.sh --test\_topic --bootstrap-server {your public ec2 ip address}:9092





------------------------------------------------------------------------------------------------------------------------------------------





Now open another terminal make sure jupyter notebook is installed or any other editor of your choice 

if not install it in your home directory in ubuntu or any other os



create a virtual environment

* &nbsp; navigate to the directory you want to create virtual env :" virtualenv my-jupyter-env"
* &nbsp; activate the virtual env: " source my-jupyter-env/bin/activate 
* &nbsp; now type " jupyter notebook" and will it open the notebook in any of the default browser





// Write the consumer and producer code where the producer is fetching the data from the api and consumer code is then receiving the message as well storing it to your S3 bucket ; make sure that your aws secret key as well access key is already configured in AWS cli(install aws cli if haven't already )





//perform the query on it using Athena aws service 

