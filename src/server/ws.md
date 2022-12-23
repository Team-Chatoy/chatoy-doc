# WebSocket

After establishing the websocket connection with the server `/ws`, the client first needs to send an authentication message.

## Auth

- **type**: `Auth` This message is for auth.
- **token**: `string` The token received from the server after login.

### Example

```json
{"type":"Auth","token":"0123456789abcdef"}
```

### Response (WIP)

- **type**: `Auth` This message is the response of the auth message.
- **code**: `number` The status code of the response. It will be `0` if the auth succeeds.
- **msg**: `string` The message of the response. It will be empty if the auth succeeds.

### Example

```json
{"type":"Auth","code":0,"msg":""}
```

```json
{"type":"Auth","code":1,"msg":"Login status expired!"}
```

## Send Message

- **type**: `Msg` This message is for sending a message.
- **uuid**: `string` The uuid of this message.
- **room**: `number` The id of the room to send the message to.
- **data**: `MessageContent` The content of the message.

### Example

```json
{
  "type": "Msg",
  "uuid": "67e55044-10b1-426f-9247-bb680e5fe0c8",
  "room": 1,
  "data": {
    "type": "Text",
    "text": "Hello, Chatoy!"
  }
}
```

### Response

You will receive a `Recv` message after sending a `Msg` message.

## Receive Message

> These messages are only sent by the server to the client.

- **type**: `Recv` You received a message from the server.
- **data**: `Message` The message you received.

### Example

```json
{
  "type": "Recv",
  "data": {
    "uuid": "67e55044-10b1-426f-9247-bb680e5fe0c8",
    "sender": 1,
    "room": 1,
    "data": {
      "type": "Text",
      "text": "Hello, Chatoy!"
    },
    "sent": "2022-12-22T14:33:59.579746716+08:00",
    "modified": false
  }
}
```
