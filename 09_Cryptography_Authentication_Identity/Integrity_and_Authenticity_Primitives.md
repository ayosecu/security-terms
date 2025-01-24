## Integrity and Authenticity Primitives
Integrity and authenticity are essential aspects of data security, ensuring that **data hasn’t been altered** and **verifying its origin**. Several cryptographic primitives serve this purpose, including **hashing functions, Message Authentication Codes (MACs), and Keyed-hash MACs (HMACs)**. Each has a distinct role in protecting data integrity and authenticity, and each has specific applications.

## 1. Hashing Functions
  - Definition: Hashing functions are algorithms that take an input (or “message”) and **return a fixed-size string of bytes**. The output, known as the **hash or digest**, is **unique to the input**.
  - Purpose: Hash functions **provide a unique identifier or fingerprint for data**, making them useful for **ensuring data integrity**. **A small change in the input will produce a drastically different hash**, which allows detection of any alteration in the data.
  - Applications
    - **Integrity Checking**: Used to verify that data has not been altered, especially useful in file integrity checks and fingerprinting malware samples.
    - **Digital Signatures**: Hashes are commonly used in digital signatures, as they provide a compact, unique representation of data.
    - **Identifiers**: Hash functions help in creating unique identifiers for files, messages, and other data elements.
  - Examples
    - **MD5**: A commonly used hash function, though it is **no longer considered secure** for cryptographic purposes **due to vulnerabilities to collision attacks**.
    - **SHA-1**: Also **deprecated** for cryptographic use, but **still used for certain non-sensitive purposes**.
    - **BLAKE**: A modern hash function designed for security and efficiency, often used in digital signatures and as an alternative to SHA-2.
  - Security Implications: Hashing functions are crucial for ensuring data integrity but **do not provide authentication** by themselves. **Collisions** (where two inputs produce the same hash) are a weakness in hash functions like MD5 and SHA-1.

## 2. Message Authentication Codes (MACs)
  - Definition: A Message Authentication Code (MAC) is **a small piece of information attached to a message to verify its integrity and authenticity**. MACs **use a secret key to generate the code**, which means only those with the key can verify or generate a valid MAC.
  - Purpose: MACs ensure that a message was created by someone with knowledge of the secret key and that it has not been tampered with.
  - Applications
    - **Data Integrity in Communication**: MACs are widely used in secure protocols to verify the integrity of messages during transmission.
    - **Authenticity Verification**: Used in scenarios where it’s important to confirm that data originated from a trusted source.
  - Types of MACs
    - **CBC-MAC**: A MAC **based on block cipher encryption in Cipher Block Chaining (CBC) mode**, commonly **used for short, fixed-length messages**.
    - CMAC: A variant of CBC-MAC that is more secure and resistant to certain attacks.
  - Security Implications: MACs **provide both integrity and authenticity**, as they rely on a **shared secret key**. However, they **do not offer non-repudiation** (i.e., proof of origin) without an additional authentication mechanism.

## 3. Keyed-Hash Message Authentication Code (HMAC)
  - Definition: HMAC is a type of MAC that **combines a hash function with a secret key to generate a message authentication code**. It is designed to work securely with existing hash functions.
  - Purpose: HMAC ensures both **data integrity and authenticity**, as only someone with the secret key can generate or verify the HMAC.
  - Applications
    - **Securing Communications**: Used extensively in secure protocols like **TLS, SSL, and IPsec** for message verification.
    - **Data Integrity Verification**: HMACs provide assurance that data has not been modified, making them useful for sensitive data storage and transmission.
  - Example Algorithms
    - **HMAC-SHA256**: Uses SHA-256 as the underlying hash function, providing a secure MAC.
    - HMAC-BLAKE2: Uses BLAKE2 as the underlying hash function, known for both security and efficiency.
  - How It Works
    - HMAC first combines the message and key using the hash function’s internal algorithm. This process is repeated with a second key, ensuring the result is strongly tied to both the data and key.
  - Security Implications: HMACs provide high levels of security due to the cryptographic strength of the underlying hash function and the secret key. They are resistant to known attacks and widely used for both data integrity and authenticity.

## Comparison Table

| Primitive | Integrity | Authenticity | Key Requirement | Use Case Examples | Common Algorithms |
| --------- | --------- | ------------ | --------------- | ----------------- | ----------------- |
| Hashing | Yes | No | No | Integrity checks, malware fingerprinting, unique identifiers | MD5, SHA-1, BLAKE |
| MAC | Yes | Yes | Yes (shared) | Secure data transmission, message authentication | CBC-MAC, CMAC |
| HMAC | Yes | Yes | Yes (shared) | Securing protocols (TLS, SSL), sensitive data verification | HMAC-SHA256, HMAC-BLAKE |

## Summary
  - **Hashing Functions**: Provide a unique identifier for data, useful for integrity checking and fingerprinting but do not offer authenticity. Commonly used hashing algorithms include MD5, SHA-1, and BLAKE.
  - **Message Authentication Codes (MACs)**: Offer both integrity and authenticity using a shared secret key, ensuring the data’s origin and unaltered state. They’re commonly used in secure communications.
  - **Keyed-Hash MACs (HMACs)**: Provide strong integrity and authenticity through a combination of hashing and secret keys, enhancing security. HMACs are widely used in secure protocols for data integrity and verification.

These primitives are fundamental to cryptography, each contributing to data security by ensuring integrity and authenticity. They are commonly applied in secure communications, data integrity checks, and protocol-level security, offering layered defenses against tampering and unauthorized access.