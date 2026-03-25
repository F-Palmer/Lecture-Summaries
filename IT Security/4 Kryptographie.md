Prev: [[3 Threat Modelling]] Next: [[5 Authentication]]


Def: Lehre der Verschlüsselung von Daten.

> Kerckhoff's  Prinzip:
> die Sicherheit eines Kryptosystems darf nicht von der Geheimhaltung des Algorithmus abhängen. Die Sicherheit gründet sich nur auf die Geheimhaltung des Schlüssels

## Symmetric Cryptography
Secret/ Private key
![[Sym Cryp.png]]
Based on a shared secrete key

1. Alice encrypts with the key
2. Bob decrypts with the key

> Stromchiffren: 
> verschlüsseln jedes Bit einzeln

### Blockchiffren: 
verschlüsseln einen Block von Bits gleichzeitig
z.B. Advanced Encryption Standard (AES)
Blocklänge ist immer 16 Byte
Schlüssellänge variiert
Jeder Block einzeln und unabhängig

Problem: 
gleiche Blöcke werden gleich verschlüsselt

#### Modes of Operation
Blöcke zu verknüpfen
Verschlüsselung nicht deterministisch zu machen

> Cipher Block Chaining mode (CBC): 
> 1. Create an initialized vecotor (IV) 
>    A block of the same size as the rest of the blocks, containing random values
> 2. For each Block: 
>    ```
>     if first block: 
> 	   cipher[0] = Encrypt(block[0] XOR IV)
> 	else:
> 		cipher[x] = Encrypt(block[x] XOR block[x-1])
>    ```
>
> Decrypting: 
> ```
> block = IV + block
> plaintext = Decrypt(block[x]) XOR block[x-1]
> ```
> IV is not secret, it is sent with the ciphertext

## Asymmetric Cryptography
Everyone can send a message with the public key but only the owner of the private key can decrypt the message
![[Async Cryp.png]]
Schlüssellängen > 2048 Bit

### RSA

Algorithmus: 
```
p, q = (big) prime numbers 
N = p * q
c = (p - 1)*(q-1)
e = so that 0 < e < c and ggT(e, c) = 1
d = so that d * e \equiv 1 mod c
```
Private key: (N, d)
Public key: (N, e) 

Zwei Primzahlen zu multiplizieren ist einfach, die Umkehrung ist extrem schwer. 

Verschlüsselungsfunktion:
$c \equiv m^e (\mod N)$
Entschlüsselung: 
$m \equiv c^d (\mod N)$

### Elliptic Curve Cryptography (ECC)
Steht nicht auf seiner Klausurthemenübersicht

## Vorteile/ Nachteile von (A)symmetrischer Verschlüsselung

|               | Symmetrisch                                                                                                                                                  | Asymmetrisch                                                                                     |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Vorteile**  | - Weniger Rechenintensiv als Public Key Krypto (Asymmetrisch??)<br>- Performance<br>- Optimierung für Hardwareimplementierung möglich<br>- kürzere Schlüssel | - Publik Key kann öffentlich abgelegt werden                                                     |
| **Nachteile** | Schlüsselverteilungsproblem (Jeder Teilnehmer muss den Schlüssel kennen)                                                                                     | - lange Schlüssel<br>- Rechenintensiv<br>- Nachricht darf max. so lang sein wie der Schlüssel () |

## Hybride Kryptoverfahren

Public Key Krypto um die symmetrischen Schlüssel zu verteilen
-> Löst Schlüsselverteilungsproblem
Daten mit symmetrischer Krypto verschlüsseln
-> Performance Gewinn 
-> beliebig lange Daten können verschlüsselt werden

![[Hybrid Crypto.png]]

## Kryptographische Hash Funktionen
Bilden beliebigen Input auf einen Output mit fixer Länge ab
- Einwegfunktion
- Starke Kollisionsresistenz

### Message Authentication Codes (MAC)
Temper proof signature so you can check: 
- Who sent it? (authenticity)
- Whether it was changed? (integrity)

Uses a shared secret key -> without key the hash can not be verified
```python
M = message
K = secret key
MAC() = MAC algorithm
# sender computes a tag: 
tag = MAC(K, M)
# Sender sends: 
M, tag
# Receiver computes: 
tag2 = MAC(K, M)
if tag = tag2: 
	# Message is authentic 
```
The message is not encrypted by this, this has to be done separately

HMAC is a standard algorithm that uses a hash function like SHA

## Signaturen
Basiert of public keys
Beim Signieren aber umgedreht

Ziel: Eindeutige Autoren
Signieren mit Private Key
Verifizieren mit Public Key

Hash der Nachricht wird signiert
RSA, DSA, ECDSA
![[Signing.png]]
