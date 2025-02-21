### 1. How Web Browsers Work

1. The user accesses a website using a web browser by entering a URL (e.g., www.example.com).
2. The browser retrieves the server's IP address by querying the Domain Name System (DNS).
3. The browser establishes a connection with the server using a process known as the 3-Way Handshake.
4. The browser sends an HTTP Request to the server to request data.
5. The server sends back an HTTP Response, containing the requested data.
6. The browser then parses the HTML content received from the server to construct a Document Object Model (DOM) Tree.
7. When a Style tag is encountered during the parsing process, the browser temporarily pauses DOM construction to parse CSS and build a CSS Object Model (CSSOM) Tree.
8. If a script tag is encountered during parsing, the browser hands over control to the JavaScript engine to parse the JavaScript code, create an Abstract Syntax Tree (AST), and execute the script.
9. The browser creates a Render Tree by combining the DOM and CSSOM.
10. The series of steps up to this point is called the Construction phase.
11. During the next phase, the rendering engine calculates the layout of each visible element and places the nodes in the Render Tree accordingly.
12. The UI backend visits each node in the Render Tree and paints the elements on the screen.
13. The nodes of the Render Tree are then composited in the correct order to form the final page.
14. This series of steps is known as the Operation phase.
15. Finally, the web browser displays the fully rendered page to the user.

---

### 2. What is Microservice Architecture (MSA)?

Microservice architecture (MSA) is an architectural style that organizes applications as a collection of loosely coupled services that implement business functions. Each microservice is independent and implements a single business function.

```bash
What is a loosely coupled service?

In the context of services such as software architecture and system design, “loosely coupled” means
A component or service with little or no knowledge of the definitions of other individual components.
Simply put, this means that each component or service operates independently of one another, minimizing direct interaction and dependencies.
```

#### Key concepts and principles

- **Modularity**: Applications are divided into smaller, independent modules (microservices). Each microservice focuses on a specific functionality and operates independently of other microservices.
- **Scalability**: Microservices can scale independently, making it easier to manage resource allocation for the various components of your application.
- **Decentralized Control**: Microservices embrace distributed data management and control, where each service manages its own data and logic.
- **Flexibility of technology stack**: Different microservices can use different technologies and frameworks, so you can use the right tool for the right job.
- **Resiliency**: If one microservice fails, other microservices continue to operate, reducing the risk of system-wide failure.
- **Continuous delivery and deployment**: Microservices support agile development practices, allowing individual services to be updated frequently and deployed quickly without impacting the entire application.

---

### 3. What is DNS (Domain Name Service)?

DNS is a system that converts host names (domain names) used on the Internet into actual IP addresses.

#### Principle of operation

1. User accesses website with browser (e.g., www.example.com)
2. The user's computer checks the local DNS cache with the domain name. If the IP address for the domain name is cached in the local DNS cache, the IP address is immediately returned.
3. If there is no IP address for the domain name in the local DNS cache, start a DNS query.
4. To find the IP address of the root DNS server, the user first obtains the IP address of the root DNS server by referring to the IP address of the highest-level DNS server preset on the user's computer.
5. The user sends a query to the root DNS server to obtain the IP address of the Top Level Domain (TLD) DNS server that manages the domain name. (e.g. .com .org .net etc.)
6. The user sends a query to the TLD DNS server and obtains the IP address of the Authoritative DNS server that manages the domain name.
7. The user sends a query to the Authoritative DNS server and obtains the IP address for the domain name.
8. Store the obtained IP address in the cache and return it to the browser to display the web page for that domain name.

---

### 4. What are a Program and a Thread?

A program is a set of instructions written to perform a specific task. It is a static entity, usually stored on a disk or other storage media. When executed, a program becomes a process.

When a program is executed, the operating system loads it from the disk into the system memory and runs it. The running instance of a program is called a process. Each process has its own memory space and system resources.

