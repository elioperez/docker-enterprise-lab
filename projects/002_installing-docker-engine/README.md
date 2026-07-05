# Project 002 – Installing Docker Engine

## Overview

This project is the second lab of my **Docker Enterprise Lab Portfolio**, based on the **DevOps with Docker** course from the University of Helsinki (MOOC.fi).

The objective of this project was to install Docker Engine on a dedicated Linux server following enterprise Linux administration best practices and the official Docker installation documentation.

By completing this project, I gained practical experience configuring software repositories, installing Docker Engine, managing Linux services, and verifying the complete Docker installation.

---

## Project Goals

- Remove any existing Docker packages
- Configure the official Docker CE repository
- Install Docker Engine
- Install Docker CLI
- Install Containerd
- Install Docker Buildx Plugin
- Install Docker Compose Plugin
- Start the Docker service
- Enable Docker at system startup
- Verify the installation
- Run the first Docker container

---

## Enterprise Scenario

A new Linux server has been approved to become a dedicated Docker Host.

As a Junior Linux Administrator, my responsibility was to install Docker Engine following enterprise best practices while documenting every step performed during the installation process.

---

## Lab Environment

### Host Computer

- Windows 10
- Visual Studio Code
- Git
- GitHub

### Virtual Machine

| Item | Value |
|------|-------|
| Hostname | docker01 |
| Operating System | CentOS Stream 9 |
| IP Address | 192.168.57.101 |
| Hypervisor | Oracle VirtualBox |
| Role | Dedicated Docker Host |

---

## Skills Practiced

- Linux package management
- DNF repository management
- Docker installation
- Linux service management
- Docker verification
- Software repository configuration
- Enterprise Linux administration

---

## Docker Components Installed

| Component | Description |
|-----------|-------------|
| Docker CE | Docker Engine |
| Docker CLI | Command-line interface |
| containerd.io | Container runtime |
| Docker Buildx Plugin | Advanced image building |
| Docker Compose Plugin | Multi-container application support |

---

## Commands Executed

### Remove Previous Docker Packages

```bash
sudo dnf remove \
docker \
docker-client \
docker-client-latest \
docker-common \
docker-latest \
docker-latest-logrotate \
docker-logrotate \
docker-engine
```

---

### Install DNF Plugins

```bash
sudo dnf install -y dnf-plugins-core
```

---

### Add Docker Repository

```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

---

### Verify Repository

```bash
dnf repolist
```

---

### Install Docker Engine

```bash
sudo dnf install -y \
docker-ce \
docker-ce-cli \
containerd.io \
docker-buildx-plugin \
docker-compose-plugin
```

---

### Start Docker

```bash
sudo systemctl start docker
```

---

### Enable Docker at Boot

```bash
sudo systemctl enable docker
```

---

### Verify Docker Installation

```bash
docker --version
```

```bash
docker info
```

---

### Run First Container

```bash
sudo docker run hello-world
```

---

## Validation Performed

The following validations were completed successfully:

- Previous Docker packages checked
- Docker repository configured
- Docker packages installed
- Docker service started
- Docker service enabled at boot
- Docker Engine verified
- Docker daemon verified
- Docker client verified
- First container executed successfully

---

## Screenshots

| Screenshot | Description |
|------------|-------------|
| 001_remove_old_docker_packages.png | Verified no previous Docker packages existed |
| 002_install_dnf_plugins.png | Installed DNF plugins |
| 003_add_repository.png | Added Docker CE repository |
| 004_install_docker_engine.png | Installed Docker Engine |
| 005_start_docker.png | Docker service running |
| 006_enable_docker.png | Docker enabled at boot |
| 007_verify_installation.png | Docker version and information |
| 008_hello_world.png | First Docker container executed |

---

## Troubleshooting

### Problem

Old Docker packages could conflict with the latest Docker Engine installation.

### Solution

Executed the package removal command before installation.

Result:

```
No packages marked for removal.
Nothing to do.
```

This confirmed that the server was clean and ready for Docker installation.

---

### Problem

Docker service may not start automatically after reboot.

### Solution

Enabled the Docker service:

```bash
sudo systemctl enable docker
```

---

## Lessons Learned

During this project I learned that installing Docker is more than simply executing one command.

A professional installation requires:

- Configuring the official repository
- Understanding every package being installed
- Managing Linux services with systemd
- Verifying Docker Engine functionality
- Testing the installation by running a container

I also learned that Docker consists of multiple components working together, including Docker Engine, Docker CLI, Containerd, Buildx, and Docker Compose.

---

## Project Outcome

Successfully installed Docker Engine on a dedicated CentOS Stream 9 server.

The Docker service is running correctly, starts automatically during system boot, and can successfully execute Docker containers.

The server is now ready for image management and container administration.