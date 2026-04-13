# API Design | Standard Actions - Create

Create:
- create new resource w/in the API
- should be readable immediately after write (strong consistency)

Created resource should be retrievable by an identifier (GET) or discoverable by
listing resources (LIST)

```ts
abstract ChatRoomApi {
    @post("/chatRooms")
    CreatechatRoom(req: CreateChatRoomRequest): ChatRoom;

    @post("/{parent=chatRooms/*}/messages")
    CreateMessage(req: CreateMessageRequest): Message;
}

// API decides the ID sever-side
interface CreateChatRoomRequest {
    resource: ChatRoom
}

// If IDs can be consumer generated at creation time (edge case)
interface CreateChatRoomRequestConsumerGeneratedId {
    id: string 
    resource: ChatRoom
}

interface CreateMessageRequest {
    parent: string
    resource: Message
}
```

Resources Identifiers:
- API should choose the identifier for resource (typically)
- consumer-chosen IDs can be used if it fits use case (see chapter 6 for guidelines)


