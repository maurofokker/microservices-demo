# microservices-demo

* Spring boot 2.0.3-RELEASE
* Java 8
* notes can be found in repositories of this demo

## Configuration of sprint cloud
* configuration for services is centralized in a repository (git or svn)
	* create a configuration git project in your local or github (for this demo is created in my local in a folder named _configuration_)
	* store services configurations (i.e. _config-client-development.properties_)
	  * simple property value: `message=Hello Microservice`
	  * encrypted property value: `message={cipher}52b9b3356c1847042d5c81aa6ca43858c995549639b00eac1d7c439118da995db376812f0a0d5c44737087fc2a093cb0`

* create a project with spring boot and spring cloud starter config server
	* demo in [spring-microservices-config-server](https://github.com/maurofokker/spring-microservices-config-server)
* create a project with spring boot and spring cloud starter config client
	* demo in [spring-microservices-config-client](https://github.com/maurofokker/spring-microservices-config-client)

## Spring Cloud: Netflix Cloud Platform

* Part of Netflix _Open Source Software (OSS)_
* Provide common solutions for distributed systems
* Allows to manage microservice architecture easily
* Has important components that address common problems bump around when working with distributed systems
* It is a trusted platform because has been tried and proven in a production capacity by Netflix

### Components in the platform

* `Eureka`: Service registry and discovery pattern allowing to catalog all of our services and making them aware to other services
  * demo in
    * [spring-microservices-eureka-server](https://github.com/maurofokker/spring-microservices-eureka-server)
    * [spring-microservices-eureka-client](https://github.com/maurofokker/spring-microservices-eureka-client)
	* [spring-microservices-eureka-client-2](https://github.com/maurofokker/spring-microservices-eureka-client-2)
* `Hystix`: (Latency and Fault tolerance)
  * provides circuit breaking
  * if a microservice is not performing to a certain level there is some latency with the service then a circuit breaker can be used
	to remove that service from the distributed system
  * hystrix can route around failing service through the fault tolerance feature
  * provides a dashboard for monitoring health of system
  * demo in
    * [simple microservice](https://github.com/maurofokker/spring-microservices-simple-service)
    * [simple microservice with hystrix](https://github.com/maurofokker/spring-microservices-hystrix)
* `Ribbon`: (Load balancing)
  * provides load balancing when working with microservices
  * it has various load balancing implementations that can be used to control how request are distributed within microservices architecture
* `Zuul`: (Edge service and Routing)
  * provides a single interface through which all the clients of our system enter
  * above provide a solit point where we can manage a variety of concerns within zuul
  * can establish routing for particular requests to the appropriate microservice
  * prevents to clients from having to know the exact detail of where a particular service lies within the architecture
  * services are hide behind Zuul as a reverse proxy and that allow to relocate services rather easily without impacting clients
