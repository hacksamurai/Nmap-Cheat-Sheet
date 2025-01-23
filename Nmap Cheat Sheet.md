# Nmap Cheat Sheet

## What is Nmap?
**Nmap** (Network Mapper) is an open-source network scanning tool used for network discovery and security auditing. It helps identify hosts, services, and their configurations in a network. Penetration testers, system administrators, and security professionals commonly use it for vulnerability assessments.

---

## Nmap Cheat Sheet
Below is a detailed cheat sheet for Nmap, covering common commands, explanations, and examples.

### 1. **Basic Scans**

#### Scan a Single Host:
```bash
nmap <target>
```
**Example:**
```bash
nmap 192.168.1.1
```
Scans the specified IP address.

#### Scan Multiple Hosts:
```bash
nmap <target1> <target2> <target3>
```
**Example:**
```bash
nmap 192.168.1.1 192.168.1.2
```
Scans multiple targets at once.

#### Scan a Range of IPs:
```bash
nmap <start_ip>-<end_ip>
```
**Example:**
```bash
nmap 192.168.1.1-254
```
Scans all IPs in the range.

#### Scan an Entire Subnet:
```bash
nmap <subnet>
```
**Example:**
```bash
nmap 192.168.1.0/24
```
Scans all devices in the specified subnet.

---

### 2. **Port Scanning**

#### Scan Common Ports:
```bash
nmap <target>
```
By default, scans the top 1,000 most common ports.

#### Scan All Ports:
```bash
nmap -p-
```
**Example:**
```bash
nmap -p- 192.168.1.1
```
Scans all 65,535 TCP ports.

#### Scan Specific Ports:
```bash
nmap -p <port_number>
```
**Example:**
```bash
nmap -p 80,443 192.168.1.1
```
Scans port 80 and 443 on the target.

---

### 3. **Service and Version Detection**

#### Detect Running Services and Versions:
```bash
nmap -sV <target>
```
**Example:**
```bash
nmap -sV 192.168.1.1
```
Identifies services and versions running on open ports.

#### Aggressive Detection:
```bash
nmap -A <target>
```
**Example:**
```bash
nmap -A 192.168.1.1
```
Enables OS detection, version detection, script scanning, and traceroute.

---

### 4. **Host Discovery**

#### Ping Sweep:
```bash
nmap -sn <target>
```
**Example:**
```bash
nmap -sn 192.168.1.0/24
```
Finds active hosts without scanning ports.

#### Bypass Ping Discovery:
```bash
nmap -Pn <target>
```
**Example:**
```bash
nmap -Pn 192.168.1.1
```
Skips host discovery and scans all ports directly.

---

### 5. **Operating System Detection**

#### OS Detection:
```bash
nmap -O <target>
```
**Example:**
```bash
nmap -O 192.168.1.1
```
Attempts to determine the operating system of the target.

---

### 6. **Stealth Scans**

#### TCP SYN Scan (Default):
```bash
nmap -sS <target>
```
**Example:**
```bash
nmap -sS 192.168.1.1
```
Performs a stealthy half-open scan.

#### TCP Connect Scan:
```bash
nmap -sT <target>
```
**Example:**
```bash
nmap -sT 192.168.1.1
```
Performs a full TCP connection scan.

---

### 7. **Advanced Scans**

#### UDP Scan:
```bash
nmap -sU <target>
```
**Example:**
```bash
nmap -sU 192.168.1.1
```
Scans for open UDP ports.

#### Idle Scan:
```bash
nmap -Pn -sI <zombie_ip> <target>
```
**Example:**
```bash
nmap -Pn -sI 192.168.1.100 192.168.1.1
```
Uses a zombie host to perform a stealth scan.

#### Script Scan:
```bash
nmap --script <script_name> <target>
```
**Example:**
```bash
nmap --script vuln 192.168.1.1
```
Runs vulnerability detection scripts.

---

### 8. **Saving Scan Results**

#### Save Results to a File:
```bash
nmap -oN <file_name> <target>
```
**Example:**
```bash
nmap -oN results.txt 192.168.1.1
```
Saves results in a readable format.

#### Save Results in XML:
```bash
nmap -oX <file_name> <target>
```
**Example:**
```bash
nmap -oX results.xml 192.168.1.1
```
Saves results in XML format.

---

### 9. **Performance Optimization**

#### Increase Speed:
```bash
nmap -T<0-5> <target>
```
**Example:**
```bash
nmap -T4 192.168.1.1
```
-T4 speeds up the scan (lower numbers are slower, higher are faster).

---

### 10. **Combining Options**

#### Combine Flags for Detailed Scans:
```bash
nmap -A -T4 <target>
```
**Example:**
```bash
nmap -A -T4 192.168.1.1
```
Performs aggressive detection with optimized speed.

---

## Examples in Practice
1. **Scan all devices on a subnet for open ports:**
   ```bash
   nmap -p- 192.168.1.0/24
   ```

2. **Perform OS detection and service version detection:**
   ```bash
   nmap -A 192.168.1.1
   ```

3. **Scan for vulnerabilities using NSE scripts:**
   ```bash
   nmap --script vuln 192.168.1.1
   ```

---

## Tips for Ethical Use
- Always get permission before scanning networks.
- Use Nmap responsibly to avoid breaking laws or damaging systems.

---

Nmap is a powerful tool that, when used ethically, can enhance network security and provide valuable insights. Share this cheat sheet with your team or use it for personal reference!

