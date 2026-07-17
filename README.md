# Docker Security & Optimization

## Project Overview

This project demonstrates industry-standard Docker image optimization and container security hardening techniques for deploying Node.js applications in production environments. The objective is to reduce image size, improve security, minimize vulnerabilities, and implement container runtime protection following DevOps best practices.

---

## Project Objectives

* Optimize Docker images using multi-stage builds
* Reduce image size using Alpine Linux
* Remove unnecessary files using `.dockerignore`
* Run containers as a non-root user
* Scan Docker images using Trivy
* Reduce vulnerabilities by using updated base images
* Apply runtime security configurations
* Demonstrate production-ready Docker practices

---

## Technologies Used

* Docker
* Node.js
* Express.js
* Alpine Linux
* Trivy
* Git
* GitHub

---

## Project Structure

```text
docker-security-optimization/
│
├── app/
│   ├── app.js
│   ├── package.json
│   └── package-lock.json
│
├── docker/
│   ├── Dockerfile.insecure
│   ├── Dockerfile.secure
│   └── .dockerignore
│
└── README.md
```

---

# Features Implemented

## Image Optimization

* Multi-stage Docker build
* Lightweight `node:alpine` base image
* Optimized dependency installation
* Reduced final image size
* `.dockerignore` implementation

---

## Security Hardening

* Created dedicated non-root user
* Container runs without root privileges
* Ownership assigned using `chown`
* Updated packages to reduce vulnerabilities
* Docker image scanned using Trivy

---

## Runtime Security

The secure container is executed with the following runtime restrictions:

* Memory Limit
* CPU Limit
* Read-only Filesystem
* Dropped Linux Capabilities

Example:

```bash
docker run -d \
-p 3000:3000 \
--memory="512m" \
--cpus="1" \
--read-only \
--cap-drop=ALL \
--name production-container \
node-secure
```

---

# Docker Image Comparison

| Feature           | Insecure Image           | Secure Image            |
| ----------------- | ------------------------ | ----------------------- |
| Base Image        | node:18                  | node:20-alpine          |
| Multi-stage Build | No                       | Yes                     |
| Non-root User     | No                       | Yes                     |
| Image Size        | ~1.09 GB                 | ~140 MB                 |
| Trivy Scan        | Multiple Vulnerabilities | Reduced Vulnerabilities |
| Runtime Security  | No                       | Yes                     |

---

# Build Instructions

## Build Insecure Image

```bash
docker build -f docker/Dockerfile.insecure -t node-insecure .
```

## Build Secure Image

```bash
docker build -f docker/Dockerfile.secure -t node-secure .
```

---

# Run Containers

## Insecure Container

```bash
docker run -d -p 3000:3000 --name insecure-container node-insecure
```

## Secure Container

```bash
docker run -d \
-p 3000:3000 \
--memory="512m" \
--cpus="1" \
--read-only \
--cap-drop=ALL \
--name production-container \
node-secure
```

---

# Vulnerability Scanning

Scan the Docker image using Trivy:

```bash
trivy image node-secure
```

The scan report is stored inside the `scans` directory.

---

# Verify Non-Root User

Enter the running container:

```bash
docker exec -it production-container sh
```

Verify the user:

```bash
whoami
```

Expected output:

```text
appuser
```

---

# Runtime Security Verification

Attempt to create a file inside the container:

```bash
touch test.txt
```

Expected result:

```text
Read-only file system
```

This confirms that the container filesystem is protected.

---

# Security Best Practices Implemented

* Multi-stage Docker builds
* Alpine Linux base image
* Reduced attack surface
* Non-root user execution
* Trivy vulnerability scanning
* Resource limits
* Read-only filesystem
* Dropped Linux capabilities
* Optimized Docker image size
* Clean Docker build context using `.dockerignore`

---

# Future Enhancements

* Docker Bench Security
* Docker Secrets
* Kubernetes Deployment
* CI/CD using GitHub Actions
* Image signing
* Container image policy enforcement
* Automated vulnerability scanning pipeline

---

# Learning Outcomes

Through this project, the following Docker security concepts were implemented and validated:

* Docker image optimization
* Multi-stage builds
* Alpine-based production images
* Non-root container execution
* Docker runtime hardening
* Vulnerability assessment with Trivy
* Production-ready container deployment
* Docker security best practices

---

# Author

**Madhuri Chennupati**

AWS DevOps Engineer | Docker | Kubernetes | Jenkins | GitHub Actions | Linux | Terraform | AWS