Programs are static, but processes are dynamic. Processes are created when a program starts and terminate when the execution ends. Multiple instances of the same program can be run simultaneously, creating multiple processes. Each process has its own memory and resources and operates independently.

**In summary, a program is code, and a process is what happens when the code is executed.**

---

### 5. What are a Process and a Thread?

Processes and threads are both related and very similar, causing confusion in understanding the differences between them.

Processes and threads are independent sequences of execution, but they differ in that processes run in separate memory spaces, while threads of the same process run in a shared memory space.

#### Process

A process is an independent entity with its own memory space, providing isolation and security for an application.
In other words, it's an instance of a program in execution. **The keyword here is Isolation.**

##### Thread

A thread is a lighter, shared memory unit within a process, enabling efficient parallel execution of tasks.
It's a subset of a process, also known as a lightweight process.
A process can have multiple threads, and these threads are independently managed by the scheduler. **The keyword for threads is Concurrency.**

<br/>

| Aspect         | Process                                                                                                        | Thread                                                                                                    |
| -------------- | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Definition     | An instance of a program that is being executed on a computer.                                                 | A small sequence of programmed instructions that can be independently managed by a scheduler.             |
| Memory         | Has its own separate memory space (heap, stack, etc.).                                                         | Shares memory space within a process (can access the heap and global variables of the process).           |
| Creation       | Creating a process involves duplicating the memory of a parent process, making it resource-intensive and slow. | Creating a thread is less resource-intensive and faster as it shares memory with the process.             |
| Communication  | Inter-Process Communication (IPC) is complex and slow due to separate memory spaces.                           | Communication between threads is easier and faster as they share the same memory space.                   |
| Control        | Controlled by the operating system. Each process operates independently.                                       | Controlled by the owning process. All threads within a process can be affected by changes in the process. |
| Overhead       | Higher overhead due to separate memory and resource management.                                                | Reduced overhead as threads share the process's resources.                                                |
| Use Case       | Suitable for applications requiring isolated execution, stability, and security.                               | Suitable for tasks within the same application that require concurrent execution.                         |
| Failure Impact | A crash in one process does not directly affect other processes.                                               | A crash in one thread can affect other threads within the same process.                                   |

---

### 6. What are Stack and Queue?

#### Stack

A stack is a linear data structure that follows the Last In, First Out (LIFO) principle, where the last data entered is the first to be removed.

##### Main Tasks

- **Push**: Adds an item to the top of the stack.
- **Pop**: Removes and returns an item from the top of the stack.
- **Peek** or **Top**: Returns the element at the top of the stack without removing it.
- **IsEmpty**: Checks whether the stack is empty.

Stacks are utilized in various areas, including expression evaluation, backtracking algorithms, and function call management in programming languages.

#### Queue

A queue is a linear data structure that adheres to the First In, First Out (FIFO) principle. The first item added to the queue is the first to be removed.

##### Main Tasks

- **Enqueue**: Adds an item to the back of the queue.
- **Dequeue**: Removes and returns an item from the front of the queue.
- **Front**: Returns the item at the front of the queue without removing it.
- **Rear**: Returns the item at the back of the queue.
- **IsEmpty**: Checks whether the queue is empty.

Queues are used in various scenarios, including scheduling systems, asynchronous data processing (like IO buffers), and breadth-first search algorithms.

#### Difference

- **Sequence of Operations**: Stacks operate on a last-in-first-out (LIFO) basis, so the last element added is removed first. Queues operate on a first-in-first-out (FIFO) basis, so the first element added is removed first.
- **Usage**: Stacks are primarily used in scenarios involving recursive algorithms, such as function calls, while queues are used in scenarios requiring sequential processing, like print queues or job scheduling.

Stacks and queues are fundamental data structures in computer science, each employed for different purposes based on their distinct characteristics.

---

### 7. StatefulSets and Stateless Applications

#### StatefulSet

