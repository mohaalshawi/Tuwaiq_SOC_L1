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

Follow the interactive prompts to configure:

- Select Linux
- Press Enter
- Choose Self-signed SSL
- Enter (localhost)
- Enter (8000)
- Enter (8889)
- Select No
- Select No
- Choose a username and password
- Select none
- Set log directory to (opt/velociraptor/logs)
- Select No
- Save the configurations:
  - Server Config: (server.config.yaml)
  - Client Config: (client.config.yaml)

### 3️⃣ Create the server package
on linux:  
```bash
./velociraptor --config server.config.yaml debian server --binary velociraptor
```

### 4️⃣ Start the Velociraptor Server
On Linux: 
```bash
chmod +x velociraptor_server_0.73.2_amd64.deb
sudo dpkg -i velociraptor_server_0.73.2_amd64.deb
sudo systemctl start velociraptor_server
sudo systemctl status velociraptor_server
```

### 5️⃣ the service will show FAILURE=1
folow the below to fix it
```bash
sudo mkdir -p /opt/velociraptor/logs
sudo chown -R root:root /opt/velociraptor
sudo chmod -R 777 /opt/velociraptor/logs
sudo systemctl restart velociraptor_server
```

### 6️⃣ Access the Web Interface
Once the server is running, access the web UI:


```bash
https://localhost:8889
```
Use the credentials generated during the setup.


### 7️⃣ Deploying Velociraptor Agents (Clients)
To monitor endpoints, install the Velociraptor agent on target machines.

Windows Agent Installation
```powershell
Invoke-WebRequest -Uri "https://github.com/Velocidex/velociraptor/releases/download/v0.73/velociraptor-v0.73.3-windows-amd64.exe" -OutFile "velociraptor.exe"

edit: client.config.yaml "  server_urls:
  - https://<Linux_Host_IP>:8000/"
.\velociraptor.exe --config client.config.yaml
```


## 📚 Additional Resources
📖 Official Documentation: https://docs.velociraptor.app/ <br>
📢 Community Support: https://github.com/Velocidex/velociraptor
### 🚀 Congratulations! You’ve successfully installed Velociraptor EDR. 🎯
