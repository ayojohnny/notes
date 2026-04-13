# Api Design | Fundamentals - Standard Actions - Update

Update
- modify existing resources (unless immutable)
- should avoid side effects
- `PATCH` method of HTTP
- needs a resource identifier to search
- should return the newly modified resource
- should only update certain aspects about the resource without affecting others

HTTP Patch
- partial modification instead of full replacement of a resource

```ts
abstract class ChatRoomApi {
    @patch("/{resource.id=chatRooms/*}")
    UpdateChatRoom(req: UpdateChatRoomRequest): ChatRoom;
}

interface UpdateChatRoomRequest {
    resoruce: ChatRoom;
    // ...
}
```

Some places where updating an existing resource is better placed:
- transitioning state of a resource (i.e. activate or archiving a chat room)
    - better done through custom method (i.e. `ArchiveChatRoom()`)


