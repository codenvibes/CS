
The `TCP/IP` model is also a layered reference model, often referred to as the `Internet Protocol Suite`. The term `TCP/IP` stands for the two protocols `Transmission Control Protocol` (`TCP`) and `Internet Protocol` (`IP`). `IP` is located within the `network layer` (`Layer 3`) and `TCP` is located within the `transport layer` (`Layer 4`) of the `OSI` layer model.

|**Layer**|**Function**|
|---|---|
|`4.Application`|The Application Layer allows applications to access the other layers' services and defines the protocols applications use to exchange data.|
|`3.Transport`|The Transport Layer is responsible for providing (TCP) session and (UDP) datagram services for the Application Layer.|
|`2.Internet`|The Internet Layer is responsible for host addressing, packaging, and routing functions.|
|`1.Link`|The Link layer is responsible for placing the TCP/IP packets on the network medium and receiving corresponding packets from the network medium. TCP/IP is designed to work independently of the network access method, frame format, and medium.|

---

With `TCP/IP`, every application can transfer and exchange data over any network, and it does not matter where the receiver is located. `IP` ensures that the data packet reaches its destination, and `TCP` controls the data transfer and ensures the connection between data stream and application. The main difference between `TCP/IP` and `OSI` is the number of layers, some of which have been combined.

![Comparison of OSI and TCP/IP models: OSI has 7 layers including Application, Presentation, Session, Transport, Network, Data-Link, and Physical. TCP/IP has 4 layers: Application, Transport, Internet, and Link.](https://academy.hackthebox.com/storage/modules/34/redesigned/net_models4.png)

The most important tasks of `TCP/IP` are:

| **Task**               | **Protocol** | **Description**                                                                                                                                                                                                                                                                                                                        |
| ---------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Logical Addressing`   | `IP`         | Due to many hosts in different networks, there is a need to structure the network topology and logical addressing. Within TCP/IP, IP takes over the logical addressing of networks and nodes. Data packets only reach the network where they are supposed to be. The methods to do so are `network classes`, `subnetting`, and `CIDR`. |
| `Routing`              | `IP`         | For each data packet, the next node is determined in each node on the way from the sender to the receiver. This way, a data packet is routed to its receiver, even if its location is unknown to the sender.                                                                                                                           |
| `Error & Control Flow` | `TCP`        | The sender and receiver are frequently in touch with each other via a virtual connection. Therefore control messages are sent continuously to check if the connection is still established.                                                                                                                                            |
| `Application Support`  | `TCP`        | TCP and UDP ports form a software abstraction to distinguish specific applications and their communication links.                                                                                                                                                                                                                      |
| `Name Resolution`      | `DNS`        | DNS provides name resolution through Fully Qualified Domain Names (FQDN) in IP addresses, enabling us to reach the desired host with the specified name on the internet.                                                                                                                                                               |

---

## References

https://academy.hackthebox.com/module/34/section/303