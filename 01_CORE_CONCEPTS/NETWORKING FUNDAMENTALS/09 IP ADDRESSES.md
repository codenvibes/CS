To communicate and maintain order, devices must be both identifying and identifiable on a network. What use is it if you don't know whom you're talking to at the end of the day?

Devices on a network are very similar to humans in the fact that we have two ways of being identified:
- Our Name
- Our Fingerprints

Now we can change our name through deed poll, but we can't, however, change our fingerprints. Every human has an individual set of fingerprints which means that even if they change their name, there is still an identity behind it. Devices have the same thing: two means of identification, with one being permeable. These are:
- An IP Address
- A Media Access Control (MAC) Address -- think of this as being similar to a serial number.

### What is an IP address?

> An **DEF-IP address** (Internet Protocol address) is a unique numerical identifier assigned to each device connected to a computer network that uses the Internet Protocol for communication.

This number is calculated through a technique known as IP addressing & subnetting. What's important to understand here is that IP addresses can change from device to device but cannot be active simultaneously more than once within the same network.

IP Addresses follow a set of standards known as protocols. These protocols are the backbone of networking and force many devices to communicate in the same language. However, we should recall that devices can be on both a private and public network. Depending on where they are will determine what type of IP address they have: a public or private IP address.

- A public address is used to identify the device on the Internet, 
- whereas a private address is used to identify a device amongst other devices. Take the table & screenshot below as an example. 

Here we have two devices on a private network:

| **Device Name** | **IP Address** | **IP Address Type** |
| --------------- | -------------- | ------------------- |
| DESKTOP-KJE57FD | 192.168.1.77   | Private             |
| DESKTOP-KJE57FD | 86.157.52.21   | Public              |
| CMNatic-PC      | 192.168.1.74   | Private             |
| CMNatic-PC      | 86.157.52.21   | Public              |