StatefulSet is an API object in Kubernetes designed for managing stateful applications. Each instance in a StatefulSet retains a unique identifier, ensuring persistent storage and network identity.

- **Characteristics**:
  - **Unique Network Identifier**: Each instance maintains a unique name and static IP address.
  - **Persistent Storage**: Each instance possesses its own Persistent Volume, ensuring data persistence.
  - **Sequential Deployment and Scaling**: StatefulSets deploy and scale instances in a sequential and predictable manner.
  - **Application State Management**: Provides consistent state across replicas and is primarily used for applications requiring a persistent state, such as databases.

#### Stateless Application

Stateless applications are those that operate without retaining any internal state. Each request is independent and does not depend on the state of previous requests.

- **Characteristics**:
  - **Stateless**: The application does not store internal state and processes each request independently.
  - **Horizontal Scalability**: Stateless applications are easily scalable horizontally since they carry all necessary information for request processing.
  - **Load Balancing**: Enables even distribution of workload across multiple instances, facilitating high availability and elastic service provision.
  - **Replication and Failure Response**: Due to the independence of each instance, quick failover to other instances is possible in case of failure.

StatefulSets and Stateless applications each cater to different use cases and requirements, playing crucial roles in Kubernetes environments. StatefulSets are ideal for applications where state persistence is critical, while Stateless applications are suited for scenarios that demand scalability and flexibility.

---

### 8. What is GitOps?

GitOps is a term first used by Weaveworks Inc. in 2017 and is one of the DevOps practices for projects. It focuses on continuous deployment targeting cloud native applications. As the word suggests, it means that all elements related to the deployment and operation of an application are coded and managed (operation) in Git.

#### GitOps core concepts

- **Git as the Source of Truth**
  - All definitions for infrastructure and applications (e.g. Kubernetes manifest, Terraform code, etc.) are stored in a Git repository.
- **Declarative System State**
  - Instead of telling the system how to reach a certain state (imperative), you declare what the state should be (declarative), and the system takes responsibility for making it that way.
- **Rollbacks and History**
  - When changes are pushed to the Git repository, the declared state is applied to the actual system through an automated process. If you declare you need three servers but if you only have two, an automated process starts and creates another server.
- **Merge Requests for Change Management**
  - Changes to infrastructure or applications are made through merge requests. Like code, infrastructure changes are proposed, reviewed, and merged once approved. This means there is a record of what changes were made, who made them, and why.
- **Continuous Monitoring and Reconciliation**
  - Continuously monitors the current state of the live system and compares it to the desired state declared in Git. If there are differences, the system automatically corrects them to match Git's declarations.

#### GitOps Workflow Example

1. The developer changes the application's configuration in the Git repository.
2. Submit a ‘pull request (PR)’ for those changes.
3. The team reviews the changes, runs tests, and merges them into the main branch.
4. Continuous deployment (CD) tools detect changes in the repository and automatically apply those changes to the environment.
5. Operators of the environment continuously check whether the live state matches the state declared in Git. If not, they make the necessary changes.

---

### 9. What is Clean Architecture?

**Clean Architecture** is a software design methodology that aims to create software systems that are flexible, maintainable, and testable. Introduced by Robert C. Martin, also known as "Uncle Bob", it integrates various software design principles to segregate an application's business logic from other aspects like interfaces, databases, and external agencies.

#### Main Principles

- **Independence**: The system's core business logic should be independent of external aspects such as user interfaces, databases, external agencies, and frameworks. This independence allows the system to adapt flexibly to changes like UI or database swaps.
- **Readability and Reusability**: The code should be clear and easy to understand, allowing for reuse in different contexts.
- **Ease of Testing**: The business logic should be testable independently from external elements.

#### Layers

Clean Architecture is typically comprised of four main layers:

