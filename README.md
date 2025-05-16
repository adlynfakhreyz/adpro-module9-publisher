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
