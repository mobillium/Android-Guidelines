In the Network Layer, we prefer to use OkHTTP Client to communicate, Gson Library to convert Json to Object or Object to Json, and Retrofit library to send and fetch the app related information to the remote service.


When executing the network requests, we use coroutines suspend functions to prevent it from blocking the thread.

We have two different data model type that we use to communicate with the network layer and the ones that we use in the domain layer. That is because we don’t want to have anything from domain layer in network layer or vice versa. To accomplish this, we are using mappers to map our network based data models to domain based data models. And the mapping process must be done in the Repository layer.

We abstract the Repository Layer with an Interface, and store all the work that a Repository can do in an Interface. When we . . .

