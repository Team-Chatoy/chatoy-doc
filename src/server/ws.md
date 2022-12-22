# WebSocket

After establishing the websocket connection with the server `/ws`, the client first needs to send an authentication message.

## Auth

- **type**: `auth` This message is for auth.
- **token**: `string` The token received from the server after login.

### Example

```json
{"type":"auth","token":"0123456789abcdef"}
```

### Response

- **type**: `auth` This message is the response of the auth message.
- **code**: `number` The status code of the response. It will be `0` if the auth succeeds.
- **msg**: `string` The message of the response. It will be empty if the auth succeeds.

### Example

```json
{"type":"auth","code":0,"msg":""}
```

```json
{"type":"auth","code":1,"msg":"Login status expired!"}
```

## Send Message

- **type**: `msg` This message is for sending a message.
- **uuid**: `string` The uuid of this message.
- **room**: `number` The id of the room to send the message to.
- **data**: `MessageContent` The content of the message.

### Example

```json
{
  "type": "msg",
  "uuid": "67e55044-10b1-426f-9247-bb680e5fe0c8",
  "room": 1,
  "data": {
    "type": "Text",
    "text": "Hello, Chatoy!"
  }
}
```

### Response

- **type**: `send` This message is the response of sending message.
- **code**: `number` The status code of the response. It will be `0` if sending message succeeds.
- **msg**: `string` The message of the response. It will be empty if sending message succeeds.
- **uuid**: `string` The uuid of the message you sent.
- **sent**: `timestamp` The time when this message was sent.

### Example

```json
{
  "type": "send",
  "code": 0,
  "msg": "",
  "uuid": "67e55044-10b1-426f-9247-bb680e5fe0c8",
  "sent": "2022-12-22T14:33:59.579746716+08:00"
}
```

## Receive Message

> These messages are only sent by the server to the client.

- **type**: `recv` This message was sent by another user.
- **data**: `Message` The message you received.

### Example

```json
{
  "type": "recv",
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
