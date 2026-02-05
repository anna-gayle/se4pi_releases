# SE4PI Audio Client

**IMPORTANT WARNING:** This client application is **USELESS** without the SE4PI Raspberry Pi server hardware. It will not function as a standalone application.

Professional audio streaming client designed specifically for the SE4PI audio processing server running on Raspberry Pi hardware.

## SYSTEM REQUIREMENTS

### **MANDATORY HARDWARE REQUIRED:**
- **SE4PI Raspberry Pi Server** (with SE4PI server software installed)
- **Raspberry Pi 4** (minimum) with SE4PI custom firmware
- **USB connection** between PC and Raspberry Pi

### **Without the SE4PI Raspberry Pi server, this application:**
- **Will NOT process audio**
- **Will NOT reduce noise**
- **Will NOT connect to anything**
- **Is completely non-functional**

## Download & Installation

### **Step 1: Verify You Have the SE4PI Hardware**
Before downloading, ensure you have:
- SE4PI Raspberry Pi unit
- USB-C cable for connection
- SE4PI server software pre-installed on the Pi

### **Step 2: Download the Client**
- Go to [Releases](https://github.com/YOUR_USERNAME/se4pi-client-releases/releases)
- Download the latest `SE4PI-Client-vX.X.X.exe` or portable zip
- **Portable version recommended** - no installation needed!

### **Step 3: Install Required PC Software**

#### Virtual Audio Cable (Required for audio routing)
**Download:** [VB-Cable Virtual Audio Device](https://vb-audio.com/Cable/)
1. Download and run the installer
2. Restart your computer if prompted
3. VB-Cable will appear as an audio device in Windows Sound Settings

#### USB RNDIS Drivers (For Raspberry Pi connection)
**Included in download:** `drivers/mod-duo-rndis.zip`

**First-Time Installation (Windows may not auto-detect):**

1. **Extract the driver zip** to a folder on your computer
2. **Connect your Raspberry Pi** via USB-C cable
3. **Wait for Windows** to attempt driver installation (it will likely fail)

4. **Manual Driver Installation:**
   - Open **Device Manager** (Win + X → Device Manager)
   - Look under **"Ports (COM & LPT)"** or **"Other devices"**
   - Find the unrecognized device (may show as "Unknown device" or "USB Serial Device")
   - **Right-click** → **"Update driver"**
   - Select **"Browse my computer for drivers"**
   - Click **"Browse"** and navigate to the extracted `mod-duo-rndis` folder
   - Check **"Include subfolders"**
   - Click **"Next"** and let Windows install the driver

5. **Verify Installation:**
   - After successful installation, check **Device Manager** → **"Network adapters"**
   - You should see **"USB Ethernet/RNDIS Gadget"**
   - The Pi will appear as a network device named `se4pi.local`

**Troubleshooting Driver Installation:**
- If Windows says "The best driver is already installed" → Choose **"Let me pick from a list"**
- If still not working, try different USB ports
- Restart PC after driver installation
- Some systems may require disabling driver signature enforcement

## Quick Start Guide

### **Connection Setup**
1. **Connect Hardware:**
   - Plug Raspberry Pi into PC's USB port using USB-C cable
   - Wait for RNDIS driver installation (first time only)
   - Green LED on Pi should be solid

2. **Audio Configuration:**
   - Set VB-Cable as your **default microphone** in Windows
   - Set your headphones/speakers as default output

3. **Launch Client:**
   - Open SE4PI Client
   - **Auto-connection** should occur within 5 seconds
   - Status should show: "Connected to se4pi.local"

### **Audio Flow (How It Works)**

[Your Microphone]
       ↓
[VB-Cable Input] → [SE4PI Client] → [USB Network] → [Raspberry Pi Server]
       ↑                                                       ↓
[Your Headphones] ← [SE4PI Client] ← [USB Network] ← [Processed Audio]

## TROUBLESHOOTING

### **"Windows Doesn't Recognize the Pi" (First Time)**
1. **Check Device Manager** under "Ports (COM & LPT)" or "Other devices"
2. **Manually install driver:**
   - Right-click unrecognized device → Update driver
   - Browse to extracted `mod-duo-rndis` folder
   - Select "USB Ethernet/RNDIS Gadget" driver
3. **After installation,** check under "Network adapters" for "USB Ethernet/RNDIS Gadget"

### **"Cannot Connect to se4pi.local"**
1. **Verify Pi is powered** (green LED should be solid)
2. **Check Network Connections:**
   - Open Network Connections (Win + R → `ncpa.cpl`)
   - Look for "USB Ethernet/RNDIS Gadget"
   - It should show "Network cable unplugged" when Pi is disconnected
   - Shows "Connected" when Pi is connected
3. **Test Connection:**
   - Open Command Prompt
   - Type: `ping se4pi.local`
   - Should get replies from `192.168.7.2`
4. **Alternative Connection:**
   - In client, use IP address: `192.168.7.2`
   - Instead of `se4pi.local`

### **"Driver Installation Failed"**
1. **Try different USB port** (preferably USB 3.0/3.1)
2. **Restart PC** and try again
3. **Disable Driver Signature Enforcement** (for Windows 10/11):
   - Settings → Update & Security → Recovery
   - Advanced startup → Restart now
   - Troubleshoot → Advanced options → Startup Settings → Restart
   - Press 7 or F7 to "Disable driver signature enforcement"
4. **Contact support** for alternative drivers

### **"Pi Shows Up But No Connection"**
1. **Check Pi server is running:**
   - Green LED should be solid (not blinking)
   - If blinking, server may not be running
2. **Restart Pi** by unplugging and reconnecting USB
3. **Wait 30 seconds** after connection for Pi to fully boot

### **"No Audio" or "App Does Nothing"**
**This is normal if you don't have the SE4PI Raspberry Pi hardware.**
The client only functions as a remote interface for the SE4PI server.

### **"Authentication Failed"**
1. **Server hardware mismatch** - each Pi has unique hardware-locked token
2. **Contact manufacturer** for hardware replacement if token mismatch

## Application Structure

SE4PI-Client-Portable/
├── SE4PI-Client.exe    # Main executable (USELESS without Pi server)
├── README.txt          # This warning document
├── config/             # Connection settings
├── logs/               # Connection logs
└── drivers/            # USB network drivers

## Updates
The client can auto-update, but **server updates require physical access** to the Raspberry Pi.

##  IMPORTANT DISCLAIMERS

1. **This is not standalone software** - it requires the SE4PI Raspberry Pi server
2. **No audio processing happens on your PC** - all processing is on the Pi
3. **Without the hardware, this is just a UI** with no functionality
4. **Each client is paired** with a specific Raspberry Pi via hardware encryption

## Support & Contact
- **Hardware Issues:** Contact your SE4PI hardware supplier
- **Connection Issues:** Check `logs/connection.log`
- **Software Bugs:** [GitHub Issues](https://github.com/YOUR_USERNAME/se4pi-client-releases/issues)

## 📄 License
**Proprietary Hardware-Locked License**
This software is licensed for use exclusively with SE4PI Raspberry Pi hardware.
Unauthorized use or distribution is prohibited.

---

**REMEMBER:** This client application is a **REMOTE INTERFACE ONLY**. All audio processing happens on the SE4PI Raspberry Pi server. Without the server hardware, this application has **ZERO functionality**.

## For the shorter version (in the repo description or top of README):

# SE4PI AUDIO CLIENT - HARDWARE REQUIRED 

**THIS APPLICATION IS USELESS WITHOUT THE SE4PI RASPBERRY PI SERVER HARDWARE**

## WHAT THIS IS:
- A remote control interface for the SE4PI audio processing server
- A network client that streams audio to/from the Raspberry Pi

## WHAT THIS IS NOT:
- A standalone audio processor
- A noise reduction software for your PC
- A functional application without the SE4PI hardware

## REQUIREMENTS:
**MANDATORY:** SE4PI Raspberry Pi 4 server with SE4PI firmware
**OPTIONAL:** VB-Cable for Windows audio routing

## WARNING:
Downloading and running this without the SE4PI hardware will result in:
- "Cannot connect to server" errors
- No audio processing functionality
- A completely non-functional interface

---

**Only proceed if you have the SE4PI Raspberry Pi server hardware.**
```
