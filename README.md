# Onion Architecture Stuff
## Project Structure
The Onion Architecture in the context of a modern web API consists of a Core, an Infrastructure, and an API project.

### Core Project

   The Core project contains models, interfaces for repositories, and services that interact with the repositories. This should be the only layer that interacts with a datasource. I like to put helper classes and other universal or static classes.

### Infrastructure Project

   Infrastructure contains implementations of your interfaces. Mostly this will be implementations of your repositories, UnitOfWork, and your db context. It should also contain implementations that interact with FileSystem, SMTP, etc. 

### API Project

   The API project is self explanatory. Here you will have controllers with endpoints that use your core services to manipulate data. The services should send off orders to repos to manipulate data or send notifications/emails, but not be concerned with how those actions are completed. All of that implementation should reside in Infrastructure. 

### Unit Tests Project

   The way that the code is laid out above results in separation of concerns and loosely coupled code resulting is easier unit testing. You should be able to easily mock out a repo and what it should return to a service. 

#### Some Extra Reading
* [Jeffrey Palermo's article](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/)
* [AutoFac](https://autofaccn.readthedocs.io/en/latest/integration/aspnetcore.html#quick-start-with-configurecontainer) - A really nice tool/SoC container for Constructor Dependency Injection. I recommend using it.
