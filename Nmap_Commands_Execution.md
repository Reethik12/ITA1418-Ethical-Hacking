# Nmap Commands Execution on macOS

**Tool:** Nmap 7.993  
**Operating System:** macOS (Apple Silicon M4)  
**Target Gateway:** `10.192.147.65`  
**Local IP Address:** `10.192.147.242`

---

## 1. Scan Common Ports

**Command:**
```bash
nmap 10.192.147.65
```

**Purpose:** Scans common TCP ports on the target host.

**Output:**
```text
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.05 seconds
```

**Result:** The host was not detected during the initial scan.

---

## 2. Discover Live Hosts

**Command:**
```bash
nmap -sn -T4 --max-retries 1 10.192.147.0/24
```

**Purpose:** Discovers live hosts on the specified subnet without scanning ports.

**Output:**
```text
Nmap scan report for 10.192.147.242
Host is up (0.00072s latency).
Nmap done: 256 IP addresses (1 host up) scanned in 41.94 seconds
```

**Result:** One live host was detected: the Mac itself.

---

## 3. Detect Service Versions

**Command:**
```bash
nmap -sV 10.192.147.65
```

**Purpose:** Attempts to identify services and their software versions on open ports.

**Output:**
```text
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.88 seconds
```

**Result:** No services were identified because the host was not detected during this scan.

---

## 4. Operating System Detection

**Command:**
```bash
nmap -O 10.192.147.65
```

**Purpose:** Attempts to identify the target's operating system using TCP/IP fingerprinting.

**Output:**
```text
TCP/IP fingerprinting (for OS scan) requires root privileges.
QUITTING!
```

**Result:** The scan did not execute because administrator privileges were required.

---

## 5. Scan Specific Ports

**Command:**
```bash
nmap -p 80,443 10.192.147.65
```

**Purpose:** Checks TCP ports 80 (HTTP) and 443 (HTTPS).

**Output:**
```text
PORT    STATE   SERVICE
80/tcp  closed  http
443/tcp closed  https
```

**Result:** Both ports were reported as closed during this scan.

---

## 6. Run Default NSE Scripts

**Command:**
```bash
nmap -sC 10.192.147.65
```

**Purpose:** Runs Nmap's default script set to gather additional information about the target.

**Output:**
```text
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.20 seconds
```

**Result:** The host was not detected during this scan, so the intended script scan did not proceed.

---

## 7. Skip Host Discovery

**Command:**
```bash
nmap -Pn 10.192.147.65
```

**Purpose:** Skips host discovery and treats the target as online.

**Output:**
```text
Nmap scan report for 10.192.147.65
Host is up (0.0059s latency).
Not shown: 999 filtered tcp ports (no-response)

PORT   STATE  SERVICE
53/tcp open   domain

Nmap done: 1 IP address (1 host up) scanned in 45.19 seconds
```

**Result:** The host was reachable, port 53 was reported open, and 999 other scanned TCP ports were filtered.

---

## 8. Save Scan Results to a File

**Command:**
```bash
nmap -oN scan.txt 10.192.147.65
```

**Purpose:** Saves scan results in normal text format to `scan.txt`.

**Output:**
```text
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.04 seconds
```

**Result:** The scan output was saved to a text file, but the target was not detected during this run.

To save the results on the Desktop instead, use:
```bash
nmap -oN ~/Desktop/scan.txt 10.192.147.65
```

---

## Conclusion

Nmap 7.993 was successfully installed and executed on macOS. The experiments demonstrated host discovery, service version detection, OS detection, specific-port scanning, default NSE scripts, skipping host discovery, and saving output to a text file.

The results varied depending on host discovery and network responses. The OS detection command required elevated privileges and did not complete.

**Note:** These results reflect the actual terminal output recorded during the experiments. Only scan systems and networks for which authorization has been granted.
