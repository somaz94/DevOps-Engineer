### 1. What is Linux?

Linux is an operating system developed by Linus Torvalds in 1991. It is based on the Unix operating system and can be considered a Unix clone.

Like Unix, Linux is a network operating system supporting multiple users, multitasking, and multithreading. It is optimized for server operation, reflecting its initial design for communication networks.

Additionally, Linux is under a free software license, allowing anyone to use, modify, and redistribute its source code. This encourages continuous improvements and upgrades.

Key Components of Linux:

- **Kernel**
  - The core part of Linux, responsible for managing system resources and facilitating communication between hardware and software.
- **Shell**
  - A command-line interface for interacting with the operating system.
- **File System**
  - Organizes how data is stored and retrieved. Linux uses a hierarchical directory structure starting from the root (**`/`**).
- **Processes**
  - Each instance of a running program.
- **User and Group Management**
  - Linux is a multi-user system, allowing multiple users to share resources and access the system simultaneously.

---

### 2. RedHat vs Debian (System)

| Feature                     | Red Hat                                | Debian                                                |
| --------------------------- | -------------------------------------- | ----------------------------------------------------- |
| **Package Manager**         | `yum` / `dnf`                          | `apt`                                                 |
| **Package Format**          | RPM                                    | DEB                                                   |
| **Release Cycle**           | Fixed with RHEL; rolling with Fedora   | Stable release cycle with Testing & Unstable branches |
| **Default Init System**     | `systemd`                              | `systemd` (since Debian 8 Jessie)                     |
| **Supported Architectures** | Wide range, including IBM Z and Power  | Wide range, with focus on i386 and amd64              |
| **Security Updates**        | Provided by Red Hat with subscription  | Provided by the Debian Security Team                  |
| **Commercial Support**      | Available from Red Hat                 | Available through third parties                       |
| **Community**               | Fedora for community-driven innovation | Debian is entirely community-driven                   |
| **Enterprise Focus**        | Strong with Red Hat Enterprise Linux   | Available via Debian stable                           |

---

### 3. RedHat vs Debian (Commands and Package Management)

| Action                                    | Debian (using APT)                                                            | Red Hat (using YUM/DNF)                                                                                          |
| ----------------------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Install a package**                     | `sudo apt install package_name`                                               | `sudo yum install package_name` or `sudo dnf install package_name`                                               |
| **Remove a package**                      | `sudo apt remove package_name`                                                | `sudo yum remove package_name` or `sudo dnf remove package_name`                                                 |
| **Search for a package**                  | `apt search package_name`                                                     | `yum search package_name` or `dnf search package_name`                                                           |
| **Update package index**                  | `sudo apt update`                                                             | `sudo yum check-update` or `sudo dnf check-update`                                                               |
| **Upgrade packages**                      | `sudo apt upgrade`                                                            | `sudo yum update` or `sudo dnf upgrade`                                                                          |
| **Add a repository**                      | `sudo add-apt-repository 'deb [options] url distribution component'`          | `sudo yum-config-manager --add-repo repository_url` or `sudo dnf config-manager --add-repo repository_url`       |
| **Remove a repository**                   | `sudo add-apt-repository --remove 'deb [options] url distribution component'` | `sudo yum-config-manager --remove-repo repository_url` or `sudo dnf config-manager --remove-repo repository_url` |
| **List installed packages**               | `apt list --installed`                                                        | `yum list installed` or `dnf list installed`                                                                     |
| **Find out what package provides a file** | `apt-file search filename`                                                    | `yum provides filename` or `dnf provides filename`                                                               |
| **Automatic removal of unused packages**  | `sudo apt autoremove`                                                         | `sudo yum autoremove` or `sudo dnf autoremove`                                                                   |
| **View package information**              | `apt show package_name`                                                       | `yum info package_name` or `dnf info package_name`                                                               |
| **Clean up package cache**                | `sudo apt clean`                                                              | `sudo yum clean all` or `sudo dnf clean all`                                                                     |
| **Verify Corrupted Dependencies**         | `sudo apt check`                                                              | `sudo yum check` or `sudo dnf check`                                                                             |

