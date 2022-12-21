# Database

Here are tables in the database.

## User

- **id**: `number` Each user has a unique id.
- **username**: `string` User uses this name to sign in.
- **nickname**: `string` This name will be displayed on the user information.
- **password**: `string` Password hashed with BLAKE3[^BLAKE3] algorithm. A hex string of length 64.
- **status**: `number`
  - `0`: The account is normal.
  - `1`: The user actively destroyed the account.
  - `2`: The administrator blocked the account.

[^BLAKE3]: [BLAKE3](https://en.wikipedia.org/wiki/BLAKE_(hash_function)#BLAKE3) is a cryptographic hash function that is **secure** and **much faster** than the existing similar algorithms. It was announced on January 9, 2020, at Real World Crypto Symposium. [Here](https://github.com/BLAKE3-team/BLAKE3/) is the official repository.
