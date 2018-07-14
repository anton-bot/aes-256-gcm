# AES-256-GCM encryption/decryption shortcuts #

A static class that simplifies encryption/decryption using the AES 256 GCM algorithm.

Just use a one-liner to encrypt or decrypt - the IV and tag are handled
automatically.

## Example ##

```js
const Aes = require('aes-256-gcm');

// Must be 32 bytes.
const SHARED_SECRET = '12345678901234567890123456789012';

// Encrypt:
let { ciphertext, iv, tag } = Aes.encrypt('hi', SHARED_SECRET);

//   ciphertext: 'VOE='
//   iv: '0K6oPWsBAHLXYtLu5VAvsQ=='
//   tag: 'hCae3Lt5sAK3oNAnUh5emA==' 


// Decrypt:
let cleartext = Aes.decrypt(ciphertext, iv, tag, SHARED_SECRET;

// `cleartext` contains:
// 'hi'

```

## Methods ##

### static encrypt(text, secret) ###

Encrypts the `text` using the 256-bit shared key (`secret`) and returns an object
containing three base64-encoded strings:

```json
{ 
  "ciphertext": "(string)", 
  "iv": "(string)", 
  "tag": "(string)"
}
```

All of those strings must be passed to the end user to successfully decrypt the
text.

### static decrypt(ciphertext, iv, tag, secret) ###

Decrypts the `ciphertext` using the `iv` and authentication tag `tag` received
from the encryption function, and using the 256-bit shared key (`secret`).

Returns the decoded string.