---

### 4. Linux System Management Commands

#### System Monitoring

| Command  | Description                                                                           | Installation Command                              |
| -------- | ------------------------------------------------------------------------------------- | ------------------------------------------------- |
| `top`    | Displays a real-time list of processes consuming the most CPU.                        |                                                   |
| `htop`   | An enhanced version of `top` with an improved user interface.                         | `sudo apt install htop` / `sudo yum install htop` |
| `vmstat` | Shows information about system memory, processes, interrupts, CPU activity, and more. |                                                   |

#### Disk Usage

| Command | Description                                                   |
| ------- | ------------------------------------------------------------- |
| `df`    | Shows the disk space available on the file system.            |
| `du`    | Displays the disk space used by a specific directory or file. |

#### Process Management

| Command | Description                                            |
| ------- | ------------------------------------------------------ |
| `ps`    | Shows a list of currently running processes.           |
| `kill`  | Terminates a process with a specific PID (Process ID). |
| `pkill` | Terminates processes based on their name.              |

#### Network Management

| Command    | Description                                                           | Installation Command                                        |
| ---------- | --------------------------------------------------------------------- | ----------------------------------------------------------- |
| `ifconfig` | Configures or displays network interface settings.                    | `sudo apt install net-tools` / `sudo yum install net-tools` |
| `netstat`  | Shows network connections, routing tables, interface statistics, etc. |                                                             |
| `ss`       | Displays socket statistics, faster than `netstat`.                    |                                                             |

#### System Information

| Command | Description                            |
| ------- | -------------------------------------- |
| `uname` | Displays information about the system. |
| `lscpu` | Shows CPU architecture information.    |
| `lsblk` | Lists mounted block devices.           |

---

### 5. Linux Basic Commands

| Command   | Description                                                                              |
| --------- | ---------------------------------------------------------------------------------------- |
| `ls`      | Lists the contents of a directory.                                                       |
| `cd`      | Changes the current directory.                                                           |
| `pwd`     | Prints the current working directory path.                                               |
| `mkdir`   | Creates a new directory.                                                                 |
| `rmdir`   | Removes an empty directory.                                                              |
| `rm`      | Removes files or directories.                                                            |
| `cp`      | Copies files or directories.                                                             |
| `mv`      | Moves or renames files or directories.                                                   |
| `touch`   | Creates an empty file or updates the timestamp of an existing file.                      |
| `echo`    | Displays a line of text/string that is passed as an argument.                            |
| `cat`     | Concatenates and displays the content of files.                                          |
| `more`    | Displays the contents of a file, one page at a time.                                     |
| `less`    | Similar to `more`, but allows backward movement in the file as well as forward movement. |
| `head`    | Displays the first part of files, defaulting to showing the first 10 lines.              |
| `tail`    | Displays the last part of files, defaulting to showing the last 10 lines.                |
| `grep`    | Searches for patterns in files.                                                          |
| `find`    | Searches for files in a directory hierarchy.                                             |
| `chmod`   | Changes the file mode (permissions).                                                     |
| `chown`   | Changes the owner of files or directories.                                               |
| `df`      | Displays disk space usage.                                                               |
| `du`      | Estimates file space usage.                                                              |
| `clear`   | Clears the terminal screen.                                                              |
| `exit`    | Exits the shell or your current session.                                                 |
| `history` | Displays the command history.                                                            |
| `sudo`    | Executes a command as another user, by default as root.                                  |
| `man`     | Displays the manual pages for commands.                                                  |
| `which`   | Shows the full path of shell commands.                                                   |

---

### 6. /etc/skel

The `/etc/skel` directory is the "template" directory on Linux/Unix systems, including Ubuntu. When you create a new user account using tools such as `useradd` or `adduser`, the contents of `/etc/skel` are copied to the new user's home directory (e.g., `/home/username`). This allows new users to start with some basic configuration files and directory structure.

#### /etc/skel Directory Purpose

