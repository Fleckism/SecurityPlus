**Hyper Text Transfer #protocol** 
- The foundation of web technology (aka internet)
- communications protocol used to connect to Web servers on the Internet or on a local network (intranet). 
- The primary function of HTTP is to establish a connection with the server and send HTML pages back to the user's browser. It is also used to download data from the server either to the browser or to any requesting application that uses HTTP.
- HTTP 
- Enables clients (typically **web browsers**) to 
	- Request resources from an HTTP server. 
	- Connects to the HTTP server using an appropriate [[TCP]] port 
	- submits a request for a resource, using a uniform resource locator (URL). 
- The **server** acknowledges the request and responds with the data (or an error message).
- When used with [[TLS]] called HTTPS
==Part of URL analysis==
## HTTP Explained
- HTTP session 
	- client ( user-agent aka Web browser)
		- Makes a request to a HTTP server
		- [[TCP]] connection is established.
			- TCP can be used for multiple requests or a new one for every request
				- **Requests** include
					- Method
					- Resource (URL path)
					- version number
					- header
					- Body
					- **Methods**
						- GET: retrieves resource
						- POST: send data to the server
						- PUT: create or replace resource
						- DELETE: Used to remove resource
						- HEAD:  Retrieve headers 