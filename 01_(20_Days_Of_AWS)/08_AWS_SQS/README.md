# Simple Queue Service (SQS)

SQS is a fast, Reliable, fully managed message queue Service. It is a webservice that gives you access to message queues that store messages waiting to be processed. 
- It ofers a reliable, highy scalable, hoted queue for storing messages between servers. 
- It allows the decoupling of application components such as failure in one coponents does not cause a bigger problem to application functionality (like in couplled app)
- Using SQS, you no longer need a highly available message cluster or the burden of running it. 
- You can delete all the messages in an SQS Queue without deletig the SQS itself.
- You can use applications on EC2 instances to read and process the SQS Queue messages.
- You can use auto scaling to scale the EC2 fleet processing the SQS messages, as the Queue size increases. 
- These applications on SQS instances can process the SQS ,essages/jobs then post the results to other SQS Queues or other AWS Service. 

AWS Queue Type 

| Standard Queue  | FIFO Queue |
| ------------- | ------------- |
| High (Unlimited) throughput  | Limited throughput (300 TPS)  |
| Atleast One dilivery  | Exactly One processing  |
| Duplicacy is possible  | Duplicacy not possible  |
| Best effort ordering  | Strict ordering First in First Out  |

FIFO queues are limited to 300 transactions per seconds (TPS), but have all the capabilities of standard Queue.  

### SQS pricing 
- The first 1 million monthly requests are free, After that pricing is according to regions. Every region has different pricing for SQS. 


### How Amazon SQS Charges 
1. **API Action :-** Every Amazon SQS action count as a request.
2. **FIFO Request :-** API actions for sending, receiving, deleting and changing visibility of messages from FIFO Queues are charged at FIFO rates. 
3. **Contents of Request :-** A single Request can have from 1 to 10 messages, upto a maximum total payload of 256kb.
4. **Size of payload :-** Each 64kb chunk of a payload is billed as 1 request  (for eg- API action with 256KB payload is billed as 4 request)
5. **Interaction with Amazon S3**
6. **Interaction with Amazon KMS** 

### SQS Polling 
polling is a tehnique to get the message from message queue. 
Two types of polling 

#### Short Polling 
- A request is returned Immediately even if the queue is empty. 
    * It does not wait for messages to apper in the queue.
    * It Queries only a subset of the Available servers for messages (based on weighted random distribution) 
    * Default by SQS
    * ReceiveMessageWaittime is Set to 0
- More request are used, which implies higher cost. 

#### Long Polling 
- It is preferred to regular/short It uses fewer requests and request cost by :- 
    *  Eliminating false empty responses by Querying all the servers.
- Reduce the number of empty responses, by allowing Amazon SQS to wait until a message is available in the queue before sending a response. unless the connection timeout (20sec)
- Receive MessageWaitTime is set to a non-zero value (max 20 sec)
- Billing is same for both pollings 

### SQS Retention Period 
- SQS messages can remain in the Queue for upto 14 days (SQS retention Period)
- Range is 1 min. to 14 days (Defaut is 4 days)
- Once the maximum retention period of a message is reached, it will be deleted automatically from the Queue.
- Message can be sent to the queue and read from the queue simultaneously
- SQS can be used with DyamoDB, EC2, ECS, Redshift, RDS, ambda, S3 to make distributed/Decoupled applications. 
- You can have multiple queues with different priorities. 


### SQS-Visibility Timeout 
- Is the duration of time a essage is locked for read by other servers. 
- Max is 12 hours and Default is 30 sec
- A server that read a message to process it, can change the message visibility timeout if it needs more time to process the message. 
- After a message is read, there are the following possibilities :-
    * An ACK is received that a message is processed, so it must be deleted from queue to avoid duplicates.
    * If a fail is received or the visibility timeout expires, the message will then be unlocked for read, such that it can e read and processed by another servers. 

### Delivery Delay 
AWS SQS provides delivery delay options to postpone the delivery of neww messages to a queue if delivery delay is defined for a Queue, a new messages will not be visible to server for the duration delay the default (min.) delay for a queue is 0 seconds The maximum is 15 minutes. 

Receive MessageWaitTime :- The default time is 0 seconds. This is max. amount of time that a long polling receive call will wait for a message to become available before returning an empty response (Max value is 20 sec)

### Dead Letter Queue 
The main task of a dead letter queue is handling message failure. A dead letter queue lets you set aside and isolate messages tat can't be processed correctly to determine why their processing did'nt succeed. 

- Dont use a ead letter queus with FIFO queue, if you dont want to break the exact order of message operations.

- DLQ must be of thee same type as the source queue (Standard or FIFO)  

