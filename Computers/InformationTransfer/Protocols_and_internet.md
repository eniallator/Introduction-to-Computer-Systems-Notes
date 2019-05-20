# Notes

## Internet

- Formed of freely growing collection of networks which transmit data packets between each other
- Independent networks make peering arrangements to exchange traffic, either via:
  - Internet exchanges
  - Direct, private interconnections
- Used for many purposes, including:
  - Document viewing
  - File transfer and sharing
  - Email
  - Social media
  - Video and audio streaming
  - Online gaming
  - E-commerce

## Network Layers

- Complexity of networks is controlled through layers
- A standard approach is the Open Systems Interconnection Basic Reference Model (OSI Model)
- This is an example of abstraction, providing a virtual network, hiding details from the programmer/user 🧐

### Physical Layer

- Layout of pins in connectors, voltages in cables, wireless frequencies, etc.

### Data Link Layer

- Deals with error correction
- Grouping bits into frames
- Making sure the frames get to the next hop of their journey successfully

### Network Layer

- Deals with getting packets right through the network
- Routing them through other computers when src and dest don't have direct connection
- Relies on the concept of a network address

### Transport Layer

- Implements protocols for wrapping up data into packets
- Responsible for flow control, putting packets into the right order when received and spotting/recovering from network errors

### Session Layer

- Manages dialogue between machines exchanging information

### Presentation Layer

- Translates data into the form that the session layer can handle

### Application layer

- Acts on requests from a user program/application, e.g email client

## Internet Addresses

- Each node has an address
  - Each packet has a destination address in it's header
- Routers move the packets accordingly
- Current addresses are 32 bits
  - So 4.3 billion nodes are possible in principle
  - Not enough 😲
- Addresses are assigned by the Internet Corporation for Assigned Names and Numbers (ICANN)
- Addresses are written in "dotted decimal" notation, e.g
  - `10001011 10111000 00011000 00010110`
  - Usually written as
  - `139.184.24.22`
- Numerical addresses aren't so easy to read so addresses have an alphabetical form, e.g
  - `unix.sussex.ac.uk`
  - This has to be translated to a numerical address before a packet is sent
  - Achieved by sending a request to a name server, name servers form a:
    - Continuously updated
    - Distributed database
    - Which maps alphabetical names to numerical addresses
  - Name servers form the domain name system; the process of getting a numerical address is called a DNS lookup
- This a single computer to support many domains for the physical computer for a name change

## The Internet's Protocols: TCP/IP

- Transmission control protocol/internet protocol, since 1983
- Set of protocols used for communication over the internet; also can be understood in layers, though not quite OSI model
  - TCP/IP layer: OSI model equivalent
  - Link layer: physical layer, data link layer
  - Internet layer: network layer
  - Transport layer: transport layer
  - Application layer: session layer, presentation layer, application layer
- Different components operate at different layers
  - Routers operate at the internet layer
  - Message assembly happens in the transport layer
  - DNS lookup happens in the application layer

### IP

- IP (Internet Protocol) operates in the internet layer
  - Supported at the link layer by systems that manage transmission across one hop of the network
  - Handles the business of passing packets of data (AKA datagrams) from the start to end points
  - Key task: making decisions about how to route the packets through a network using tables of which IP addresses can be reached along a given link
  - Is an unreliable protocol (not because it doesn't work well, but if there's an error it's not reported to the sender/recipient)
  - Is connectionless: packets are launched to the recipient without a connection already being established
  - Packets can arrive in any order, may be lost or duplicated
  - Current version is IPV4, moving to IPV6
  - Used by the transport layer

### TCP

- TCP (Transmission Control Protocol) operates in the transport layer
  - Supported by the internet layer
  - Accepts data in the form supplied by an application and splits it into packets which can be given to IP for transmission
  - Reassembles packets received over internet layer into a form suitable for applications
  - Carries out flow control if the receiver can't keep up
  - Is reliable: checks that all packets have been received, and are correct
    - Asks for retransmission if there's a problem
  - Uses connections: gets acknowledgement from receiver before sending data
  - Puts reliability above speed - not so good for streaming audio/video (connectionless protocols such as UDP exist for higher speed, however less reliability)
  - Uses port numbers to establish connections between specific programs on different computers
  - Used by the application layer
