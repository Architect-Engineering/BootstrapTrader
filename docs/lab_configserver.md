# Creating the Configuration service.

All our microservices will retrieve their configuration from a Configuration service.

Underneath the covers, this discovery service is implemented using the [Spring Cloud Config](http://cloud.spring.io/spring-cloud-config/).

### Exercise

1. Log in to the Apps Manager through your browser. The URL will be: `https://console.<your_cloud_foundry_url>/`

Go the *Marketplace* and choose a *Config Server for Pivotal Cloud Foundry*.

When prompted for the name of the service, insert **"config-server"** and bind it to the space you are using to deploy your applications.

> You can pick any name of the service, however, the service is already specified in the manifest files, so it is easier to re-use that name. If you do modify the name, ensure you modify it in the manifest files as well.

2. Click on *Manage* for the service you created to open the service dashboard. It will prompt you to enter either a Git or Subversion URI. Choose Git and enter **https://github.com/Architect-Engineering/BootstrapTrader-config.git** as the URI.

##Deploying without Spring Cloud Services
If the cloud does not provide us with the services, then we can deploy the services ourselves. Bare in mind that our deployment of the Config Service will not be highly available or load balanced.

Follow the guidelines to deploy the Config service [here](https://github.com/dpinto-pivotal/cf-SpringBootTrader-extras).

### Exercise
1. Create a *user provided service* using the CLI.

  Name this service **config-server** and specify the URI of your instance of the registry service. For example:

  `cf cups config-service -p '{"tag":"config","uri":"<my-config-service-URI>"}'`

  The URI of your Config server is the URI where your config server is deployed. This was displayed at the end of `cf push` command when deploying the service.

2. Multiple spaces.

    If you are deploying the services to multiple spaces, then you must create the user-provided service in each space.

##Running it locally
If you want to run all the services locally, you'll need to start the discovery service.

Follow the guidelines to run the Discover service locally  [here](lab_local.md).

You can now move on to [pushing the quote service](lab_pushquote.md)
