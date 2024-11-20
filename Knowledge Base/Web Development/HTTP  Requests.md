# HTTP Requests

### Request Format

The request that the browser generates may include:

-   The HTTP method. This defines the operation that will be performed. There are several such methods, the most popular of which are the GET and POST methods. The first one is used when getting data from the server, while the second one is used to send data.
-   The path to the resource. This is the part of the web address after the website's name. Take a look at `example.com/hello`, in this case, the path is `/hello`.
-   The version of the HTTP protocol that is used to send the request, e.g. HTTP/1.1.
-   Request headers. They can be used to transfer additional information to the server.
-   The request body. However, not all requests have this. For example, the body of a POST request is the data being sent.

Here's what a request for a page on yandex.com looks like:

![image](https://pictures.s3.yandex.net/resources/sprint_9___1__228_local_1594026893.png)

### Response Format

The response may include:

-   The HTTP version.
-   An HTTP status code. For example, we might get "200 OK" if everything went swimmingly. If things didn't go so well, we might get back "404 Not Found," an infamous response which is received whenever the requested resource wasn't found.
-   Headers providing additional information for the browser.
-   The response body. For example, when you visit yandex.com, the HTML code of this page will be contained in the response body.

So, upon requesting the [yandex.com](http://yandex.com/) webpage, the response we receive looks like this:

![image](https://pictures.s3.yandex.net/resources/sprint_9___1__226_local_1594026948.png)

