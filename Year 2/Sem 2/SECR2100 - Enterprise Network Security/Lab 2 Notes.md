lab notes:
make a root CA (don't join it to the domain) you need to do AIA and CRL |  - once you make a key from it you can take it offline (put the key on the enterprise CA)
then make an enterprise CA that is connected to the network - have to change the time it takes to expire (defaults 1 week)
& an AD (DC?)

---
