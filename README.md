# Cryptography and Network Security

I started this repository to keep track of what I am learning in **Cryptography and Network Security (CNS)**.

I did not want to upload class notes as they are. After each topic, I come back here and write what I understood in my own words, keep the notation consistent, add the doubts I had while learning it, work through examples, and then look at the same idea from the Attacker's side.

Some topics also use **_Introduction to Modern Cryptography, Second Edition_ by Jonathan Katz and Yehuda Lindell** as a reference. I use it to check concepts and go a little deeper where needed, but I am not reproducing the book here.

---

## Topics so far

| # | Topic | Status |
|---|---|---|
| 01 | [Cryptography Fundamentals](./01-Cryptography-Fundamentals/) | Done |
| 02 | [OSI Security Architecture](./02-OSI-Security-Architecture/) | Done |
| 03 | [Network Security Model](./03-Network-Security-Model/) | Done |
| 04 | [Classical Cryptography — Caesar Cipher](./04-Classical-Cryptography/) | Done |
| 05 | [Playfair Cipher — Part I](./05-Playfair-Cipher/) | Current |

I am adding topics in the same order I learn them in class. If something has not been taught yet, I leave it for later instead of filling the repo with material I have not actually worked through.

---

## The notation I am keeping everywhere

One thing that confused me while reading different sources was that the same thing was sometimes written with different symbols. I do not want that happening here.

So I am keeping this fixed:

| Symbol | Meaning |
|---|---|
| `P` | Plaintext |
| `K` | Key |
| `E` | Encryption operation |
| `C` | Ciphertext |
| `D` | Decryption operation |

I write encryption as:

```text
C = E_K(P)
```

and decryption as:

```text
P = D_K(C)
```

If I need to talk about one letter inside a message, I use an index without changing the base notation:

```text
P_i = one plaintext symbol
C_i = one ciphertext symbol
```

---

## Words I keep consistent

I also keep the same names for the people and data in the examples:

```text
Sender
Receiver
Attacker
Plaintext P
Ciphertext C
Key K
Encryption
Decryption
```

I use **Attacker** throughout instead of randomly changing between hacker, intruder, adversary, enemy, and other words unless a later topic really needs a more specific term.

---

## How I write a topic

I normally start with what was discussed in class, then I follow the questions that came to me while trying to understand it.

Something like this:

```text
What was introduced?
        ↓
What does it actually mean?
        ↓
Why is it done this way?
        ↓
How does it work step by step?
        ↓
Can I solve one example myself?
        ↓
What does the Attacker see?
        ↓
Where does this method fail?
```

I do not force every topic into exactly the same template. Some topics need equations, some need diagrams, and some make more sense when I can actually try them in a small simulator.

---

## Interactive labs

I do not want the repo to be only something to scroll through.

For topics where trying the method helps, I am adding small browser labs. The plan is to keep them guided so a person opening one for the first time knows what to do instead of being dropped into a page full of inputs.

Current labs cover:

- Caesar encryption and decryption;
- Caesar brute-force from the Attacker's side;
- frequency analysis;
- Playfair keyword-matrix construction and plaintext digraph preparation.

The live-lab files are kept under [`docs/`](./docs/). Once GitHub Pages is enabled for the repository, they can be opened directly as a small website instead of downloading HTML files.

---

## Where I am now

I started with the basic terms such as plaintext, ciphertext, key, encryption, and decryption. From there I moved into the OSI security architecture and then the basic sender–receiver–attacker model.

After that I started classical cryptography. I first worked only with **symmetric encryption**, then substitution and transposition, monoalphabetic and polyalphabetic substitution, and finally the Caesar cipher. Once Caesar was clear, I looked at why it fails from the Attacker's side using brute force and frequency analysis.

The next topic I am working on is **Playfair Cipher**. For now I am stopping at the 5×5 keyword matrix and the preparation of plaintext into digraphs. I will add the actual Playfair encryption rules only after they are taught in class.

---

## Reference I am using

Jonathan Katz and Yehuda Lindell, **_Introduction to Modern Cryptography_**, Second Edition, CRC Press.

I use it along with what is taught in class and other checks when I need to make sure I have understood a concept correctly.