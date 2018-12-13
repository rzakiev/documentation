# Getting Started with MBS API

MBS Web Console enables providers to interact with the service's backend via a special API. This API offers you a diverse set of requests that you can incorporate into your automation workflow or various remote management solutions like ConnectWise.

This article explains how to get started with MBS API. There are three components to it:

1. Generating MBS API Credentials
2. Generating an Access Token
3. Sending HTTPS Requests via MBS API

## Generating MBS API Credentials

To start using MBS API, you first need to generate MBS API credentials.These credentials will subsequently be used for the initial token generation.

In the MBS Web Console, under **Settings**, click **General**. Then click **Change Credentials**.

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/mbsapiintro1.png)

In the newly appeared pop-up window, click **Generate**.

![](https://github.com/rzakiev/documentation/tree/825c2f64ff90af49b1daa32930a61d866bc1dc67/.gitbook/assets/mbsapiintro2.png)

Now that the credentials are generated, proceed to request the initial authentication token that will later be used in all of the HTTPS requests to MBS. Arguably the easiest way of sending the requests is with the help of an app called _Postman_. It's a popular solution for sending all sorts of requests and it has a very intuitive and easy-to-follow UI. In this tutorial, however, we will demonstrate how to send requests using Python.

## Generating an Access Token

First, you need to request a token by sending a POST request that contains the credentials from the first step. For simplification purposes, we'll leverage a Python library called _requests_ that provides powerful methods for sending HTTPS requests with just a few lines of code. If you don't have one, simply run the following command in your terminal:

```bash
pipenv install requests
```

To send the first request, execute the following code:

```python
#The library required to make HTTP requests
import requests

#MBS API credentials generated earlier
apiCreds = {
    "UserName" : "fakeJKZcsy",
    "Password": "fakekjwZmAJvAQBYjja"
}

#Creating an object of class 'request' and initializing it with MBS API URL and credentials
authenticationRequest = requests.post('https://api.mspbackups.com/api/Provider/Login', json = apiCreds)
```

As you can tell, we're essentially creating an object of class requests and use the post method to construct and send a request. The first argument in the method is the request URL that consists of the base URL and the text copied from the previous screenshot. The second argument is JSON data that contains your credentials.

```python
print ("Status code: " + str(authenticationRequest.status_code) + "\n")

#Printing out the response
jsonData = authenticationRequest.json()

for key, value in jsonData.items():
    print (str(key) + ": " + str(value) + "\n")
```

If you execute the code, the request will be constructed and sent. In response you should receive another JSON that contains your token. Let's run the following code to ensure that everything worked out perfectly and then print out the received JSON:

```text
Status code: 200

access_token: fakeEkt8_niPVUehjYUSgKCTqC6w40s7aUfakez16m7egNZQkId1LMUhUEeMlNGfake

token_type: bearer

expires_in: 1209599

userName: wejfiwejf

.issued: Sat, 28 Apr 2018 13:50:43 GMT

.expires: Sat, 12 May 2018 13:50:43 GMT
```

And there you have it – the access token along with other critical information. Notice that each token expires two weeks after its generation. Write down the token somewhere, you'll need it to send all the other requests.

The following pages in this section describe all available requests in detail.

