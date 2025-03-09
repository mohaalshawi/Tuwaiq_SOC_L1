# 🦖 Velociraptor EDR - Installation Guide  

Velociraptor is an advanced endpoint monitoring, digital forensics, and incident response tool. This guide provides step-by-step instructions for installing and configuring Velociraptor on your system.  

## 📋 Prerequisites  

Before installing Velociraptor, ensure you have the following:  

- A Linux or Windows machine (Ubuntu 20.04+ recommended for Linux)  
- Administrative/root privileges  
- Internet connectivity for package downloads  
- Firewall rules allowing communication between the Velociraptor server and agents  

## 🚀 Installation Steps  

### 1️⃣ **Download Velociraptor**  
Visit the official Velociraptor GitHub releases page:  
🔗 [https://github.com/VelociraptorApp/Velociraptor/releases](https://github.com/VelociraptorApp/Velociraptor/releases)  

Download the appropriate binary for your system:  

```bash
# Linux (64-bit)
wget https://github.com/VelociraptorApp/Velociraptor/releases/latest/download/velociraptor-linux-amd64 -O velociraptor
chmod +x velociraptor
