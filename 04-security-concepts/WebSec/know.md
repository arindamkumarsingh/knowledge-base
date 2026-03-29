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


<mark>Use cyberchef magic mode to automatically know which encoding is used</mark>

## Index of Coincidence

This is an indicator used in cryptanalysis makes it possible to evaluate global distribution of letters in an encrypted message.

A text in english language has IC of 0.0667.

If the Index of coincidence is high (close to 0.070), i.e. similar to plain text, then the message has probably been encrypted using a transposition cipher (letters were shuffled) or a monoalphabetic substitution (a letter can be replaced by only one other).

If the Index of coincidence is low (close to 0.0385), i.e. similar to a random text, then the message has probably been encrypted using a polyalphabetic cipher (a letter can be replaced by multiple other ones).

use dcode.fr to search for many tools and find accordingly the answers.

## Caesar cipher

Take each letter and shift it forward or backward by a fixed number. Its considered very weak but pioneer in cryptography.

## ROT13 

A special case in caesar cipher, just shifts each letter 13 positions forward.

So applying ROT13 twice can give back the original texts, so its literally the same operations.

This is used for casually obscuring or hiding spoilers etc.


## Substitution cipher

Here we replace each letter with a different letter based on fixed mapping.

We first create a substitution alphabet blueprint and gets replaced accordingly

```
Plain:  ABCDEFGHIJKLMNOPQRSTUVWXYZ  
Cipher: QWERTYUIOPASDFGHJKLZXCVBNM
```

THis has 26! combinations rather than caesar which has only 25, so brute force is not possible.

1. Why is it harder for it to solve shorter text? Or put better, why is it easier to solve with longer text?

in english E approx occurs 12-13% T 9 % and A 8% which are expected.

So this is basically a game of statistics the higher the data the more info we can get and easier to solve, if the word is of 5 letters, we get less info as the sample space increases so does the image becomes clearer.
