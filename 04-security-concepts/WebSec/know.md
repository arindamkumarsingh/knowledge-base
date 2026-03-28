# yo

## Hashing vs Encryption vs Encoding vs Obfuscation

### ENcoding

It transforms data into another using a format available pubilically like ascii to hex4 or man more and doesnt require a key to decode the msg.

### Encryption

Transform data to keep it a secret from others, main focus is that the data must be consumed by the intended reciever rather than anyone else. and uses a key. Cypher text + algo + key

Eg = AES, RSA, Blowfish etc.

### Hashing

Takes any input and outputs a fixed length fingerprint.

It is not possible or feasible to find two inputs with the same hash, cannot reverse the hash to get the input.

need to know more.

### Obfuscation

It is more of an obstacle rather than an encryption, purpose is to make it difficult to understand, eg is obfuscation of source code so makes it dificult to reverse engineer, the program must still function and doesnt depend on how much obfuscated you make it.

