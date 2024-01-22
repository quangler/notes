#### AES
- current gold standard
- block cipher - separates data input 128bit, 192bit, 256bit blocks
- key sizes of 128, 192, 256 (AES, AES-192, AES-256)
- no efficient attack currently exists

#### Symmetric Encryption Summary
importance of symmetric algorithms:
- comparatively fast
- few computational requirements
main weaknesses:
- all parties need an exact match of keys - if one is discovered 🫢 womp womp
- simple keys can be quickly brute-forced
- securely getting someone a key can be an issue

#### Asymmetric Encryption Summary
- uses a pair of keys:
	- private key that is kept secret
	- a public key that can be sent to anyone
- allows for digital signatures - allows for faster and more efficient exchange
- addresses the main issue of symmetric encryption (no single key to break the whole thing)
- exchanges of keys via digital certificates
- ability to send messages securely without senders and receivers having had prior contact

#### Symmetric vs Asymmetric
##### Symmetric
faster, less computationally involved, better for bulk transfers
- suffers from a key management problem - key has to be safe, otherwise everything is compromised
##### Asymmetric
resolves key security issue with public keys
- add significant computational complexity that makes them less suited for bulk encryption

We can use both asymmetric and symmetric keys: *
1. use symmetric to encrypt large files
2. save shared secret to a text file > `keyfile.txt`
3. use asymmetric to encrypt `keyfile.txt` (use other person's public key)
4. send them the (symmetrically) encrypted file and the asymmetrically encrypted `keyfile.txt`