#### Important terms
- **Plaintext** is the original, readable message or data before it’s encrypted. It can be a document, an image, a multimedia file, or any other binary data.
- **Ciphertext** is the scrambled, unreadable version of the message after encryption. Ideally, we cannot get any information about the original plaintext except its approximate size.
- **Cipher** is an algorithm or method to convert plaintext into ciphertext and back again. A cipher is usually developed by a mathematician.
- **Key** is a string of bits the cipher uses to encrypt or decrypt data. In general, the used cipher is public knowledge; however, the key must remain secret unless it is the public key in asymmetric encryption. We will visit asymmetric encryption in a later task.
- **Encryption** is the process of converting plaintext into ciphertext using a cipher and a key. Unlike the key, the choice of the cipher is disclosed.
- **Decryption** is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key. Although the cipher would be public knowledge, recovering the plaintext without knowledge of the key should be impossible (infeasible).

- **Authentication**: You want to be sure you communicate with the right person, not someone else pretending.
- **Authenticity**: You can verify that the information comes from the claimed source.
- **Integrity**: You must ensure that no one changes the data you exchange.
- **Confidentiality**: You want to prevent an unauthorised party from eavesdropping on your conversations.

## Old Cyphers
## 1. Caesar Cipher

**How it works:**  
Shifts each letter a fixed number of places in the alphabet (e.g., A → D with a shift of 3).

**Example:**  
HELLO → KHOOR

**Why it matters:**

- One of the **earliest known ciphers**
- Easy to break using brute force (only 25 possible shifts)

## 2. Atbash Cipher

**How it works:**  
Reverses the alphabet (A ↔ Z, B ↔ Y).

**Example:**  
HELLO → SVOOL

**Why it matters:**

- Simple substitution cipher
- Used in ancient Hebrew texts

## 3. Substitution Cipher

**How it works:**  
Each letter is replaced with another letter using a fixed but random mapping.

**Example:**  
A → Q, B → M, C → L, etc.

**Why it matters:**

- Much stronger than Caesar
- Vulnerable to **frequency analysis**

## 4. Vigenère Cipher

**How it works:**  
Uses a keyword to shift letters differently throughout the message.

**Example:**  
Text: HELLO  
Key: KEY  
Result: RIJVS

**Why it matters:**

- Once called _“le chiffre indéchiffrable”_ (unbreakable cipher)
- Later broken using statistical analysis (Kasiski examination)

## 5. Playfair Cipher

**How it works:**  
Encrypts **pairs of letters** using a 5×5 grid based on a keyword.

**Why it matters:**

- Used by militaries in the 19th–20th century
- Harder to break than single-letter ciphers

## 6. Rail Fence Cipher (Transposition)

**How it works:**  
Rearranges letters by writing them in a zigzag pattern across rows.

**Example:**  
HELLO WORLD → HLOOL ELWRD

**Why it matters:**

- Changes **letter order**, not letters themselves
- Weak alone, stronger when combined with substitution

## 7. Scytale (Ancient Greek Cipher)

**How it works:**  
Message is wrapped around a rod; only a rod of the same diameter can read it.

**Why it matters:**

- One of the first **transposition ciphers**
- Physical-key based encryption

## 8. Enigma Machine (WWII)

**How it works:**  
Electromechanical cipher using rotating rotors and plugboards.

**Why it matters:**

- Used by Nazi Germany
- Broken by Alan Turing and others
- Changed the course of WWII

## 9. One-Time Pad (OTP)

**How it works:**  
Uses a random key as long as the message, used only once.

**Why it matters:**

- **Provably unbreakable** if used correctly
- Impractical for most real-world use

## Type of encryption

#### Symmetric Encryption

**Symmetric encryption**, also known as **symmetric cryptography**, uses the same key to encrypt and decrypt the data, as shown in the figure below. Keeping the key secret is a must; it is also called **private key cryptography**. Furthermore, communicating the key to the intended parties can be challenging as it requires a secure communication channel.

Examples of symmetric encryption are DES (Data Encryption Standard), 3DES (Triple DES) and AES (Advanced Encryption Standard).

- **DES** was adopted as a standard in 1977 and uses a 56-bit key. With the advancement in computing power, in 1999, a DES key was successfully broken in less than 24 hours, motivating the shift to 3DES.
- **3DES** is DES applied three times; consequently, the key size is 168 bits, though the effective security is 112 bits. 3DES was more of an ad-hoc solution when DES was no longer considered secure. 3DES was deprecated in 2019 and should be replaced by AES; however, it may still be found in some legacy systems.
- **AES** was adopted as a standard in 2001. Its key size can be 128, 192, or 256 bits.


#### Asymmetric Encryption

