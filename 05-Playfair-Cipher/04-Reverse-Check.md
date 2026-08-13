# Playfair Cipher — Reverse Check

To recover the prepared pairs, I undo the movement used before:

```text
same row    → one place left
same column → one place up
rectangle   → keep rows and swap columns
```

The same edge wrapping still applies.

For the examples I already used:

```text
ON → MO
CL → ME
BF → HI
```

This gives me an easy check that the forward and reverse rules are consistent.