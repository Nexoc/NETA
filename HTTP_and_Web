✅ Topic D: HTTP and Web Communication
Covers: HTTP requests, HTTP methods, request analysis
(все эти вопросы были в 2022 экзамене)



13. Analyze the HTTP request: 
What method is used, who is the sender, and what is the full URL?

✅ Answer:
A typical HTTP request from a client looks like this:
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0

Key elements:
	• Method: The action requested → e.g. GET
	• Sender: Always the client (e.g. browser, curl) initiates the request
	• Full URL: Combine Host + Path → http://www.example.com/index.html
📌 In HTTP/1.1, the Host header is mandatory, so the full URL is reconstructed from it.




14. Explain 3 HTTP methods (e.g. GET, POST, PUT)
✅ Answer:
HTTP defines several methods (also called verbs) to perform actions on web resources:
Method	Purpose	Example use case
GET	Retrieve a resource	Load a webpage or image
POST	Submit data to a server	Login form, comment submission
PUT	Upload or replace a resource	Update a user's profile via REST API

Other common methods:
	• DELETE — remove a resource
	• HEAD — like GET but no response body (used for checks)
	• OPTIONS — ask server which methods are supported
📌 GET and POST are most commonly used by browsers.




15. What is the structure of an HTTP request? 
Which headers are required?
✅ Answer:
Structure of an HTTP/1.1 request:
METHOD /path HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html
...
(blank line)
(request body for POST/PUT)
Header	Purpose
Host	Required in HTTP/1.1 to identify domain
User-Agent	Identifies the browser/client
Accept	Indicates preferred response formats
Content-Type	Required if body is present (e.g. POST)
📌 The request always starts from the client and follows the HTTP protocol over TCP (usually port 80 or 443 for HTTPS).