![https://assets.tryhackme.com/additional/cmn-aoc2020/day-8/1.png](https://assets.tryhackme.com/additional/cmn-aoc2020/day-8/1.png)

These two devices will be able to use their private IP addresses to communicate with each other. However, any data sent to the Internet from either of these devices will be identified by the same public IP address. Public IP addresses are given by your **I**nternet **S**ervice **P**rovider (or **ISP**) at a monthly fee (your bill!)

![https://assets.tryhackme.com/additional/cmn-aoc2020/day-8/2.png](https://assets.tryhackme.com/additional/cmn-aoc2020/day-8/2.png)

As more and more devices become connected, it is becoming increasingly harder to get a public address that isn't already in use. For example, Cisco, an industry giant in the world of networking, estimated that there would be approximately 50 billion devices connected on the Internet by the end of 2021. [(Cisco., 2021)](https://www.cisco.com/c/dam/en_us/about/ac79/docs/innov/IoT_IBSG_0411FINAL.pdf). Enter IP address versions. So far, we have only discussed one version of the Internet Protocol addressing scheme known as IPv4, which uses a numbering system of 2^32 IP addresses (4.29 billion) -- so you can see why there is such a shortage!

IPv6 is a new iteration of the Internet Protocol addressing scheme to help tackle this issue. Although it is seemingly more daunting, it boasts a few benefits:
- Supports up to 2^128 of IP addresses (340 trillion-plus), resolving the issues faced with IPv4
- More efficient due to new methodologies

The screenshot below compares both an IPv6 and IPv4 address.

![](https://assets.tryhackme.com/additional/networking-fundamentals/intro-to-networking/ipv6.png)


Each host in the network located can be identified by the so-called `Media Access Control` address (`MAC`). This would allow data exchange within this one network. If the remote host is located in another network, knowledge of the `MAC` address is not enough to establish a connection. Addressing on the Internet is done via the `IPv4` and/or `IPv6` address, which is made up of the `network address` and the `host address`.

It does not matter whether it is a smaller network, such as a home computer network, or the entire Internet. The IP address ensures the delivery of data to the correct receiver. We can imagine the representation of `MAC` and `IPv4` / `IPv6` addresses as follows:

- `IPv4` / `IPv6` - describes the unique postal address and district of the receiver's building.
- `MAC` - describes the exact floor and apartment of the receiver.

It is possible for a single IP address to address multiple receivers (broadcasting) or for a device to respond to multiple IP addresses. However, it must be ensured that each IP address is assigned only once within the network.

---

## IPv4 Structure

The most common method of assigning IP addresses is `IPv4`, which consists of a `32`-bit binary number combined into `4 bytes` consisting of `8`-bit groups (`octets`) ranging from `0-255`. These are converted into more easily readable decimal numbers, separated by dots and represented as dotted-decimal notation.

Thus an IPv4 address can look like this:

|**Notation**|**Presentation**|
|---|---|
|Binary|0111 1111.0000 0000.0000 0000.0000 0001|
|Decimal|127.0.0.1|

Each network interface (network cards, network printers, or routers) is assigned a unique IP address.

The `IPv4` format allows 4,294,967,296 unique addresses. The IP address is divided into a `host part` and a `network part`. The `router` assigns the `host part` of the IP address at home or by an administrator. The respective `network administrator` assigns the `network part`. On the Internet, this is `IANA`, which allocates and manages the unique IPs.

In the past, further classification took place here. The IP network blocks were divided into `classes A - E`. The different classes differed in the host and network shares' respective lengths.

|**`Class`**|**Network Address**|**First Address**|**Last Address**|**Subnetmask**|**CIDR**|**Subnets**|**IPs**|
|---|---|---|---|---|---|---|---|
|`A`|1.0.0.0|1.0.0.1|127.255.255.255|255.0.0.0|/8|127|16,777,214 + 2|
|`B`|128.0.0.0|128.0.0.1|191.255.255.255|255.255.0.0|/16|16,384|65,534 + 2|
|`C`|192.0.0.0|192.0.0.1|223.255.255.255|255.255.255.0|/24|2,097,152|254 + 2|
|`D`|224.0.0.0|224.0.0.1|239.255.255.255|Multicast|Multicast|Multicast|Multicast|
|`E`|240.0.0.0|240.0.0.1|255.255.255.255|reserved|reserved|reserved|reserved|

---

## Subnet Mask

A further separation of these classes into small networks is done with the help of `subnetting`. This separation is done using the `netmasks`, which is as long as an IPv4 address. As with classes, it describes which bit positions within the IP address act as `network part` or `host part`.

|**Class**|**Network Address**|**First Address**|**Last Address**|**`Subnetmask`**|**CIDR**|**Subnets**|**IPs**|
|---|---|---|---|---|---|---|---|
|**A**|1.0.0.0|1.0.0.1|127.255.255.255|`255.0.0.0`|/8|127|16,777,214 + 2|
|**B**|128.0.0.0|128.0.0.1|191.255.255.255|`255.255.0.0`|/16|16,384|65,534 + 2|
|**C**|192.0.0.0|192.0.0.1|223.255.255.255|`255.255.255.0`|/24|2,097,152|254 + 2|
|**D**|224.0.0.0|224.0.0.1|239.255.255.255|`Multicast`|Multicast|Multicast|Multicast|
|**E**|240.0.0.0|240.0.0.1|255.255.255.255|`reserved`|reserved|reserved|reserved|

---

## Network and Gateway Addresses

The `two` additional `IPs` added in the `IPs column` are reserved for the so-called `network address` and the `broadcast address`. Another important role plays the `default gateway`, which is the name for the IPv4 address of the `router` that couples networks and systems with different protocols and manages addresses and transmission methods. It is common for the `default gateway` to be assigned the first or last assignable IPv4 address in a subnet. This is not a technical requirement, but has become a de-facto standard in network environments of all sizes.

|**Class**|**Network Address**|**`First Address`**|**Last Address**|**Subnetmask**|**CIDR**|**Subnets**|**`IPs`**|
|---|---|---|---|---|---|---|---|
|A|1.0.0.0|`1.0.0.1`|126.255.255.255|255.0.0.0|/8|126|16,777,214 `+ 2`|
|B|128.0.0.0|`128.0.0.1`|191.255.255.255|255.255.0.0|/16|16,384|65,534 `+ 2`|
|C|192.0.0.0|`192.0.0.1`|223.255.255.255|255.255.255.0|/24|2,097,152|254 `+ 2`|
|D|224.0.0.0|`224.0.0.1`|239.255.255.255|Multicast|Multicast|Multicast|Multicast|
|E|240.0.0.0|`240.0.0.1`|255.255.255.255|reserved|reserved|reserved|reserved|

---

## Broadcast Address

The `broadcast` IP address's task is to connect all devices in a network with each other. `Broadcast` in a network is a message that is transmitted to all participants of a network and does not require any response. In this way, a host sends a data packet to all other participants of the network simultaneously and, in doing so, communicates its `IP address`, which the receivers can use to contact it. This is the `last IPv4` address that is used for the `broadcast`.

|**Class**|**Network Address**|**First Address**|**`Last Address`**|**Subnetmask**|**CIDR**|**Subnets**|**IPs**|
|---|---|---|---|---|---|---|---|
|A|1.0.0.0|1.0.0.1|`127.255.255.255`|255.0.0.0|/8|127|16,777,214 + 2|
|B|128.0.0.0|128.0.0.1|`191.255.255.255`|255.255.0.0|/16|16,384|65,534 + 2|
|C|192.0.0.0|192.0.0.1|`223.255.255.255`|255.255.255.0|/24|2,097,152|254 + 2|
|D|224.0.0.0|224.0.0.1|`239.255.255.255`|Multicast|Multicast|Multicast|Multicast|
|E|240.0.0.0|240.0.0.1|`255.255.255.255`|reserved|reserved|reserved|reserved|

---

## Binary system

The binary system is a number system that uses only two different states that are represented into two numbers (`0` and `1`) opposite to the decimal-system (0 to 9).

An IPv4 address is divided into 4 octets, as we have already seen. Each `octet` consists of `8 bits`. Each position of a bit in an octet has a specific decimal value. Let's take the following IPv4 address as an example:

- IPv4 Address: `192.168.10.39`

Here is an example of how the `first octet` looks like:

#### 1st Octet - Value: 192

  IP Addresses

```shell-session
Values:         128  64  32  16  8  4  2  1
Binary:           1   1   0   0  0  0  0  0
```

If we calculate the sum of all these values for each octet where the bit is set to `1`, we get the sum:

|**Octet**|**Values**|**Sum**|
|---|---|---|
|1st|128 + 64 + 0 + 0 + 0 + 0 + 0 + 0|= `192`|
|2nd|128 + 0 + 32 + 0 + 8 + 0 + 0 + 0|= `168`|
|3rd|0 + 0 + 0 + 0 + 8 + 0 + 2 + 0|= `10`|
|4th|0 + 0 + 32 + 0 + 0 + 4 + 2 + 1|= `39`|

The entire representation from binary to decimal would look like this:

#### IPv4 - Binary Notation

  IP Addresses

```shell-session
Octet:             1st         2nd         3rd         4th
Binary:         1100 0000 . 1010 1000 . 0000 1010 . 0010 0111
Decimal:           192    .    168    .     10    .     39
```

- IPv4 Address: `192.168.10.39`

This addition takes place for each octet, which results in a decimal representation of the `IPv4 address`. The subnet mask is calculated in the same way.

#### IPv4 - Decimal to Binary

  IP Addresses

```shell-session
Values:         128  64  32  16  8  4  2  1
Binary:           1   1   1   1  1  1  1  1
```

|**Octet**|**Values**|**Sum**|
|---|---|---|
|1st|128 + 64 + 32 + 16 + 8 + 4 + 2 + 1|= `255`|
|2nd|128 + 64 + 32 + 16 + 8 + 4 + 2 + 1|= `255`|
|3rd|128 + 64 + 32 + 16 + 8 + 4 + 2 + 1|= `255`|
|4th|0 + 0 + 0 + 0 + 0 + 0 + 0 + 0|= `0`|

#### Subnet Mask

  IP Addresses

```shell-session
Octet:             1st         2nd         3rd         4th
Binary:         1111 1111 . 1111 1111 . 1111 1111 . 0000 0000
Decimal:           255    .    255    .    255    .     0
```

- IPv4 Address: `192.168.10.39`
- Subnet mask: `255.255.255.0`

---

## CIDR

`Classless Inter-Domain Routing` (`CIDR`) is a method of representation and replaces the fixed assignment between IPv4 address and network classes (A, B, C, D, E). The division is based on the subnet mask or the so-called `CIDR suffix`, which allows the bitwise division of the IPv4 address space and thus into `subnets` of any size. The `CIDR suffix` indicates how many bits from the beginning of the IPv4 address belong to the network. It is a notation that represents the `subnet mask` by specifying the number of `1`-bits in the subnet mask.

Let us stick to the following IPv4 address and subnet mask as an example:

- IPv4 Address: `192.168.10.39`
- Subnet mask: `255.255.255.0`

Now the whole representation of the IPv4 address and the subnet mask would look like this:

- CIDR: `192.168.10.39/24`

The CIDR suffix is, therefore, the sum of all ones in the subnet mask.

  IP Addresses

```shell-session
Octet:             1st         2nd         3rd         4th
Binary:         1111 1111 . 1111 1111 . 1111 1111 . 0000 0000 (/24)
Decimal:           255    .    255    .    255    .     0
```


---

## References

https://academy.hackthebox.com/module/34/section/305