# NETWORK SECURITY ANALYSIS REPORT

### SWYNEX Cyber Security Internship – Task 2

**Prepared by:** Fathima Ifadha
**Internship Role:** Cyber Security Intern
**Task:** Network Security Analysis
**Tool Used:** Wireshark
**Operating System:** Windows
**Environment:** Personal Laptop and Wi-Fi Network

---

## 1. Introduction

Network security is important for protecting computers and data from different security threats. Monitoring network traffic helps us understand how devices communicate with each other and identify possible security concerns.

For this task, I used Wireshark to capture and analyse network traffic from my own computer. I applied different display filters to study protocols such as DNS, TCP, UDP, TLS, QUIC and HTTP.

The main purpose of this task was to understand normal network communication and identify any unusual or potentially suspicious activities.

## 2. Objectives

The main objectives of this task were:

* To capture and analyse network traffic using Wireshark.
* To identify common network protocols.
* To understand source and destination IP addresses and port numbers.
* To observe TCP connections and network activities.
* To identify TCP retransmissions and duplicate ACKs.
* To understand the security differences between HTTP and HTTPS.
* To identify unusual or potentially suspicious network activity.

## 3. Tools Used

### Wireshark

Wireshark is a network protocol analyser that helps users capture and inspect network packets.

I used Wireshark to:

* Capture network traffic.
* Identify different network protocols.
* Apply display filters.
* Examine packet details.
* Observe possible network communication issues.

### Computer and Network

I used my own Windows laptop and Wi-Fi connection to capture network traffic.

## 4. Methodology

I followed these steps to complete the task:

1. Installed Wireshark on my laptop.
2. Selected the Wi-Fi network interface.
3. Started capturing network traffic.
4. Browsed websites to generate network traffic.
5. Applied different display filters to analyse specific protocols.
6. Examined packet details, IP addresses and port numbers.
7. Observed packet activities such as retransmissions and duplicate ACKs.
8. Captured screenshots of the analysis as evidence.

The following display filters were used:

| No. | Analysis            | Display Filter                             |
| --- | ------------------- | ------------------------------------------ |
| 1   | Traffic Overview    | No filter                                  |
| 2   | DNS Analysis        | `dns`                                      |
| 3   | TCP Analysis        | `tcp`                                      |
| 4   | UDP Analysis        | `udp`                                      |
| 5   | TLS Analysis        | `tls`                                      |
| 6   | QUIC Analysis       | `quic`                                     |
| 7   | TCP Retransmissions | `tcp.analysis.retransmission`              |
| 8   | TCP Duplicate ACKs  | `tcp.analysis.duplicate_ack`               |
| 9   | TCP SYN Traffic     | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |
| 10  | HTTP Analysis       | `http`                                     |

## 5. Network Traffic Analysis

### 5.1 Traffic Overview

**Figure 1 – General Network Traffic**

I first captured network traffic without applying any display filter.

The capture showed different protocols, including:

* TCP
* UDP
* TLS 1.2
* TLS 1.3
* IPv4
* IPv6

I also observed web communication using ports 80 and 443.

Some TCP retransmission packets and a connection reset were visible.

These activities can occur during normal network communication. No clear evidence of malicious activity was identified in this overview.

### 5.2 DNS Analysis

**Figure 2 – DNS Traffic**

I used the `dns` display filter to analyse DNS traffic.

DNS (Domain Name System) is used to translate website domain names into IP addresses.

The capture showed DNS queries and responses for domains such as:

