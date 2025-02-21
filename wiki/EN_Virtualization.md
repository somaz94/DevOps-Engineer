### 1. What is virtualization?

Virtualization is a technology that involves creating virtual versions of physical devices or resources within a system. This process allows for the abstraction of physical components into logical units, enhancing flexibility and efficiency in resource usage. Virtualization can be applied to various system aspects, including hardware platforms, storage devices, network resources, and operating systems.

#### RAID and LVM

The comparison to RAID and LVM helps to contextualize virtualization within the broader scope of IT infrastructure:

**RAID (Redundant Array of Independent Disks)**: This technology combines multiple physical storage devices, like hard drives, into a single logical unit for improved redundancy and performance. Although commonly associated with Windows systems, RAID is not exclusive to them and can be implemented in various environments.

**LVM (Logical Volume Manager)**: Primarily used in Linux systems, LVM is a method of managing storage that allows for more flexible allocation of space on physical storage devices. It provides a layer of abstraction over physical storage, allowing for resizing and management of storage space without being limited by the physical layout of the disks.

<br/>

#### Full-Virtualization vs. Para-Virtualization

Focuses on the level of hardware emulation and interaction between guest OS and the hypervisor:

##### Full-Virtualization:

- **Hardware Emulation**: Full-virtualization involves completely emulating the hardware for each virtual machine. The guest OS does not need modifications as it interacts with a simulated hardware environment.
- **Guest OS**: It can run unmodified operating systems as if they were running on actual hardware.
- **Hypervisor Role**: The hypervisor manages and abstracts the hardware, offering a virtual hardware layer to each VM.

##### Para-Virtualization:

- **Direct Hypervisor Interface**: In para-virtualization, the guest OS is aware that it is running in a virtualized environment and directly communicates with the hypervisor.
- **Guest OS**: Modifications are required in the guest OS to enable it to interact with the hypervisor API for better performance.
- **Performance**: It generally offers better performance than full-virtualization, especially in I/O operations, due to lower overhead.

#### Host Virtualization vs. Container Virtualization vs. Hypervisor Virtualization

Differentiates based on where the virtualization layer sits (on top of an OS, sharing an OS, or directly on hardware) and its operational efficiency and use cases:

##### Host Virtualization (Type 2 Hypervisor):

- **Layering**: Runs on top of a host operating system. The hypervisor is a software layer installed on the OS.
  Use Case: Generally used for development, testing, and educational purposes.
- **Example**: VMware Workstation, Oracle VirtualBox.

##### Container Virtualization:

- **OS Sharing**: Containers share the host OS kernel but isolate the application and its dependencies in a user space.
- **Resource Efficiency**: More resource-efficient than VMs as they don’t need to emulate a full OS.
- **Example**: Docker, Kubernetes.

##### Hypervisor Virtualization (Type 1 Hypervisor):

- **Direct Hardware Interface**: Runs directly on the system’s hardware to control the hardware and manage guest operating systems.
- **Performance**: Typically offers better performance and efficiency than host virtualization.
- **Example**: VMware ESXi, Microsoft Hyper-V.

---

### 2. Docker & DockerFile & Docker Compose

Docker is an open-source platform for deploying applications within software containers. It provides additional abstraction and automation for operating system-level virtualization on Linux.

Docker utilizes Linux kernel's resource isolation features (like cgroups and kernel namespaces) and union file systems (such as OverlayFS) to allow independent containers to run within a single Linux instance, thus avoiding the overhead of starting and maintaining virtual machines.

#### Main Features of Docker

1. **Containerization**: Packages applications and their dependencies into containers, ensuring consistency across development, test, and production environments.
2. **Lightweight**: Containers share the machine's OS kernel and do not require an OS for each application, making them lighter than virtual machines.
3. **Portability**: Dockerized applications can run anywhere on any platform that supports Docker.
4. **Isolation**: Ensures each container is isolated, having its own file system, networking, and process space.
5. **Docker Hub**: A repository for Docker images where users can pull images and use them as the basis for their applications.

#### Dockerfile

A Dockerfile is a text document containing all commands a user can call from the command line to assemble an image. Using `docker build`, users can create automated builds that execute a series of command line instructions.

##### Basic Structure of Dockerfile

- **FROM**: Specifies the base image.
- **RUN**: Executes commands in a new layer above the current image and commits the results.
- **COPY**: Copies new files, directories, or remote file URLs from `src` to the container's `dest` path.
- **CMD**: Provides default values for running containers. Only the last `CMD` takes effect.
- **EXPOSE**: Informs Docker that the container listens on specified network ports at runtime.
- **ENV**: Sets an environment variable `<key>` to the value `<value>`.
- **ENTRYPOINT**: Configures a container to run as an executable.

##### Example Dockerfile

```Dockerfile
# Use the official Python runtime as a parent image
FROM python:3.7-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "./app.py"]
```

- This Dockerfile creates a Python environment, sets the working directory, copies the current directory's contents, installs dependencies, exposes a port, sets an environment variable, and specifies the command to run on container startup.

#### Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. You can configure your application's services, networks, and volumes using the docker-compose.yml file.

##### Example docker-compose.yml

```yaml
version: "3"
services:
  web:
    image: "webapp:latest"
    ports:
      - "5000:5000"
  db:
    image: "postgres:latest"
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```

- The corresponding `doker-compose.yml` file defines web application services and postgreSQL database services. The web service runs on 5000 ports, and the db service is configured through environmental variables.

---
