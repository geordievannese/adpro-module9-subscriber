1. What is amqp?
AMQP, or the Advanced Message Queuing Protocol, is a vendor-neutral standard for exchanging messages across distributed applications. It facilitates dependable, non-blocking communication between services, which is essential for building systems that can grow and adapt. AMQP offers capabilities such as message queuing, guaranteed delivery, and flexible routing, and is often paired with brokers like RabbitMQ. By leveraging this protocol, you can decouple components so each service can run independently without having to wait for others.


2. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for?
   
This string is the connection URI for an AMQP broker, typically RabbitMQ, running locally. It breaks down like this:
- guest – the username
- guest – the password
- localhost – indicates the broker is on your own machine
- 5672 – the default AMQP port RabbitMQ listens on
Altogether, it directs our client to connect to a RabbitMQ server on localhost:5672 using the default guest/guest credentials.


3. ## Simulation slow subscriber
![Screenshot 2025-05-14 at 09.19.22.png](img/Screenshot%202025-05-14%20at%2009.19.22.png)

When I ran the publisher program, I saw that it delivered sixteen messages to RabbitMQ, which showed up on the “Queued messages” chart under the “Total” line. That initial spike meant those sixteen messages were waiting for a consumer to pick them up either because my consumer hadn’t started yet or because it was processing more slowly than I was publishing.

Over time, my consumer caught up: each message was acknowledged and removed from the queue, causing the total count to fall back to zero. This behavior confirms that the messaging pipeline is operating correctly messages get enqueued when produced and then removed once they’re processed. Depending on how quickly the consumer starts or how many messages I send, that peak count may vary on different machines.