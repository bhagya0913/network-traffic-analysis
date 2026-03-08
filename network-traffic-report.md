# Network Traffic Analysis Investigation

## Executive Summary

This project presents a network traffic investigation performed in a controlled cybersecurity laboratory environment. The purpose of this investigation was to capture network traffic and analyze it in order to detect suspicious activity such as network scanning or unauthorized connection attempts.

Network packets were captured using Wireshark while performing a network scan from a Kali Linux machine targeting a Metasploitable system. Analysis of the captured traffic revealed multiple TCP SYN packets sent to several service ports, which is a common indicator of port scanning activity.

This project demonstrates how packet analysis can be used to identify reconnaissance activities that often occur during the early stages of cyber attacks.

## Objective

The objective of this project was to simulate the workflow of a security analyst investigating network traffic to identify suspicious patterns and potential attack behavior.

## Tools Used

The following cybersecurity tools were used during the investigation:

- Kali Linux
- Wireshark
- Nmap
- Metasploitable
- Oracle VM VirtualBox

These tools allowed the creation of a virtual penetration testing lab environment for capturing and analyzing network traffic.

## Lab Environment

The investigation was conducted in a controlled virtual lab environment.

Attacker Machine  
Kali Linux

Target Machine  
Metasploitable

Virtualization Platform  
Oracle VM VirtualBox

The Kali Linux machine was used to generate network traffic while the Metasploitable system acted as the vulnerable target.

## Traffic Capture

Network traffic was captured using Wireshark on the Kali Linux system. The capture was performed on the active network interface (eth0).

During the capture process, a network scan was performed against the Metasploitable machine using Nmap in order to generate suspicious traffic.

Scanning command used:

nmap -sS 192.168.1.3

This command performs a TCP SYN scan which is commonly used to discover open ports on a target system.

## Packet Analysis

After capturing network traffic, Wireshark filters were used to analyze suspicious packets.

The following display filter was applied:

tcp.flags.syn == 1 && tcp.flags.ack == 0

This filter displays TCP packets that initiate new connection attempts. These packets are commonly seen during port scanning activities.

The filtered results revealed multiple SYN packets sent from the attacker machine to various ports on the target system.

## Findings

### TCP SYN Port Scanning Activity

Analysis of the captured traffic revealed multiple TCP SYN packets originating from the Kali Linux machine and targeting several ports on the Metasploitable system.

This pattern is consistent with a TCP SYN port scanning attack used to identify open services on a network host.

### Targeted Service Ports

The captured scan activity targeted several common service ports including:

Port 21 – FTP  
Port 22 – SSH  
Port 23 – Telnet  
Port 80 – HTTP

These services are commonly probed by attackers during reconnaissance to identify potential vulnerabilities.

### Traffic Pattern Observed

The packet capture showed a sequence where a single source IP attempted connections to multiple destination ports within a short period of time. This behavior is typical of automated scanning tools such as Nmap.

## Security Impact

Port scanning itself does not compromise a system, but it allows attackers to discover open services and potential vulnerabilities.

Once attackers identify exposed services, they may attempt to exploit vulnerabilities in those services to gain unauthorized access to the system.

Therefore, detecting port scanning activity is an important step in early threat detection.

## Mitigation Recommendations

Organizations can implement the following security measures to reduce the risk of reconnaissance attacks:

- Configure firewall rules to block unauthorized scanning attempts
- Deploy intrusion detection or intrusion prevention systems
- Monitor network traffic for abnormal connection patterns
- Disable unnecessary network services
- Regularly update systems and apply security patches

Network monitoring and log analysis can help security teams detect suspicious activity early.

## Conclusion

The network traffic investigation successfully identified reconnaissance activity in the form of a TCP SYN port scan targeting the Metasploitable system. Packet analysis using Wireshark confirmed multiple connection attempts across several service ports, indicating the use of a network scanning tool.

This project demonstrates how packet capture and traffic analysis techniques can be used to detect suspicious behavior and support cybersecurity incident investigations.

## Evidence

Screenshots of the packet capture and filtered analysis results are included in the screenshots directory of this project.