- The files and directories inside `/etc/skel` provide new users with basic configuration files such as `.bashrc`, `.bash_profile`, or `.profile` and sometimes directories such as `Documents`, `Downloads`, etc.
- These basic configuration files set environment variables, shell behavior, default paths, etc.
- System administrators can customize the default environment for new users by modifying the contents of `/etc/skel`. For example, you can add specific scripts, environment variables, or predefined directory structures.

#### Common files in /etc/skel

- `.bashrc`: Bash shell configuration file that runs when the user opens a new shell.
- `.profile`: Script run during login session to configure user environment.
- `.bash_profile`: Run on login as an alternative to `.profile` for bash shell users.
- `.bash_logout`: Script that runs when the user logs out of a shell session.

#### Utilize /etc/skel

For example, if you want all new users to receive a `.bashrc` file that customizes their prompt, you can place the `.bashrc` file in `/etc/skel`. When you create a new user, this `.bashrc` file is copied to the home directory, and the user automatically gets a customized prompt.

```bash
somaz@/etc/skel$ ls -al
total 20
drwxr-xr-x 2 root root 4096 Apr 21 2022 .
drwxr-xr-x 119 root root 4096 Oct 24 17:25 ..
-rw-r--r-- 1 root root 220 Feb 25 2020 .bash_logout
-rw-r--r-- 1 root root 3771 Feb 25 2020 .bashrc
-rw-r--r-- 1 root root 807 Feb 25 2020 .profile
```

#### How to use /etc/skel

Use `useradd` with the `-m` option, or when you create a new user using `adduser`, files and directories in `/etc/skel` are automatically copied to the new user's home directory.

```bash
sudo useradd -m somaz
```

- This command creates a new user `somaz` and the contents of `/etc/skel` are copied to `/home/somaz`.
- Unless you use the `-m` option (or the equivalent in another tool), the user's home directory will not be created, and the contents of `/etc/skel` will not be copied.

#### How to apply /etc/skel to an already created user

Sometimes, due to a mistake or not adding the `-m` option, or an error, the home directory is not created. The solution is as follows:

```bash
sudo su -
sudo mkdir /home/somaz
sudo cp -r /etc/skel/. /home/somaz
sudo chown -R somaz:somaz /home/somaz
# Edit /etc/passwd
somaz:x:1001:1001::/home/somaz:/bin/sh -> somaz:x:1001:1001::/home/somaz:/bin/bash
```

- When applied as above, the home directory is created normally, the bash shell is applied, and all files in `/etc/skel` are copied to the home directory.

---

### 7. Linux Kernel

The core of the operating system: The kernel is the core part of all operating systems. It is a layer that communicates directly with the hardware and provides essential services to applications and system processes.

**Linux Kernel as a Monolithic Kernel**:  
Linux is specifically a "Monolithic" kernel. This means that most of the core system functions (e.g., file system management, device drivers, memory management, etc.) are contained within a single large binary. This keeps these components in separate processes for modularity and security, but also for efficiency. This is different from the microkernel design, which can be dropped.

#### Linux Kernel Main Role
The kernel is responsible for managing hardware resources, ensuring efficient operation of processes, and providing essential services on which applications depend. Let's break down these responsibilities:
- **Process management**
- **Memory management**
- **Device management**
- **File system management**
- **Network stack**

#### Major components of the Linux kernel
- **System call interface**:  
  This is the gateway between user space applications and the kernel. Through system calls, an application can request specific services from the kernel, such as file operations, process control, and network communication.

- **Kernel module**:  
  A part of the kernel that can be loaded dynamically. This includes device drivers, file system drivers, and network protocol handlers. Modules provide flexibility because they can be loaded and unloaded without rebooting the system.

- **Interprocess communication (IPC)**:  
  The kernel provides mechanisms for processes to communicate with each other, such as pipes, message queues, and shared memory. IPC is essential for complex applications where multiple processes work together.

- **Security and access control**:  
  The Linux kernel includes powerful security mechanisms such as Security-Enhanced Linux (SELinux) and AppArmor. These frameworks enforce strict access control policies, allowing granular security settings at the process and file level.

#### Reference

- [What is Linux Kernel?](https://somaz.tistory.com/345)

---
