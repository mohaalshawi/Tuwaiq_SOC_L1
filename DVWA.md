
### Step 1: Install DVWA
```bash
sudo apt install dvwa
```

### Step 2: Start DVWA
Once installed, start DVWA using:
```bash
dvwa-start
```

You're now ready to use DVWA on Kali Linux! 🚀


------------
# IF IT DIDN'T RUN DO:
## Fixing Kali Linux Update Issues & Installing DVWA

### Step 3: Update the System
Run the following command to update your package list:
```bash
sudo apt update
```

### If the update fails with an error related to `EXPKEYSIG ED444FF07D8D0BF6`, follow these steps:

1. Remove the expired key:
   ```bash
   sudo apt-key del ED444FF07D8D0BF6
   ```
2. Add the new Kali GPG key:
   ```bash
   curl -fsSL 'https://archive.kali.org/archive-key.asc' | sudo tee /etc/apt/trusted.gpg.d/kali-archive-keyring.asc
   ```
3. Try updating again:
   ```bash
   sudo apt update
   ```