* [www.wikipedia.org](http://www.wikipedia.org)
* upload.wikimedia.org
* en.wikipedia.org
* Other service-related domains.

I also observed DNS communication using UDP port 53.

The DNS traffic appeared to be related to website browsing and background services. No clear suspicious activity was identified.

### 5.3 TCP Analysis

**Figure 3 – TCP Traffic**

I used the `tcp` display filter to examine TCP communication.

The capture showed different TCP activities, such as:

* SYN packets
* ACK packets
* FIN, ACK packets
* TCP Keep-Alive
* TCP Retransmissions

TCP (Transmission Control Protocol) is used to establish and maintain reliable connections between devices.

I observed communication involving ports 80 and 443.

These activities are commonly seen during normal web browsing. No clear evidence of a cyberattack was identified.

### 5.4 UDP Analysis

**Figure 4 – UDP Traffic**

I used the `udp` display filter to analyse UDP packets.

The capture showed UDP traffic related to DNS and QUIC.

I observed:

* DNS queries and responses.
* Communication with Google-related services.
* QUIC packets using UDP port 443.

UDP (User Datagram Protocol) is used for communication that does not require the same connection-management features as TCP. QUIC also uses UDP to provide secure and efficient connections.

The observed traffic appeared to be normal network communication. No clear suspicious activity was identified.

### 5.5 TLS Analysis

**Figure 5 – TLS Traffic**

I used the `tls` display filter to examine TLS communication.

The capture showed TLS 1.2 and TLS 1.3 traffic.

Some important TLS activities were visible:

* Client Hello
* Server Hello
* Change Cipher Spec
* Application Data

TLS (Transport Layer Security) is used to protect data during communication between a client and a server.

I also observed a TCP retransmission in this filtered view.

The traffic appeared to be related to normal encrypted web communication. No clear evidence of malicious activity was identified.

### 5.6 QUIC Analysis

**Figure 6 – QUIC Traffic**

I used the `quic` display filter to analyse QUIC packets.

QUIC is a modern transport protocol that works over UDP. It is used by modern browsers and web applications.

The capture showed:

* Initial packets
* CRYPTO packets
* PADDING packets
* PING packets
* 0-RTT packets
* Protected Payload packets

I also observed QUIC communication using port 443.

These packets are part of QUIC connection establishment and data communication. No clear suspicious activity was identified.

### 5.7 TCP Retransmission Analysis

**Figure 7 – TCP Retransmissions**

I used the `tcp.analysis.retransmission` display filter to identify retransmitted TCP packets.

Several retransmission packets were visible in the capture.

TCP retransmission happens when a packet is sent again because the expected acknowledgement was not received within the required time.

Possible reasons include:

* Packet loss
* Network delay
* Network congestion
* Temporary connection problems

The retransmissions may be related to packet delivery or network performance issues. However, they do not directly indicate a cyberattack. Further investigation would be required to identify their exact cause.

No clear evidence of malicious activity was identified.

### 5.8 TCP Duplicate ACK Analysis

**Figure 8 – TCP Duplicate ACKs**

I used the `tcp.analysis.duplicate_ack` display filter to identify duplicate acknowledgement packets.

Duplicate ACKs can occur when data arrives out of order or when some data is missing.

The capture showed multiple TCP Duplicate ACK packets.

Possible reasons include:

* Packet loss
* Out-of-order packet delivery
* Network delay
* Network congestion

Duplicate ACKs are part of TCP's normal error-recovery process. Their presence alone does not confirm a network attack.

### 5.9 TCP SYN Traffic Analysis

**Figure 9 – TCP SYN Packets**

I used the following display filter:

`tcp.flags.syn == 1 && tcp.flags.ack == 0`

This filter shows TCP SYN packets used to initiate new connections.

TCP uses a three-way handshake:

1. **SYN** – The client requests a connection.
2. **SYN-ACK** – The server responds to the request.
3. **ACK** – The client confirms the connection.

I observed SYN packets targeting ports 80 and 443. Some SYN retransmissions were also visible.

These retransmissions may be related to network delays or packet loss.

A large number of SYN packets alone does not prove a SYN flood attack. No clear evidence of a SYN flood attack was identified in this capture.

### 5.10 HTTP Analysis

**Figure 10 – HTTP Traffic**

I used the `http` display filter to examine HTTP communication.

The capture showed a request to `neverssl.com`.

I observed:

* **Packet 518** – HTTP GET request.
* **Packet 523** – HTTP 200 OK response.

The communication used TCP port 80.

HTTP (Hypertext Transfer Protocol) does not encrypt communication. This means information sent through HTTP may be visible to others who can monitor the network traffic.

For this reason, HTTPS should be used when transmitting passwords or other sensitive information.

The observed request and response appeared to be normal website communication. However, the use of unencrypted HTTP is a security concern.

## 6. Findings and Evidence

Based on the 10 Wireshark screenshots, I identified the following findings:

| No. | Finding             | Observation                                                               |
| --- | ------------------- | ------------------------------------------------------------------------- |
| 1   | General Traffic     | TCP, UDP and web communication were observed.                             |
| 2   | DNS Traffic         | DNS queries and responses were observed.                                  |
| 3   | TCP Traffic         | Different TCP connection activities were observed.                        |
| 4   | UDP Traffic         | DNS and QUIC communication were observed.                                 |
| 5   | TLS Traffic         | TLS 1.2 and TLS 1.3 communication were observed.                          |
| 6   | QUIC Traffic        | QUIC connection and Protected Payload packets were observed.              |
| 7   | TCP Retransmissions | Multiple retransmission packets were observed.                            |
| 8   | TCP Duplicate ACKs  | Duplicate acknowledgement packets were observed.                          |
| 9   | TCP SYN Traffic     | TCP connection initiation packets and some retransmissions were observed. |
| 10  | HTTP Traffic        | An unencrypted HTTP GET request and HTTP 200 OK response were observed.   |

### Main Findings

**1. TCP Retransmissions and Duplicate ACKs**

These packets may be related to packet loss, network delays or out-of-order packet delivery. Further investigation would be needed to identify the exact cause.

**2. Unencrypted HTTP Communication**

The HTTP traffic to neverssl.com was not encrypted. This demonstrates why HTTPS is important when transmitting sensitive information.

**3. No Clear Malicious Activity**

Based on the traffic examined, I did not identify clear evidence of malware communication, a network attack or other malicious activity.

## 7. Potential Security Concerns

During the analysis, I identified the following potential security concerns:

* HTTP communication does not provide encryption.
* TCP retransmissions may indicate packet delivery problems.
* Duplicate ACKs may indicate missing or out-of-order packets.
* Network traffic should be monitored regularly to identify unusual communication.

These observations do not confirm that an attack occurred. Further investigation would be needed if unusual activity or network problems were reported.

## 8. Security Recommendations

Based on my analysis, I recommend the following security practices:

1. Use HTTPS instead of HTTP for websites and sensitive communication.
2. Avoid sending passwords or personal information through unencrypted connections.
3. Monitor network traffic regularly using tools such as Wireshark.
4. Check Wi-Fi signal strength and network performance if frequent retransmissions continue.
5. Keep the operating system, browser and security software updated.
6. Use a firewall to help protect the computer from unwanted network connections.
7. Investigate unusual network traffic when there is clear evidence of suspicious behaviour.

## 9. Conclusion

In this task, I used Wireshark to capture and analyse network traffic from my own computer.

I studied different protocols, including DNS, TCP, UDP, TLS, QUIC and HTTP. I also used display filters to identify TCP retransmissions, duplicate ACKs and SYN packets.

During the analysis, I observed network activities that may be related to packet loss or network delays. I also identified unencrypted HTTP communication, which can create security risks when sensitive information is transmitted.

No clear evidence of malicious activity was identified in the captured traffic.

This task helped me understand how network communication works and how Wireshark can be used to monitor and analyse network traffic. It also improved my basic knowledge of network protocols and common network security concerns.

---

**End of Report**
