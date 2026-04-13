# API Design | Standard Actions - GET


GET
- retrieving a resource based on some identifier
- should be idempotent
- should not contain side effects
- read-only

```ts
abstract class ChatRoomApi
{
    @get("/{id=chatRooms/*}")
    GetChatRoom(req: GetChatRoomRequest): ChatRoom;
}

interface GetChatRoomRequest {
    id: string;
}
```
