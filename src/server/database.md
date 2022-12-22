# Database

Here are tables in the database.

## User

- **id**: `number` Each user has a unique id.
- **username**: `string` User uses this name to sign in.
- **nickname**: `string` This name will be displayed on the user information.
- **password**: `string` Password hashed with BLAKE3[^BLAKE3] algorithm. A hex string of length 64.
- **slogan**: `string` Introduction or motto, or something else.
- **status**: `number`
  - `0`: The account is normal.
  - `1`: The user actively destroyed the account.
  - `2`: The administrator blocked the account.
- **registered**: `timestamp` The time when this account was registered.

## Session

- **user**: `number` The id of the user.
- **agent**: `string` The user agent of this session.
- **token**: `string` The token of this session. A hex string of length 64.
- **generated**: `timestamp` The time when this session was generated.
- **expired**: `timestamp` The time when this session expires.

## Room

- **id**: `number` Each room has a unique id.
- **name**: `string` The name of the room.
- **description**: `string` About this room.
- **created**: `timestamp` The time when this room was created.

## Member

When a user joins a room, a *Member* will be created.

- **user**: `number` Who joins the room.
- **room**: `number` Which room the user joins.
- **joined**: `timestamp` When the user joins the room.

---

> TODO:

## Message

- **id**: `number` Each message has a unique id.
- **sender**: `number` The id of the sender of this message.
- **room**: `number` The id of the room where this message was sent.
- **data**: `MessageContent` The content of this message.
- **sent**: `timestamp` The time when this message was sent.
- **modified**: `boolean` Whether the message has been modified.

### MessageContent

There are 3 types of message content.

#### Text Message

- **type**: `Text` The type of this message.
- **text**: `string` The text of this message.

#### Picture Message

- **type**: `Picture` The type of this message.
- **pic**: `number` The *resource id* of the picture.
- **note**: `string` The note sent with this picture.

#### File Message

- **type**: `File` The type of this message.
- **file**: `number` The *resource id* of the file.
- **note**: `string` The note sent with this file.

[^BLAKE3]: [BLAKE3](https://en.wikipedia.org/wiki/BLAKE_(hash_function)#BLAKE3) is a cryptographic hash function that is **secure** and **much faster** than the existing similar algorithms. It was announced on January 9, 2020, at Real World Crypto Symposium. [Here](https://github.com/BLAKE3-team/BLAKE3/) is the official repository.
