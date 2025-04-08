### 🖥️ Step 1: Enable Receiving on the Splunk (Windows) Server
Open Splunk Web on your Windows server:
```
http://<splunk-VM-IP>:8000
```
Go to:
Settings → Forwarding and receiving → Receive data

Click + Add new under "Receive data"

Select TCP, then enter port 9997


----------
### 🔥 Step 2: Allow Port 9997 in Windows Firewall
Open Windows Defender Firewall with Advanced Security

Click Inbound Rules → New Rule

Select Port

Protocol: TCP

Port: 9997

Action: Allow the connection

Apply to all profiles, name it (e.g., Splunk Forwarder), and save

--------------
### 🐧 Step 3: Install Splunk Universal Forwarder on the Linux Server
Go to the official site:
https://www.splunk.com/en_us/download/universal-forwarder.html?locale=en_us

Download the appropriate Linux package (e.g., .deb or .rpm)

Install it:

Ubuntu/Debian:
```
wget -O splunkforwarder.deb "https://download.splunk.com/products/universalforwarder/releases/9.4.1/linux/splunkforwarder-9.4.1-e3bdab203ac8-linux-amd64.deb"
```
```
sudo dpkg -i splunkforwarder.deb
```
Start and accept license:
```
sudo /opt/splunkforwarder/bin/splunk start --accept-license
sudo /opt/splunkforwarder/bin/splunk enable boot-start
```

----------
### Step 4: Configure the Forwarder to Send Logs to the Splunk Windows Server
Add the Splunk server as a forwarder destination:
```
sudo /opt/splunkforwarder/bin/splunk add forward-server <Splunk_VM_IP>:9997
```
confirm status
```
/opt/splunkforwarder/bin/splunk list forward-server
```
-----------
### Step 5: Choose Which Logs to Forward
To monitor a log file or folder:
```
sudo /opt/splunkforwarder/bin/splunk add monitor /var/log/dvwa/access.log -sourcetype access_combined   
```
### 🔁 Step 6: Verify in Splunk Web
In Splunk Web, search for incoming data:
```
index=* 
```




