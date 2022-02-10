# Fraud Detection Application
Building a Real-Time Fraud Detection System With Kafka, Python, Docker-Compose

We will use two docker container groups in this project, one container for the Kafka service which consists of zookeeper and Kafka broker, and another container for our application that generates and processes a stream of transactions to detect potential fraudulant activity. The two containers will communicate via a shared network.
### Architecture
![alt text](https://github.com/Rogercli/Fraud_Detection_Kafka/blob/main/architecture.png?raw=true)

### Run and Verify
**Step 1**: Build and start kafka and zookeeper cluster
* docker-compose -f docker-compose.kafka.yml up --build 

**Step 2**: Build and start our application container for generator and detector
* docker-compose up --build

**Step 3**: Check Kafka legitimate and fraudulant transactions
* docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consumer --bootstrap-server localhost:9092 --topic streaming.transactions.fraud
* docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consume --bootstrap-server localhost:9092 --topic streaming.transactions.legit

