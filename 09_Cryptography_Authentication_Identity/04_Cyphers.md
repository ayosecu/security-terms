<br>

# Ciphers
Ciphers are **the algorithms used to encrypt and decrypt data**. They fall into two main categories: **block ciphers and stream ciphers**. The method by which block ciphers handle data is influenced by different modes of operation. Below is an overview of each type, how they differ, and details on AES-GCM, a popular mode of operation for block ciphers.

## 1. Block Ciphers vs. Stream Ciphers
  - Block Ciphers
    - Definition: Block ciphers **encrypt data in fixed-size chunks, called blocks**. For instance, AES (Advanced Encryption Standard) uses **128-bit blocks**.
    - How It Works: The cipher **splits the plaintext into blocks**, each of which is **processed independently** through the encryption algorithm.
    - Block Sizes: Common sizes include **64-bit (e.g., DES)** and **128-bit (e.g., AES)**.
    - Examples: **AES, DES, and Blowfish**.
    - Advantages: **Generally more secure and versatile**; well-suited for **encrypting data at rest**.
    - Disadvantages: **Requires padding** for data that doesn’t align with the block size, **potentially increasing data size**.
  - Stream Ciphers
    - Definition: Stream ciphers **encrypt data one bit or byte at a time**, making them ideal for applications where **data is transmitted in a continuous stream**.
    - How It Works: Stream ciphers **generate a pseudo-random keystream** based on the encryption key, which is then **XORed with the plaintext** to produce the ciphertext.
    - Examples: **RC4, ChaCha20, and Salsa20**.
    - Advantages: **Faster and more efficient for real-time data encryption**, particularly for smaller data sizes or continuous streams.
    - Disadvantages: Vulnerable to certain attacks if the keystream is reused (as seen in RC4), and **typically less secure than block ciphers for data at rest**.  
<br>

## 2. Block Cipher Modes of Operation

Block cipher modes of operation define how block ciphers handle data that exceeds the standard block size, allowing them to be used for larger data sets. Here are some popular modes.  

  - **ECB (Electronic Codebook)**
    - Definition: **Each block** of plaintext is **encrypted independently with the same key**.
    - Weakness: Identical plaintext blocks produce identical ciphertext blocks, making it vulnerable to pattern analysis.
    - Use: Rarely used in practice due to its vulnerability.
  - **CBC (Cipher Block Chaining)**
    - Definition: **Each plaintext block is XORed with the previous ciphertext block before encryption**, chaining blocks together.
    - Security: Offers stronger security than ECB but **requires an initialization vector (IV) for the first block**.
    - Use: Commonly used in data storage and file encryption, though vulnerable to padding oracle attacks if not implemented securely.
  - **CFB (Cipher Feedback) and OFB (Output Feedback)**
    - Definition: These modes **turn a block cipher into a stream cipher** by feeding parts of the ciphertext or key stream back into the cipher.
    - Security: Secure for certain applications but susceptible to specific attacks depending on the implementation.
    - Use: Typically used in applications requiring real-time encryption, like network encryption.
  - **CTR (Counter)**
    - Definition: **Each block is XORed with an encrypted counter value**, incremented for each block.
    - Security: Enables **parallel encryption** of blocks, making it **fast and efficient**.
    - Use: Suitable for applications **requiring high performance, such as disk encryption and VPNs**.
  - **GCM (Galois/Counter Mode)**
    - Definition: GCM is a mode of operation for block ciphers that **provides both encryption and authentication through Galois field multiplication**.
    - Security: Ensures both **data confidentiality and integrity**, making it popular in secure communications.
    - Use: **Common in TLS and other secure communication protocols** due to its combined encryption and authentication features.  
<br>

## 3. AES-GCM (Galois/Counter Mode)
  - Definition: AES-GCM (Advanced Encryption Standard with Galois/Counter Mode) is a mode of operation for the AES block cipher that combines encryption with authentication, providing both confidentiality and integrity.
  - How It Works
    - Counter Mode: AES-GCM **uses a counter** to generate a unique keystream for each block, which is XORed with the plaintext to produce the ciphertext.
    - Galois Authentication: It then performs Galois field multiplication to **authenticate** the ciphertext, ensuring **data integrity**.
  - Benefits
    - **Efficiency**: AES-GCM supports **parallel processing**, making it **highly efficient** and suitable for high-performance applications.
    - **Security**: The combination of **encryption and authentication** provides both confidentiality and integrity. If any part of the ciphertext is modified, GCM detects it, preventing tampering.
  - Use Cases: AES-GCM is widely used in secure communication protocols, including **TLS, IPsec, and secure file transfer**, due to its speed and combined security features.  
<br>

## 4. Comparison Table

| Feature | Block Cipher | Stream Cipher |
| ------- | ------------ | ------------- |
| Encryption Process | Encrypts data in fixed-size blocks | Encrypts data one bit/byte at a time |
| Typical Applications | Disk/file encryption, data at rest | Real-time data encryption (e.g., video streaming) |
| Common Algorithms | AES, DES, Blowfish | RC4, ChaCha20, Salsa20 |
| Padding Requirement | Yes (for data not aligning with block size) | No |
  
<br>

## 5. Summary
  - **Block Ciphers** encrypt data in **chunks** and use different modes of operation (ECB, CBC, CFB, OFB, CTR, and GCM) to handle larger data and add security features.
  - **Stream Ciphers** encrypt data **one bit or byte** at a time and are efficient for real-time encryption needs.
  - **AES-GCM** is a mode of AES that combines **encryption with authentication**, ensuring both **confidentiality and integrity**. It’s widely used in secure communication due to its efficiency and security.

Understanding the differences between block and stream ciphers, the available block cipher modes, and the added security of AES-GCM provides a comprehensive view of encryption options, allowing for informed choices in securing various types of data.  
<br>