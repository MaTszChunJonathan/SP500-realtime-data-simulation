# SP500-realtime-data-simulation
Description:


Dataflow:
![Drawing (1)](https://github.com/MaTszChunJonathan/SP500-realtime-data-simulation/assets/66008170/23a6f158-1a1a-4b06-995f-b485896f4d7c)

Dataset:
https://www.kaggle.com/datasets/joebeachcapital/s-and-p500-index-stocks-daily-updated

wget https://downloads.apache.org/kafka/3.7.1/kafka_2.13-3.7.1.tgz
tar -xvf kafka_2.13-3.7.1.tgz

sudo yum install java-1.8.0-openjdk


ssh -i "kafka-stock-market-project.pem" ec2-user@ec2-13-229-124-127.ap-southeast-1.compute.amazonaws.com
cd kafka_2.13-3.7.1

bin/zookeeper-server-start.sh config/zookeeper.properties



bin/kafka-server-start.sh config/server.properties

bin/kafka-topics.sh --create --topic jonathan_test --bootstrap-server 13.229.124.127:9092 --replication-factor 1 --partitions 1

bin/kafka-console-producer.sh --topic jonathan_test --bootstrap-server 13.229.124.127:9092 

bin/kafka-console-consumer.sh --topic jonathan_test --bootstrap-server 13.229.124.127:9092

