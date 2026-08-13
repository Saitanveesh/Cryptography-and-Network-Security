# 05 — Playfair Cipher

I have now completed the Playfair cipher material covered in class.

I split it into small parts because the setup and the matrix movement are easier to follow separately.

1. [Keyword matrix and plaintext preparation](./01-Preparation.md)
2. [The three matrix rules](./02-Rules.md)
3. [Full worked example](./03-Worked-Example.md)
4. [Reverse check](./04-Reverse-Check.md)

The short rule set I keep beside the matrix is:

```text
Forward:
ROW       → RIGHT
COLUMN    → DOWN
RECTANGLE → SWAP COLUMNS

Reverse:
ROW       → LEFT
COLUMN    → UP
RECTANGLE → SWAP COLUMNS
```

The same `MONARCHY` matrix and the same `I/J` convention are used across all four pages so I do not change rules halfway through the topic.