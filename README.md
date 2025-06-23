# Local Network Scanning with Nmap

This guide provides step-by-step instructions for scanning a local network using **Nmap**, a powerful open-source network scanning tool. The focus is on performing a SYN scan to identify open ports on live hosts within a local network.

> **⚠️ Important Disclaimer**:  
> Network scanning can be intrusive and may violate network policies or laws if performed without explicit permission. Always obtain proper authorization from the network owner before scanning. This guide is intended for educational purposes only, and the author is not responsible for any misuse of the information provided.

## Prerequisites

- A computer running **Windows**, **Linux** (e.g., Kali Linux), or **macOS**.
- Administrative or root privileges to run Nmap scans.
- Basic familiarity with terminal/command prompt usage.

## Installation

1. **Download Nmap**:
   - Visit the official Nmap website: [https://nmap.org/download](https://nmap.org/download).
   - Choose the appropriate installer for your operating system (Windows, Linux, or macOS).
   - Follow the installation instructions provided on the website.

2. **Verify Installation**:
   - Open a terminal (Linux/macOS) or Command Prompt/PowerShell (Windows).
   - Run `nmap --version` to confirm Nmap is installed correctly.

## Steps to Scan Your Local Network

### 1. Find Your Local IP Address
   - **Windows**:
     ipconfig
   - **Linux/macOs**:
     ifconfig

### 2. Understand Basic Nmap Commands:
  - Below are common Nmap commands for network scanning:
  - 
 - Ping Scan: Discover live hosts.
   nmap -sn 192.168.1.0/24
 - Legacy Ping Scan: Alternative to -sn
   nmap -sP 192.168.1.0/24
 - SYN Scan: Identify open ports on live hosts.
   nmap -sS 192.168.1.0/24
 - ervice Version Detection: Detect services and versions running on open ports.
   nmap -sV 192.168.1.0/24
 - OS Detection: Identify operating systems of devices.
   nmap -O 192.168.1.0/24
 - Aggressive Scan: Comprehensive scan including OS detection, version detection, scripts, and traceroute.
   nmap -A 192.168.1.0/24
 - Skip Ping Scan: Scan hosts even if they don’t respond to ping (useful if ping is blocked).
   nmap -Cn 192.168.1.0/24
 - Fast Scan: Scan fewer ports with aggressive timing for faster results.
   nmap -T4 -F 192.168.1.0/24
   
### 3. Perform a SYN Scan:
   - we’ll use the SYN scan to identify open ports on live hosts in the 192.168.1.0/24 subnet.
     Command: nmap -sS 192.168.1.0/24
  
     Steps:
           Open a terminal or command prompt.
           Enter the above command, replacing 192.168.1.0/24 with your network’s subnet if different.
           Run the command as an administrator/root (e.g., use sudo on Linux/macOS).

     Alternatively, if using the Nmap GUI (Zenmap):
           Launch Zenmap.
           Enter the target subnet (e.g., 192.168.1.0/24) in the Target field.
           Select the Scan Profile (e.g., "Intense scan" or "Quick scan") or manually enter the command nmap -sS 192.168.1.0/24 in the Command field.
           Click Scan.
     
### 4. Analyze the Output
  After the scan completes, Nmap will display:
   - Live Hosts: IP addresses of devices responding on the network.
   - Open Ports: Ports that are open on each live host, along with the associated service (e.g., HTTP on port 80).
   - State: Whether ports are open, closed, or filtered.

Example Output:Nmap scan report for 192.168.1.100
Host is up (0.0023s latency).
PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
443/tcp  open   https

In this repository, sample scan results are provided in the results directory as HTML files for reference.

### Troubleshooting
Permission Denied: Ensure you run Nmap with administrative/root privileges (sudo on Linux/macOS).
No Hosts Found: Verify your subnet (e.g., 192.168.1.0/24) matches your network. Try a ping scan (-sn) first.
Firewall Blocking: Use -Pn to skip ping if hosts don’t respond to ICMP.
Slow Scans: Use -T4 for faster timing or -F to scan fewer ports.

```markdown
# Local Network Scanning with Nmap

This guide provides step-by-step instructions for scanning a local network using **Nmap**, a powerful open-source network scanning tool. The focus is on performing a SYN scan to identify open ports on live hosts within a local network.

> **⚠️ Important Disclaimer**:  
> Network scanning can be intrusive and may violate network policies or laws if performed without explicit permission. Always obtain proper authorization from the network owner before scanning. This guide is intended for educational purposes only, and the author is not responsible for any misuse of the information provided.

## Prerequisites

- A computer running **Windows**, **Linux** (e.g., Kali Linux), or **macOS**.
- Administrative or root privileges to run Nmap scans.
- Basic familiarity with terminal/command prompt usage.

## Installation

1. **Download Nmap**:
   - Visit the official Nmap website: [https://nmap.org/download](https://nmap.org/download).
   - Choose the appropriate installer for your operating system (Windows, Linux, or macOS).
   - Follow the installation instructions provided on the website.

2. **Verify Installation**:
   - Open a terminal (Linux/macOS) or Command Prompt/PowerShell (Windows).
   - Run `nmap --version` to confirm Nmap is installed correctly.

## Steps to Scan Your Local Network

### 1. Find Your Local IP Address
   - **Windows**:
     ```bash
     ipconfig
     ```
     Look for the `IPv4 Address` under your active network adapter (e.g., `192.168.1.100`).
   - **Linux/macOS**:
     ```bash
     ifconfig
     ```
     Alternatively, use:
     ```bash
     ip addr
     ```
     Identify the IP address (e.g., `192.168.1.100`) under the active network interface.

   **Note**: The subnet for your local network is typically `192.168.1.0/24` (check your subnet mask to confirm).

### 2. Understand Basic Nmap Commands
   Below are common Nmap commands for network scanning:
   - **Ping Scan**: Discover live hosts.
     ```bash
     nmap -sn 192.168.1.0/24
     ```
   - **Legacy Ping Scan**: Alternative to `-sn`.
     ```bash
     nmap -sP 192.168.1.0/24
     ```
   - **SYN Scan**: Identify open ports on live hosts.
     ```bash
     nmap -sS 192.168.1.0/24
     ```
   - **Service Version Detection**: Detect services and versions running on open ports.
     ```bash
     nmap -sV 192.168.1.0/24
     ```
   - **OS Detection**: Identify operating systems of devices.
     ```bash
     nmap -O 192.168.1.0/24
     ```
   - **Aggressive Scan**: Comprehensive scan including OS detection, version detection, scripts, and traceroute.
     ```bash
     nmap -A 192.168.1.0/24
     ```
   - **Skip Ping Scan**: Scan hosts even if they don’t respond to ping (useful if ping is blocked).
     ```bash
     nmap -Cn 192.168.1.0/24
     ```
   - **Fast Scan**: Scan fewer ports with aggressive timing for faster results.
     ```bash
     nmap -T4 -F 192.168.1.0/24
     ```

### 3. Perform a SYN Scan
   For this guide, we’ll use the **SYN scan** to identify open ports on live hosts in the `192.168.1.0/24` subnet.

   **Command**:
   ```bash
   nmap -sS 192.168.1.0/24
   ```

   **Steps**:
   1. Open a terminal or command prompt.
   2. Enter the above command, replacing `192.168.1.0/24` with your network’s subnet if different.
   3. Run the command as an administrator/root (e.g., use `sudo` on Linux/macOS).

   Alternatively, if using the **Nmap GUI (Zenmap)**:
   1. Launch Zenmap.
   2. Enter the target subnet (e.g., `192.168.1.0/24`) in the **Target** field.
   3. Select the **Scan Profile** (e.g., "Intense scan" or "Quick scan") or manually enter the command `nmap -sS 192.168.1.0/24` in the **Command** field.
   4. Click **Scan**.

### 4. Analyze the Output
   After the scan completes, Nmap will display:
   - **Live Hosts**: IP addresses of devices responding on the network.
   - **Open Ports**: Ports that are open on each live host, along with the associated service (e.g., HTTP on port 80).
   - **State**: Whether ports are `open`, `closed`, or `filtered`.

   **Example Output**:
   ```
   Nmap scan report for 192.168.1.100
   Host is up (0.0023s latency).
   PORT     STATE  SERVICE
   22/tcp   open   ssh
   80/tcp   open   http
   443/tcp  open   https
   ```

   In this repository, sample scan results are provided in the `results` directory as HTML files for reference.

## Repository Contents
- `README.md`: This guide.
- `results/`: Sample Nmap scan output files in HTML format.

## Troubleshooting
- **Permission Denied**: Ensure you run Nmap with administrative/root privileges (`sudo` on Linux/macOS).
- **No Hosts Found**: Verify your subnet (e.g., `192.168.1.0/24`) matches your network. Try a ping scan (`-sn`) first.
- **Firewall Blocking**: Use `-Pn` to skip ping if hosts don’t respond to ICMP.
- **Slow Scans**: Use `-T4` for faster timing or `-F` to scan fewer ports.

## Additional Resources
- [Nmap Official Documentation](https://nmap.org/docs.html)
- [Nmap Cheat Sheet](https://www.stationx.net/nmap-cheat-sheet/)
- [Network Security Basics](https://www.cisa.gov/topics/cybersecurity-best-practices)

## Contributing
Contributions are welcome! Please submit a pull request or open an issue to suggest improvements or report errors.
