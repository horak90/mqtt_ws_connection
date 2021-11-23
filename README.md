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

Finally you can open the index.html in the root folder.
