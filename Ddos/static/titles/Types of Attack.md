## DDoS' Types

![ddos-types](/osi_model_7_layers.png)



While a DDoS attack intends to disrupt some or all of its target's services, not all DDoS attacks are the same. They feature unique characteristics, methods, and attack vectors. There are three common types of DDoS attacks:

- Volumetric (Gbps).
- Protocol (pps).
- Application layer (rps) attacks.


## Volumetric (Gbps)

This type of attack aims to control all available bandwidth between the victim and the larger internet. Domain name system (DNS) amplification is an example of a volume-based attack. In this scenario, the attacker spoofs the target's address, then sends a DNS name lookup request to an open DNS server with the spoofed address.

When the DNS server sends the DNS record response, it is sent instead to the target, resulting in the target receiving an amplification of the attacker’s initially small query.



![ddos-gbps](/amplification_ddos_example.png)



##  Protocol Attacks

Protocol attacks consume all available capacity of web servers or other resources, such as firewalls. They expose weaknesses in Layers 3 and 4 of the OSI protocol stack to render the target inaccessible. 
A SYN flood is an example of a protocol attack, in which the attacker sends the target an overwhelming number of transmission control protocol (TCP) handshake requests with spoofed source Internet Protocol (IP) addresses. The targeted servers attempt to respond to each connection request, but the final handshake never occurs, overwhelming the target in the process.
Below is a sampling of different network-layer DDoS attack types:

    - UDP floods
    - SYN floods
    - NTP amplification
    - DNS amplification
    - SSDP amplification
    - IP fragmentation
    - SYN-ACK floods




![ddos-pps](/syn_flood_ddos_example.png)




##  Application-Layer Attacks

These attacks also aim to exhaust or overwhelm the target's resources but are difficult to flag as malicious. Often referred to as a Layer 7 DDoS attack-referring to Layer 7 of the OSI model-an application-layer attack targets the layer where web pages are generated in response to Hypertext Transfer Protocol (HTTP) requests. 

A server runs database queries to generate a web page. In this form of attack, the attacker forces the victim's server to handle more than it normally does. An HTTP flood is a type of application-layer attack and is similar to constantly refreshing a web browser on different computers all at once. In this manner, the excessive number of HTTP requests overwhelms the server, resulting in a DDoS.



![ddos-rps](/application_layer_ddos_example.png)