- **Entities**: These encapsulate the application's core business rules. They represent business objects or data structures and are positioned in the innermost layer.
- **Use Cases**: This layer implements the application's business logic. It utilizes entities to meet user requirements.
- **Interface Adapters**: This layer acts as a bridge between use cases and the application's external environment (e.g., web, database). It includes components like controllers, presenters, and gateways.
- **Frameworks and Drivers**: This outermost layer contains external interfaces and tools, such as databases, web frameworks, and device drivers, detailing the application's specifics.

#### Conclusion

Clean Architecture aims to ensure the system's flexibility to change, ease of testing, and centralization of business logic by strictly separating the business logic from other application aspects. This architectural approach enhances the system's long-term maintainability and scalability.

---

### 10. Cloud-Native Application Communication and Data Access Patterns

### AWS

A 3-tier architecture on AWS can be implemented using services such as Amazon Elastic Kubernetes Service (EKS) for container orchestration, Route 53 for DNS, Elastic Load Balancing (ELB) for request routing, and AWS PrivateLink or VPC Peering for secure internal communication.

#### 1. Presentation Layer

- **AWS Service**: Amazon Route 53
- **Process**:
  - The user sends a request to the application's domain name (e.g., www.example.com) through a web browser or app.
  - Amazon Route 53 resolves the requested domain name to the IP address of an AWS Elastic Load Balancer (ELB) or an Ingress resource in Amazon EKS.

#### 2. Application Layer

- **AWS Services**: Amazon Elastic Kubernetes Service (EKS), Elastic Load Balancing (ELB)
- **Process**:
  - An ELB or Ingress controller within EKS routes external requests to the appropriate pods within the EKS cluster.
  - These pods, running application servers, handle domain requests and can access data storage such as databases or Redis to process business logic.

#### 3. Data Layer

- **AWS Services**: Amazon RDS/Aurora for databases, Amazon ElastiCache for Redis, AWS PrivateLink, or VPC Peering
- **Process**:
  - Databases and Redis instances are hosted within AWS services such as Amazon RDS/Aurora and Amazon ElastiCache, respectively, and are deployed within a private network.
  - These services can be securely accessed within the cloud using AWS PrivateLink or VPC Peering, so they are not directly accessible from the internet.
  - Application servers within the EKS cluster securely access these databases and Redis instances through configured VPC networking to support data processing and management.

#### Summary

- **External Request Processing**: User → DNS (Amazon Route 53) → AWS ELB → EKS Pod (Application Server)
- **Internal Data Access**: EKS Pod (Application Server) → VPC Networking → DB/Redis Access via AWS PrivateLink or VPC Peering (Amazon RDS/Aurora, Amazon ElastiCache)

### GCP

The communication process from a 3-tier architecture perspective for external domain calls and internal database (DB) and Redis access for applications hosted on Google Kubernetes Engine (GKE) is as follows:

#### 1. Presentation Layer

- A user sends a request to the application's domain name through a web browser or app (e.g., www.example.com).
- DNS lookups resolve the requested domain name to the IP address of GKE's Ingress resource or Load Balancer. Services such as GCP's Cloud DNS can fulfill this role.

#### 2. Application Layer

- An Ingress controller or Load Balancer routes external requests to the appropriate pods within the GKE cluster. Pods are running application servers and are responsible for processing domain requests.
- The application server accesses data storage such as a database (DB) or Redis as needed to process business logic.

#### 3. Data Layer

- The database (DB) and Redis instance are placed on a private network through GCP's Private Access. This means they cannot be accessed directly from the internet and can only be accessed from within the cloud or through a connection via a VPN.
- Application servers within a GKE cluster securely access DB and Redis through private access configured within the VPC. This allows the processing of requests to view or change data.

#### Summary

- **External Request Processing**: User → DNS → GCP Load Balancer/Ingress → GKE Pod (Application Server)
- **Internal Data Access**: GKE Pod (Application Server) → VPC Networking → DB/Redis Access through Private Access

---

### Synchronous and Asynchronous Processing

