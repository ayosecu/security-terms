<br>

# Anti Forensics
In anti-forensics, **malware developers use various techniques to conceal malicious activities and make it harder for investigators to detect or analyze the malware**. Two primary methods include hiding techniques and timestomping.

## 1. How Malware Tries to Hide
Malware employs several methods to evade detection and avoid forensic scrutiny, making it harder for investigators to detect its presence.
  - **File Obfuscation and Renaming**: Malware often renames files to mimic legitimate ones or uses random, benign-looking names to blend in with system files.
  - Process Injection: Malware injects code into legitimate processes (e.g., svchost.exe or explorer.exe). This approach allows malicious code to hide within trusted processes, making it less likely to be flagged by security tools.
  - **Rootkits**: Rootkits **modify the operating system’s kernel or drivers, hiding processes, files, and network connections from the system itself**. They allow malware to operate invisibly by tampering with the system’s view of active files and processes.
  - **Code Obfuscation and Packing**: Malware frequently encrypts or “packs” its payload to obscure its code, making it challenging for signature-based antivirus tools to detect it. The code only decrypts or unpacks itself in memory, leaving minimal trace on disk.
  - **Registry Manipulation (on Windows)**: Malware may hide configuration settings or autostart entries in obscure registry locations, making detection harder. By doing this, it ensures it can persist across reboots without creating obvious startup files.
  - **Network Traffic Hiding**: Malware may use stealth techniques such as tunneling through common protocols (e.g., HTTPS) or using popular cloud services to avoid detection by security monitoring.  
<br>

## 2. Timestomping
  - Definition: Timestomping is **the manipulation of file timestamps—creation, last modification, and last access—to disguise when files were created or altered**.
  - Purpose: By modifying timestamps, attackers make it look as though files were created or modified during routine operations or on different dates, making it challenging to reconstruct timelines of the attacker’s activities.
  - Commonly Altered Timestamps
    - Creation Date: Often backdated to make a file look as though it was on the system long before the malware execution.
    - Modification and Access Dates: Altered to prevent the file from appearing as recently accessed or changed, especially in response to recent attacks.
  - Forensic Countermeasures
    - Forensic tools can sometimes identify inconsistencies in metadata or logs that reveal timestomping.
    - **File System Journals** (where available) record original timestamps and changes, helping investigators detect manipulation.
    - Analyzing related artifacts, such as log files or other time-stamped data, can also reveal unusual gaps or mismatches in the timeline.  
<br>

## 3. Summary
Malware employs hiding techniques such as **file renaming, rootkits, and process injection to evade detection**. **Timestomping is a common anti-forensics tactic**, altering file timestamps to conceal malicious activity within a system’s timeline. To counter these techniques, forensic investigators use specialized tools and methods, including **metadata verification, log analysis, and tracking inconsistencies, to detect and mitigate the effects of these anti-forensics tactics**.  
<br>