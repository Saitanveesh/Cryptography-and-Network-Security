# Cryptography and Network Security

A beginner-friendly learning repository where I rebuild the concepts I study in **Cryptography and Network Security (CNS)** using consistent terminology, simple explanations, diagrams, equations, examples, and an attacker-focused view.

This is **not a dump of classroom notes**. Each topic is rewritten as a small learning module so that the idea can be understood without being in the class where it was taught.

---

## How this repository is organized

Each major topic has its own folder and its own `README.md`.

| # | Topic | Status |
|---|---|---|
| 01 | [Cryptography Fundamentals](./01-Cryptography-Fundamentals/) | Complete |
| 02 | [OSI Security Architecture](./02-OSI-Security-Architecture/) | Complete |
| 03 | [Network Security Model](./03-Network-Security-Model/) | Complete |
| 04 | Classical Cryptography | Next |

The repository grows in the same order as the course. Topics are added after they are studied, then improved with clearer explanations, diagrams, examples, and security reasoning.

---

## One notation used throughout

To avoid changing symbols from one topic to another, the same notation is used across this repository.

| Symbol | Meaning |
|---|---|
| `P` | Plaintext: the original readable data |
| `K` | Key: the value used by the cryptographic algorithm |
| `E` | Encryption operation |
| `C` | Ciphertext: the encrypted form of the plaintext |
| `D` | Decryption operation |

Encryption is written as:

```text
C = E_K(P)
```

Decryption is written as:

```text
P = D_K(C)
```

These symbols keep the same meaning everywhere in this repository.

---

## One set of words used throughout

For clarity, the repository also keeps the same wording from topic to topic.

- **Sender**: the person or system sending data.
- **Receiver**: the intended person or system receiving data.
- **Attacker**: an unauthorized party trying to observe, modify, recover, or misuse protected information.
- **Plaintext**: readable original data.
- **Ciphertext**: encrypted data.
- **Key**: a value used by a cryptographic algorithm.

The repository uses **attacker** consistently instead of switching between terms such as intruder, hacker, enemy, or adversary unless a later topic requires a more precise distinction.

---

## How each topic is explained

Most modules follow the same learning flow:

```text
Concept
  ↓
Simple meaning
  ↓
How it works
  ↓
Equation or model
  ↓
Example
  ↓
Attacker's View
  ↓
Key takeaway
```

The **Attacker's View** is important. Security is easier to understand when we study not only what the sender and receiver are doing, but also what information an attacker can observe and what the attacker would need to break the protection.

---

## Session 01

The first session currently covers three foundations:

1. **Cryptography Fundamentals**: what cryptography means and the basic vocabulary used throughout the subject.
2. **OSI Security Architecture**: security attacks, security services, and security mechanisms.
3. **Network Security Model**: sender, receiver, encryption, ciphertext, decryption, keys, key space, and the attacker's position in the communication path.

Classical cryptography will be added next as the course progresses.

---

## Goal

The goal is simple: by the end of the course, this repository should work as a connected map of CNS concepts rather than a collection of disconnected definitions.

Each new topic should make the previous topics more useful, not replace their terminology.