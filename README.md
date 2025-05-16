# Reflection

## Data Volume
The publisher program sends 5 UserCreatedEventMessage objects to the message broker in one run. Each message contains:
- A user_id (String)
- A user_name (String)

The program sends data for 5 different users (Amir, Budi, Cica, Dira, and Emir).

## Connection URL Explanation
The URL `amqp://guest:guest@localhost:5672` is used in both publisher and subscriber programs because:
- It represents the connection details to the same RabbitMQ message broker
- Components:
  - `amqp://` - The protocol used (Advanced Message Queuing Protocol)
  - `guest:guest` - Default username and password credentials
  - `localhost` - The broker is running on the local machine
  - `5672` - The default port for AMQP connections

Using the same URL ensures both programs connect to the same message broker instance, enabling communication between the publisher and subscriber.

## Running RabbitMQ as Message broker

![Image](https://github.com/user-attachments/assets/46e969af-9d3c-46bc-bfe5-4c859cf42961)

## Sending and Processing Event

![Image](https://github.com/user-attachments/assets/63204fe2-5d19-47bf-8fbe-82ea6415b00b)
![Image](https://github.com/user-attachments/assets/b84ad69d-7d4d-428c-807a-fd16b45094d1)

The demonstration shows the interaction between the publisher and subscriber applications:

1. Publisher Operation:
   - When executed with `cargo run`, the publisher sends 5 user creation events
   -  sequential IDs (1-5) paired with names (Amir, Budi, Cica, Dira, Emir)Each event is a UserCreatedEventMessage containing
   - Messages are sent to the RabbitMQ message broker

2. Subscriber Operation:
   - Connects to RabbitMQ using the URL "amqp://guest:guest@localhost:5672"
   - Listens continuously on the "user_created" queue
   - When messages arrive, they are processed by UserCreatedHandler.handle()
   - Each processed message is displayed in the console

The terminal screenshots demonstrate this workflow, with the publisher execution on the top picture and the subscriber receiving and processing messages on the bottom picture.

## Monitoring chart based on publisher

![Image](https://github.com/user-attachments/assets/6e3947e6-ac36-49af-98a3-cc01ebac98a0)

The image shows a spike in the RabbitMQ message rate chart, which corresponds to the times when I ran the publisher program. This indicates that the spike was caused by messages being published to the queue, confirming that the publisher is functioning and interacting correctly with RabbitMQ.   