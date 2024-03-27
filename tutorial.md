Fitness Tracker-2
======================
In this activity, you will display the data received from the sensor.




<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/11144266/PCP.gif" width = "100%" height = "50%">




Follow the given steps to complete this activity.




1. Create a callback function for handling incoming MQTT messages by accepting the three parameters client, userdata, and message.
    ~~~python
    def on_message(client, userdata, msg):
        global sensorData
        topic = msg.topic
        payload = msg.payload.decode('utf-8')
        sensorData[topic] = payload
    ~~~
2. Create an MQTT client instance. set the callback function for incoming messages, and connect to the broker.
    ~~~python
    mqtt_client = mqtt.Client(mqtt.CallbackAPIVersion.VERSION1)
    mqtt_client.on_message = on_message
    mqtt_client.connect(mqtt_broker_ip, 1883, 60)
    ~~~
3. Subscribe to the MQTT topics and listen to incoming messages.
    ~~~python
    mqtt_client.subscribe("/Temperature")
    mqtt_client.subscribe("/Humidity")
    mqtt_client.subscribe("/Steps")
   
    mqtt_client.loop_start()
    ~~~
* Save and run the code to check the output.
