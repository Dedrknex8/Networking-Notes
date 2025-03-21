
# OSI model

> Let's first start with OSI model what it is and why it's used?

## OSI model stands for `Open System Interconnection`

- It's developed by ISO `International Organization for Standardization`

- OSI model consist of 7 layers 
```
+---+    +----------------------------------+
| 7 |    |        Application Layer         |
+---+    +----------------------------------+
+---+    +----------------------------------+
| 6 |    |        Presentation Layer        |
+---+    +----------------------------------+
+---+    +----------------------------------+
| 5 |    |        Session Layer             |
+---+    +----------------------------------+
+---+    +----------------------------------+
| 4 |    |        Transport Layer           |
+---+    +----------------------------------+
+---+    +----------------------------------+
| 3 |    |        Network Layer             |
+---+    +----------------------------------+
+---+    +----------------------------------+
| 2 |    |        Data Link Layer           |
+---+    +----------------------------------+
+---+    +----------------------------------+
| 1 |    |        Physical Layer            |
+---+    +----------------------------------+

```

### Layer 1 {Physical Layer}

- It is the lowest layer in OSI model which is responsible for the actual physical connection b\w the devices. The physical layer contains the info the form of bits.
- responsible for transmitting individual bits from one node to the next. 
- Node is defined as - Devices connected to each other are called as **nodes.**
- And the term used for wireless n\w is known as **Station**
- Devices operating at Physical layer are :
	*  Transceivers : it is a part of network interface that sends and receives signals over the network media
	* Repeater : A device that amplifies electronic signal to extend the maximum allowable distance for a media type.
	* -Hubs : A multiport repeater.
	*  Media Converters : Converts one media signaling type to another.
	- Modems : converts between digital and analog signal transmission


![[Networking/assests/Pasted image 20250315134051.png]]

----------------------------------------
## Some Important Concepts

> Before Diving deep into the layers some **imp* concepts need to learn

- When we send information over the internet it does go as a big chunk of data. Instead it broken down into small chunks of pieces. These pieces are called Segements, Packets & Frames. 
- Each type has its own job in making sure the information gets where it needs to go.
1. Segments : `Data is recived in application layer is broken down in smaller parts as per the max window size and the Tcp header is added to the smaller parts.The size of the header can be vary from 20 to 60 Byte` 
-  The TCP header includes :
```
1. Source IP Address  
2. Destination IP Address  
3. TTL(time to live)  
4. Identification  
5. Protocol type   
6. Version (version of protocol)  
7 Options
```

2. Packets  : `The segments received from the Transport layer are further processed to form the Packets. The IP packet has a header of varying sizes from 20B to 60B. But usually, it is 20B. `

- The `IP` header includes

```
****1.**** Source IP Address  
****2.**** Destination IP Address  
****3.**** TTL(time to live)  
****4.**** Identification  
****5.**** Protocol type   
****6.**** Version (version of protocol)  
****7.**** Options
```


3. Frames : `The Packets received from the Network Layer further processed to form the Frames. Here is the [Data link layer](https://www.geeksforgeeks.org/data-link-layer-in-osi-model/) the header is added, the header consists of the fields that are mentioned below :`
```
1. Source Mac Address
2. Destination Mac Address
3.Data
3. Length
4. Checksum (CRC)
```

- What is PDU?

> - PDU stands for Protocol data unit.
> - When we have to transmit the information, we need to pass the data between each layer one by one. During this process, at each layer (except physical layer), the sending device add a header to the data payload in the form of a chunk, this chunk is called as Protocol data unit i.e. PDU. And the process is called as `encapsulation`. The reverse is called as `de-encapsulation` or `decapsulation`.

# Layer 2 {Data Link Layer}

-  It is responsible for the node-to-node delivery of data within the same local network
-  Data transmission from one physical device address to another.

- Sub layer of DLL
### Logical Link Control (LLC)

`This sublayer of the data link layer deals with multiplexing, the flow of data among applications and other services, and LLC is responsible for providing error messages and acknowledgments as well. `

### Media Access Control (MAC)

`MAC sublayer manages the device’s interaction, responsible for addressing frames, and also controls physical media access. The data link layer receives the information in the form of packets from the Network layer, it divides packets into frames and sends those frames bit-by-bit to the underlying physical layer.`

 > The function of data Link Layer

- Flow control means controlling the rate at which data flows
 ![[assests/Pasted image 20250316123616.png]]
----------------------------------------
# Layer 3 Network layer

- It's the layer responsible for moving the data along the networks
- It offers route for the data packets to transfer across the n\w

#### Function of n\w layer

![[assests/Pasted image 20250317184601.png]]

----------------------------------------
# Layer 4 : Transport Layer


- This layer is also known as host-to-host or end-to-end layer.
- This layer receives data from application layer and then performs segmentation divides the actual message into segments. add the src and destination port number into the header of the segments and transfer into the message to N\w layer .
- Responsible for reliable data delivery
- Also provide congestion control


#### What is congestion in N\W ?

> Congestion is a situation in which too many sources over a network attempt to send data and the router buffers start overflowing due to which loss of packets occurs.

 - There are some algorithm to control it and transport layer provides that solution like => Leaky Bucket Algorithm.
 -----------------------------------------------------------------------
# Layer 5 {Session layer}

- This layer plays an important role in controlling the dialogues (connections) between computers. This layer is responsible for setting up, coordinating, and terminating conversations, exchanges, and dialogues between the applications at each end.
- Mainly this layer is used manage, establish and terminate connection b/w local and remote applications

> Functions of layer layer

- Session Establishment 
- Communicatoin synchronization

How Session layer manage handle synchronization?
`It uses checkpoints to allow data recovery in case of communication failure.`

--------------------------------------------------------------------------
# Layer 6 Presentation Layer

- Also known as Data Translation layer
- Data received from application layer is converted into other form of data
- Data compression
- Data encryption and decryption 
- - ****Interoperability****: Bridges differences in data formats between devices.

Some important Questions in Presentation Layer

****What is TLS in presentation layer?****

`TLS (Transport Layer Security) is a cryptographic protocol that operates at the Presentation Layer. It ensures secure communication between devices by encrypting data, maintaining its integrity, and providing authentication.`
 
2. ****What is SSL vs TLS?****

> ****SSL (Secure Sockets Layer)**** and ****TLS (Transport Layer Security)**** are protocols for securing communication. TLS is the modern, more secure successor to SSL. While SSL (now outdated) had vulnerabilities, TLS improves encryption, authentication, and overall security. TLS is widely used for secure web browsing, replacing SSL.

3. What is Mac and HMAC in SSL/TLS in presentation layer?
`The SSL protocol uses the MD5 algorithm—which is now outdated—for MAC generation(message authentication codes). TLS uses Hash-Based Message Authentication Code (HMAC) for more complex cryptography and security.`


------------------------------------------------------------------------
# Layer 7 Application layer

- It deals with data representation i.e it ensure data is readable format for both the sender and receiver, including data translation, compression and encryption
- It deals with protocols like http, ftp, ssh
- The main function of application layer is to provide an interface to send and receive data from user.
-----------------------------------------------------------
