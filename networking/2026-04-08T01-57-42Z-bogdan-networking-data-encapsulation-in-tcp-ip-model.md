# Networking | Data Encapsulation - TCP/IP Model

Secnario: Sending an email from SMTP client A to another SMTP client B. 

The following demonstrates taking the data in the email (sent from some mail client like gmail) and gives
high-level overview of what happens during the "data encapsulation" process of sending the email. The data,
generated from L4 is passed to lower layers. At L3 a transport segement header is added. At L2 (network) 
a packet header is added. At L1 (network access - data link) the data + headers from L3 and L2 are packaged
between a data link PDU (i.e. a data frame). Then that data frame is converted to bits (0 & 1's) to be sent
over the network to destination client. 

On arriving to the destination, data decapsulation happens (essentially unwrapping headers to get to the data).

Workflow - Data Encapsulation (i.e. sending data from some source)
L4  - Application   => Data
L3  - Transport     => Data + Segement Header
L2  - Network       => Data + Segement Header + Packet
L1  - Data Link     => Frame Header + Packet Header + Segment Header + Data + Frame Trailer
L1  - Physical      => Bits

Data Frame example:
---------------------------------------------------------------------------------------
Frame Header | Packet header | Setgement header | data (from app / L4) | frame trailer 
---------------------------------------------------------------------------------------

The above is what gets serialized into bits at L1 (network access - physical) before being sent
over the network to destination machine.


## Data Encapsulation

Process of formatting data to send over the network. Due to adding headers to initially generated data and
then stuffing into a data frame, there is performance overhead at each layer. 

L4 (application) generates/sends data. L3-L2 wrap the data with headers. L1 (data link) stuffs the data into a
data frame. Lower layers cannot modify the data generated at L4?

Once entire data frame made -> serialized into bits and sent to destination over network

