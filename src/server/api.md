# Web API

Here are the APIs provided to the client.

> Note: When an API is preceded by `⚠️`, this API is only for debugging and can **NOT** be used in the production environment!

## User

### Login

**POST** `/login` Login with username and password.

- Payload
  - **username**: `string` User will use this name to sign in.
  - **password**: `string` User will use this password to sign in.
- Response
  - **code**: `number` The status code of the response. It will be `0` when the request succeeds.
  - **msg**: `string` The message of the response. It will be a *token* when the request succeeds.

### Register

**POST** `/users` Register a new account.

- Payload
  - **username**: `string` User will use this name to sign in.
  - **password**: `string` User will use this password to sign in.
- Response
  - **code**: `number` The status code of the response. It will be `0` when the request succeeds.
  - **msg**: `string` The message of the response. It will be empty when the request succeeds.

### ⚠️ List users

**GET** `/users` List all users, including deleted and banned users.

- Param
  - *None*
- Response
  - `User[]` All users.

### ⚠️ List sessions

**GET** `/sessions` List all sessions.

- Param
  - *None*
- Response
  - `Session[]` All sessions.

### Get user info

**GET** `/users/:id` Get information of a user.

- Param
  - *None*
- Response
  - `User` The user you want to get.

## Room

### Create new room

**POST** `/rooms` Create a new room.

You will join the room automatically after creating it.

- Payload
  - **token**: `string` The token of the user.
  - **name**: `string` The name of the room.
- Response
  - **id**: `number` The id of the room you created.

### ⚠️ List rooms

**GET** `/rooms` List all rooms.

- Param
  - *None*
- Response
  - `Room[]` All rooms.

### ⚠️ List *member*s

**GET** `/members` List all *member*s.

- Param
  - *None*
- Response
  - `Member[]` All *member*s.

### Join room

**POST** `/rooms/:id/join` Join a room.

- Payload
  - **token**: `string` The token of the user.
- Response
  - **code**: `number` The status code of the response. It will be `0` when the request succeeds.
  - **msg**: `string` The message of the response. It will be empty when the request succeeds.

### Get room info

**GET** `/rooms/:id` Get information of a room.

- Param
  - *None*
- Response
  - `Room` The room you want to get.

### Get user's rooms

**GET** `/rooms/me` List all rooms you joined.

- Headers
  - **Authorization**: `Bearer <token>` The token of the user.
- Response
  - `Room[]` All rooms you joined.
