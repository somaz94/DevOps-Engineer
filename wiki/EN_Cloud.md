### 1. What is cloud computing?

Cloud computing is a technology that allows users to access and use computing resources (e.g. servers, storage, databases, networking, software, etc.) through the Internet. Instead of owning and maintaining physical servers and data centers, businesses and individuals can lease access to these resources from cloud service providers. This approach offers several advantages:

#### Key Benefits

- **Scalability**: Can be easily expanded or contracted depending on demand.
- **Cost-Efficiency**: Reduce initial investment by paying only for the resources you use.
- **Accessibility**: You can access the service from anywhere as long as you have an Internet connection.
- **Flexibility**: You can choose from a variety of services to meet your specific needs.
- **Maintenance**: The cloud provider is responsible for hardware maintenance and updates.

<br/>

#### Public Cloud vs. Private Cloud

Both public and private clouds offer cloud computing capabilities, but the main differences lie in accessibility and tenancy. Public clouds are shared by a variety of users and can be accessed over the Internet, while private clouds are dedicated to a single organization and provide more control and privacy.

##### Public Cloud

Public cloud is a cloud computing model in which services are provided over the public Internet and shared among multiple customers. These services are provided by third-party providers and are highly scalable and flexible.

Public cloud examples include:

- **Amazon Web Services (AWS)**: Provides a wide range of cloud services such as computing performance (EC2), storage (S3), and database (RDS).
- **Microsoft Azure:** Provides various services such as virtual machines, app services, and Azure SQL database.
- **Google Cloud Platform (GCP)**: Well known for services such as Google Compute Engine, Google Cloud Storage, and BigQuery.

##### Private Cloud

Private cloud refers to cloud computing resources used exclusively by one company or organization. Services and infrastructure are maintained on a private network, and hardware and software are dedicated to the organization. This model provides greater control and security.

Private cloud examples include:

- **VMware vSphere**: Often used to create and manage private clouds in enterprise environments.
- **OpenStack**: An open source platform used to control pools of compute, storage, and networking resources in a private cloud.
- **Microsoft Azure Stack**: Companies can run Azure cloud services in their own data centers, creating a private version of Azure.

---

### 2. What is a cloud service?

Cloud services are generally classified into three basic service models: Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS). Each of these models represents a different way to provide cloud services to users and businesses.

#### Infrastructure as a Service (IaaS)

IaaS provides virtualized computing resources over the Internet. In this model, the cloud provider provides infrastructure such as servers, storage, and networking hardware along with a software bundle that includes the operating system.

##### characteristic

- Scalable resources based on demand.
- Clients can control the infrastructure without having to manage the underlying hardware.
- Flexible and cost-effective as it does not require physical hardware investment.

##### example

- Amazon Web Services (AWS) EC2
- Microsoft Azure virtual machine
- Google Compute Engine (GCE)

<br/>

#### Platform as a Service (PaaS)

PaaS provides a framework that allows developers to build, test, deploy, and manage applications without the complexity of maintaining the infrastructure typically associated with developing and shipping apps.

##### characteristic

- Provides a platform with tools to test, develop, and host applications in the same environment.
- Developers can focus on software development without worrying about operating systems, software updates, storage, or infrastructure.
- PaaS solutions may include development tools, database management systems, and business analytics.

##### example

- Google App Engine
- Microsoft Azure App Services
- Heroku

<br/>

#### Software as a Service (SaaS)

SaaS is a method of delivering software applications over the Internet on-demand and usually on a subscription basis. With SaaS, the cloud provider hosts and manages the software applications and underlying infrastructure.

##### characteristic

- Accessible from any device with Internet access.
- User is not responsible for hardware or software updates. The supplier manages this.
- It can be expanded to various tiers to suit small and medium-sized businesses and large corporations.

##### example

- Google Workspace (formerly G Suite)
- Microsoft Office 365
- Salesforce

---

### 3. What is a Cloud-native applications?

Cloud-native applications are designed from the ground up to take advantage of the scalability, elasticity, and flexibility of cloud computing architecture. It leverages a suite of technologies focused on building and running scalable applications in dynamic environments such as public, private, and hybrid clouds. Cloud-native applications are not only about where applications run, but also about how they are built, deployed, and operated. Cloud-native development, with its emphasis on microservices, containers, DevOps, and elasticity, aims to maximize the benefits of cloud computing to achieve more agile, scalable, and reliable software.

- Designed for the Cloud
- Microservices Architecture
- Containers
- DevOps and Continuous Delivery
- Scalability
- Resilience and Fault Tolerance
- API-based Communication
- Infrastructure as Code (IaC)

---

### 4. Serverless Computing

**Serverless computing** is a cloud computing execution model in which the cloud provider dynamically manages the allocation and provisioning of servers. Serverless architecture allows users to write and deploy code without worrying about the underlying infrastructure. The term "serverless" is somewhat misleading; it means that servers are still used, but developers don't have to manage those servers.

#### Main Features

- **Event-driven**: Serverless applications are often event-driven, operating in response to events or triggers from various cloud services (e.g., HTTP requests, file uploads, database events).
- **Scalability**: It automatically scales according to application demand, capable of handling everything from a few requests per day to thousands per second.
- **Usage-based costing**: Billing is based on the actual amount of resources consumed by the application, rather than on pre-purchased units of capacity.

#### Advantages

- **No server management required**: Developers don't need to provision or maintain servers. The cloud provider handles all aspects of server management.
- **Cost-effective**: There's no charge when your code isn't running, so you only pay for the compute time you use.
- **Scalability**: Infrastructure automatically adjusts—expanding or contracting—in response to the application's needs.

#### Use Cases

- **Web Applications**: Serving API requests or backend services for web applications.
- **Data Processing**: Handling database change events, processing data streams, or managing file uploads.
- **Integrations**: Connecting to and extending third-party services and APIs.

#### Providers

The major serverless computing providers include:

- AWS Lambda
- Azure Functions
- Google Cloud Functions
- IBM Cloud Functions

#### Example

Here's an example of a simple serverless function (AWS Lambda in Python) that returns the current time:

```python
import json
import datetime

def lambda_handler(event, context):
    current_time = datetime.datetime.now().isoformat()
    return {
        'statusCode': 200,
        'body': json.dumps({'current_time': current_time})
    }
```

---
