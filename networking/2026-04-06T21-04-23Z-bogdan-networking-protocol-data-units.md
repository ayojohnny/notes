# Networking | Protocol Data Units (PDUs)
> Remember, **bit** is the smallest piece of data that can be sent over
> physical media (wired connection, wireless connection, etc.)

Protocol Data Units
- smallest unit of data for a given layer in the OSI model

## Layer 1 - Physical 
PDU: Bits

Responsible for transmission of data over various mediums (Ethernet, Wi-Fi, Bluetooth,
LTE, etc.)

## Layer 2 - Data Link
PDU: Frames/Data Frames

Physical addressing (Ethernet)

## Layer 3 - Network
PDU: Packets

Logical addressing & routing (IPv4, IPv6)

## Layer 4 - Transport
PDU: Segments

End-to-end connections (TCP & UDP)

## Layer 5 - Sessions
PDU: Data

Establish & control sessions (L2TP, H.245)

H.245 -> phone calls over computer network
L2TP -> Layer 2 tunnel protocol

## Layer 6 - Presentation
PDU: Data

Data representation (JPEG, UTF-8)

## Layer 7 - Application
PDU: Data

Interaction with end-user (HTTP, FTP)

Media Layers => 1, 2, 3

Host Layers => 4, 5, 6, 7
