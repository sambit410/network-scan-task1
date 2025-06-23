# network-scan-task1
## Tools Used
- **Nmap** (version 7.95): For scanning the local network and identifying open ports.
- **Wireshark** (version 4.4.5) : For capturing and analyzing network traffic.
- **Operating System**: Windows 11.

## Steps Performed
1. **Installed Nmap**:
2. **Identified Local IP Range**:
   - Used `ipconfig` (Windows) to find my network range
3. **Ran TCP SYN Scan**:
   - Executed `nmap -sS 192.168.171.236` to scan a specific host.
   - Results showed open ports: 135 (MSRPC), 139 (NetBIOS-SSN), 445 (Microsoft-DS), 2869 (ICSLAP).
4. **Saved Scan Results**:
   - Exported as text.
5. **Attempted Wireshark Analysis**:
   - Installed Wireshark and selected the Wi-Fi interface.
   - Applied filter: `ip.addr == 192.168.171.236
   - Issue: No traffic captured, likely due to inactive services.
   - Troubleshooting:
     - Confirmed device connectivity with `ping 192.168.171.236`.
6. **Researched Services**:
   - Port 135: Microsoft RPC, used for Windows services.
   - Port 139: NetBIOS, legacy file sharing.
   - Port 445: SMB, modern file sharing.
   - Port 2869: ICSLAP/UPnP, likely for device discovery.
7. **Identified Security Risks**:
   - Port 135: Vulnerable to RPC exploits if unpatched.
   - Port 139: Unencrypted, risks enumeration.
   - Port 445: SMBv1 (if present) is exploitable (e.g., EternalBlue).
   - Port 2869: UPnP vulnerabilities if exposed.
   - Recommendations: Disable SMBv1, block ports 135/139/445 at firewall, verify port 2869 usage.


## Key Findings
- **Device**: `192.168.171.236` (likely a Windows machine).
- **Open Ports**:
  - 135 (MSRPC): Windows RPC, high-risk if exposed.
  - 139 (NetBIOS-SSN): Legacy, unencrypted, disable if unused.
  - 445 (Microsoft-DS): SMB, critical if running SMBv1.
  - 2869 (ICSLAP): Possible UPnP, needs investigation.
- **Risks**: SMB and NetBIOS ports pose significant vulnerabilities if unpatched or exposed to the internet.
