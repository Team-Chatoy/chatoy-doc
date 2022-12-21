# General API

Here are some APIs that are widely used in the client.

> Note: When data can **NOT** be exchanged in binary form, please use JSON consistently.

## Message

Currently we only support the _Text Message_, but leave open the possibility of future expansion.

### Text Message

A text message should contain the following structure:

- **type**: `string` For the text message, it should be `text`.
- **content**: `string` The content of the message.

The JSON representation of a valid _Text Message_ might look like this:

```json
{"type":"text","content":"Hello, world!"}
```

> TODO...
