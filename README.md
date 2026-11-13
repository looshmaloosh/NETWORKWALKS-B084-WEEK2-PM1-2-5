<div align="center">
  
# NETWORKWALKS-B084-WEEK2-PM1-2-5
This project involves conducting reconnaissance on an authorized domain in a controlled environment. 
</div>

# 1. Liability Disclaimer

This report was prepared as part of the NetworkWalks Cybersecurity Internship Program (B084) for educational purposes. Written authorisation was obtained prior to conducting the security assessments.
All activities were performed within the authorised scope, focusing on footprinting, reconnaissance, and network scanning. No attempts were made to exploit vulnerabilities, disrupt services, or gain unauthorised access.
The findings are intended solely for educational and security awareness purposes and should not be interpreted as confirmed vulnerabilities unless supported by evidence.

# 2. Introduction

This report documents the activities completed during Week 2 of the NetworkWalks Cybersecurity Internship Program (B084). The exercises focused on footprinting and reconnaissance, alongside network scanning using Zenmap (W2-PM5).

The first activity involved gathering publicly available information about the networkwalks.com domain using various Kali Linux tools. This included WHOIS lookups, DNS enumeration, HTTP header analysis, and Web Application Firewall (WAF) detection. Google Dorking was also performed to identify publicly indexed resources, including potentially exposed IP cameras and mathematics textbook directories.

The second activity focused on identifying active devices within my local network using Zenmap on Windows. This involved performing ping scans to discover live hosts and examining their IP and available MAC addresses.

The purpose of these exercises was to develop practical skills in information gathering, network discovery, and understanding potential security risks. Each activity is supported by relevant commands, observations, screenshots, and explanations of the findings.

# 3. Tools Used

The table below lists each tool used in this report and each of their respective purpose.

| Tool | Purpose |
|---|---|
| Kali Linux / Windows | Operating systems used for reconnaissance activities           |
| WHOIS                | Find any domain registration details (owner, dates, name servers).   |
| whatweb              | Fingerprint any web technologies         |
| nslookup             | Resolve the domain name to its IP address using DNS.             |
| curl -I              | Read the HTTP response headers of the website.                   |
| wafw00f              | Detects any Web Application Firewall protecting a site or domain.     |
| dnsrecon             | Enumerate all DNS records (NS, MX, SPF, TXT, SRV).               |
| Zenmap (Nmap GUI)    | Scans the local subnet to find live hosts, IPs and MAC addresses. |
| Windows CMD          | Local IP and MAC address identification                          |

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance
(BUFFER)

## 4.2 Footprinting & Reconnaissance
(BUFFER)

## 4.3 Network Scanning with Zenmap

I used Zenmap on Windows to perform network discovery and identify active devices within my local network. The activity involved identifying network configurations, performing ping scans, and recording available IP and MAC addresses.

I first used the ipconfig command to identify my network interfaces. My home LAN address was 192.168.0.147, belonging to the 192.168.0.0/24 subnet. I also identified separate virtual networks associated with VirtualBox and VMware.

Ping Scan & Host Discovery

I performed a ping scan against the VirtualBox host-only network using:
nmap -sn 192.168.56.0/24

The scan covered 256 IP addresses and identified one active host (192.168.56.1), corresponding to my Windows ethernet adapter. The adapter's MAC address was recorded as 0A-00-27-00-00-3C.

I also scanned my home LAN (192.168.0.0/24), which identified multiple household devices, including smartphones and a PlayStation 5.

Network Topology

Following the scan, I used Zenmap's Topology feature to visualise the VirtualBox host-only network and exported the results as a PDF.

The topology displayed localhost and 192.168.56.1, consistent with the scan results.

Overall, this activity demonstrated how network scanning can identify active hosts, reveal network addressing information, and distinguish between physical and virtual network environments.

# 5. Risk Analysis / Impact

(BUFFER)

# 6. Recommendations
(BUFFER)


# 7. Conclusion/Lessons Learned

(BUFFER)

# 8. Evidences Collected
(BUFFER)

## 9. Challenges



## Author Information
Ali Fares

Cybersecurity Intern | Networkwalks B084

https://www.linkedin.com/in/ali-fares-86870733a/
## Project Information
Program Name: Cybersecurity at Networkwalks | Week: 02 | Project: Domain Fingerprinting & Reconnaissance
