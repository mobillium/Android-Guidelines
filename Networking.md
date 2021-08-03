# NETWORK LAYER
## _OKHTTP_

We use the OKHTTP Client to communicate with the server.

## _GSON_

With Gson library we convert our Json texts to Object Classes or Object Classes to Json texts.

## _RETROFIT_

We prefer to use Retrofit Library to end and fetch the app related data to/from the remote server.

## _EXECUTING THE REQUESTS_

When executing the requests that we need, we use coroutine's suspend functions to prevent the request process to block the main thread.

## _MODEL CLASSES_

We have two different data model class types:

 - One for type of class to communicate with the network layer.

 -  One for type of class to use in the domain layer.

There are two type of data models because we don't want to have anything that related to domain layer in our network later or vice versa.

## _MAPPERS_

When using two type of data model classes, we use our mappers to map one type of model class to another one. With this structure; we can separate each layer with layer spesific components and be able to use our model classes related layers.

  - Mapping process happens in the Repository Layer.

## _REPOSITORY LAYER ABSTRACTION_

We abstract the Repository Layer with an interface, and store all the features that a Repository can perform in this interface. 

When we want to use these feature, we simply inject the interface to the repository and implement the features as we want to use.

## _ERROR HANDLING_

We use a sealad class - which named Result - to wrap our network responses. It takes a generic object in it and returns this object when the Result type is success or returns Nothing when the Result type is error.

When request process ends with a Result type of error, we handle the error in our BaseViewModel. In the BaseViewModel class, we control the error type to choose which type of error message will be shown to user. 

If the error type is related to Http, we get the error message from errorBody and show to the user with the reason of the error. If the error type is not related to Http, we show the error with a pre-determinated error message.

## _TESTING THE NETWORK LAYER_