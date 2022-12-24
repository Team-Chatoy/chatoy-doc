# Web API

Here is the API provided to the client.

> Note: When an API is preceded by ⚠️, this API is only for debugging and can **NOT** be used in the production environment!

## User

**POST** `/login` Login account.

### Payload

- **username**: `string` User will use this name to sign in.
- **password**: `string` User will use this password to sign in.

### Response

- **code**: `number` The status code of the response. It will be `0` when the request succeeds.
- **msg**: `string` The message of the response. It will be a *token* when the request succeeds.

---

**POST** `/users` Register a new account.

### Payload

- **username**: `string` User will use this name to sign in.
- **password**: `string` User will use this password to sign in.

### Response

- **code**: `number` The status code of the response. It will be `0` when the request succeeds.
- **msg**: `string` The message of the response. It will be empty when the request succeeds.

---

⚠️ **GET** `/users` List all users.

### Param

None

### Response

`User[]` All users, including deleted and banned users.

---

⚠️ **GET** `/sessions` List all sessions.

### Param

None

### Response

`Session[]` All sessions.

---

**POST** `/rooms` Create a new room.

You will join the room automatically after creating it.

### Payload

- **token**: `string` The token of the user.
- **name**: `string` The name of the room.

### Response

- **id**: `number` The id of the room you created.

---

⚠️ **GET** `/rooms` List all rooms.

### Param

None

### Response

`Room[]` All rooms.

---

⚠️ **GET** `/members` List all *member*s.

### Param

None

### Response

`Member[]` All *member*s.

---

**POST** `/rooms/:id/join` Join a room.

### Payload

- **token**: `string` The token of the user.

### Response

- **code**: `number` The status code of the response. It will be `0` when the request succeeds.
- **msg**: `string` The message of the response. It will be empty when the request succeeds.

---

**GET** `/users/:id` Get information of a user.

### Param

None

### Response

`User` The user you want to get.

---

**GET** `/rooms/:id` Get information of a room.

### Param

None

### Response

`Room` The room you want to get.

---

**GET** `/rooms/me` List all rooms you joined.

### Headers

- **Authorization**: `Bearer <token>` The token of the user.

### Response

`Room[]` All rooms you joined.
