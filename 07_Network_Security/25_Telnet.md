<br>

# Telnet
Telnet is **a network protocol that allows for remote communication with hosts over the internet or a local network**. It was one of the first protocols developed for remote access to systems and is commonly used to remotely control devices such as servers, network equipment, or other computers.

## 1. Key Features of Telnet
  - **Remote Communication**: Telnet enables a user to log into another device on the network and control it as if they were physically present at the device. It allows users to execute commands, configure systems, or troubleshoot problems remotely.
  - **Plaintext Communication**: One of the major drawbacks of Telnet is that it transmits data, including sensitive information like usernames and passwords, in plaintext (unencrypted). This makes Telnet insecure on public or unsecured networks, as it can easily be intercepted by attackers.  
<br>

## 2. Port 23
  - **Port 23** is the default port used by Telnet for communication. When a user initiates a Telnet session, it typically connects to the target host on port 23. This port is standard for Telnet services, but since Telnet transmits data in plaintext, using port 23 on unsecured networks is considered risky.  
<br>

## 3. Secure Alternatives and Port 992
  - Due to the inherent insecurity of Telnet, **SSH (Secure Shell) has largely replaced it for remote access to systems** because SSH provides encrypted communication.
  - **Port 992 is used for Telnet over SSL/TLS** (often referred to as TelnetS), which adds encryption to Telnet, making it more secure. However, this is not as widely adopted as SSH.  
<br>

## 4. Telnet Process
1. **Client Request**: The Telnet client initiates a connection to a server (typically on port 23).
2. **Remote Access**: Once the connection is established, the user can communicate with the remote system, run commands, configure settings, and receive output, as if they were working directly on the host machine.
3. **Plaintext Transmission**: Without encryption, all communication (including sensitive information) is visible to anyone who intercepts the data.  
<br>

## 5. Summary
  - **Telnet** allows for remote communication with hosts but is insecure because it transmits data in plaintext.
  - **Port 23** is the default port for Telnet communication.
  - **Port 992 is used for Telnet over SSL/TLS**, offering encryption, but SSH is a more secure and modern alternative.  
<br>