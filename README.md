# 🔒 Docker Security & Optimization

## 📌 Project Overview

This project demonstrates **industry-standard Docker image optimization** and **container security hardening** techniques for deploying Node.js applications in production environments.

The primary goal is to build lightweight, secure, and production-ready Docker images by following Docker and DevOps best practices, including multi-stage builds, non-root execution, vulnerability scanning, and runtime security.

---

## 🎯 Project Objectives

- Optimize Docker images using **multi-stage builds**
- Reduce image size with **Alpine Linux**
- Exclude unnecessary files using **`.dockerignore`**
- Run containers as a **non-root user**
- Scan Docker images using **Trivy**
- Reduce vulnerabilities with updated base images
- Apply **runtime security** configurations
- Demonstrate production-ready Docker best practices

---

## 🛠️ Technologies Used

- Docker
- Node.js
- Express.js
- Alpine Linux
- Trivy
- Git
- GitHub

---

## 📁 Project Structure

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
├── scans/
│   └── trivy-report.txt
│
└── README.md
```

---

# ✨ Features Implemented

## 🚀 Image Optimization

- ✅ Multi-stage Docker build
- ✅ Lightweight `node:20-alpine` base image
- ✅ Optimized dependency installation
- ✅ Reduced final image size
- ✅ `.dockerignore` implementation

---

## 🔐 Security Hardening

- ✅ Created a dedicated non-root user
- ✅ Container runs without root privileges
- ✅ File ownership managed using `chown`
- ✅ Updated packages to reduce vulnerabilities
- ✅ Docker image scanned using Trivy

---

## 🛡️ Runtime Security

The secure container is executed with the following runtime restrictions:

- Memory Limit
- CPU Limit
- Read-only Filesystem
- Dropped Linux Capabilities

### Example

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

# 📊 Docker Image Comparison

| Feature | Insecure Image | Secure Image |
|----------|----------------|--------------|
| Base Image | `node:18` | `node:20-alpine` |
| Multi-stage Build | ❌ No | ✅ Yes |
| Non-root User | ❌ No | ✅ Yes |
| Image Size | ~1.09 GB | ~140 MB |
| Trivy Scan | Multiple Vulnerabilities | Reduced Vulnerabilities |
| Runtime Security | ❌ No | ✅ Yes |

---

# ⚙️ Build Instructions

## Build Insecure Image

```bash
docker build -f docker/Dockerfile.insecure -t node-insecure .
```

---

## Build Secure Image

```bash
docker build -f docker/Dockerfile.secure -t node-secure .
```

---

# ▶️ Run Containers

## Run Insecure Container

```bash
docker run -d \
-p 3000:3000 \
--name insecure-container \
node-insecure
```

---

## Run Secure Container

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

# 🔍 Vulnerability Scanning

Scan the Docker image using **Trivy**:

```bash
trivy image node-secure
```

Example output:

```text
Total: 0 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 0, CRITICAL: 0)
```

The complete scan report can be stored inside the **`scans/`** directory.

---

# 👤 Verify Non-Root User

Access the running container:

```bash
docker exec -it production-container sh
```

Check the current user:

```bash
whoami
```

Expected Output

```text
appuser
```

This confirms that the application is **not running as the root user**.

---

# 🔒 Runtime Security Verification

Try creating a file inside the running container:

```bash
touch test.txt
```

Expected Output

```text
touch: test.txt: Read-only file system
```

This confirms that the container's filesystem is protected against unauthorized modifications.

---

# ✅ Security Best Practices Implemented

- Multi-stage Docker builds
- Alpine Linux base image
- Reduced attack surface
- Non-root user execution
- Trivy vulnerability scanning
- Resource limits
- Read-only filesystem
- Dropped Linux capabilities
- Optimized Docker image size
- Clean Docker build context using `.dockerignore`

---

# 📈 Future Enhancements

- Docker Bench Security
- Docker Secrets
- Kubernetes Deployment
- CI/CD using GitHub Actions
- Docker Scout
- Image signing with Cosign
- Container image policy enforcement
- Automated vulnerability scanning pipeline

---

# 📚 Learning Outcomes

Through this project, the following Docker security concepts were implemented and validated:

- Docker image optimization
- Multi-stage builds
- Alpine-based production images
- Non-root container execution
- Docker runtime hardening
- Vulnerability assessment using Trivy
- Production-ready container deployment
- Docker security best practices

---

# 🎓 Key Takeaways

- Reduced Docker image size from **~1.09 GB** to **~140 MB**
- Improved security by eliminating root user execution
- Implemented runtime restrictions for production deployments
- Reduced vulnerabilities using updated base images
- Followed industry-standard Docker security practices

---

# 👩‍💻 Author

**Madhuri Chennupati**

**AWS DevOps Engineer**

### Skills

- 🐳 Docker
- ⚙️ GitHub Actions
- 🐧 Linux

---
⭐ **If you found this project helpful, consider giving it a star on GitHub!**
