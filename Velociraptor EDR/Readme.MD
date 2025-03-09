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
wget https://github.com/Velocidex/velociraptor/releases/download/v0.73/velociraptor-v0.73.2-linux-amd64 -O velociraptor
chmod +x velociraptor
```

### 2️⃣ Initialize the Velociraptor Configuration
Run the following command to generate the initial configuration:
```bash
 ./velociraptor config generate -i
```

Follow the interactive prompts to configure:

- Server or Client: Choose "Server" for a standalone setup
- Hostname/IP: Enter the public IP or domain of your server
- Certificates: Self-signed certificates will be generated
- Data Storage: Choose a directory for storing logs and collected data


### 3️⃣ Start the Velociraptor Server
On Linux: 
```bash
./velociraptor --config server.config.yaml frontend
```

### 4️⃣ Access the Web Interface
Once the server is running, access the web UI:


```bash
https://localhost:8889
```
Use the credentials generated during the setup.


### 5️⃣ Deploying Velociraptor Agents (Clients)
To monitor endpoints, install the Velociraptor agent on target machines.

Windows Agent Installation
```powershell
Invoke-WebRequest -Uri "https://github.com/Velocidex/velociraptor/releases/download/v0.73/velociraptor-v0.73.3-windows-amd64.exe" -OutFile "velociraptor.exe"
.\velociraptor.exe --config client.config.yaml
```


## 📚 Additional Resources
📖 Official Documentation: https://www.velociraptor.app/docs/
📢 Community Support: https://github.com/VelociraptorApp/Velociraptor/discussions
### 🚀 Congratulations! You’ve successfully installed Velociraptor EDR. 🎯
