### 1. HTTP vs HTTPS

#### HTTP

HTTP (Hypertext Transfer Protocol) is the protocol used for transmitting data over the web, including HTML, images, and multimedia content. Data transferred via HTTP is unencrypted, making it susceptible to security threats.

Here's how HTTP works:

- A client sends an HTTP request to the server, which includes an HTTP method (GET, POST, etc.) and a URI (Uniform Resource Identifier).
- GET requests data, while POST submits data to the server.
- The server responds with an HTTP message that has a status code (like 200 for success) and the requested content.
- The client processes this content, rendering web pages from files like `HTML, CSS, and JavaScript`.

#### HTTPS

HTTPS (HTTP Secure) encrypts data transfers using SSL (Secure Sockets Layer) or TLS (Transport Layer Security) and verifies server identities with certificates.

The HTTPS process goes as follows:

- A client connects to an HTTPS-protected server using an SSL/TLS-capable browser.
- The server shares its SSL/TLS certificate, which includes a public key and certification authority (CA) details.
- The client authenticates the server's certificate using the CA's public key.
- The client then creates a session key, encrypts it with the server's public key, and sends it over.
- The server decrypts the session key with its private key.
- Encrypted HTTPS communication is now established, securing the data exchange.
- Using HTTPS ensures data privacy and security, protecting against eavesdropping and man-in-the-middle attacks.

---

### 2. What is OSI 7 layer & TCP/IP 4 layer?

OSI layer 7 and TCP/IP layer 4 are both components of the network protocol stack. However, each constructs the hierarchy in a different way.
Comparing the 7th layer of OSI and the 4th layer of TCP/IP, the top three layers of the OSI model, the session layer, presentation layer, and application layer, are responsible for functions related to application programs, and standard protocols are defined for them.
On the other hand, in the TCP/IP model, the application layer includes TCP and UDP protocols, so it serves to connect the application layer and the transport layer.

While the session layer and presentation layer are responsible for functions such as data format conversion, data structuring, compression, and encryption, the TCP/IP model has no layer responsible for these functions. These functions can be handled directly in the application layer.

#### OSI Layer 7

OSI layer 7 stands for Open Systems Interconnection model. This model is a reference model for the network protocol stack developed by the International Organization for Standardization (ISO).

Layer 7 consists of:

- **Physical Layer**: A layer that transmits electrical and physical signals.
  - Protocol: `Ethernet, Fast Ethernet, Gigabit Ethernet, Wi-Fi, Bluetooth, USB`
- **Data Link Layer**: Responsible for reliable data transmission in the network.
  - Protocol: `Ethernet, Token Ring, FDDI, HDLC, PPP, SLIP`
- **Network Layer**: Selects the path to deliver data to the destination and manages packet transmission.
  - Protocol: `IP, ICMP, ARP, RARP, OSPF, BGP, IS-IS`
- **Transport Layer**: Ensures data transmission and is responsible for error detection and recovery.
  - Protocol: `TCP, UDP, SCTP`
- **Session Layer**: Manages the connection between users at both ends and controls the communication method.
  - Protocol: `NetBIOS, RPC, SQL`
- **Presentation Layer**: Converts the format of data or performs processing such as encryption and decryption.
  - Protocol: `JPEG, MPEG, SMB`
- **Application Layer**: This is a layer that provides services to applications.
  - Protocol: `HTTP, FTP, SMTP, POP3, IMAP, Telnet, SSH`

#### TCP/IP Layer 4

TCP/IP layer 4 refers to the Transmission Control Protocol/Internet Protocol model. This model is a reference model for the Internet Protocol stack. The 4th layer is composed as follows.

- **Network Interface Layer**: Manages the physical network. It performs the roles of the physical layer and data link layer. Equipment such as network interfaces and LAN cards are used in this layer.
- **Internet Layer**: Data is transmitted using IP addresses. It performs the role of the network layer. The IP protocol is used in this layer.
- **Transport Layer**: Ensures data transmission using TCP or UDP protocols and is responsible for error detection and recovery. It performs a role corresponding to the transport layer of the OSI model.
- **Application Layer**: This is a layer that provides services to applications. It performs the roles of the application layer, expression layer, and session layer of the OSI model. Protocols such as HTTP, FTP, and SMTP are used in this layer.

---

### 3. What is AS (Autonomous System)?

AS stands for **Autonomous System** and is a group of routers managed by one network manager, a group of routers operated under one management regulation, or a group of routers composed of one management strategy.

