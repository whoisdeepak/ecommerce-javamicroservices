# ecommerce-javamicroservices

This project aims to tackle the online shopping software paradigm through the use of microservices working together and communication with each other as a distributed system.
To achieve this, I leveraged some of the common design patterns in distributed systems such as: service discovery, centralized configuration, distributed tracing, event driven architecture, centralized logging, circuit breaker.
The high-level architecture can be understood through below design:

![micro1](https://github.com/whoisdeepak/ecommerce-javamicroservices/assets/101911034/48ec67f8-da4a-4fda-ad5d-497071b1408b)

It entails 4 main microservices: Product, Order, Inventory and Notification services.
Product service: This service is used to create and view products and stores information in its own MongoDB database, acting like a product catalog.
Order service: This service lets the user place an order and this information is stored in its own MySQL database.
Inventory service: This checks the stock/availability of a given product.
Notification service: Used to send out notifications after order is placed.

Order service communicates with inventory service to check the stock of the order that is currently being placed through synchronous communication.
On the other hand, order service communicates with notification service in an asynchronous fashion to send out notifications after the order is placed.

For asynchronous communication, I made use of Kafka and RabbitMQ.
API Gateway has been implemented using Spring Cloud Gateway.
Application is secured using authorization server called KeyCloak.
Service Discovery is implemented using Netflix Eureka Server, Distributed tracing is handled by Zipkin and Logging is achieved through Elasticsearch, Logstash and Kibana.
Finally, I made use of Prometheus and Grafana to monitor microservices and troubleshoot performance issues.
