# Introduction
Axios is a popular JavaScript library used for making HTTP requests from web browsers or Node.js. It provides an easy-to-use API for sending asynchronous HTTP requests to a server and handling the responses.

    // Send a POST request
    axios({
      method: 'post',
      url: '/user/12345',
      data: {
        firstName: 'Fred',
        lastName: 'Flintstone'
      }
    });


    // GET request for remote image in node.js
    axios({
      method: 'get',
      url: 'http://bit.ly/2mTM3nY',
      responseType: 'stream'
    })
      .then(function (response) {
        response.data.pipe(fs.createWriteStream('ada_lovelace.jpg'))
      });


# Instance with Custom Config
In Axios, one can create an instance of the Axios client with custom configurations using the `axios.create()` method. 
This allows to customize the default behavior of the Axios client for specific use cases or endpoints in the application.

### Example
    import axios from 'axios';

    const instance = axios.create({
      baseURL: 'https://api.example.com',  // Set a base URL for all requests
      timeout: 5000,  // Set a default timeout for requests
      headers: {
        'Authorization': 'Bearer token123',  // Set default headers for all requests
        'Content-Type': 'application/json',
      },
    });

    // Use the instance to make requests
    instance.get('/users')
      .then(response => {
        // Handle response
      })
      .catch(error => {
        // Handle error
      });

### Benefits
1. **Custom default configurations**: Default configurations can be set such as base URL, headers, timeout, and more for all requests made with the instance. 
This eliminates the need to repeat these configurations in every request and ensures consistency across application.
2. **Interceptors**: Interceptors can be added to the instance to globally handle request and response behaviors.
For example, requests or responses can be intercepted and modified, add authentication headers, handle errors, and perform logging or analytics.
3. **Reusability and modularity**: By creating multiple instances with different configurations, these can be easily reused throughout the application. 
This allows to modularize and organize API calls based on different endpoints or specific requirements.
4. **Performance optimization**: Creating separate instances can help optimize performance by allowing to configure specific settings, 
such as different timeouts or headers, for different parts of your application. This ensures that each part has the appropriate settings tailored to its requirements.


# Config defaults
The config defaults can be specified that will be applied to every request.

    axios.defaults.baseURL = 'https://api.example.com'; 
    axios.defaults.headers.common['Authorization'] = AUTH_TOKEN; 
    axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
    

# Interceptors
Interceptors are functions that can be registered to handle requests and responses at various stages. There are two types of interceptors available in Axios: request interceptors and response interceptors.
1. **Request Interceptors**: Request interceptors are functions that are executed before an HTTP request is sent. They can be used to modify the request headers, add authentication tokens, 
or perform other operations on the request before it is sent to the server.
2. **Response Interceptors**: Response interceptors are functions that are executed after an HTTP response is received. They can be used to handle common response errors, 
transform the response data, or perform other operations on the response before it is passed to the calling code.

<br>

    // Add a request interceptor
    axios.interceptors.request.use(function (config) {
        // Do something before request is sent
        return config;
      }, function (error) {
        // Do something with request error
        return Promise.reject(error);
      });


    // Add a response interceptor
    axios.interceptors.response.use(function (response) {
        // Do something with response data
        return response;
      }, function (error) {
        // Do something with response error
        return Promise.reject(error);
      });


# Handling Error
Using the `validateStatus` config option, HTTP code(s) that should trigger an error can be defined. 
<br><br>
By default, Axios considers any HTTP status code within the range of 200 to 299 (inclusive) as a successful response, resolving the promise. Any status code outside this range is regarded as an error and causes 
the promise to be rejected.
<br><br>
However, the behavior can be customized with the validateStatus parameter. A function can be provided that takes the HTTP status code as a parameter and returns true (to resolve the promise) or 
false (to reject the promise).

    axios.get('/user/12345', {
      validateStatus: function (status) {
        return status < 500; // Resolve if the status code is less than 500
      }
    })
    

# Cancellation
## Signal
Starting from v0.22.0 Axios supports AbortController to cancel requests in fetch API way.
    
    const controller = new AbortController();

    axios.get('/foo/bar', {
       signal: controller.signal
    }).then(function(response) {
       //...
    });
    // cancel the request
    controller.abort()
    
 ## Timeout
timeout using latest AbortSignal.timeout() API [nodejs 17.3+]

    axios.get('/foo/bar', {
       signal: AbortSignal.timeout(5000) //Aborts request after 5 seconds
    }).then(function(response) {
       //...
    });
    
### Timeout Helper Function
    function newAbortSignal(timeoutMs) {
      const abortController = new AbortController();
      setTimeout(() => abortController.abort(), timeoutMs || 0);

      return abortController.signal;
    }

    axios.get('/foo/bar', {
       signal: newAbortSignal(5000) //Aborts request after 5 seconds
    }).then(function(response) {
       //...
    });


## Reference
https://axios-http.com/docs/intro