#### Interior Routing Protocols

- Protocol used by routers to exchange routing information between routers within the AS
- Types: `RIP, IGRP, EIGRP, OSPF`

#### Exterior Routing Protocols

- Protocol used by routers to exchange routing information externally between ASs
- Type: `EGP, BGP (nowadays, the trend is to use BGP rather than EGP)`

#### Necessity of AS

You can manage the information contained in the router efficiently and provide Internet services more easily.
The routers in the AS only know the internal network information about the routers belonging to their own AS, and when going outside, that is, outside the AS, they ask the ASBR (Autonomous System Boundary Router), the gatekeeper router, for information and then go out to the external Internet. will be.
The gatekeeper router ASBR has information about other ASs adjacent to its own AS and has
It serves to provide information to the router coming from an external AS to its own AS.
Because of this system, routers do not need to have information about all networks around the world even when connected to the Internet.
All you need is information about the AS you belong to.
At this time, the routing protocol used by the router inside the AS is called Interior Routing Protocols or IGP.
The routing protocols used to exchange routing information between ASs, that is, outside the AS, are called Exterior Routing Protocols, or EGP.

---

### 4. What is BGP (Border Gateway Protocol)?

BGP is Border Gateway Protocol. The protocol between BGs (Border Gateways) located at the edge of the AS is called BGP.
Therefore, not all BGP protocols connect different ASs.
So, of course, it is involved in connections between BGs belonging to different ASs, but it is also involved in connections between BGs within the same AS. According to these differences in roles, BGP is largely divided into two types.

#### iBGP

BGP is responsible for connecting border gateways on the same AS.

#### eBGP

BGP, inter-AS routing, is responsible for connecting border gateways on different AS.

<br/>

Additionally, the BGP router uses the decision-making algorithm and policy set in the AS peering contract to analyze the data it collects through prefix declarations and select the optimal peer to send each packet stream to at that point.
In most cases, the path with the fewest number of network hops is chosen, but longer paths may be faster due to congestion and delay.
As traffic travels through an AS and reaches another BGP router connected to another AS, this process repeats until the data reaches the AS where the destination site is located.
TCP port 179 is used and exchanged using unicast method.
Unlike IGP, it is possible to form a BGP Peer (Neighbor) relationship with devices that are not directly connected.

#### Network communication method

**Unicast (1:1)**

- One-to-one communication where origin and destination must be accurate
- One-to-one method in which one transmitting node transmits data to one receiving node

**Broadcast(1:All)**

- A way to communicate with all devices in the network I belong to
- Affects the performance of individual PCs and overall network traffic.

**Multicast(1:Group)**

- Used when information needs to be sent to a specific group of people at the same time (ex. 8 out of 10 people)
- Prevent unnecessary traffic or performance degradation by selectively transmitting data

**Anycast (1:1)**

- Method of communicating with the nearest node
- The difference with unicast is that the sending node transmits data to only one of the receiving nodes connected to the network.

---

### 5. What is an HTTP method?

HTTP methods are **a way for a client to indicate to a web server what kind of behavior it wants**.
Each method is designed to perform a specific kind of task.

#### GET

- Mainly used when retrieving information from a server. (Get)
- GET requests are not used to change or create data; they are only used to read data.

#### POST

- Mainly used when adding resources to the server. (Create)
- Used when a client attempts to create a server resource.
- A POST request sends data to the server and uses the data to create a new resource or update an existing resource.

#### HEAD

- It is almost similar to a GET request, but returns only HTTP header information without actual body content. (No Body)
- There is no body in the response.
- It is efficient because you can obtain information about the resource without having to retrieve it.

#### PUT

- Used to update the entire contents of the resource corresponding to a specific URL. (Update)
- If a resource already exists in the URL, a PUT request replaces the resource with a new one. If the resource does not exist, a new resource is created.

#### DELETE

- Used to remove specific resources.
- When a DELETE request is successful, it usually does not include data in the response body.

#### PATCH

- Used to apply partial changes to the source.
- PATCH requests can be more efficient than PUT requests because they only change part of the request.

#### OPTIONS

- Used to check the type of method supported by the resource.
- The OPTIONS request returns a list of HTTP methods available on the resource along with a header called “Allow”.

#### TRACE

- Mainly used for diagnostic purposes.
- TRACE requests are sent from the client to the server and can be used to check whether any changes or additions are made during this process. When the TRACE request reaches the server, the server returns the request as is as the response body.
- Through this, the client can check how the request was processed.

