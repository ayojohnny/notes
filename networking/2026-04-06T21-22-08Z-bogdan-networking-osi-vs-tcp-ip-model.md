# Networking | OSI vs. TCP/IP Model

Models are used to help reason about data flowing through devices and a network. 
They do not strictly define how data moves. For instance, some protocols can be
mapped to multiple layers of either model. One such procotol being **IPSec**.


TCP/IP Layer    | Name                  | OSI Layer     | Name
--              | --                    | --            | --
1               | Network Access        | 1             | Physical
1               | Network Access        | 2             | Data link
2               | Internet              | 3             | Network
3               | Transport             | 4             | Transport
4               | Application           | 5             | Session
4               | Application           | 6             | Presentation
4               | Application           | 7             | Application