Unlike symmetric encryption, which uses the same key for encryption and decryption, **asymmetric encryption** uses a pair of keys, one to encrypt and the other to decrypt, as shown in the illustration below. To protect confidentiality, asymmetric encryption or **asymmetric cryptography** encrypts the data using the public key; hence, it is also called **public key cryptography**.

Examples are RSA, Diffie-Hellman, and Elliptic Curve cryptography (ECC). The two keys involved in the process are referred to as a **public key** and a **private key**. Data encrypted with the public key can be decrypted with the private key. Your private key needs to be kept private, hence the name.

## Public key encryptions

#### RSA
RSA is based on the mathematically difficult problem of factoring a large number. Multiplying two large prime numbers is a straightforward operation; however, finding the factors of a huge number takes much more computing power.

It’s simple to multiply two prime numbers together even on paper, say 113 × 127 = 14351. Even for larger prime numbers, it would still be a feasible job, even by hand. Consider the following numeric example:

- Prime number 1: 982451653031
- Prime number 2: 169743212279
- Their product: 982451653031 × 169743212279 = 166764499494295486767649

#### Diffie-Hellman Key Exchange
**Key exchange** aims to establish a shared secret between two parties. It is a method that allows two parties to establish a shared secret over an insecure communication channel without requiring a pre-existing shared secret and without an observer being able to get this key. Consequently, this shared key can be used for symmetric encryption in subsequent communications.

If you found the previous paragraphs too abstract, let’s investigate the exact process.

1. Alice and Bob agree on the **public variables**: a large prime number _p_ and a generator _g_, where 0 < _g_ < _p_. These values will be disclosed publicly over the communication channel. Although insecurely small, we will choose _p_ = 29 and _g_ = 3 to simplify our calculations.
2. Each party chooses a private integer. As a numerical example, Alice chooses _a_ = 13, and Bob chooses _b_ = 15. Each of these values represents a **private key** and must not be disclosed.
3. It is time for each party to calculate their **public key** using their private key from step 2 and the agreed-upon public variables from step 1. Alice calculates _A_ = _g__a_ mod _p_ = 313 mod 29 = 19 and Bob calculates _B_ = _g__b_ mod _p_ = 315 mod 29 = 26. These are the public keys.
4. Alice and Bob send the keys to each other. Bob receives _A_ = _g__a_ mod _p_ = 19, i.e., Alice’s public key. And Alice receives _B_ = _g__b_ mod _p_ = 26, i.e., Bob’s public key. This step is called the **key exchange**.
5. Alice and Bob can finally calculate the **shared secret** using the received public key and their own private key. Alice calculates _B__a_ mod _p_ = 2613 mod 29 = 10 and Bob calculates _A__b_ mod _p_ = 1915 mod 29 = 10. Both calculations yield the same result, _g__a__b_ mod _p_ = 10, the shared secret key.

## SSH

- **DSA (Digital Signature Algorithm)** is a public-key cryptography algorithm specifically designed for digital signatures.
- **ECDSA (Elliptic Curve Digital Signature Algorithm)** is a variant of DSA that uses elliptic curve cryptography to provide smaller key sizes for equivalent security.
- **ECDSA-SK (ECDSA with Security Key)** is an extension of ECDSA. It incorporates hardware-based security keys for enhanced private key protection.
- **Ed25519** is a public-key signature system using EdDSA (Edwards-curve Digital Signature Algorithm) with Curve25519.
- **Ed25519-SK (Ed25519 with Security Key)** is a variant of Ed25519. Similar to ECDSA-SK, it uses a hardware-based security key for improved private key protection.

#### Steps 
-  SSH client confirms whether we recognise the server’s public key fingerprint.
- If SSH client didn’t recognise this key it asks us to confirm whether we want to continue with the connection. This warning is because a man-in-the-middle attack is probable; a malicious server might have intercepted the connection and replied, pretending to be the target server.
- In many cases, SSH users are authenticated using usernames and passwords like you would log in to a physical machine
- In some cases SSH may be configured with key authentication instead. This authentication uses public and private keys to prove the client is a valid and authorised user on the server. By default, SSH keys are RSA keys.

## Digital Signatures and Certificate

Digital signatures provide a way to verify the authenticity and integrity of a digital message or document. Proving the authenticity of files means we know who created or modified them. Using asymmetric cryptography, you produce a signature with your private key, which can be verified using your public key. Only you should have access to your private key, which proves you signed the file. In many modern countries, digital and physical signatures have the same legal value.

Certificates are an essential application of public key cryptography, and they are also linked to digital signatures.

## PGP and GPG
**PGP** stands for Pretty Good Privacy. It’s software that implements encryption for encrypting files, performing digital signing, and more. [GnuPG or GPG](https://gnupg.org/) is an open-source implementation of the OpenPGP standard.
GPG is commonly used in email to protect the confidentiality of the email messages. Furthermore, it can be used to sign an email message and confirm its integrity.