#### CONNECT

- Mainly used to create network tunnels. The most common example is an SSL tunnel for HTTPS communication.
- When the client uses the CONNECT method, the web server establishes a network connection with the destination server and relays data between the client and the destination server.

---

### 6. What is HTTP Status Code?

HTTP Status Code is **a method by which the server delivers the result of request processing to the client in an HTTP response**.

This code consists of three digits, and what each means is as follows.

- **1xx (Informational)**: Indicates that the request has been received and the process is continuing.
- **2xx (Successful)**: Indicates that the request has been successfully received, understood, and accepted. The most common code is `200 OK`, indicating that the request was processed successfully.
- **3xx (Redirection)**: Indicates that the client must take additional action to complete the request. For example, `301 Moved Permanently` indicates that the URI of the requested resource has changed, and a new URI is provided to the client.
- **4xx (Client Error)**: Indicates that the client's request is incorrect or cannot be completed. The most commonly seen code is `404 Not Found`, which is returned when the requested resource cannot be found on the server.
- **5xx (Server Error)**: Indicates that the server failed to process a valid request. `500 Internal Server Error` is the most common code indicating a problem with the server.

---

### 7. What is DNS?

DNS (Domain Name System) is a system used on the internet to convert host names (domain names) into actual IP addresses.

#### Root DNS Server

The Root DNS Server is one of the most crucial DNS servers on the internet. These servers are distributed globally and act as the top-level DNS servers for all domain names on the internet, forming the foundation of the entire DNS system.

They manage root domain names, which are the highest-level domain names used on the internet. Root domain names are denoted by a period (.) and, for example, the root domain name for `www.aaa.com` is `.com`.

Root DNS Servers know the IP addresses of TLD DNS Servers. So, when a user queries a domain name like `www.aaa.com`, it first asks the Root DNS Server for the location of that domain's TLD DNS Server. The Root DNS Server then returns the IP address of the TLD DNS Server, and the user's DNS query is forwarded to that TLD DNS Server.

In essence, the Root DNS Server is the starting point for all DNS servers on the internet and plays a crucial role in the entire DNS system. These servers are distributed worldwide and managed by ICANN (Internet Corporation for Assigned Names and Numbers).

#### TLD DNS Server (Top-Level Domain)

TLD DNS Servers manage the top-level domain names (TLDs) used on the internet, like `.com, .org, .edu`. They process DNS queries for each domain name.

These servers manage the IP addresses and other DNS record information for each TLD. For instance, the TLD DNS Server for `.com` domain names processes all DNS queries for `.com` domains. The primary purpose of these queries is to find the IP address associated with a domain name.

TLD DNS Servers also collaborate with domain name registrars to update information about domain names under their TLD. They receive DNS queries from Root DNS Servers, which know their IP addresses and forward queries for domain names under their management. Thus, TLD DNS Servers play a vital role in processing DNS queries for all domain names on the internet. They are distributed globally and managed by domain name registrars and ICANN.

#### Second-Level DNS Server (Authoritative DNS Server)

Second-Level DNS is a critical component of DNS, providing IP address information for specific domain names.

Typically, these servers refer to the nameservers of domain/hosting companies and serve as the ultimate responders for information about a domain. For example, if there is a DNS server that knows the IP address for `aaa.com`, it acts as a Second-Level DNS Server.

#### DNS Records

DNS records are data entries used in the Domain Name System (DNS) to map domain names to their associated IP addresses. They contain information related to domain names and are used by servers performing DNS queries.

There are various types of DNS records. Here are some common examples:

- **A Record**: Maps a domain name to an IP address.
- **CNAME Record**: Maps a domain name to another domain name.
- **MX Record**: Specifies the priority of mail servers associated with a domain name.
- **NS Record**: Identifies the authoritative DNS servers for a domain name.
- **TXT Record**: Contains text information associated with a domain name.
- **SPF Record**: Used to verify email sending authority to prevent spam.
- **SRV Record**: Identifies the location of specific services provided by a DNS server.
- **AAAA Record**: Maps a domain name to an IPv6 address.
- **SOA Record**: Provides basic settings for a domain name.
- **PTR Record**: Maps an IP address back to a domain name, used primarily in reverse DNS queries, especially for email servers.

---

### 8. Service Mesh vs API Gateway

#### Service Mesh

Service Mesh is an infrastructure layer for managing communication between services in distributed applications. In a microservices architecture, an application is composed of several small services that communicate with each other to form a cohesive application. Since this inter-service communication happens over a network, an infrastructure to manage it is necessary.

