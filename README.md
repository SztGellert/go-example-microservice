# go-example-microservice

An example golang application to show how to work with microservices in golang.
Building scalable, resilient, distributed applications.
  
  Frontend app that connects to 5 Microservices:
  
    Broker(single point of entry to microservices),
    Authentication(postgres),
    Logger(mongo),
    Mail (email with template),
    Listerner(rabbitMQ + init process) 


Init frontend: go run ./cmd/web
Init broker service: go run ./cmd/api


Monolithic vs Distributed vs Microservices?

Monoliths: One piece of software, one compiled binary, one application where all the logic exists in one place.
Everything exists in one place and compiles to one binary in Go. Everything from user auth, email, log, business logic

In a lot of cases this is okay.

Though in modern application we need to scale.

User hits one or more frontends that is an application by itself, it serves a webpage. If the user needs to send an email, frontend contacts mail microservice.
It has one purpose to send mail, knowing nothing about the frontend just how to receive a request from it.

And the same goes for authentication service.

Microservices are loosely coupled, if one needs a change we change only that one.

Microservices benefit from doing one thing and doing it well - the Unix philosophy (many smaller applications).

Each microservice can have its own database.

Auth reads from Postgres, logging reads from Mongo, amqp talks to RabbitMQ (Advanced Message Queuing Protocol -  AMQP). 

Distributed app consisting microservices is like taking a monolith and and breaking up packages or individual functions into completely separate programs.

MicroServices can communicate via JSON/REST, RPC, gRPC, messaging queues. Messaging queue receives messages, something consumes them and then takes an individual action based on the msg it received.

Easier to scale and maintain but harder to write.

Easier to scale if having each service in its own Docker image. For example this can be put into a Kubernetes cluster and can have many instances of individual microservice as we need, making it easy to scale ang get more traffic to our application.
Easier to maintain, not one large complex monolith, small services insterad doing one thing: drawback can be harder to write them.





