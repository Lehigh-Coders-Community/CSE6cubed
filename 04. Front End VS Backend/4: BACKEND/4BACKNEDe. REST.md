## Intro

As computer scientists, this is the only rest that we will ever [know](https://www.youtube.com/watch?v=t7hsVa18yfA&ab_channel=LuisGranados).

REST stands for **RE**presentational **S**tate **T**ransfer and, in simple terms, is a way of architecture for designing APIs. Remember, APIs are application programming interfaces so REST allows us to make simple ways of interacting with resources (those resouces can be anything, like a document, photo, etc.)

As an example of a RESTful API, if you have a twitter account and have made a post, then Twitter's API accepted your request and put it onto their network. An important distinction to note here is that REST is commonly associated with the HTML operations GET, POST, PUT, and DELETE, but they are not technical requirements of REST. REST, as mentioned earlier, is a design pattern for APIs and must conform to 6 different constraints. 

## Quick Definitions

A **client** is the software that is reponsibile for interfacing with users. A **server** is software responsibile for maintaining resources and providing information to clients about those resources.

## Constraints

1. **Client Server Separation**: A server and a client will act independently of one another and only interact through the form of requests made by the client to the server and responses made from the server to the client. A server simply waits to be prompted by a client before ever doing anything.

2. **Stateless**: An API will not remember anything about a user that makes a request on the client software. That is, all requests should always contain all the information needed by the server to perform the requisite action. This may seem obvious, but it is important to realize that all requests are independent of one another.

3. **Uniform Interface**: This constraint can be best summarized in 4 parts.
  * The request must specifically identify a resource (think URL or universal resource locator)
  * The response provided by the server must provide enough information to the server that the client may modify its representation of the resource.
  * All information that the client/server would require to perform an action is included in a request/response.
  * The server should inform the client, via a response, how to change the state of an application. The actual constraint is "hypermedia as the engine of application state" but that is a bit difficult to parse and understand (for more on that, look [here](https://restfulapi.net/hateoas/). Basically, "hypermedia" is a way of saying the server can provide links to the client to get other resources, and importantly, those links drive the application's state. 

4. **Layered System**: At times, a request fromm the client may not be made directly to the server, rather a request is passed through a series of middlemen servers that perform functions like encryption. The client should not care about the complexities of this though and from the client's perspective, this can be treated as a blackbox. The requests made by the client should make no consideration to those servers and the response receieved from the server should also be the same as if the client were directly interfacing with the server.

5. **Cacheable**: Caches are really great at improving speed, but they can complicate things at times. For instance, if a client needs a particular resource that it does not have cached, it can request it (taking the time associated with the overhead of making a request.) Then, if that same resource is requested soon enough that it is still in the cache, then the cached version can be used and it is much faster! However, how does the client know that a resource has not been updated in the time since it was cached? This is where this concept comes into play. A server should inform a client whether or not a resource is cacheable as well as provide it with a version number if it is cacheable so that the server can notfiy the client if a particular version is expired.

6. **Code-on-demand**: This is an oxymoron, as it is considered an optional constraint. The basic gist of this is that, to simply a client, a server can provide code to a client and the client will run that code. As an example, a server may provide a web application some HTML (yea, I know that it's actually XML, but that is still code, right?) that the client can then render to the user.

## Additional Resources

* https://restfulapi.net/ (this is like everything I said above, but stated differently)
* https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm (some of Roy Fielding's 2000 PhD dissertation on REST, which was its origin)
