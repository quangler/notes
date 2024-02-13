EncryptPad - literally not data in use. key is just "hidden" on desktop. Not safe. 
- idk

SEV-ES (secure encryption virtualization - encrypted state) - used for VMs - encrypts a VMs data - not memory tho??
- can't live migrate

Fortanix RTE - data can only be decrypted by CPU, cant be accessed by OS
- ECC - elliptic-curve cryptography

total memory encryption - TME
- encrypts memory through AES XTS
- key generated through CPU - software can't see the key
- TME - PCs  |  TME - multi key - Servers
- **encryption along the bus** - anything entering or leaving gets encrypted / decrypted

AWS Nitro System
- ecosystem linked in bro
- fips 140 HSM (AWS Key management service)

Intel SGX
- 128GB enclave size
- uses AES for encryption
- encrypts CPU and memory (MEE)
- memory dump app - scanmem

PySyft
- encrypts data within RAM
- data can be worked on without being revealed / unencrypted
- works with hardware encryption solutions (SGX / AMD SEV)

Kernel Level Anti Cheat
- makes your computer slower
- games need access to memory space
- game devs install software to your kernel which detects what is affecting game memory, checks for hardware IDs
- DMA board - direct memory access - between your hardware and software - lets you spoof your kernel and change hardware IDs
	- effectively allow cheating

AMD SME - secure memory encryption
- securing unencrypted data in RAM
- hardware level security - feature in AMD processors
- 