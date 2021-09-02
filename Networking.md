<center> <h1>NETWORK LAYER</h1> </center>

<center> <h5>_The best practices that we follow when creating our network layer_</h5> </center>

### Table of Contents
1. [Common Libraries That We Use](#common_libraries)
2. [Executing the Requests](#executing_requests)
3. [Model Classes](#model_classes)
4. [Mappers](#mappers)
5. [Repository Layer Abstraction](#repository_layer_abstraction)
6. [Error Handling](#error_handling)
7. [Testing the Network Layer](#testing_the_layer)

<a name="common_libraries"></a>
<h3>COMMON LIBRARIES THAT WE USE</h3>

- _OKHTTP_

	We use the OKHTTP Client to communicate with the server.

- _GSON_

	With Gson library we convert our Json texts to Object Classes or Object Classes to Json texts.

- _RETROFIT_

	We prefer to use Retrofit Library to send and fetch the app related data to/from the remote server.

<a name="executing_requests"></a>
<h3>EXECUTING THE REQUESTS</h3>

- When executing the requests that we need, we use coroutine's suspend functions to prevent the request process to block the main thread.

<a name="model_classes"></a>
<h3>MODEL CLASSES</h3>

 - We have two different data model class types:

 	1. One for to communicate with the network layer.

	2. One for to use in the domain layer.

- There are two type of data models because we don't want to have anything that related to domain layer in our network later or vice versa.

<a name="mappers"></a>
<h3>MAPPERS</h3>

- When using two type of data model classes, we use our mappers to map one type of model class to another one.
-  With this structure; we can separate each layer with layer spesific components and be able to use our model classes related layers.

  - Mapping process happens in the Repository Layer.

<a name="repository_layer_abstraction"></a>
<h3>REPOSITORY LAYER ABSTRACTION</h3>

* We abstract the Repository Layer with an interface, and store all the features that a Repository can perform in this interface. 

* When we want to use these feature, we simply inject the interface to the repository and implement the features as we want to use.

<a name="error_handling"></a>
<h3>ERROR HANDLING</h3>

* We use a sealad class - which named Result - to wrap our network responses. It takes a generic object in it and returns this object when the Result type is success or returns Nothing when the Result type is error.

	```
	sealed class Result<out R> {
		data class Success<out R> (val data: T) : Result<T>()
    	data class Error(val exception: Exception) : Result<Nothing>()
    	object Loading : Result<Nothing>()
	}
	```

* When request process ends with a Result type of error, we handle the error in our BaseViewModel. In the BaseViewModel class, we control the error type to choose which type of error message will be shown to user. 

	```
    when (val result = request.invoke()) {
        is Result.Success -> success?.invoke(result.data)
        is Result.Error -> if (error != null) {
            error.invoke(result)
        } else {
            handleException(result.exception)
        }
	}
	```
* If the error type is related to Http, we get the error message from errorBody and show to the user with the reason of the error. If the error type is not related to Http, we show the error with a pre-determinated error message.

<a name="testing_the_layer"></a>
<h3>TESTING THE NETWORK LAYER</h3>
