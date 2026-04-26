# Encryption | Key Based 

Symmetric encryption
- single key
- key is used to both encrypt and decrypt data
- can be reversed

plaintext -> symmetric key -> cipher text -> symmetric key -> plaintext

Asymmetric encryption
- two keys (i.e. a "key pair")
- 1 key used for encryption (public key)
- 1 key used for decryption (private key)
- 2 keys must be mathematically related (comes from the base data set)
- either key can encrypt, the other key will decrypt
- more commpuationally intensive than symmetric encryption
- one-way encryption (trapdoor function)
    - easy to compute in one direction
    - difficult to invert without special knowledge (i.e. the trapdoor)

Asymmetric encryption removes the need to send a shared key over the wire (like in
symmetric encryption). This is because the public key (the encryption key) can be
shared publicly, and the private key (decryption key) is meant to be confidential.

Private key:
- sensitive, never meant to be shared
- if hacked, can decrypt all data

Public key
- used for encryption
- meant to be shared

plaintext -> public key -> ciphertext -> private key -> plaintext

Rivest-Shamir-Adleman (RSA)
- asymmetric encryption algorithm
- 2048 bits (large space)
- rely on mathematical properties of prime numbers

Elliptic Curve Cryptography (ECC)
- asymmetric algorithm
- 256 bits (more efficient than RSA)
- rely on structure of elliptic curves over finite fields

Advanced Encryption Standard
- symmetric algorithm
- rely on plaintext, divided into fixed-sized blocks of 128 bits

HTTPS uses a combination of algorithms. For example, the connection could use
RSA or ECC for generating asymmetric keys during the handshake (and also
contribute to the creating of the premaster key), and then later
transition to using AES encryption for ongoing communication.


Given base data set [a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z]

Algo: Shift 4 letters from current.

~~ Symmetric Scenario
"secret" -> encryption algo (move letters from current) + private key (4) -> wigvix
wigvix -> algo (reverse letters from current) + private key (4) -> "secret"

~~ Asymmetric Scenario

"secret" -> encryption algo (move forward letters from current) + encryption key (4) -> wigvix
wigvix -> algo (move forward letters from current) + decryption key (22) -> "secret"

The ecryption:decryption (public:private) key pairs must be related in some way.
In the alphabet dataset there are 26 letters. The ecryption key has 4 letters,
the decryption key has 22 letters. 4 + 22 => 26, or a valid mathematical relation
between the keys.

A public:private keypair must always be mathematically related & valid.
--- 

HTTPS:
- session establishment cannot be initially done with **symmetric keys**
- uses a combination of asymmetric & symmetric encryption

