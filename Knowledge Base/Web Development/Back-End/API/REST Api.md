# REST Api

REST = Representational State Transfer

### Key requirements, or constraints, that an API must feature in order to be considered a compliant or "RESTful" API:

**1.  Client-Server Separation**
- Any interaction - in the form of requests
- The client is responsible for making requests to the server, while the server is in charge of storing and sending data.
- **because of this single API works with mobile and web**
	
**2. Stateless**
- Each request must contain all the information the server needs to process and properly respond to a request.
- In the "Around the U.S project", in order to fetch the card from the database, you sent a token to the server. In doing so, you gave the server information that could be used to complete your request.
- By using token authentication, the server doesn't need to store any session information. 
- Thus, as the server doesn't store any information about the current session, we use the term "stateless".

**3. Uniform Interface**
Having a uniform interface means that the REST API has a standard and consistent way to access that interface, like via the standard HTTP methods and a consistent URL scheme formatted like so: `/<resource name>/<resource id>`. As with `GET /cards/1` or `POST /cards`, the response should include enough information to be able to understand it and act on it, without any additional special knowledge.

**4. Layered System**
- The fourth constraint allows us to create these complex systems, and to include more servers in the middle of our operations, without breaking the first constraint.
- The Yandex Taxi API itself uses the Yandex Navigator API. 
- When using the Yandex Taxi app, its API is a client of the Navigator API.

**5. Cachable**
- Data can be cached on client side
- This prevents clients from unnecessarily requesting the same data over and over again across multiple visits.

**6. Code-on-demand *(optional)***
- Server can extend a client's functionality using server code.
- The server sends JavaScript and the client executes it in the browser.


