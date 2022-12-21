# Web API

Here is the API provided to the client.

> Note: When an API is preceded by ⚠️, this API is only for debugging and can **NOT** be used in the production environment!

## User

**POST** `/users` Register a new account.

### Payload

- **username**: `string` User will use this name to sign in.
- **password**: `string` User will use this password to sign in.

### Response

- **code**: `number` The status code of the response. It will be `0` when the request succeeds.
- **msg**: `string` The message of the response. It will be empty when the request succeeds.

---

**POST** `/login` Login account.

### Payload

- **username**: `string` User will use this name to sign in.
- **password**: `string` User will use this password to sign in.

### Response

- **code**: `number` The status code of the response. It will be `0` when the request succeeds.
- **msg**: `string` The message of the response. It will be JWT when the request succeeds.

---

⚠️ **GET** `/users` List all users.

### Payload

None

### Response

`User[]` All users, including deleted and banned users.
