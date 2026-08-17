# Laboratory-03-Multi-Cloud-Explorer

# Checkpoint 7 — Continue Your Linux Investigation

## Linux Server Information (via KillerCoda Playground)

The following information was gathered from a Linux server running on the KillerCoda Playground using standard Linux commands.

### Operating System
Command used: `cat /etc/os-release`
PRETTY_NAME="Ubuntu 24.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.4 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian

### CPU Information
Command used: `lscpu`
Architecture: x86_64
CPU op-mode(s): 32-bit, 64-bit
Byte Order: Little Endian
CPU(s): 1
On-line CPU(s) list: 0
Vendor ID: GenuineIntel
Model name: Intel Xeon E312xx (Sandy Bridge, IBRS update)
Thread(s) per core: 1
Core(s) per socket: 1
Socket(s): 1
Virtualization features:
Hypervisor vendor: KVM
Virtualization type: full

### Memory
Command used: `free -h`
Mem: 1.9Gi 417Mi 866Mi 1.1Mi 786Mi 1.5Gi
Swap: 1.0Gi 0B 1.0Gi

### Disk Space
Command used: `df -h`
Filesystem Size Used Avail Use% Mounted on
/dev/vda1 19G 5.4G 13G 30% /
/dev/vda16 881M 117M 703M 15% /boot
/dev/vda15 105M 6.2M 99M 6% /boot/efi

> *Screenshots of the terminal output for each command above are included in the `screenshots` folder.*

---

## Cloud Migration Analysis

**Question: If this Linux server were migrated to the cloud, which AWS, Azure, and GCP services could host it?**

Based on the server's specifications gathered above (1 vCPU, ~2 GB RAM, ~19 GB disk, Ubuntu 24.04 LTS), this is a small, lightweight Linux server. It could be hosted on the cloud using the following equivalent compute services:

- **AWS**: This server matches a small burstable instance such as **Amazon EC2 t3.micro** (2 vCPU burstable, 1 GB RAM) or **t3.small** (2 GB RAM), with **Amazon EBS** (General Purpose SSD, ~20 GB) providing equivalent disk storage.

- **Microsoft Azure**: This server matches an **Azure Virtual Machine B1s** or **B1ms** size (burstable, low-cost tier suited for small workloads), with **Azure Managed Disks** (Standard SSD, ~20 GB) for storage.

- **Google Cloud Platform**: This server matches a **Compute Engine e2-micro** or **e2-small** instance (cost-efficient, low-CPU workloads), with a **Persistent Disk** (~20 GB) providing equivalent storage.

All three providers offer virtual machine services that can run the same Ubuntu 24.04 LTS operating system, meaning this server's workload is not tied to any single cloud provider — it could realistically run on any of the three. Given the server's small resource footprint (1 CPU core, under 2 GB RAM), the most cost-effective options would be AWS's `t3.micro`, Azure's `B1s`, or GCP's `e2-micro` — all of which are part of each provider's free-tier or low-cost burstable instance families, making this an ideal candidate for a low-traffic web server, development environment, or lightweight application.