Service Mesh abstracts and manages the communication between these services, essentially aiding in managing the network infrastructure for inter-service communication. It offers functionalities like distributed tracking, security, logging, and load balancing, which help in handling communication between services safely and efficiently.

Implementation of Service Mesh often uses the sidecar pattern, deploying a sidecar container on each service instance and managing communication through it. This container typically consists of a proxy or agent provided by the Service Mesh solution. Popular Service Mesh solutions in Kubernetes environments include Istio and Linkerd.

##### Key Features of Service Mesh

- **Distributed Tracking**: Facilitates rapid response to issues by tracking and analyzing communication between services.
- **Security**: Enhances security through traffic encryption, authentication, authorization, and access control.
- **Logging**: Logs details of inter-service communication for troubleshooting.
- **Load Balancing**: Distributes traffic among multiple service instances, ensuring stable service delivery.

Major Service Mesh solutions include Istio, Linkerd, and Consul, which simplify the implementation and operation of a Service Mesh.

#### API Gateway

API Gateway serves as a single point of entry in a microservices architecture, exposing multiple backend services as one API. When clients send HTTP requests to the API Gateway, it invokes internal services, processes the results, and returns them to the clients.

##### Main Features of API Gateway

- **Authentication and Authorization**: Verifies client requests and performs user authentication and authorization checks, ensuring secure API access.
- **Load Balancing**: Distributes requests across multiple services, improving service availability and load distribution.
- **Caching**: Utilizes cache for repetitive requests, reducing the load on backend services.
- **Logging and Monitoring**: Records and monitors client requests and service responses, enabling quick response to issues.
- **API Management**: Manages APIs and their versions, allowing deployment of new API versions or removal of old ones.

API Gateway is an essential component in microservices architecture, offering various functionalities and flexibility for efficient application management and operation.

#### Differences between Service Mesh and API Gateway

**API Gateway** and **Service Mesh** are both tools for managing communication in distributed applications but differ in their purpose and methods of implementation.

**API Gateway** acts as a server that mediates communication between clients and backend services. Clients send requests to the backend services via the **API Gateway**, which performs necessary authentication, authorization, and logging before forwarding these requests. **API Gateway** provides a unified entry point, simplifying client-to-backend communication and enhancing security and monitoring.

Conversely, **Service Mesh** manages communication between services within distributed applications. Each service instance has a sidecar container to facilitate inter-service communication. **Service Mesh** offers functionalities like distributed tracking, security, logging, and load balancing to ensure safe and efficient communication between services.

Thus, **API Gateway** mediates communication between clients and backend services, managing and protecting externally accessed services. In contrast, **Service Mesh** handles communication within distributed applications, safeguarding and stabilizing the operation of these applications.

---

### 9. What is Reverse Proxy?

**Reverse Proxy** is a type of server that sits in front of a web server and forwards client (e.g. web browser) requests to the web server. The main difference between reverse proxy and forward proxy is the direction of service. A forward proxy acts as a gateway between users and the vast resources of the Internet, while a reverse proxy acts as a gateway between the Internet and a smaller group of servers.

#### Features of Reverse Proxy

- **Load Balancing**: Improves the speed and stability of resources by balancing the load by distributing client requests to multiple servers.
- **Global Server Load Balancing**: This involves improving user response time by routing client requests to the closest server based on the client's geographic location.
- **SSL Encryption**: Centralizes SSL certificate management in one place instead of managing it on individual servers.
- **Caching Content**: Reduces server load by providing static and dynamic content cached on the web server.
- **Compression**: Compresses the file before sending it to the client to reduce response bandwidth.
- **Security and Anonymity**: Provides security by hiding the characteristics and origin of the backend server.

#### Example reverse proxy tool: Nginx

In addition to being used as a web server, load balancer, HTTP cache, and mail proxy, Nginx is one of the most popular reverse proxy servers in the world. It is well known for its high performance, stability, rich feature set, simple configuration, and low resource consumption.

