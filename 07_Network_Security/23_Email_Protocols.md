<br>

# Email Protocols
Email protocols define how email clients and servers communicate to send, receive, and manage emails. Several key protocols are used in email communication, including **SMTP, IMAP, and POP3**, each operating over specific ports and serving different purposes.

## SMTP (Simple Mail Transfer Protocol)
SMTP is used for **sending emails from a client to a server or between servers**. It’s **the standard protocol for email transmission** across the internet.
  - **Port 25**: Traditionally used for SMTP communication between mail servers. However, due to the risk of spam and abuse, many ISPs block this port for outgoing traffic from clients.
  - **Port 587**: Used for **SMTP submission**. Modern **email clients use this port for sending outgoing mail securely with authentication** (i.e., logging in to the server).
  - **Port 465**: Originally assigned to **SMTPS (SMTP over SSL) for encrypted email transmission**. Although deprecated, some servers still use this port for secure email communication with SSL.

## IMAP (Internet Message Access Protocol)
IMAP is used for **retrieving and managing emails from a mail server**. Unlike POP3, **IMAP allows users to access and manage emails directly on the server, keeping them synchronized across multiple devices**.
  - **Port 143**: The **default port for unencrypted IMAP communication**.
  - **Port 993**: Used for **IMAP over SSL/TLS**, providing encrypted communication between the client and the mail server.
IMAP is ideal for users who **access their email from multiple devices**, as it synchronizes email folders (like Inbox, Sent, etc.) across all devices in real time.

## POP3 (Post Office Protocol 3)
POP3 is another protocol used to **retrieve emails from a mail server**. Unlike IMAP, **POP3 downloads emails from the server to the local device and usually removes them from the server afterward**. This makes it less ideal for multi-device access but suitable **for users who want to store emails locally**.
  - **Port 110**: The **default port for unencrypted POP3 communication**.
  - **Port 995**: Used for **POP3 over SSL/TLS**, providing secure, encrypted retrieval of emails from the server.

## Overview of Protocols and Ports
  - SMTP: Used to send emails.
    - Port 25: Server-to-server communication (legacy).
    - Port 587: Secure submission of outgoing email with authentication.
    - Port 465: Deprecated, but still used for encrypted email submission.
  - IMAP: Used to retrieve and manage emails, keeping them synchronized across devices.
    - Port 143: Unencrypted.
    - Port 993: Secure, encrypted.
  - POP3: Used to retrieve emails, typically downloading and deleting them from the server.
    - Port 110: Unencrypted.
    - Port 995: Secure, encrypted.

## Security Considerations
In modern email communication, **encrypted versions of these protocols (like SMTPS, IMAPS, and POP3S) are widely used to ensure the confidentiality and security of email data**. Most email providers enforce the **use of TLS (Transport Layer Security)** to protect the connection between the client and server, particularly on **ports 587, 993, and 995**.  
<br>