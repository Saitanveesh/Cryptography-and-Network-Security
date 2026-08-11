# 01 — Cryptography Fundamentals

This was where I started in class: before touching any cipher, I first had to be clear about the words being used.

The first question I wrote down was simple:

> If I send some readable information through a place where someone else may see it, how do I stop that person from understanding it?

That question led to the basic terms below.

---

## 1. Cryptography

I understood **cryptography** as the use and study of methods that protect information by transforming it in a controlled way.

For the examples in this repo, I keep the basic flow as:

```text
Plaintext P
    ↓
Encryption using K
    ↓
Ciphertext C
```

The first thing I noticed is that these words are not interchangeable. `P`, `K`, and `C` each mean something different, so I keep them separate everywhere in the repo.

---

## 2. Plaintext `P`

**Plaintext** is the original readable information before encryption.

I write it as:

```text
P
```

Example:

```text
P = MEET AT 10
```

It could be text, a file, part of a network packet, or any other data that is being protected.

---

## 3. Key `K`

Next came the **key**.

I write the key as:

```text
K
```

The easiest way I understood it was this: the algorithm is the method, while `K` is the value used with that method.

So I do not treat these as the same thing:

```text
Algorithm ≠ Key
```

---

## 4. Encryption `E`

Encryption takes plaintext `P` and uses key `K` to produce ciphertext `C`.

I keep the same equation throughout the repo:

```text
C = E_K(P)
```

I read it as:

```text
Encrypt P using K and get C.
```

---

## 5. Ciphertext `C`

**Ciphertext** is the encrypted output.

I write it as:

```text
C
```

So the flow becomes:

```text
P ── E_K ──> C
```

At this point I had a useful distinction:

```text
P = readable original data
C = encrypted data
```

---

## 6. Decryption `D`

To get the plaintext back, decryption is applied to `C` using the required key `K`.

I write:

```text
P = D_K(C)
```

So the full cycle is:

```text
P ── E_K ──> C ── D_K ──> P
```

These are the two equations I keep using later:

```text
C = E_K(P)
P = D_K(C)
```

---

## 7. Cipher

Then came another word that is easy to mix up with the key.

A **cipher** is the defined method used to perform a cryptographic transformation.

I keep it like this:

```text
Cipher / algorithm = the method
K                  = the key used with it
P                  = input plaintext
C                  = output ciphertext
```

---

## 8. Cryptography, cryptanalysis, and cryptology

These three names sounded almost the same at first, so I separated them.

### Cryptography

This is the side where methods are designed or used to protect information.

### Cryptanalysis

This is the side where someone studies a cryptographic system to find weaknesses or recover protected information without being given the intended secret.

### Cryptology

This is the broader field containing both.

```text
Cryptology
├── Cryptography
└── Cryptanalysis
```

That made the naming much easier for me:

```text
Cryptography  → protection side
Cryptanalysis → breaking / analysis side
Cryptology    → both together
```

---

## 9. Then I looked at the Attacker

Once `P`, `K`, and `C` were clear, I asked a different question:

> What does the Attacker actually get to see?

For a simple network example:

```text
Sender                              Receiver
  │                                    ▲
  │ P                                  │ P
  ▼                                    │
E_K(P) ─────────── C ───────────────> D_K(C)
                    │
                    │ copied
                    ▼
                 Attacker
```

The Attacker may be able to copy:

```text
C
```

but that does not mean the Attacker automatically knows:

```text
P
K
```

Another thing that became clear here is that I should not assume the algorithm itself is secret. The Attacker may know how `E` works and still be missing `K`.

So the version I keep in mind is:

```text
Attacker may know: E and C
Attacker should not automatically know: K and P
```

This is the same Attacker view I use in the later topics.