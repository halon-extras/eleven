# eleven eXpurgate anti-spam client

## Installation

Follow the [instructions](https://docs.halon.io/manual/comp_install.html#installation) in our manual to add our package repository and then run the below command.

### Ubuntu

```
apt-get install halon-extras-eleven
```

### RHEL

```
yum install halon-extras-eleven
```

## Exported functions

These functions needs to be [imported](https://docs.halon.io/hsl/structures.html#import) from the `extras://eleven` module path.

### expurgate(fp[, options])

Client for the eleven eXpurgate anti-spam.

**Params**

- fp `File` - the mail file
- options `array` - options array

The following options are available in the **options** array.

- address `string` - Address of the eXpurgate Spamd server. The default is `127.0.0.1`.
- port `number` - TCP port. The default is `783`.
- id `string` - The ID to be logged with the message (see Custom-Connection-ID)
- senderip `string` - The sender IP.
- sender `string` - The envelope sender.
- recipients `array` - The envelope recipients in [this](https://docs.halon.io/hsl/eodonce.html#recipient) format.
- size_limit `number` - Size limit in bytes. The default is `500 * 1024`.
- timeout `number` - Timeout in seconds. The default is `30` seconds.

**Returns**

An associative array with the following properties set.

* `spam` (boolean) if the message is spam
* `score` (number) representing the spam score
* `threshold` (number) representing the spam limit
* `category` (string) representing the category for the message
* `id` (string) representing a unique ID

If an error occures an `error` property (string) is set contaning the error message.