http {
upstream backend {
server backend1.example.com weight=5;
server backend2.example.com;
server backend3.example.com;
}

    server {
        listen 80;

        location / {
            proxy_pass http://backend;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }

}

- `upstream backend` defines a group of server backends with different weights (if not specified, each weight is the same). This allows Nginx to distribute the load by not only forwarding traffic to different servers, but also assigning more traffic to servers with higher weights.
- The `proxy_pass` directive passes the request to the upstream server group.
- The `proxy_set_header` directive modifies the request headers passed to the backend server. This may include passing the actual client IP address and other details to the backend.

---

### 10. What are STP (Spanning Tree Protocol) and RSTP (Rapid Spanning Tree Protocol)?

Spanning Tree Protocol (STP) and Rapid Spanning Tree Protocol (RSTP) are two network protocols used to prevent loop conditions in network environments. This is especially important in Ethernet networks that include multiple paths between switches.

#### Spanning Tree Protocol (STP)

STP, standardized as IEEE 802.1D, is designed to maintain a loop-free topology for Ethernet networks. It works by selectively blocking some of the redundant paths that could cause loops. STP requires network design to provide fault tolerance and automatic backup path activation if an active link fails, without the risk of bridge loops or associated broadcast emissions.

The way it works is as follows.

- **Root Bridge Selection**: All switches participate in the selection process to select the root bridge, which is the logical center of the network. The switch with the lowest bridge ID becomes the root.
- **Path Selection**: Each switch determines the shortest path from itself to the root bridge based on the path cost.
- **Blocking Redundant Paths**: To prevent loops, STP blocks redundant paths that could form loops but maintains them as backup links.
- **Port States and Roles**: Ports in an STP topology can be in one of several states: blocking, listening, learning, forwarding, or disabled. Each non-root bridge port has one of the following roles: root port (best port to reach the root bridge), designated port (port forwarding frames to and from network segments), or unspecified port (blocked port).

#### Rapid Spanning Tree Protocol (RSTP)

RSTP, defined in IEEE 802.1w, is an evolution of STP that provides faster convergence during network changes. It is designed to be backward compatible with standard STP.

The way it works is as follows.

- **Faster Convergence**: RSTP can achieve faster convergence through fast state transitions. By introducing new port roles and states, the switch can actively check whether a port can safely be moved to the forwarding state without having to wait for a timer to expire.
- **Port Roles**: RSTP defines roles such as root port, designated port, alternate port (backup to root port), and backup port (backup to designated port).
- **Port States**: RSTP uses only 3 port states compared to STP's 5 port states (discard, learn, and forward).
- **Edge Ports**: Ports connected directly to an end station are unlikely to create network loops, so these ports can be configured as edge ports to bypass the existing listen/learn state and transition directly to the forwarding state. there is.
- **Link Type**: RSTP can also identify the link type, and if the link is a point-to-point link, RSTP increases the convergence speed of the link.

The advantages are as follows.
Provides much faster recovery in response to network changes or failures, reducing time from tens of seconds (using STP) to less than a second in many cases.
Simplifies network troubleshooting and improves network stability and performance.

#### Summary of STP and RSTP

In summary, STP is effective at preventing network loops, but RSTP improves on STP by providing faster convergence. This can be very important in networks where minimizing downtime is important.

---

### 11. What is Hub & Spoke Network Architecture?

Hub & Spoke network architecture is a foundational model widely used in various sectors that require centralized control and efficient connectivity. It's particularly effective for organizations aiming to centralize management of a main office while efficiently expanding network infrastructure.

#### Structure

- **Hub**: Acts as the central node and common connection point for all other nodes in the network. The hub is pivotal, as all data traffic flows through it, facilitating centralized management of data.
- **Spoke**: These are the nodes that connect directly to the hub. Each spoke connects solely to the hub and not to each other, simplifying the network design by reducing the number of direct connections.

#### Characteristics and Usage

- **Centralized Management**: The architecture enables centralized control, easing the enforcement of policies and oversight of network operations.
- **Resource Efficiency**: Centralizing essential resources at the hub enhances bandwidth management and traffic prioritization, which is crucial for large-scale networks like WANs.
- **Scalability**: It's easy to expand the network by adding spokes, which connect back to the hub without altering existing connections.

#### Advantages & Disadvantages

- Advantages:
  - **Simplified Infrastructure**: Lowers network complexity by limiting the number of direct connections between nodes.
  - **Cost Efficiency**: Less infrastructure is needed compared to mesh networks, where each node is interconnected.
  - **Streamlined Maintenance and Troubleshooting**: Centralizing administrative tasks at the hub simplifies updates and problem-solving.
- Disadvantages:
  - **Single Point of Failure**: The hub's critical role makes it a potential failure point that can disrupt the entire network.
  - **Bottleneck Risks**: The hub can become a bottleneck if not adequately equipped, especially under high traffic conditions.
- **Extended Hub & Spoke**: Introducing a secondary hub can help distribute the load and add redundancy, reducing the risks associated with a single hub setup.

---

### 12. IPsec vs SSL/TLS

**IPsec (Internet Protocol Security)** and **SSL (Secure Socket Layer)** along with its successor, TLS (Transport Layer Security), are protocols used for securing network communications. Both provide data integrity, confidentiality, and authentication over the Internet, but they operate at different layers of the network stack.

#### IPsec

- **Function**: Suite of protocols for securing Internet Protocol (IP) communications by authenticating and encrypting each IP packet of a communication session.
- **Layer**: Operates at the network layer, capable of securing all traffic that passes through it.
- **Modes**: Includes transport mode (encrypts only the payload of each packet) and tunnel mode (encrypts the entire packet).
- **Use Cases**: Particularly useful for setting up Virtual Private Networks (VPNs) across untrusted networks like the internet.

#### SSL/TLS

- **Function**: Protocols for securing connections between networked computers, widely used for secure communication over the internet.
- **Layer**: Operates at the session layer, securing specific applications that are designed to utilize SSL/TLS.
- **Features**: Uses encryption algorithms to encrypt data before transmission and uses certificates for authentication.
- **Use Cases**: Commonly used to secure credit card transactions, data transfers, and logins on websites.

#### Differences

- **Operational Layer**:
  - IPsec operates at the network layer.
  - SSL/TLS operates at the session layer.
- **Certificate Management**:
  - SSL/TLS typically uses a hierarchy of trusted certificate authorities for endpoint authentication.
  - IPsec can use certificates but often uses pre-shared keys or network-level authentication.
- **Setup and Flexibility**:
  - SSL/TLS is generally easier to set up per application.
  - IPsec requires more comprehensive setup as it integrates into the network infrastructure.
- **Usage Scenarios**:
  - IPsec is favored for VPNs that secure all network traffic.
  - SSL/TLS is preferred for securing specific applications, particularly for web security over HTTPS.

| Feature          | IPsec                         | SSL/TLS                             |
| ---------------- | ----------------------------- | ----------------------------------- |
| Layer            | Network (IP layer)            | Session (Application)               |
| Security         | Encrypts entire packet        | Encrypts session data               |
| Usage            | VPNs, site-to-site            | Web browsers, specific applications |
| Authentication   | Certificates, pre-shared keys | Certificates, often from a CA       |
| Configuration    | Complex, network-level        | Simpler, application-specific       |
| Encryption Modes | Transport and Tunnel          | Secure channel per session          |

#### IPsec VPN vs SSL/TLS VPN

| Characteristics       | IPsec VPN                                                                                                                         | SSL/TLS VPN                                                                                                          |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Definition**        | Protocol suite that protects Internet protocol communications by encrypting and authenticating all IP packets (TCP/UDP supported) | Protocol that encrypts and protects the connection, encrypting only the data portion (TCP/UDP supported)             |
| **Encryption**        | Works at the network layer, encrypting all traffic at the IP level and is ideal for full network encryption                       | Operates at the session layer and encrypts at the application level to secure specific applications or services      |
| **Protocol**          | IP                                                                                                                                | TCP                                                                                                                  |
| **Tier**              | Works at the network layer of the OSI model (3 Layer)                                                                             | Works at the session layer of the OSI model (6 Layer)                                                                |
| **Ease of Use**       | More complex to set up and manage. Works at network level and requires more comprehensive configuration                           | Easy to use and implement through your browser for standard secure web browsing                                      |
| **Certification**     | Can use certificates, pre-shared keys, or other forms of network-level authentication                                             | Primarily uses certificates and keys managed by a trusted certification authority                                    |
| **Distribution**      | Best for full network access, site-to-site VPNs, or entire subnets requiring secure access                                        | Ideal for remote access to individual applications or services via the Internet                                      |
| **Flexibility**       | Provides strong security features with less flexibility in client settings                                                        | More flexible for web-based access and can be used without installing client software using Web SSL VPN              |
| **Typical Use Cases** | Preferred for securing site-to-site connections, often used in corporate environments                                             | Commonly used to secure connections to web applications, SaaS products, and other web-based resources                |
| **Security**          | Offers strong security at the cost of complexity, covering all data transmitted over the network                                  | Provides good security and is easy to set up and manage over an Internet connection, especially for temporary access |
| **Features**          | Requires 2 server devices, requires software installation, can be used as if connected directly to a private network              | Requires 1 server device, uses only a web browser, connects through SSL portal                                       |

---
