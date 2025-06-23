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
#### Command used to check if the tool already exisit:
```bash
apt list nmap
nmap -V
```
![already installed](https://github.com/Amish-C-K/Elevate-Labs--task1/blob/main/images/t1-1.png)

#### Download and Install nmap:

Visit the official Nmap website and download the installer package that’s appropriate for your operating system (Windows, macOS, or Linux).

Follow the installation instructions provided on the website. On Linux, you might install Nmap via your package manager (e.g., sudo apt-get install nmap on Debian/Ubuntu).

### 2. Local IP Range Discovery
#### Command used:
```bash
ifconfig
```
![local ip range](https://github.com/Amish-C-K/Elevate-Labs--task1/blob/main/images/t1-2.png)

>> IP: 192.168.5.134

>> Subnet: /24

>> Range: 192.168.5.0/24

### 3. TCP SYN Scan
#### Command used:
```bash
nmap -sS 192.168.5.0/24 -oN local_network_scan.txt
```
 we can save the result as html file by
 ```bash
nmap -sS 192.168.5.0/24 -oX local_network_scan.xml
```
Then converting it to html format
```bash
xsltproc Desktop/local_network_scan.xml -o scan_results.html
```
![nmap result](https://github.com/Amish-C-K/Elevate-Labs--task1/blob/main/images/t1-3.png)

### Result
| IP Address      | Status | MAC Address         | Open/Filtered Ports                      |
| --------------- | ------ | ------------------- | ---------------------------------------- |
| `192.168.5.1`   | Up     | 00:50:56\:C0:00:08  | 135, 139, 445, 902, 912, 2869 (filtered) |
| `192.168.5.2`   | Up     | 00:50:56\:EE:15\:CA | 53 (filtered)                            |
| `192.168.5.254` | Up     | 00:50:56\:F6:78:39  | All 1000 ports filtered                  |
| `192.168.5.134` | Self   | 00:0c:29:60\:ca:85  | All 1000 ports closed                    |

### 5. Wireshark Capture
Live packet capture on interface eth0 during the scan:

-- Captured ARP requests

-- TCP SYN packets to discovered hosts

![WireShark Captures](https://github.com/Amish-C-K/Elevate-Labs--task1/blob/main/images/t1-4.png)

### ⚠️Risk Analysis
| Port          | Service         | Risk                                                |
| ------------- | --------------- | --------------------------------------------------- |
| 135, 139, 445 | Windows RPC/SMB | Commonly exploited; risk of RCE or lateral movement |
| 53            | DNS             | Can be used for exfiltration or DNS attacks         |
| 2869          | UPnP            | May expose internal devices to external networks    |
| All Closed    | —               | Indicates host is hardened or behind a firewall     |


