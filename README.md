# mqtt_ws_connection
A repository to reproduce a problem with dropping WS connection

First you will need to build a RabbitMQ image :

```
cd rabbitmq
docker build -t my_rabbitmq .
```

When you are done with building the image, you can start it with the following command : 

```
docker run -d --rm -it --hostname my-rabbit -p 15672:15672 -p 5672:5672 -p 15675:15675 my_rabbitmq
```

Finally you can open the index.html in the root folder (I use chrome version 96.0.4664.55).

Once the application is running you can observe a WS connection between the RabbitMQ server and the application. This connection will close at some time depending on a keepalive configuration of the mqtt client. For keepalive 60s it closes after 1~2 minutes, with keepalive 30s it closes after 10~12 minutes.

From my observation, with the keepalive 30s, the client will be sending PINGREQ every 30s but after the 10~12 minutes it stops and the rabbitMQ server closes the connection.

please see the following [issue](https://stackoverflow.com/questions/70064452/mqtt-over-ws-keep-closing-connection-after-several-minutes).