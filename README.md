# No Longer Maintained
This repository is no longer maintained. The functionality of this project has been merged into [YouTube.js](https://github.com/LuanRT/YouTube.js). We highly recommend switching to that package in order to have the latest functionality. We cannot promise stability if you continue to use this package as is.

# youtube-chat
> Fetch Youtube live chat without API

This module is a fork of `youtube-chat`, which was written by [LinaTsukusu](https://github.com/LinaTsukusu) and fixed up by [IcedCoffeee](https://github.com/IcedCoffeee).

Since the original maintainer doesn't work on this package, we forked it and maintain it for the needs of FreeTube.

***You will need to take full responsibility for your actions***

## Getting started
1. Install
    - `npm i @freetube/youtube-chat`
    - `yarn add @freetube/youtube-chat`
2. Import
    - Javascript
    ```javascript
    const LiveChat = require('@freetube/youtube-chat').LiveChat
    ```
    - Typescript
    ```typescript
    import {LiveChat} from '@freetube/youtube-chat'
    ```
3. Create instance with ChannelID or LiveID
    ```javascript
    // If channelId is specified, liveId in the current stream is automatically acquired.
    const liveChat = new LiveChat({channelId: 'UCxkOLgdNumvVIQqn5ps_bJA?'})
    
    // Or specify LiveID in Stream manually.
    const liveChat = new LiveChat({liveId: 'bc5DoKBZRIo'})
    ```
4. Add events
    ```typescript
    // Emit at start of observation chat.
    // liveId: string
    liveChat.on('start', (liveId) => {})
   
    // Emit at end of observation chat.
    // reason: string?
    liveChat.on('end', (reason) => {})
    
    // Emit at receive chat.
    // comment: CommentItem
    liveChat.on('comment', (comment) => {})
    
    // Emit when an error occurs
    // err: Error
    liveChat.on('error', (err) => {})
    ```

## Types
### CommentItem
```typescript
interface CommentItem {
  id: string
  author: {
    name: string
    thumbnail?: ImageItem
    channelId: string
    badge?: {
      thumbnail: ImageItem
      label: string
    }
  }
  message: MessageItem[]
  superchat?: {
    amount: string
    color: number
  }
  membership: boolean
  isOwner: boolean
  timestamp: number
}
```

### MessageItem
```typescript
type MessageItem = { text: string } | ImageItem
```

### ImageItem
```typescript
interface ImageItem {
  url: string
  alt: string
  width: number
  height: number
}
```
