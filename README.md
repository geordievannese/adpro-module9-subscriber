1. What is amqp?
AMQP, or the Advanced Message Queuing Protocol, is a vendor-neutral standard for exchanging messages across distributed applications. It facilitates dependable, non-blocking communication between services, which is essential for building systems that can grow and adapt. AMQP offers capabilities such as message queuing, guaranteed delivery, and flexible routing, and is often paired with brokers like RabbitMQ. By leveraging this protocol, you can decouple components so each service can run independently without having to wait for others.


2. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for?
   
This string is the connection URI for an AMQP broker, typically RabbitMQ, running locally. It breaks down like this:
- guest – the username
- guest – the password
- localhost – indicates the broker is on your own machine
- 5672 – the default AMQP port RabbitMQ listens on
Altogether, it directs our client to connect to a RabbitMQ server on localhost:5672 using the default guest/guest credentials.