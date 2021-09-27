# Project name: Vicino
Please complete it on or before Monday (presentation would be on Monday) and fill this form

Vicino is known for its hotel search product which enables users to compare thousands of accommodations and prices in USA. Additionally,it is also present on other hotel ads platforms such as Google Hotel Ads.
Such platforms provide an API to enable businesses to connect to their back-end services and to provide inventory and pricing to be advertised on the target platform.

Objective: Build a web application for Vicino ( a platform that compares the prices of different hotels for a particular region that would be used by the consumer).

## Technical Aspects:
### Microservices:
- Reading price data for the target hotel ads platform from a Kafka topic
- Converting the data to a different format required by the target hotel ads platform
- Sending the data to the target hotel ads platform
- Write information about sent data to a business log
- Implementation:
- Handling of fluctuating processing volumes: non-blocking IO, backpressure
- For API quotas: Rate limiting of requests and buffering of data.
- Resilience: Streamlined error handling and propagation.
- Scalability: Vertical due to non-blocking nature and making use of Schedulers, horizontal using your favorite container orchestration.

Below options can be used to address the above challenges/implementation requirements:

• Spring Boot as our fundamental application framework
• Reactor (Core), implementation of the reactive API
• Spring’s WebFlux for HTTP based communication with reactive API
• Reactor Kafka, a reactive API built on top of Apache’s Kafka API

High-level processing steps for the application:

• Consume prices from the input Kafka topic.
• Buffer prices to create larger batches for HTTP bursts.
• Following more compute-intensive and data-independent steps are scheduled to a thread pool to increase the throughput of the application:
• Transform the batch of prices to a data structure expected by the target hotel ads platform, e.g. a Transaction for Google’s API
• Send the resulting object to the designated HTTP endpoint
• If successful, log the sent prices to a business log (Kafka topic)

Group 1:
Andrew Gregersen (project coordinator)
Rolando Leiva
SEZIN DEMIR
Tam Nguyen
Taryn Jones

Group 2:
Tyler Bagala (project coordinator)
Daniel Westfall
Gabriela Amezcua
Jesus Esquer
Jonathan Gomez
