# Fixing Kali Linux Update Issues & Installing DVWA

## Step 1: Update the System
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

## Step 2: Install DVWA
If the update completes successfully, proceed with installing DVWA (Damn Vulnerable Web Application):

```bash
sudo apt install dvwa
```

## Step 3: Start DVWA
Once installed, start DVWA using:
```bash
dvwa-start
```

You're now ready to use DVWA on Kali Linux! 🚀