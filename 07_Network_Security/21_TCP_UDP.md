<br>

# TCP/UDP
TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are **two fundamental transport layer protocols** used for transmitting data over the internet, each designed with different priorities and use cases.

## TCP (Transmission Control Protocol)
  - **Reliable, Connection-Oriented**: TCP establishes a connection between a client and server before data transmission starts. It guarantees the reliable delivery of data by ensuring that packets are received in the correct order and retransmitting lost packets if necessary.
  - **Flow Control and Congestion Control**: TCP throttles back (slows down) if packets are lost or the network becomes congested. It adjusts its transmission rate to ensure that data is delivered without overwhelming the network. This makes TCP well-suited for web traffic (HTTP/HTTPS) where reliable, ordered data transmission is crucial.
  - Use Cases
    - **Web Traffic (HTTP/HTTPS)**: Browsing the web requires reliable transmission of data to ensure pages load correctly and all content is delivered without corruption.
    - **Chat**: For text-based chat applications, TCP ensures messages are reliably sent and received in the correct order.

## UDP (User Datagram Protocol)
  - **Unreliable, Connectionless**: UDP, unlike TCP, does not establish a connection or guarantee that packets are received in order or even received at all. It is **faster** because it has lower overhead, but it sacrifices reliability for speed.
  - **No Flow Control**: UDP does not throttle back if packets are lost. It continues sending data regardless of packet loss, making it ideal for **real-time applications where speed is more important than reliability**.
  - Use Cases
    - **Streaming**: Streaming media (like video and audio) often uses UDP because it’s more important for the data to arrive quickly than to arrive perfectly. For instance, slight packet loss in video or audio might result in minor quality degradation, but delays (as would occur with TCP retransmissions) would be more disruptive.
    - **VoIP (Voice over IP)**: VoIP uses UDP because **real-time voice communication requires low latency**, and slight packet loss won’t noticeably affect the conversation, while retransmissions would cause delays.
    - **Traceroute**: Traceroute, a tool for diagnosing network paths, uses UDP by default. It sends packets to various routers on the path to determine how long it takes for the packets to reach each hop, helping to identify where network issues might occur.

## Impact on Network
  - TCP vs. UDP in Shared Networks: When TCP and UDP connections share the same network, **UDP’s lack of congestion control can impact the performance of TCP**. For example, if multiple devices are streaming (using UDP), this can saturate the network bandwidth. Since TCP throttles back in response to congestion, web traffic (which relies on TCP) can become slower as streaming (UDP) continues to consume network resources without slowing down.

## Summary
  - **TCP** ensures **reliable** communication and is used for tasks like web browsing and messaging, where data integrity is crucial.
  - **UDP** is **faster** but less reliable, making it ideal for real-time applications like streaming and VoIP, where speed is more important than perfect accuracy.
  - In a shared network, **UDP streaming can slow down TCP connections due to UDP’s lack of congestion control**.  
<br>