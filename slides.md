
BDP LEC REPORT Presentation
===========================


---
# Group Members:


David Samuel - 2301850304.

Egivenia - 2301850134.

Aurelius Vannes Leander - 2301862102.

Juanrico Alvaro - 2301847316.

---
# Case Problem


FreshMart is an established large-scale supermarket with branches in Jakarta and big cities, such as Surabaya and Bandung.

On average, FreshMart implements cashier-guided checkout and self-checkout in their supermarket.

With cashier-guided checkout, the cashier has the responsibility to scan products and manage transactions using cash registers, whereas, with self-checkout, the customers scan the products before paying without needing one-to-one staff assistance.

FreshMart is already well-established, they have enough resources to buy and own their own servers.

They prefer to outsource the server management to another party so they don’t need to search and hire talents to run and manage the servers.

---
# I. Data Source


The data source of this system is obtained from Fresh Mart’s surveillance cameras that track customers and the products that they take in real-time through live videos.

These data will be ingested in the ingestion layer using Apache Kafka.

---
# II. Ingestion Layer


The most suitable type of ingestion is real-time data processing.

We ingest the data in real-time so we can analyze it in real-time as well.

In this layer, we use Apache Kafka to ingest the data source.

The reason why we choose Apache Kafka is that it can handle a lot of data per unit of time and has low latency.

A Kafka cluster is made up of multiple nodes and several components, which are producer, broker, and consumer.

Producer reads the videos and publishes them to a Kafka Topic, which is managed by a Kafka Broker.

Consumers subscribe to one or more topics to gain access to the video data and process them.

We use Apache Spark for real-time and batch analysis of the data.

For the real-time analysis, using Spark Streaming, it takes the data from Kafka, processes them further with complex algorithms, and outputs the processed data that can be pushed to databases.

Apache Spark supports in-memory cluster computing and promises to be faster than Hadoop.

It supports multiple high-level tools for data analysis such as Spark Streaming, which we used for real-time analysis, Spark for analysis of structured data, MLlib library for spark, and GraphX for graph processing.

---
# III. Infrastructure Layer


This layer is built on a distributed computing concept which means the data will be physically or cloud-stored in many distinct locations.

On-premise also provides the speed of processing data, and the data that is saved on-premise is controllable in the local server.

---
# IV. Storage Layer


This storage is also known as a non-relational, distributed, flexible, and scalable database.

Since this database is a distributed database, this means that the data stored in the database will be able to ensure the company data availability and reliability.

For the database, we will use MongoDB which is the Document Stores type.

A document is MongoDB's fundamental data storage unit.

For saving large images such as image and video files up to 16MB per file, we can use MongoDB specification which is GridFS.

---
# V. Analytics Engines


This section will explain about the different analytical engine steps required which is as following.

This section will explain about the different analytical engine steps required which is as following.
## A. Data Preparation


We should perform data cleaning to make sure that there isn’t any missing or corrupted data.

We can perform data wrangling to make sure that the data are in their correct formats to perform analysis on.

To perform these tasks we will use the Open Refine framework.
## B. Analysis Type and Mode


There will be 2 main types of analysis that we will be performing on the FreshMart data.

Real-time analysis on the sensor data (live video) such as person detection, object detection, and customer association.

The Spark Streaming instance connects to Kafka by creating a new Data Stream called DStream.

The streaming data from Kafka will be ingested and analyzed in micro-batches.

We can then use deep learning models such as YOLO to perform real-time object and person detection.

This second analysis is a statistical analysis on a batch of transactional data.

We perform statistical analysis to get an average of weekly sales and count how many of a specific product is sold on a specific day.

---
# VI. Visualization Layer

## Web Framework


For our web framework, we use Django to develop a web application to display the analysis results which are stored in MongoDB with the help of Seaborn as the visualization framework.

Seaborn is an open-source Python library based on matplotlib that is used for exploratory data analysis and data visualization.

Matplotlib is usually used for basic plotting that generally consists of bars, pies, lines, scatter plots, and others.

Seaborn has a variety of visualization patterns to create more attractive and informative statistical graphics.

Django is a popular Python web framework to develop web applications.

A Django model is a Python class that describes the variables and functions for a certain data type.

The view is what connects the model with the template.

Django is a great web framework for big data analytics applications.

It consists of a collection of solutions, packages, and best practices to develop web applications.

The great capabilities of the Python language and ecosystem, the separation of the models from business rules and user interface (templates and views) make Django a suitable web framework for big data analytics applications.

Django is a great match with MongoDB for building powerful, secure, and easy-to- maintain applications.

Support for a non-relational database like MongoDB can be implemented by installing additional Django-MongoDB engines for MongoDB.
## Serving Database


A MongoDB database is also used to store the inferences after the deep learning models are applied to the data streams as well.

For saving large images such as image and video files up to 16MB per file, we can use MongoDB specification which is GridFS.
## Interactive Querying


Then, for querying or analyzing the data from the database such as to see the transaction of the day, etc. we can use Spark.

The MongoDB Connector for Spark provides integration between MongoDB and Apache Spark where when we have the connector, we can access all Spark Libraries.

---
# VII. Security Layer


MongoDB provides native encryption so that we do not need to pay extra money or to hire 3rd party to protect sensitive data.

MongoDB has also gone through intensive testing and has additional capabilities to improve its performance.

MongoDB supports encryption protocols such as TLS (Transport Layer Security) and SSL (Secure Socket Layer)

 TLS and SSL are cryptographic methods which means it's a method to make data unreadable or indecipherable by anyone except the authorized recipient.

MongoDB uses database encryption which is called Transparent Data Encryption (TDE)

While database keys are kept on the same server with the encrypted data, MongoDB never allows the master key to be stored on the same server as the encrypted data.

MongoDB encrypts each database using an encrypted storage engine which is WiredTiger.

When a user reads or writes data to the encrypted database, the operation will only affect the page on which the data is stored, not the entire database.

encrypting the motion and rest of data with a high-performance storage engine.

All the private and sensitive information of the company’s data such as credit card numbers will be safe and encrypted in storage.

---
# VIII. Monitoring Layer


This is the layer that will help us monitor all of the moving parts in the distributed Hadoop grid architecture.

This needs to be done so that the data that is ingested into the process flow, are reliable and consumable.

Nagios provides us with high-efficiency worker processes.

The ease of use, the customizability, and the extendable architecture that Nagios provides can also help us in creating the most suitable customized monitoring layer.