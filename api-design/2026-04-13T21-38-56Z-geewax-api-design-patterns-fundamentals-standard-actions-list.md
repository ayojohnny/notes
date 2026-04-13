# API Design | Standard Actions - List

List:
- retrieve all resources belonging to some collection

Collections can be independent or belong to another resource. For instance, a Chatroom
API that has `ChatRoom` and `Message` resources might have 2 `List` actions. One to
list all available chatrooms. Another to view all messages tied to a specific chat room.

```ts
abstract class ChatRoomApi {
    @get("/chatRooms")
    ListChatRooms(req: ListchatRoomsRequest): ListChatRoomsResponse;

    @get("/{parent=chatRooms/*}/messages")
    ListMessages(req: ListMessagesRequest): ListMessagesResponse;
}

interface ListChatRoomsRequest {
    filter: string;
}

interface ListChatRoomsResponse {
    results: ChatRoom[];
}

interface ListMessagesRequest {
    parent: string;
    filter: string;
}

interface ListMessagesResponse {
    results: ChatRoom[];
}
```
Access Control Considerations:

How should the List action behave when different requests have access to different
resources? What if a user wants to list all available `ChatRoom` resources in an
API but only has access to see some of those resources? What should the API do?

A common occurence & edge case: user listing a collection an only has access to
some of the items 

Include:
- filtering

Avoid:
- adding item counts
- applying ordering over a list of items (sorting)

Problems with Sorting:
1. as N items in the list grows, more computational time is required
2. can be hard to apply global sort a list when that it comes from multiple backend storage engines (distributed systems)
3. can result in overloaded API servers

Case:
Trying to consolidate & sort 1 billion items spread across 100 different storage backends.

