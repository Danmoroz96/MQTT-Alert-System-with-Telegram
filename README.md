# MQTT-Alert-System-with-Telegram
In this lab I extended IoT system by adding a real-time alert system.  When the received temperature value exceeds a threshold, the system will send a Telegram notification.  This simulates a cloud monitoring service.


1. System Architecture
This project demonstrates a multi-stage IoT pipeline where data flows from a local sensor through an edge device to a cloud-based alert system.

Flow of Data:

Sensor (Laptop 1): Simulates temperature data and sends it via Python Sockets.

Edge Device (Laptop 2): Acts as a gateway, receiving socket data and Publishing it to the MQTT Broker.

MQTT Broker (broker.emqx.io): Routes the messages to all active subscribers.

Cloud Server (Laptop 1): Subscribes to the topic. If the temperature exceeds 28°C, it triggers the Telegram API to send a notification.

2. MQTT Configuration


Broker: broker.emqx.io

Port: 1883

Topic: savonia/iot/temperature

3. How the System Works


The system uses a Decoupled Architecture. This means the sensor and the alert system don't need to know each other's IP addresses; they only need to communicate with the MQTT Broker. 

The mqtt_alert_subscriber.py script constantly listens for new data. When a message arrives, it converts the payload to a float and compares it against a predefined threshold. If the condition is met, a POST request is sent to the Telegram Bot API.


4. Reflection: Why MQTT?

 Why is MQTT useful for building monitoring and alert systems in IoT?

Low Overhead: MQTT is "lightweight," meaning it uses very little bandwidth and battery power, which is essential for remote sensors.

Asynchronous Communication: The alert system doesn't have to "wait" or "poll" for data. The broker pushes the information the millisecond it becomes available.

Reliability: MQTT ensures that critical alerts are delivered even if the network is unstable.

## Screenshots


![Screenshot 2026-03-16 214848](https://github.com/user-attachments/assets/a6ec39e0-ff4f-40ca-a1d3-d6075c6a7fb1)

![Screenshot 2026-03-16 214934](https://github.com/user-attachments/assets/2f548ff3-df19-4717-8c59-44fc6104620c)

![Screenshot 2026-03-16 215006](https://github.com/user-attachments/assets/acd32e07-8ccc-4b9f-8401-ae646fb33b8e)

![Screenshot 2026-03-16 215027](https://github.com/user-attachments/assets/a759e8a3-a222-4c53-9852-64f05564e86f)





