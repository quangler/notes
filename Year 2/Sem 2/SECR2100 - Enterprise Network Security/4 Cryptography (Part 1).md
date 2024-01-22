#### Introduction
**Cryptography** - the science of encrypting, or hiding, information
**Cipher** - complex method of cryptographic algorithm, for concealing information
**Plaintext** - can be protected from unauthorized interception or alteration encrypting it into ciphertext
- uses an algorithm and a key
**Cryptanalysis** - the process of analyzing available information in an attempt to return the encrypted message to its original form
- **Differential Cryptanalysis** - compares the input plaintext to the output ciphertext to try and determine the key used to encrypt the information
- **Linear Cryptanalysis** - uses both plaintext and ciphertext; put the plaintext through a simplified cipher to try and deduce what the key is likely to be in the full version of the cipher
#### Cryptography in Practice
Cryptography is much more than encryption
- data protection
- data hiding
- integrity checks
- nonrepudiation services (making sure the message has been sent and received)
- policy enforcement
- key management and exchange
Strong cryptography is rendered weak via implementation mistakes like:
- known plaintext
- poorly protected keys
- repeated passphrases
Weaknesses in cryptosystems come from the system surrounding the algorithm, implementation, and operationalization details.
#### Levels of protection of a Cryptosystem
descending list of risks/benefits
1. mechanism is no longer useful for any purpose
2. cost of recovering the clear text without benefit of the key has fallen to a low level
3. the cost has fallen to equal to or less than the value of the data or the next least cost attack
4. the cost has fallen to within sever orders of magnitudes of the cost of encryption or the value of the data
5. the elapsed time of attack has fallen to within magnitudes of the life of the data, regardless of the cost thereof
6. the cost has fallen to less than the cost of a brute-force attack against the key
7. someone has recovered one key or one message

#### Fundamental Methods
modern cryptography uses:
- algorithm
- key
operations include:
- encryption (for the protection of confidentiality)
- hashing (for the protection of integrity)
- digital signatures (to manage nonrepudiation)
- and a mass of specialty operations such as key exchanges

Encryption methods are based on two different operations:
**Substitution** - replacing an item with a different item
**Transposition** - changing the order of items

Data can be characterized by:
- its state - data in transit, data at rest, or data in use
- how it's used - **block** form or **stream** form
	- block cipher - faster than stream, encrypts chunks at a time, will pad the file if there is not enough data
	- stream - sequential, slow but does the same amount as data

#### Comparative Strengths and Performance of Algorithms
The strength of an algorithm depends on:
- size of the key and resulting **keyspace** - a set of every possible key value
The bigger they keyspace, the more secure, but the more performance hit it takes

**Plaintext** - unencrypted input text
**Ciphertext** - encrypted output

#### Algorithms
**Algorithm** - a step-by-step procedure for solving a problem in a finite number of steps
**Cryptographic algorithm** - aka **encryption algorithm**, or **cipher**

**Hashing** - one way encryption, fast, used for verification that the file is the same from upload to download
**Symmetric algorithms** / shared secret algorithms - uses the same key for encryption and decryption
**Asymmetric algorithms** - employs two keys, a public key and a private key, making up a *key pair*.
- the best algorithms are always public algorithms
- they are peer reviewed by other cryptographers
- any flaws are revealed by others before it becomes the commonly used thing
#### Random Numbers
Software libraries have pseudo-random generators.
- they can't be truly random because they are deterministic.
Entropy is the level/amount of randomness.
#### Hashing Functions
A one-way function that turns from plaintext to ciphertext.
there is currently no feasible way to generate two different plaintexts that compute to the same hash value
hashes are used to:
- store computer passwords - doesn't have the actual password, but checks to the see if the password is the same (checks hash against hash)
- ensuring message integrity - if hashes are different, don't believe the message
#### Collision Attack
- a collision attack compromises a hash algorithm
	- occurs when an attacker finds two different messages that hash to the same value
	- very difficult and requires generating a separate algorithm that attempts to find a text that will has to the same value of a known hash
	- must occur faster than a brute-force type attack
- hash functions suffering from collisions lose integrity; user can be tricked into running malicious code
#### Symmetric Encryption
older, simpler, and faster method of encryption
both the sender and the receiver of the message have the same key
all symmetric algorithms are based upon the **shared secret** principle
**used for encrypting large files**
 
popular algorithms: DES, 3DES, AES, IDEA, EFS