- In synchronous processing, tasks are completed one at a time in order. This means that each task must be completed before the next one begins. This type of processing is simple and easy to understand.
- Asynchronous processing allows tasks to be executed independently of the main program flow, enabling background processing. This type of processing is essential in environments where tasks may take significant time, such as web servers or applications with user interfaces.

#### Characteristics of Synchronous Processing

- **Blocking**: Each task must be completed before the next one begins, blocking subsequent tasks until the current task is finished.
- **Linear Execution**: Tasks are executed in the exact order they appear in the code.
- **Simplicity**: The sequential nature of task execution makes programming and debugging easier.
- **Usage Examples**: Used for reading or writing files, database transactions, or any task where subsequent operations depend on the results of previous ones.

#### Characteristics of Asynchronous Processing

- **Non-blocking**: Tasks can start and complete independently, and the program can continue without waiting for tasks to finish.
- **Concurrent Execution**: Multiple tasks can be processed in parallel, improving the efficiency and responsiveness of applications.
- **Complexity**: Programming and debugging are more challenging due to potential issues like race conditions and deadlocks.
- **Usage Examples**: Used for API requests, file uploads, or long-running I/O operations where you don't want to freeze the user interface or delay other computations.

#### Summary

The choice between synchronous and asynchronous processing depends on the application requirements.

- **Synchronous**: Used when tasks need to be completed in a specific order or when each task's output is needed for the next task.
- **Asynchronous**: Used to enhance the throughput and responsiveness of applications, especially when tasks are independent or can be performed in parallel.

---

### 12. What is 3-Tier Architecture?

Traditional 3-tier architecture is a widely used software application architecture that organizes applications into three logical and physical computing layers: presentation, application, and data. However, in modern web development, especially with the advent of cloud technologies and services, the distinction between web and application servers (WAS) has become blurred.

#### Traditional 3-Tier Architecture

- **Presentation Layer (Client Tier)**: This is the user interface of the application. It presents the application to the user, communicates with the application layer for all data, and returns the results to the user.
- **Application Layer (Business Logic/Logic Tier)**: This layer coordinates the application, processes commands, makes logical decisions and evaluations, and performs calculations. It also moves and processes data between the two surrounding layers.
- **Data Layer (Data Tier)**: This includes databases and data management systems. The data layer manages the physical storage and retrieval of data.

#### Modern Web Development Approach

In modern web development, especially with the advent of cloud technologies and services, the distinction between web and application servers (WAS) has become blurred.

- **Web Server (Web)**: Traditionally handled HTTP requests, served static content, and forwarded dynamic content requests to the application server.
- **Application Server (WAS)**: Handled the business logic and interactions between the user interface and the database. It executed applications and processed data returned from the database.
  > Nowadays, many web frameworks come with built-in servers (e.g., Tomcat in Spring Boot) capable of handling both static and dynamic content, thus, in many scenarios, separate web and application servers are not required.

#### Comparison between Traditional 3-Tier Architecture and Modern Web Development

| Aspect                      | Traditional 3-Tier Architecture                         | Modern Web Development                                                                               |
| --------------------------- | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Separation                  | Clear separation of concerns                            | Blurred lines, often combined layers                                                                 |
| Web Server (WS)             | Served only static content                              | Serves both static and dynamic content                                                               |
| Application Server (WAS)    | Exclusively handled business logic                      | Embedded within applications to handle all business logic                                            |
| Scalability                 | Enhanced by adding more intermediary layers             | Scalable through services like microservices, container nodes                                        |
| Deployment Complexity       | Increased need for maintenance and updates              | Simplified by adopting services and understanding cloud provisioning along with lifecycle management |
| Development and Maintenance | Required diverse part integrations for interoperability | Internally manages dependencies with a multitude of frameworks and services                          |
| Example Technologies        | Apache Web Server, Oracle WebLogic, IBM WebSphere       | Node.js, Spring Boot, Django (using built-in servers like Tomcat or Gunicorn)                        |

---
