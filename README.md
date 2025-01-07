# Jano Messaging Core

A TypeScript library providing core interfaces and types for instant messaging systems.

## Installation

```bash
npm install jano-messaging-core
```

## Features

- Type definitions for chat messages and instant messaging systems
- Support for multiple messaging platforms (WhatsApp, Stream)
- Message processing and transformation interfaces
- Conversation cache management
- Written in TypeScript with full type definitions

## Usage

```typescript
import { JanoChatMessage, IMMessage, MessageHandler } from 'jano-messaging-core';

// Example: Creating a chat message
const chatMessage: JanoChatMessage = {
    contentType: ChatContentType.TEXT,
    messageText: "Hello!",
    caregiverHandle: "caregiver123",
    caregiverId: "cg123",
    doctorHandle: "doctor123",
    doctorId: "dr123",
    msgCategory: JanoMessageCategory.CHAT
};
```

## Message Types

### JanoChatMessage
Represents a chat message with support for:
- Text messages
- Audio messages
- Video messages
- Image messages
- Documents
- Reactions
- Contact sharing
- Location sharing

### IMMessage
Represents an instant messaging system message with:
- Source and destination IM systems
- Message priority
- Unique message ID

## Interfaces

### MessageHandler
Interface for handling messages from different messaging systems:
```typescript
interface MessageHandler {
    getMessageCategory(extMsg: any): JanoMessageCategory;
    lookupProcessor(msgCategory: JanoMessageCategory): InMessageProcessor;
}
```

### MessageProcessor
Handles the lifecycle of incoming/outgoing instant messages:
```typescript
interface InMessageProcessor {
    processMessage(extMessage: any): Promise<any>;
    getSteps(waMsgBody: any, cacheEntry: BaseConversationCacheEntry): IStep[];
    executeSteps(steps: IStep[], ctx: ProcessorContext): void;
}
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)