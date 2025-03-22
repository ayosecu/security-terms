<br>

# Intrusion Detection System (IDS)
An IDS is designed to monitor a network or system for **abnormal activities and potential intrusions or attacks**. There are two main methods of intrusion detection: **Signature-Based** Detection and **Behavior-Based** Detection.

  - Signature-Based IDS
    - Signature-based detection identifies **known attack patterns**. A signature refers to a rule or pattern that defines the unique characteristics of an attack, which is stored in a database. The IDS checks whether events or traffic in the system **match any known signatures**.
    - Advantages: It can detect known attacks **quickly and accurately**.
    - Disadvantages: It **struggles to detect new or zero-day attacks**. If an attacker **can bypass** the signature, the system won’t detect the threat.
    - Examples: **Snort and Suricata** are well-known signature-based IDS tools that analyze network traffic based on **predefined patterns**.
  - Behavior-Based IDS
    - Behavior-based detection **learns what normal system behavior** looks like and **detects deviations from these norms**. It monitors real-time activity on the network or system and flags any **anomalies as potential threats**.
    - Advantages: It can **detect new types of attacks** by recognizing abnormal behavior patterns. It’s also useful for **detecting zero-day attacks**.
    - Disadvantages: It may generate **many false positives** since not all abnormal behavior is malicious.

## 1. Snort/Suricata/YARA Rule Writing
For IDS tools like Snort and Suricata, creating detection rules is essential for defining specific patterns of behavior or signatures to identify threats.

  - Snort/Suricata Rule Writing
    - Snort and Suricata are signature-based network IDS tools. Rules written for these systems define patterns to be detected in network packets, such as **certain strings, ports, or protocols**.
    - Example rule  
    
```
alert tcp any any -> 192.168.1.100 80 (msg:"Possible HTTP Attack"; content:"/cmd.exe"; sid:1001;)
```  

This rule triggers an alert if any packet directed to IP 192.168.1.100 on port 80 contains the string /cmd.exe, which is common in certain attack types.
Writing effective rules **requires a solid understanding of attack scenarios** and how to define the signatures of these attacks.

  - YARA Rule Writing
    - YARA is a tool designed to identify malware by writing rules that look for **specific patterns in files, processes, or memory**. These rules can include strings, byte patterns, and other conditions.
    - Example rule  

```
rule MyMalware
{
  strings:
    $a = "malicious_string"
    $b = { 6A 40 68 00 30 00 00 6A 14 8D 91 }

  condition:
    $a or $b
}
```  

This rule detects a file or memory pattern containing the defined string or byte sequence, identifying potential malware.  
<br>

## 2. Host-based Intrusion Detection System (HIDS)
A HIDS focuses on monitoring and analyzing the activities **on individual hosts** (like servers or PCs), unlike network-based IDS that monitors network traffic. HIDS typically **examines log files, checks file integrity, and monitors system calls** to detect intrusions.

  - OSSEC
    - **OSSEC is an open-source HIDS** that performs real-time log analysis, file integrity monitoring, rootkit detection, and alerting. It tracks changes in critical files and directories, ensuring their integrity.
    - Key Features
      - Log Analysis: OSSEC analyzes logs from various operating systems to detect attacks.
      - File Integrity Monitoring: It tracks changes to important files, alerting if unauthorized modifications occur.
      - Rootkit Detection: It checks for modifications or tampering with core system files and processes.

HIDS provides detailed monitoring **at the host level** and can be paired with network-based IDS for a more comprehensive security strategy.  
<br>