# 🔍 Task 1: Scan Your Local Network for Open Ports

## 📌 Objective
To discover open ports and active devices within the local network in order to understand the exposure of internal services and enhance basic network reconnaissance skills.

---

## 🧰 Tools Used
- **Nmap**: Network scanning and enumeration
- **Wireshark**: Packet sniffing and analysis
- **Kali Linux**: OS environment for testing

---

## 🧠 Methodology

### 1. Nmap Installation & Version Check
```bash
apt list nmap
nmap -V
```
![already installed](https://github.com.com/Amish-C-K/images/t1-1.png)

Download and Install:

Visit the official Nmap website and download the installer package that’s appropriate for your operating system (Windows, macOS, or Linux).

Follow the installation instructions provided on the website. On Linux, you might install Nmap via your package manager (e.g., sudo apt-get install nmap on Debian/Ubuntu).

### 2. Local IP Range Discovery
```bash
ifconfig
```
![local ip range](https://github.com.com/Amish-C-K/images/t1-2.png)
