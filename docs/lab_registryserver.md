# Creating the discovery service.

All our microservices will connect to a Service Registry. We will use the Discovery service provided by the Spring Cloud Services.

Underneath the covers, this discovery service is implemented using the [Spring Cloud Netflix - Eureka](http://cloud.spring.io/spring-cloud-netflix/).

As such, all we have to do to implement a discovery service is to create a service instance.
### Exercise

1. Log in to the Apps Manager through your browser. The URL will be: `https://console.<your_cloud_foundry_url>/`

Go the *Marketplace* and choose a *Service Registry for Pivotal Cloud Foundry*.

When prompted for the name of the service, insert **"discovery-service"** and bind it to the space you are using to deploy your applications.

> You can pick any name of the service, however, the service is already specified in the manifest files, so it is easier to re-use that name. If you do modify the name, ensure you modify it in the manifest files as well.

##Deploying without Spring Cloud Services
If the cloud does not provide us with the services, then we can deploy the services ourselves. Bare in mind that our deployment of the Discovery Service will not be highly available or load balanced.

Follow the guidelines to deploy the Discover service [here](https://github.com/dpinto-pivotal/cf-SpringBootTrader-extras).


### Exercise
1. Create a *user provided service* using the CLI.

  Name this service **service-registry** and specify the URI of your instance of the registry service. For example:

  `cf cups service-registry -p '{"tag":"eureka","uri":"<my-discovery-service-URI>"}'`

  The URI of your discovery service is the URI where your discovery service is deployed. This was displayed at the end of `cf push` command when deploying the discovery service.
  > The URI will be similar to `eureka-dpinto.cfapps.io`.

  > Do **not** specify the protocol!!! ie. "http://"

2. Multiple spaces.

    If you are deploying the services to multiple spaces, then you must create the user-provided service in each space.

##Running it locally
If you want to run all the services locally, you'll need to start the discovery service.

Follow the guidelines to run the Discover service locally  [here](lab_local.md).

## Alternative to Registry service
The registry service allows us to have a dynamic registration and discovery of services. However, it is not the only way for microservices to connect to each other.

An alternative is to use [Spring Cloud Connectors](http://cloud.spring.io/spring-cloud-connectors/) with user-provided or managed services

It is also possible to deploy your own Eureka server to the platform.

# Summary

The registry server has a UI that can be accessed on the link provided in the console UI. Find the discovery service you created and click on **Manage**.

If you deployed your own Discovery service or are running it locally, you can also access the UI by going to the deployed application's URL.

You can now move on to [Creating the Circuit Breaker Dashboard](lab_circuitbreaker.md)
