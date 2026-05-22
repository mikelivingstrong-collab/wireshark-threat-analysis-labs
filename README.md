# wireshark-threat-analysis-labs

# Port Scan and Data Exfiltration Analysis

# Wireshark Threat Analysis Lab – Port Scanning & Data Exposure

## Objective
Analyze suspicious network traffic using Wireshark to identify reconnaissance activity, determine communicating ports, inspect TCP streams, and identify sensitive data transmitted across the network.

---

# Tools Used
- Wireshark
- TCP Stream Analysis
- Packet Inspection
- Display Filters
- Network Traffic Analysis

---

# Scenario Overview
A packet capture (.pcapng) file was analyzed to investigate suspicious traffic occurring between two hosts on an internal network.

The investigation focused on:
- Identifying source and destination hosts
- Determining which ports were communicating
- Detecting suspicious scanning activity
- Inspecting packet payloads for transmitted data
- Reconstructing TCP conversations

---

# Hosts Identified

## Suspicious Source Host
10.0.2.19

## Target Host
10.0.2.20

---

# Findings

## 1. Port Scanning Activity Detected
Analysis revealed that 10.0.2.19 initiated TCP SYN requests to multiple ports on 10.0.2.20, consistent with reconnaissance or port scanning behavior.

### Indicators
- Multiple SYN packets
- Rapid connection attempts
- Numerous destination ports targeted

### Wireshark Filter Used

```wireshark
tcp.flags.syn == 1
```

---

## Responsive/Open Ports Observed
- 21 (FTP)
- 135 (RPC)
- 139 (NetBIOS)
- 445 (SMB)

---

# Sensitive Data Exposure Identified

The TCP stream contained plaintext sensitive data fields including:

```text
id,first_name,last_name,email,gender,birthday,social_security,credit_card
```

Additional exposed data included:
- Names
- Email addresses
- Dates of birth
- Social Security numbers
- Credit card numbers
- Home addresses
- Phone numbers

---

# Analyst Assessment

The packet capture indicates suspicious reconnaissance activity originating from 10.0.2.19 targeting 10.0.2.20. Analysis identified TCP port scanning behavior followed by plaintext transmission of sensitive personally identifiable information (PII).

The investigation demonstrates:
- Packet inspection
- TCP stream reconstruction
- Port scan detection
- Network traffic analysis
- Identification of unsecured data transmission

---

# Skills Demonstrated
- Wireshark Analysis
- TCP/IP Fundamentals
- Packet Inspection
- Threat Detection
- Network Traffic Investigation
- TCP Stream Reconstruction
- Security Documentation

---

# Conclusion

This investigation demonstrated how Wireshark can be used to identify suspicious network reconnaissance activity, analyze TCP communications, reconstruct application streams, and detect exposure of sensitive data transmitted across a network.
---

# Investigation Evidence

## TCP Stream Analysis

![TCP Stream Analysis](Screenshot%202026-05-22%20102451.png)
