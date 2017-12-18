---
layout: post
title:      "Going Down the Rabbi Hole with RabbitMQ"
date:       2017-12-18 18:09:15 +0000
permalink:  going_down_the_rabbi_hole_with_rabbitmq
---


Modern web applications can be complex. Many processes might need to happen at the same time. One process might be initiated but needs another process to complete before it can be finished, while that second process is dependent on other asynchronous functions to also be fulfilled. There are various methods to handle these layers of complexity in application development. Some of the most popular frameworks around today have built in functionality that helps address these&nbsp;issues.

This past week I went down the rabbit hole of one way to address handling multiple inter-dependent tasks by beginning to learn about [RabbitMQ](https://www.rabbitmq.com/).

![](https://cdn-images-1.medium.com/max/1024/1*KEmYc1dyOpiJiRwo7b-0QQ.jpeg)

What is RabbitMQ? RabbitMQ is an open source message broker software package. With RabbitMQ you can set up the infrastructure to connect the various components of your application that are dependent on each other. RabbitMQ works by creating producers and consumers that interact with message queues. Producers create the message, while consumers receive the message. Messages live in a message queue. The consumers are always listening for new messages and when a new message is received it is interpreted and acted upon as specified in the&nbsp;program.

Let us simulate what this looks like with a simple “Hello World” message. The RabbitMQ website contains an abundance of materials on the software, including excellent tutorials and I highly recommend exploring it for a more in-depth&nbsp;look.

The producer for our “Hello World” message written in Javascript will look like&nbsp;this:

```
#!/usr/bin/env node

const amqp = require('amqplib/callback_api');

serveramqp.connect('amqp://localhost', function(err, conn) {
 conn.createChannel(function(err, ch) {   
   let q = "hello";    
   let msg = process.argv.slice(2).join(' ') || "Hello World!";     
   ch.assertQueue(q, {durable: false});    
   ch.sendToQueue(q, new Buffer(msg), {persistent: true});
   console.log(" Message was sent %s", msg);
 });
 setTimeout(function() {conn.close(); process.exit(0) }, 500)
});
```

What we have done above is first setup the [AMQP client library](https://www.npmjs.com/package/amqp-client), which allows us to send and receive RabbitMQ messages. Then, we setup a connection serveramqp.connect, which takes two arguments: the server we are setting up and a function. In this function we create a message channel, which also takes an argument of a function, wherein we define our queue (let q = hello;) and our message as either what we input on the command line or “Hello World. We proceed from there to create the queue and send to our queue the message. In the process of doing so, we also log to console that we sent it to the queue, so we know it succeeded. Lastly, we close the channel connection and exit the process after 5&nbsp;seconds.

Now, we need to setup our RabbitMQ consumer. In this example below we are going to simulate the workload that each message will bring to our program by waiting a second for each “.” present in the message. You can run multiple RabbitMQ consumers to listen to the same message queue and each time one receives a message it works on the content of that message, but the other running consumers are free to receive additional messages. The system knows to send to open consumers first, instead of creating waitlists of messages behind each consumer, whenever possible.

```
#!/usr/bin/env node

const amqp = require('amqplib/callback_api');

amqp.connect('amqp://localhost', function(err, conn) {
  conn.createChannel(function(err, ch) {
    let q = "hello";
    ch.assertQueue(q, {durable: false});
    
    console.log("Listening for new messages in %s. To exit press CTRL+C", q);
    ch.consume(q, function(msg) {
      let secs = msg.content.toString().split('.').length - 1; console.log(" [x] Received %s", msg.content.toString());
     setTimeout(function() {
        console.log("Work done");
      }, secs * 1000);
    }, {noAck: true});
  });
});
```

Our consumer function has some overlap with our producer function. Just like our producer function, we need to require the AMQP library. We also need to define our message queue, and it is important here that it is named the same as it is named in the producer. Unlike our producer, the consumer does not shutdown after a specified period of time, because its job is simply to listen for new messages and then to send them to the right places to be acted upon. As mentioned above, we simulate a workload by waiting a second for each “.” in the message: let secs = msg.content.toString().split(‘.’).length — 1;.

What we have defined above is a simple mockup of a RabbitMQ system. RabbitMQ is an incredibly powerful tool to incorporate into a complex application and we have only scratched the surface. If you are interested in taking a deeper dive I’d highly recommend working your way through the [tutorials](https://www.rabbitmq.com/getstarted.html) that they provide on their site. The code above is a combination of the first two tutorials they present. One word of warning though: Once you start going down the rabbit hole, you might have a hard time coming back&nbsp;up.
