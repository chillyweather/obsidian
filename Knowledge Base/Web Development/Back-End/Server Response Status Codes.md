# Server Response Status Codes

-   **1xx: Informational response —** These responses indicate that the request was received by the server and the client must wait for the final response.
-   **2xx: Success response —** The request was successful!
-   **3xx: Redirection —** The request has been redirected to another server and the client needs to take some further action to complete the request.
-   **4xx: Client Error —** This means there was an error on the client-side. This means the request wasn't generated correctly or the client doesn't have the required access rights.
-   **5xx: Server Error —** This status indicates a server-side error, meaning something has broken or the server is overloaded.

### Common Status Codes

**200 OK:** This request means the request was successful. A response with this status must contain a body. Most often, this status code is used when responding to a GET request on a resource.

**201 Created:** This means that a resource was successfully created on the server. For example, this is a valid code to send upon creating a new blog post.

**202 Accepted:** The server has started processing the request but hasn't finished it yet. This status is used to respond to requests that take a long time to process, for example, when processing a large amount of data.

**301 Moved Permanently:** The API has been modified and the resource was moved to a new URI. This is indicated in the "Location" header of the server response.

**302 Found:** The request must be redirected to a different URI. In the Location header, the server should send a new URI. When a request is received, the browser will automatically send a request to the new URL.

**400 Bad Request:** This represents a client-side error. For example, we might see this error if the request was malformed. This is a general status. It is sent when no other 4xx status fits the context.

**401 Unauthorized:** The request requires authorization, but the corresponding authorization headers are missing or malformed.

**403 Forbidden:** The request is correct, but the client doesn't have the rights to complete it. For example, this can happen when a client tries to delete someone else's post.

**404 Not Found:** This means a resource could not be found. For example, when trying to find a user and the requested id doesn't exist. This is probably the most recognisable code for many people.

**405 Method Not Allowed:** The requested resource doesn't support the HTTP method that was used to make the request.

**500 Internal Server Error:** This is a generic status for server-side errors. This isn't the client's fault.

**501 Not Implemented:** The resource is on the server, but the request method is not supported by the server.