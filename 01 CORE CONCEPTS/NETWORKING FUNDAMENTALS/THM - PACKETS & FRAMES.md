#THM-PRE_SECURITY #2-NETWORK_FUNDAMENTALS

## 1. What are Packets and Frames

Packets and frames are small pieces of data that, when forming together, make a larger piece of information or message. However, they are two different things in the OSI model. 

A **packet** is a piece of data from Layer 3 (Network Layer) of the OSI model, containing information such as an IP header and payload. A **frame**, however, is used at Layer 2 (Data Link) of the OSI model, which, encapsulates the packet and adds additional information such as MAC addresses.
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

| Feature           | **Packet**                                                                                                                              | **Frame**                                                                                                                                                   |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OSI Layer**     | Network Layer (Layer 3)                                                                                                                 | Data Link Layer (Layer 2)                                                                                                                                   |
| **Definition**    | A packet is a formatted unit of data that carries **logical addressing information** (such as IP addresses) along with the actual data. | A frame is a structured unit of data that carries **physical addressing information** (such as MAC addresses) along with error detection bits.              |
| **Purpose**       | Used for routing data **from the source device to the destination device** across multiple networks.                                    | Used for reliable **delivery of packets between directly connected devices** (like from your laptop’s NIC to the switch, or from the switch to the router). |
| **Addressing**    | Uses **IP addresses** (logical addressing).                                                                                             | Uses **MAC addresses** (physical addressing).                                                                                                               |
| **Encapsulation** | Encapsulates a transport layer segment (e.g., TCP/UDP).                                                                                 | Encapsulates a packet.                                                                                                                                      |
| **Contents**      | Header (IP info) + Payload (data).                                                                                                      | Header (MAC info) + Encapsulated packet + Trailer (error detection, e.g., CRC).                                                                             |
| **Example**       | IP packet.                                                                                                                              | Ethernet frame, Wi-Fi frame.                                                                                                                                |
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※ ADDED NOTES ※※※※※※※※※※※※※※※※※※※※
<br>
<br>
</div>

You can think of this process as similar to mailing a letter through the post. The envelope is a frame, which, is used to move the contents (in this analogy, the packet) of the envelope to another place. Once the recepient opens the envelop (frame), they will know how to forward the letter (packet) itself.

This process is called encapsulation which we discussed in [room 3: the OSI model](https://tryhackme.com/room/osimodelzi). At this stage, it's safe to assume that when we are talking about anything IP addresses, we are talking about packets. When the encapsulating information is stripped away, we're talking about the frame itself.

Packets are an efficient way of communicating data across networked devices such as those explained in Task 1. Because this data is exchanged in small pieces, there is less chance of bottlenecking occurring across a network than large messages being sent at once.

For example, when loading an image from a website, this image is not sent to your computer as a whole, but rather small pieces where it is reconstructed on your computer. Take the image below as an illustration of this process. The cat's picture is divided into three packets, where it is reconstructed when it reaches the computer to form the final image.

Packets have different structures that are dependant upon the type of packet that is being sent. As we'll come on to discuss, networking is full of standards and protocols that act as a set of rules for how the packet is handled on a device. With billions of devices connected on the internet, things can quickly break down if there is no standardisation.

Let's continue with our example of the Internet Protocol. A packet using this protocol will have a set of headers that contain additional pieces of information to the data that is being sent across a network.

Some notable headers include:

| **Header**          | **Description**                                                                                                                                                         |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Time to Live        | This field sets an expiry timer for the packet to not clog up your network if it never manages to reach a host or escape!                                               |
| Checksum            | This field provides integrity checking for protocols such as TCP/IP. If any data is changed, this value will be different from what was expected and therefore corrupt. |
| Source Address      | The IP address of the device that the packet is being sent **from** so that data knows where to **return to**.                                                          |
| Destination Address | The device's IP address the packet is being sent to so that data knows where to travel next.                                                                            |
<div>
<br>
<br>
</div>

### Questions

##### What is the name for a piece of data when it **does have** IP addressing information?
##### What is the name for a piece of data when it **does not have** IP addressing information?
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 2. TCP/IP (The Three-Way Handshake)
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 3. Practical - Handshake
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 4. UDP/IP
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 5. Ports 101 (Practical)
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## 6. Continue Your Learning: Extending Your Network
<div align="center">
<br>
<br>
※※※※※※※※※※※※※※※※※※※※※※※※
<br>
</div>
<!-- PAGE BREAK -->
<div style="page-break-after: always;"></div>

## References

https://tryhackme.com/room/packetsframes