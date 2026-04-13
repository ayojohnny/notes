# API Design | Design Principles - Serialization - Booleans

Boolean: a `true` or `false` value

Use cases:
- storing flags
- simple yes or no questions

```ts
interface Chatroom {
    id: string;
    // ...
    archived: boolean;
    allowChatbots: boolean;
}
```

Tips:
- avoid using double negatives w/ booleans fields

```ts
allowChatBots: true;        // implies chatbots are allowed
disallowChatBots: false;    // implies chatbots are allowed

allowchatBots: false;       // implies chatbots are disallowed
disallowChatBots: true;     // implies chatbots are disallowed
```

```ts

// Negative boolean usage.
function addChatbotToRoom(chatbot: Chatbot, roomId: number): void {
    const room = getChatRoomById(roomId);
    if (room.disallowChatBots === false) chatbot.join(room.id);
}

// Positive boolean usage.
function addChatbotToRoom(chatbot: Chatbot, roomId: number): void {
    const room = getChatRoomById(roomId);
    if (room.allowChatBots) chatbot.join(room.id);
}

```
