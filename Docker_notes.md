# Docker Notes

Docker: Accelerated Container Application Development

Docker
https://www.docker.com
Docker is a platform designed to help developers build, share, and run container applications. We handle the tedious setup, so you can focus on the code.


## Containers vs. Virtual Machines

Containers are often compared to Virtual Machines (VMs), but this is not accurate.  

| Feature              | Virtual Machines (VMs)                         | Containers                                |
|----------------------|------------------------------------------------|-------------------------------------------|
| **Virtualization**   | Hardware (via hypervisor)                      | Operating system kernel                   |
| **OS**               | Each VM runs its own OS                        | Share the host OS                         |
| **Resources**        | Heavy (emulated memory/disks)                   | Lightweight                               |
| **Startup**          | Slow (must boot OS)                            | Fast (no boot needed)                     |
| **Isolation**        | Strong, apps can’t see each other or the host  | Weaker, containers can sometimes see host |
| **Use case**         | Multiple apps per VM                           | One app per container (best practice)     |

**Summary:**  
VMs are like full computers running on virtual hardware, while containers are isolated processes sharing the host OS.  

---

## Anatomy of a Container

A container is built from **two key Linux kernel features**:

- **Namespaces**  
  Provide isolated views of system resources:  
  - `USERNS`: users  
  - `MOUNT`: filesystems  
  - `NET`: networking  
  - `IPC`: inter-process communication  
  - `TIME`: system time (not used in Docker)  
  - `PID`: process IDs  
  - `CGROUP`: control groups  
  - `UTS`: hostnames  

- **Control Groups (cgroups)**  
  Limit and monitor resources for each container:  
  - CPU time  
  - Memory consumption  
  - Network & disk bandwidth  

**Notes:**  
- Much lighter than VMs (no hardware virtualization).  
- Containers are OS-specific (Linux images run only on Linux, Windows on Windows).  
- Disk quotas aren’t handled by cgroups but by storage drivers.  

---

## Docker Alternatives

Docker is popular, but other runtimes exist:  

- **Kubernetes** introduced the **CRI (Container Runtime Interface)** for pluggable runtimes.  
- Examples: **CRI-O**, **runc**, **Firecracker** (AWS).  
- **Podman** (Red Hat): focuses on security  
  - Supports **rootless containers** (not running as root).  
  - Can run multiple apps in one container using `systemd`.  

**Security Note:**  
Most Docker containers run as root, which can be risky. Podman offers safer alternatives.  

---

## Key Takeaways

- Containers are **lightweight, fast, and efficient** compared to VMs.  
- They rely on **Linux kernel features** (namespaces + cgroups).  
- Multiple runtimes exist, each with unique trade-offs.  
- Security matters: avoid running containers as root when possible.  
