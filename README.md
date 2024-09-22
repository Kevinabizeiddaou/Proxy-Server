# Proxy-Server
### Proxy Server with HTTPS Support
# Overview

This project implements a basic HTTP and HTTPS proxy server. The proxy server allows clients to connect and forward their requests to external servers, retrieve the responses, and return them to the clients. It also supports caching and blocking of specific websites and can handle secure HTTPS connections using SSL.

1. Key Features:
- HTTP and HTTPS Support: The proxy handles both HTTP and HTTPS requests.
- Website Blocking: Allows blocking specific URLs or websites.
- Response Caching: Stores responses for faster repeated requests and reduced server load.
- Multi-threaded: Handles multiple client connections concurrently using threads.
- Basic Logging: Logs incoming requests and actions, such as blocked requests or cached responses.

2. How it Works
- Client Request Handling:

When a client connects to the proxy, the request is processed.
If the requested website is blocked, a 403 Forbidden response is sent back.
If the request is allowed, it is forwarded to the destination server.

- Caching:

The proxy caches responses from servers for previously requested URLs.
If a cached response is available and up-to-date, it is returned without forwarding the request again to the destination server.

- HTTPS Support:

The proxy uses SSL certificates to handle secure HTTPS requests.
When a client sends an HTTPS request, the proxy forwards it securely using SSL.
Multi-threading:

Each incoming connection is handled in a separate thread, allowing the proxy to manage multiple clients simultaneously.

3. Installation: 
- Clone the repository:

git clone https://github.com/yourusername/proxy-server.git
cd proxy-server

- Install Dependencies: This project uses Python 3 and the ssl module, which is part of the Python standard library. Make sure you have Python installed:

sudo apt-get install python3

- Add SSL Certificates: The proxy requires SSL certificates for handling HTTPS requests. You can generate a self-signed certificate using OpenSSL:

openssl req -x509 -newkey rsa:4096 -keyout server-key.pem -out server-cert.pem -days 365 -nodes

- Run the Proxy Server:

python3 proxy_server.py


4. Configuration:
- Blocking Websites
You can block specific websites by editing the self.blockedSites list in the ProxyServer class. Add or remove websites as needed:

self.blockedSites = ['example.com', 'amazon.com']

- Caching
The proxy caches responses by default. You can adjust caching policies or add expiration logic in the handleClient method.

- Customization
Port Configuration: By default, the proxy listens on 127.0.0.1:17903. You can change the proxyHost and proxyPort values in the startProxyServer method:

proxyHost = '127.0.0.1'
proxyPort = 17903

5. How to Use:
- Configure your browser to use the proxy:

Host: 127.0.0.1
Port: 17903

- Make HTTP/HTTPS requests through your browser or tools like curl, and the proxy will handle the requests, forward them to the appropriate server, and return the responses.

Example
- Blocked Request:
[*] Accepted connection from 127.0.0.1:54321
[!] Blocked request to http://example.com
- Cached Request:
[*] Serving http://example.com from cache (Not Modified)
- HTTPS Request:
[*] Accepted connection from 127.0.0.1:54321
[*] Received response from https://google.com at 2024-09-22 15:45:12
[*] Sent response to 127.0.0.1 at 2024-09-22 15:45:12
Contributing
Feel free to contribute to this project by opening issues or submitting pull requests. Contributions in adding new features, improving caching, or enhancing security are welcome.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Contact
For any questions or suggestions, please open an issue or contact me at [kevinabizeiddaou@gmail.com].

