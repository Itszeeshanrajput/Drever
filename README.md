# 🔐 Drever - Professional ESP32 Wi-Fi Security Testing Tool

<div align="center">

**Universal ESP32 Platform for Advanced Wi-Fi Security Research & Penetration Testing**

[![C++](https://img.shields.io/badge/C++-17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)](https://en.cppreference.com/)
[![ESP32](https://img.shields.io/badge/ESP32-Professional-FF7139?style=for-the-badge&logo=espressif&logoColor=white)](https://www.espressif.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![PlatformIO](https://img.shields.io/badge/PlatformIO-Supported-orange?style=for-the-badge)](https://platformio.org/)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)](https://github.com/Itszeeshanrajput/Drever)

**#WiFiSecurity #ESP32 #Penetration #802.11 #CyberSecurity #Research**

[Features](#-features) • [Quick Start](#-quick-start) • [Installation](#-installation) • [Usage](#-usage) • [Documentation](#-documentation)

</div>

---

## 📺 Overview

**Drever** is a comprehensive, educational security research tool for the ESP32 microcontroller. It demonstrates Wi-Fi vulnerabilities and provides hands-on learning about 802.11 security protocols. This project is built for **security professionals, researchers, and educators** to understand wireless network security.

### Key Highlights
- ✅ **Educational Purpose** - Learn about Wi-Fi security mechanisms
- ✅ **Modular Architecture** - Reusable components for custom implementations
- ✅ **Advanced Capabilities** - Professional-grade security testing features
- ✅ **Low Power** - Runs on affordable, portable ESP32 boards
- ✅ **Web Interface** - Intuitive management through browser
- ✅ **Reversible** - Full control over all operations

---

## ✨ Features

### 🛡️ Security Testing Capabilities

#### PMKID Capture
- Extract PMKID (Pairwise Master Key Identifier) from WPA/WPA2 APs
- Passive capture without active connection
- Exportable for offline analysis with Hashcat

#### WPA/WPA2 Handshake Capture
- Capture complete 4-way authentication handshakes
- Passive handshake sniffing
- Parse and analyze captured frames
- Export to HCCAPX format for cracking tools

#### Deauthentication Attacks
- **Broadcast Method** - Send deauth to all connected clients
- **Rogue AP Method** - Create duplicate AP to intercept traffic
- Configurable attack parameters
- Multiple simultaneous targets

#### Denial of Service (DoS)
- Network availability testing
- Load simulation capabilities
- Rate-limited attack modes
- Research & educational purposes only

#### Frame Analysis
- Capture and parse 802.11 frames
- Extract security information
- Analyze signal strength (RSSI)
- Channel monitoring

#### Data Capture
- PCAP format export for Wireshark/tcpdump
- Complete frame logging
- Traffic analysis capabilities
- Replay attack preparation

### ⚙️ System Features

- **Management AP** - Easy configuration via web interface
- **Wireless Configuration** - Change networks on the fly
- **Extensible Framework** - Add custom attack implementations
- **Component-Based** - Modular, reusable code structure
- **Doxygen Documentation** - Full API reference
- **Low Power Design** - Battery-friendly operation (~100mA typical)

---

## 🚀 Quick Start

### Hardware Requirements

**Minimum Setup:**
- ESP32 Development Board (e.g., ESP32-DEVKITC-32E)
- USB Cable for flashing
- Computer with PlatformIO

**Recommended for Portability:**
- ESP32-DEVKITC-32E + Li-Po Battery + Voltage Regulator
- ~17g total weight
- ~3-4 hours battery life

### Step 1: Install PlatformIO
```bash
# Install PlatformIO CLI
python -m pip install platformio

# Or use VSCode extension: PlatformIO IDE
```

### Step 2: Build & Flash
```bash
# Clone repository
git clone https://github.com/Itszeeshanrajput/Drever.git
cd Drever

# Build project
platformio run

# Flash to ESP32 (replace /dev/ttyUSB0 with your port)
platformio run --target upload --upload-port /dev/ttyUSB0
```

### Step 3: Connect to Management AP
```
1. Power on the ESP32
2. Connect to Wi-Fi: "ManagementAP" (password: "mgmtadmin")
3. Open browser: http://192.168.4.1
4. Start testing!
```

---

## 📖 Documentation

### 🏗️ Architecture

```
Drever/
├── main/                          # Main component & attack implementations
├── components/
│   ├── wifi_controller/          # Wi-Fi operations (AP, STA, scan)
│   ├── webserver/                # Web UI & control interface
│   ├── wsl_bypasser/             # Wi-Fi Stack Libraries bypasser
│   ├── frame_analyzer/           # Frame parsing & analysis
│   ├── pcap_serializer/          # PCAP format export
│   └── hccapx_serializer/        # HCCAPX format export
├── doc/                          # Documentation & diagrams
│   ├── ATTACKS_THEORY.md        # Technical background
│   └── images/                   # Screenshots & diagrams
├── platformio.ini                # PlatformIO configuration
└── README.md                     # This file
```

### 📚 Technical Documentation

- **[Attacks Theory](doc/ATTACKS_THEORY.md)** - Deep dive into attack mechanisms
- **[Component READMEs](main/README.md)** - Component-specific documentation
- **API Reference** - Generate with: `doxygen` (from repo root)
- **Academic Paper** - [Research publication (PDF)](https://excel.fit.vutbr.cz/submissions/2021/048/48.pdf)

### 🔧 Building Documentation
```bash
# Generate Doxygen API documentation
doxygen
# Open ./doc/html/index.html in browser
```

---

## 📋 Usage Modes

### 1. Passive Frame Sniffing
```
- Monitor Wi-Fi traffic without transmission
- Analyze signal strength (RSSI)
- Identify nearby networks
- No active connection required
- Logs saved to PCAP format
```

### 2. PMKID Capture
```
- Target specific access point
- Initiate connection attempt
- Capture PMKID from first handshake frame
- No de-authentication required
- Exportable for Hashcat cracking
```

### 3. WPA Handshake Capture
```
- Monitor target network
- Wait for client connection
- Capture complete 4-way handshake
- Or force capture via de-authentication
- Export to HCCAPX for Hashcat
```

### 4. De-Authentication Attacks
```
Method 1 - Broadcast:
- Send to all connected clients
- Some devices ignore this method
- Effective against most clients

Method 2 - Rogue AP:
- Create duplicate access point
- More effective against newer devices
- Requires active monitoring
```

### 5. Denial of Service Testing
```
- Flood target with management frames
- Test network stability
- Educational purposes only
- Configurable intensity levels
```

---

## ⚙️ Configuration

### Web Interface Settings
```
1. Open http://192.168.4.1 in browser
2. Configure attack parameters:
   - Target SSID / BSSID
   - Attack type
   - Duration & intensity
   - Output format (PCAP/HCCAPX)
3. Click "Start" to begin
4. Monitor progress in real-time
5. Download captured data
```

### Default Credentials
```
Management AP:
- SSID: ManagementAP
- Password: mgmtadmin
- IP: 192.168.4.1
```

---

## 🔧 Troubleshooting

### Issue: "Device Not Detected"
```
✅ Solution:
1. Check USB cable connection
2. Install CH340 drivers (common for ESP32 boards)
3. Verify port: `platformio device list`
4. Run `platformio run --target upload --upload-port COM3` (Windows)
```

### Issue: "Build Fails - Missing Dependencies"
```
✅ Solution:
1. Update PlatformIO: `platformio upgrade`
2. Clean build: `platformio run --target clean`
3. Full rebuild: `platformio run --target upload --upload-port /dev/ttyUSB0`
```

### Issue: "Web Interface Not Responding"
```
✅ Solution:
1. Verify Management AP is running
2. Check Wi-Fi connection to ManagementAP
3. Try different browser
4. Restart ESP32
5. Check serial monitor for errors
```

### Issue: "Attacks Not Working"
```
✅ Solution:
1. Verify target network is visible
2. Check ESP32 antenna connection
3. Try different location (reduce interference)
4. Update to latest firmware
5. Check documentation for target compatibility
```

---

## ⚠️ Legal & Ethical Information

### Important Disclaimer

**This project is for EDUCATIONAL and RESEARCH purposes ONLY.**

- ⚠️ Only use on networks **you own or have explicit permission to test**
- ⚠️ Unauthorized access to networks is **ILLEGAL**
- ⚠️ Follow all applicable laws and regulations in your jurisdiction
- ⚠️ Use only in controlled lab environments
- ⚠️ Respect others' privacy and network security
- ⚠️ Never use for malicious purposes

### Responsible Disclosure

If you discover vulnerabilities:
1. Report responsibly to affected parties
2. Give reasonable time to patch
3. Avoid public disclosure until fixed
4. Follow disclosure best practices

---

## 📊 Hardware Specifications

### Supported Boards
- ✅ ESP32-DEVKITC-32E
- ✅ ESP32-WROOM-32
- ✅ ESP32-S3
- ✅ Other ESP32 variants

### Power Consumption
- **Idle:** ~80 mA
- **Active Attack:** ~100 mA
- **Peak:** ~200 mA

### Range
- Typical: 30-50 meters
- Can be extended with external antenna

### Storage
- Flash: 4MB (sufficient)
- SPIFFS: 2MB available

---

## 🤝 Contributing

Contributions welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### How to Contribute
1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Follow Doxygen notation for code comments
4. Test thoroughly on ESP32 hardware
5. Commit: `git commit -m 'Add feature'`
6. Push: `git push origin feature/amazing-feature`
7. Open Pull Request

### Areas for Contribution
- 🐛 Bug fixes and stability improvements
- ✨ New attack implementations
- 📝 Documentation improvements
- 🧪 Hardware compatibility testing
- 🎨 Web UI enhancements

---

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

**Important:** Even though MIT licensed, please use this responsibly and legally.

---

## 📚 Related Projects

Similar educational tools:
- [GANESH-ICMC/esp32-deauther](https://github.com/GANESH-ICMC/esp32-deauther)
- [SpacehuhnTech/esp8266_deauther](https://github.com/SpacehuhnTech/esp8266_deauther)
- [justcallmekoko/ESP32Marauder](https://github.com/justcallmekoko/ESP32Marauder)
- [Jeija/esp32free80211](https://github.com/Jeija/esp32free80211)

---

## 📞 Support & Contact

### Get Help
- 📖 [Full Documentation](doc/)
- 📚 [Attacks Theory Guide](doc/ATTACKS_THEORY.md)
- 🐛 [Report a Bug](https://github.com/Itszeeshanrajput/Drever/issues)
- 💡 [Request a Feature](https://github.com/Itszeeshanrajput/Drever/issues)
- 📧 **Email:** itszeeshanrajput@gmail.com
- 🔗 **GitHub:** [@Itszeeshanrajput](https://github.com/Itszeeshanrajput)

---

## 🙏 Acknowledgments

- **ESP-IDF** - Espressif's development framework
- **PlatformIO** - Embedded development platform
- **Academic Research** - Security researchers who inspired this project
- **Community** - All contributors and testers

---

<div align="center">

### ⭐ If you find this educational tool valuable, please star it!

**Made with ❤️ for security researchers and enthusiasts**

**Learn responsibly. Use ethically. Contribute meaningfully.**

[🔝 Back to Top](#-drever---professional-esp32-wi-fi-security-testing-tool)

</div>
