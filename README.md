![Linux Doge Node Setup for dummies](https://github.com/user-attachments/assets/4f333fd7-0efc-4bef-998c-97eb383c0a3b)

# **Dogecoin Node Setup Guide 🚀**  
*A step-by-step guide to setting up a Dogecoin node, even if you're a Linux beginner.*

---

## **📌 Prerequisites**
Before we begin, ensure you:  
👉 Have a stable internet connection  
👉 Have access to your **router settings** (needed for port forwarding)  
👉 Have a **Linux machine** (or Raspberry Pi) ready to install Dogecoin  

---

## **📡 Configuring Router (Port Forwarding & Static IP)**
To allow your node to connect properly, follow these steps:  

### **Step 1: Log into your router**
1. Open a web browser and go to:  
   ```
   192.168.0.1
   ```
2. Log in (default password is usually on the router label).  

### **Step 2: Assign a Static IP**
1. Go to **DHCP Settings**.
2. Find your machine in the list of connected devices.
3. Assign it a **static IP**, e.g.:  
  
  eg 192.168.0.24 set your own 

4. **Remember this IP**, you'll need it later.

### **Step 3: Open Port 22556**
1. Go to **Port Forwarding** settings.
2. Create a new rule:  
   - **Internal IP:** *(Your static IP from Step 2)*  
   - **Port:** `22555` (start) '22556'(end)  
   - **Protocol:** **Both (TCP & UDP)**  
   - **Enable the rule**  

💚 **Done!** Your router is now configured.  

---

## **🐶 Dogecoin Node Installation**
### **Step 1: Download Dogecoin Core**
Go to the official GitHub repository:  
👉 **[Dogecoin Core v1.14.9](https://github.com/dogecoin/dogecoin/releases/tag/v1.14.9)**  

Download the appropriate file:  
- **PC/Linux** → `x86_64` binaries  
- **Raspberry Pi** → `arm-linux` binaries  

---

### **Step 2: Install Dogecoin Core**
1. Open a terminal (**`Ctrl + Alt + T`**).
2. Extract the downloaded file:
   ```bash
   tar xvf dogecoin-1.14.9-x86_64-linux-gnu.tar.gz
   ```
3. Change directory:
   ```bash
   cd dogecoin-1.14.9/bin/
   ```
4. Start Dogecoin Core (let it run for 60 sec):
   ```bash
   ./dogecoind
   ```
5. Stop the process:
   ```bash
   Ctrl + C
   ```
6. Move Dogecoin binaries to a system-wide location:
   ```bash
   sudo cp dogecoin* /usr/bin/
   ```

🚀 **Dogecoin Core is installed!**

---

## **⚙️ Configuring Dogecoin Node**
### **Step 1: Create the Dogecoin Configuration File**
1. Go to the Dogecoin data directory:
   ```bash
   cd ~/.dogecoin/
   ```
2. Open the config file in nano:
   ```bash
   nano dogecoin.conf
   ```
3. **Copy & paste** the following configuration (modify username/password/IP):
   ```ini
   rpcuser=your_username
   rpcpassword=your_password
   rpcallowip=127.0.0.1
   maxconnections=50
   rpcport=22555
   server=1
   ```
4. **Save the file** (`Ctrl + X`, then `Y`, then `Enter`).

🚀 **Configuration is set up!**

---

## **🚀 Starting the Dogecoin Node**
### **Step 1: Create a Start Script**
1. Open a new file:
   ```bash
   nano start.sh
   ```
2. **Copy & paste** the following:
   ```bash
   dogecoind -conf=/home/your_username/.dogecoin/dogecoin.conf -daemon
   ```
   *(Replace `your_username` with your Linux username.)*

3. **Save the file** (`Ctrl + X`, then `Y`, then `Enter`).
4. Make the script executable:
   ```bash
   chmod +x start.sh
   ```
5. Run the script:
   ```bash
   ./start.sh
   ```

🚀 **Your node is now running!** 🎉

---

## **🔍 Checking Node Status**
Run the following commands to check your node:

1. **Check block sync progress:**
   ```bash
   dogecoin-cli getblockcount
   ```
2. **Check active connections:**
   ```bash
   dogecoin-cli getconnectioncount
   ```
   If **connections = 8**, your **port forwarding is incorrect**!  

🚀 **Your node is fully operational!** ✨

---

## **🌟 Summary**
### **✔️ What We Did:**
- Configured **Router Port Forwarding**
- Installed **Dogecoin Core**
- Created **Configuration Files**
- Started **Dogecoin Node**
- Verified **Node Sync Status**

💚 **You now have a fully functional Dogecoin Node!** 🐶🚀  

---

## **🙋 Need Help?**
If you have any issues, feel free to **open an issue** or reach out to the **Dogecoin community**! 🐕✨  

---
🚀 **Happy Mining & Supporting the Dogecoin Network!** 🐶

