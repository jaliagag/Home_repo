# IP

192.168.101.1/24

What's after the "/" is the subnet _MASK_. A mask of 24 gives us 255.255.255.0. _THE FIRST 24 BITS ARE TURNED **ON** AND THEY ARE **NETWORK BITS**_ 

We have:

- Host (or node) addresses: single entity on an entity (my phone number)
- Network address: a group of hosts (local area code)

Each section in an IPv4 is called an octet or _byte_ they match to 8 bits. Every bit has a corresponding decimal value, ranging from 1 to 128.

Example address: 208.79.115.3

- 208: 11010000
- 79: 01001111
- 115: 01110011
- 3: 00000011

## RFC 1918

Class A --> large number of nodes (16 million nodes). **1 - 126**.H.H.H. The first octet is for the network portion and the last 3 are the host part of the address.
Class B --> for medium size hosts. **128-191**.N.H.H. First two octets used for the network portion of the address and the last two for the host.
Class C --> **192-223** .N.N.H the first three octets are used for the network part of the address and the last octet is for the host portion.

###

For every IP address there is always a **_subnet mask_**. A Subnet mask identifies which bits in the IP address are network bits and which bits are host bits.

In order for two nodes to communicate on a network, the network bits of their IP address must match or a router must be placed between them.

Subnet address extends the network bit of the IP address to include some portion of the Host section of the octet.

## Networking for dummies

An IP address is a number that uniquely identifies every host on an IP network.
IP stands for Internet Protocol, and its primary purpose is to enable communications between networks. As a result, a 32-bit IP address actually consists of two parts:
- The network ID (or network address): Identifies the network on which a host computer can be found
- The host ID (or host address): Identifies a specific device on the network indicated by the network ID

The Class C addressing scheme, which uses eight bits for the host ID, allows only 254 hosts — not the 256 hosts you’d expect. **The host ID can’t be 0 (the host ID is all zeros) because that address is always reserved to represent the network itself**. And the host ID can’t be 255 (the host ID is all ones) because that host ID is reserved for use as a broadcast request that’s intended for all hosts on the network.

### Subnetting

Subnetting provides a more flexible way to designate which portion of an IP address represents the network ID and which portion represents the host ID.

For subnetting to work, the router must be told which portion of the host ID should be used for the subnet network ID. This is accomplished by using a _subnetmask_. Those IP address bits that represent the network ID are represented by a 1 in the mask, and those bits that represent the host ID appear as a 0 in the mask.

A subnet mask doesn't represent any device or network on the Internet. It's just a way of indicating which portion of an IP address should be used to determine the network ID.

The **network prefix** is indicated with a slash immediately after the IP address, followed by the number of the network ID bits to use. A subnet mask that is "/20" has 1 for the first 20 bits, and the remaining bits are 0s for the host ID porting of the subnetted address.

**Classless interdomain routing (CIDR)** notation provides a way of indicating which portion of an address is the network ID and which is the host ID.

# Ale

255.255.255.00000000 /24    --> there are no 1 on the last octet. 2 elevado a 0 = 1 --> only one subnet whose IP addresses can vary from 1 to 255.
255.255.255.10000000 /25    --> there is one 1 on the last octet. 2 elevado a 1 = 2 --> 2 subnets are possible.

- the first one ranges from 0 to 127
- the second one ranges from 128 to 255

255.255.255.11111000 /29    --> there are 5 1s on the last octet. 2 elevado a 5 = 32 --> there are 32 possible subnets available. 256/32 = 8

# Telnet

Command to install telnet using pwsh
´´´´
Install-WindowsFeature telnel-client
´´´´
## Telnetl commands

from **cmd**:

- telnet www.google.com 80
- telnet SERVER IP ADDRESS 3389         (3389 --> RDP)

### Public vs private IP addresses

When using a public IP address to communicate with a server, it's more secure to use the private IP address. To encrypt the connection we need a VPN or a Gateway. Gatways must be kept on a separate subnet --> **gateway subnet**.

To create this gateway we need:

1. Virtual network gateway
2. A certificate to encrypt the traffic
3. VPN client

### Creating a Point to Site VPN (P2S)

