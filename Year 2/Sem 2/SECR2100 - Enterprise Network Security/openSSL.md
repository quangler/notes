# Open SSL Cheat Sheet
- [Open SSL Cheat Sheet](#open-ssl-cheat-sheet)
  - [Create an SSH key pair](#create-an-ssh-key-pair)
  - [Symmetric Encryption](#symmetric-encryption)
    - [AES (CBC mode)](#aes-cbc-mode)
    - [3DES](#3des)
  - [Asymmetric Encryption (RSA)](#asymmetric-encryption-rsa)
  - [Hash Generation](#hash-generation)
  - [Verifying File Integrity with Hashes](#verifying-file-integrity-with-hashes)

## Create an SSH key pair

```
ssh-keygen -t rsa -f C:\Users\WINDOWS_USER\.ssh\KEY_FILENAME -C USERNAME -b 2048
```
- WINDOWS_USER: your username on the Windows machine.

- KEY_FILENAME: the name for your SSH key file.

  - For example, a filename of my-ssh-key generates a private key file named my-ssh-key and a public key file named my-ssh-key.pub.

- USERNAME: your username on the VM. For example, cloudysanfrancisco, or cloudysanfrancisco_gmail_com

Absolutely, here's the updated OpenSSL cheat sheet with examples:

## Symmetric Encryption

### AES (CBC mode)

```
# Encryption
openssl enc -aes-256-cbc -in plaintext.txt -out ciphertext.bin -pass pass:mysecretpassword -pbkdf2 -iter 100000

# Decryption
openssl enc -d -aes-256-cbc -in ciphertext.bin -out plaintext.txt -pass pass:mysecretpassword -pbkdf2 -iter 100000
```

### 3DES

```
# Encryption
openssl enc -des-ede3-cbc -in plaintext.txt -out ciphertext.bin -pass pass:mysecretpassword -pbkdf2 -iter 100000

# Decryption
openssl enc -d -des-ede3-cbc -in ciphertext.bin -out plaintext.txt -pass pass:mysecretpassword -pbkdf2 -iter 100000
```

## Asymmetric Encryption (RSA)

```
# Generate a private key
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048

# Extract the public key
openssl rsa -pubout -in private_key.pem -out public_key.pem

# Encryption
openssl pkeyutl -encrypt -pubin -inkey public_key.pem -in plaintext.txt -out ciphertext.bin

# Decryption
openssl pkeyutl -decrypt -inkey private_key.pem -in ciphertext.bin -out plaintext.txt
```

## Hash Generation

```
# SHA1
openssl dgst -sha1 file.txt

# SHA256
openssl dgst -sha256 file.txt

# MD5
openssl dgst -md5 file.txt
```

## Verifying File Integrity with Hashes

```
# Generate a hash of the file
openssl dgst -sha256 file.txt > hash.txt

# Verify the integrity
openssl dgst -sha256 -verify public_key.pem -signature hash.txt file.txt
```

**Note:** EFS (Windows Encryption File System) is a feature of the Windows operating system and not directly related to OpenSSL. You can use it by right-clicking on a file or folder in Windows, selecting Properties, and then the Advanced button on the General tab. There you'll find the option to encrypt the file or folder with EFS. 
