# Networking | Data Decapsulation - TCP/IP Model

Data Decapsulation:
- process of unpacking data sent from a source (so the original data can be worked with)
- "bottom-up" workflow (start with L1 (network access - physical) and works to L4 (application))


Scenario: Recieving bits (i.e. formatted data as binary) from some source

L1  - Network Access/Physical   => recieve bits
L1  - Network Access/Data Link  => frame header + packet header + segement header + data (app) + frame trailer
L2  - Network                   => packet header + segement header + data (app) 
L3  - Transport                 => segement header + data (app)
L4  - Application               => data

When decapsulating (unpacking) data frames only look at their respective PDUs:
- L1 (data link)    -> frame header + frame trailer
- L2 (network)      -> packet header
- L3 (transport)    -> segment header
- L4 (application)  -> data
