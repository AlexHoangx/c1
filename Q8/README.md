# Q8: What is a system you had to implement using queues or streams like redis, rabbit mq, kinesis, kafka, pub/sub, sqs and why did you choose the queueing or streaming system?

### I have experienced with each kind of Message Queue, Stream and PubSub system below:
</br>

## Kafka
---
### I already implemented it for blockchain system, it's the best use-case for any kind of system need data streaming. Especially when we face with heavy workload system, Kafka easily to manage millions message per second without any issue.
</br>

## RabbitMQ
---
### Opposite of Kafka, RabbitMQ is more fittable for less complex system. Easier to manage and fast to implement is the huge advantage of RabbitMQ. RabbitMQ is not a good suggestion for any kind of system need data availability and persistence. But if we looking for a complex routing system, RabbitMQ could have one ticket for this case.
</br>

## Redis
---
### Redis well-know for kind of in-memory data store, a . Redis is very powerful and flexible with consistence, easy horizontal scale with clustering and a good choice for any kind of system. I've used Redis for web cached, 

</br>

## Memcached
---
### In other hand, Memcached is not a good choice if you have various of data type. Memcache focus on main purpose "cache" as it's name, they are not support for consistence as store data in local disk. Advantage of Memcached is easier to implement and management, simply focus on main function as a cache system and support multi-threaded. Many POC project with single type of data I've used Memcache as a cache component to prevent complexity.
