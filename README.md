# Cryptography and Network Security

I started this repository to keep track of what I am learning in **Cryptography and Network Security (CNS)**.

I do not upload class notes as they are. After each class, I come back here and write what I understood in my own words, keep the notation consistent, work through examples, and add small labs where trying the idea helps more than only reading it.

Some topics also use **_Introduction to Modern Cryptography, Second Edition_ by Jonathan Katz and Yehuda Lindell** as a reference. I use it to check concepts and go a little deeper where needed, but I am not reproducing the book here.

---

## Topics so far

| # | Topic | Status |
|---|---|---|
| 01 | [Cryptography Fundamentals](./01-Cryptography-Fundamentals/) | Done |
| 02 | [OSI Security Architecture](./02-OSI-Security-Architecture/) | Done |
| 03 | [Network Security Model](./03-Network-Security-Model/) | Done |
| 04 | [Classical Cryptography — Caesar Cipher](./04-Classical-Cryptography/) | Done |
| 05 | [Playfair Cipher](./05-Playfair-Cipher/) | Done |
| 06 | [Hill Cipher](./06-Hill-Cipher/) | Current |

I add topics in the same order I learn them in class. If something has not been taught yet, I leave it for later.

---

## Notation I keep consistent

```text
P = Plaintext
K = Key
E = Encryption
C = Ciphertext
D = Decryption
```

I write:

```text
C = E_K(P)
P = D_K(C)
```

For Hill cipher I also keep this convention:

```text
A = 0, B = 1, ..., Z = 25
column vectors
C = K P mod 26
P = K^-1 C mod 26
```

---

## Interactive labs

Current guided labs include:

- Caesar cipher;
- frequency analysis;
- Playfair matrix preparation and pair rules;
- Hill matrix checking, forward calculation, modular inverse, and reverse calculation.

The lab files are under [`docs/`](./docs/).

---

## Where I am now

I started with the basic terminology, moved through the OSI security architecture and the basic network-security model, and then started classical cryptography.

I completed Caesar cipher first. After that I completed **Playfair cipher**, including keyword-matrix construction, digraph preparation, same-row, same-column, rectangle rules, and reverse checking.

The current topic is **Hill cipher**. I am working through the matrix calculation carefully, especially the part that is usually skipped too quickly: checking whether the key matrix has an inverse modulo 26, calculating that inverse, and then using it in the reverse calculation.

---

## Reference I am using

Jonathan Katz and Yehuda Lindell, **_Introduction to Modern Cryptography_**, Second Edition, CRC Press.