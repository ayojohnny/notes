# API Design Patterns | Design Principles - Serialization

Serialization:
- transforming data into a language-agonstic format (i.e. JSON, protocol buffers)
- enables APIs to be used by any programming language

Serialization & deserialization is needed since programming languages don't share
the same underlying primitive data types and data structures.

Serialization Flow
1. server generates some data
2. server serializes that data into a language-agnostic format (i.e JSON, etc.)
3. server sends the serialized data to client (via the internet)

4. client receives the serialized data
5. client deserializes the serialized payload
6. client can now interact with the data via its own primitives & data structures

