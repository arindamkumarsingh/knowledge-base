# CIA Triad

Without proper security of info stored in the digital world, it can suffer drastic consequences. As data is becoming imp these days, the security becomes utmost important for govt etc.

Confidentiality, Integrity and Availability(CIA)

These are the three main pillars in which cybersec revolves.

1. Confidentiality means authorised users have access to sensitive infos. if not, then these can be the factor of financial losses, privacy violations etc.

2. Integrity means unauthorised users cannot modify the data.

3. Availability ensures that the data and services is available to the users when needed. If services are down, the buisnesses will not be able to function. Attacks like DDos are prime example for this.

# Cryptography concepts

how do we actually protect data from attackers?

* Plaintext - Able to read

* Ciphertext - gibberish

* key - like a pass, which is used to encrpyt the text.

* algorithm - public available

**Encryption** - plain text + encryption algorithm + key

**decryption** - cipher text + 

decryption algorithm + key


**THE LOCKBOX ANALOGY**


    The algorithm is how the lock works. Anyone can see you insert a key and turn it, hence it's not secret.
    The key is your specific metal key. Only people with that exact key can open your box.
    The plaintext is the letter inside the box.
    The ciphertext is that locked box travelling through the postal system.


#### CAESAR CIPHER

Now, we select a number as a key and each letter of the word is shifted to that number and gets encrypted
 so for the word to get decrypted, one has to go through 25 different combinations, which is tedious for human, but takes a millisecond in a computer.

**symmetric encyrption** means same key is used for encryption as well as decryption so its fast and efficient.

**key distribution problem** is an achilles heel in symmetric encrpytion, if we encrypt the key, then we would require another key, and for that another key and etc.

<mark> never use caeser cipher for real security.</mark>

### Asymmetric encryption

How to share the key safely:-

If use plain text, attacker can grab, if we encrypt the key, you know.

So we can use two keys instead of one. A public key and a private key. 

When Alice wants to send Bob a secret:

    Alice finds Bob's public key (the mail slot). This isn't a secret—Bob can post it on his website or email it around.
    Alice writes her message, encrypts it with Bob's public key, and sends it.
    Only Bob can decrypt it because he is the only one with the private key (the key to the door).

The most common use is HTTPS that we see in our browser. They use both sym and asym approach, they start using sym after they have established a shared secret through asymm approach to make things efficient. 

To know that the key which we are using is of the trusted source that's where certificate authority comes in view(CA's), the OS and browser comes with preloaded CA's so it verifies with it accordingly and then agrees to use public key.