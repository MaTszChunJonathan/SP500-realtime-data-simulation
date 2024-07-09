# SP500-realtime-data-simulation

## Architecture
![Drawing (1)](https://github.com/MaTszChunJonathan/SP500-realtime-data-simulation/assets/66008170/23a6f158-1a1a-4b06-995f-b485896f4d7c)

## Dataset:
https://www.kaggle.com/datasets/joebeachcapital/s-and-p500-index-stocks-daily-updated

## How to use
1. **Download necessary files and packages**: 
   - wget https://downloads.apache.org/kafka/3.7.1/kafka_2.13-3.7.1.tgz
   - tar -xvf kafka_2.13-3.7.1.tgz
   - sudo yum install java-1.8.0-openjdk
   - Download "kafka-stock-market-project.pem" key from aws
   
2. **ssh into ec2 instance and start zookeeper server**: 
   - ssh -i "kafka-stock-market-project.pem" ec2-user@ec2-13-229-124-127.ap-southeast-1.compute.amazonaws.com
   - cd kafka_2.13-3.7.1
   - bin/zookeeper-server-start.sh config/zookeeper.properties
  
3. **open new command prompt, ssh into ec2 instance and start Kafka server**: 
   - ssh -i "kafka-stock-market-project.pem" ec2-user@ec2-13-229-124-127.ap-southeast-1.compute.amazonaws.com
   - cd kafka_2.13-3.7.1
   - export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
   - bin/kafka-server-start.sh config/server.properties
     
4. **Run both producer.py and consumer.py on local machine**:

## AWS technologies used
- **AWS S3 bucket**: Receives json files from consumer every second
![image](https://github.com/MaTszChunJonathan/SP500-realtime-data-simulation/assets/66008170/53b6448e-6c84-4322-990a-303cae904bc6)

- **AWS Crawler**: Converts json files in S3 bucket to useful SQL schema
![image](https://github.com/MaTszChunJonathan/SP500-realtime-data-simulation/assets/66008170/7ebee744-9164-4370-a5d7-b547f67f21b1)

- **AWS Athena**: Queries can be run on created schema which refreshes data every second
![image](https://github.com/MaTszChunJonathan/SP500-realtime-data-simulation/assets/66008170/d7f341b8-74f9-4084-9d4b-4469f8186c4f)




