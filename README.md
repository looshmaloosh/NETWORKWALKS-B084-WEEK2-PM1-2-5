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

I performed reconnaissance on the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon. Each tool was used to gather publicly available information about the domain and its infrastructure.

WHOIS identified the domain's registrar, registration dates, and name servers, while WhatWeb revealed website technologies including WordPress, Apache, Bootstrap, and jQuery. Nslookup resolved the domain to 192.232.216.135, and Curl retrieved HTTP headers, including the WordPress REST API endpoint /wp-json/.

Wafw00f identified ModSecurity (SpiderLabs) as the website's Web Application Firewall, while DNSRecon revealed several DNS records, including A, NS, MX, TXT/SPF, and SRV records.

These findings demonstrate how publicly available information can reveal details about a website's technologies, infrastructure, and security configuration.

## 4.2 Footprinting with Google Dorking
I performed Google Dorking using advanced search operators such as intitle: and inurl: to identify publicly indexed resources. The investigation focused on two categories: potentially exposed IP cameras and mathematics textbook directories.

Potentially Exposed IP Cameras
| No | Link | Relevant Dork |
|---|---|-------------------|
|1|http://144.129.11.86:88/cgi-bin/guestimage.html|"Camera Live Image" inurl:"guestimage.html"|
|2|http://208.105.211.147:9247/#view|intitle:”Live View / - AXIS|
|3|http://109.233.191.130:8080/|inurl:view/view.shtml|
|4|http://camp850.com/sub06/cam.php|intitle:”Live View / - AXIS 206M”|
|5|http://82.127.206.236/axis-cgi/mjpg/video.cgi?resolution=704x480&camera=1&dummy=1620387728755|inurl:indexFrame.shtml Axis|
|6|http://24.39.107.185:8000/view/viewer_index.shtml?id=4322|inurl:indexFrame.shtml Axis|
|7|http://212.41.248.38/indexFrame.shtml?newstyle=One&cam=4|intitle:Axis 2400 video server|
|8|http://31.132.43.196:81/indexFrame.shtml?newstyle=One&cam=4|intitle:"Live View / — AXIS" | inurl:view/view.shtml|
|9|http://80.152.138.183/ViewerFrame|inurl:ViewerFrame?Mode=Refresh|
|10|http://188.69.136.122/Pages/login.htm?0.8335860804563987|intitle:"NoVus IP camera" -com|

Mathematics Textbook Directories
| No | Link | Relevant Dork |
|---|---|-------------------|
|1|https://education.giakonda.org.uk/Maths/|intitle:"Index of /maths"|
|2|https://hub.melroseps.vic.edu.au/Maths/|intitle:"Index of /maths"|
|3|http://meteck.org/files/|intitle:"Index of /maths"|
|4|http://erewhon.superkuh.com/library/Math/|index of : "mathematics"|
|5|https://theswissbay.ch/pdf/Books/Mathematics/|inurl: intitle:"Mathematics"|
|6|https://theswissbay.ch/pdf/Gentoomen%20Library/Maths/|inurl: intitle:"Maths"|
|7|https://lira.epac.to/DOCS-TECH/Math/Engineering%20and%20Applied/|intitle:index.of "mathematics.pdf"|
|8|https://petermc.net/maths/olympiad/|inurl: intitle:"Maths"|
|9|http://library.cusat.ac.in/cat/2013/|inurl: intitle:"Maths"|
|10|https://www.williamle.com/staticstuff/Textbooks/	|inurl: intitle:"Maths"|

These results highlight how publicly accessible documents and directories can be located using search engines. While some resources may be intentionally public, others could reveal information that was not intended for public access.

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
