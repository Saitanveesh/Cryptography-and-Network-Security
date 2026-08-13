# 06 — Hill Cipher

After Playfair, I moved to the **Hill cipher**. This is where I started using matrix multiplication instead of looking up letters in a substitution table or grid.

I keep one convention from start to end:

```text
A = 0, B = 1, ..., Z = 25
plaintext blocks = column vectors
C = K P mod 26
P = K^-1 C mod 26
```

For a 2×2 key matrix, I work with two letters at a time.

I split the topic because the inverse calculation needs more space than the basic multiplication:

1. [Forward calculation](./01-Forward-Calculation.md)
2. [Finding the matrix inverse mod 26](./02-Matrix-Inverse.md)
3. [Reverse calculation using K^-1](./03-Reverse-Calculation.md)
4. [Solved questions and shortcuts](./04-Solved-Questions.md)

The first check I make before reverse work is:

```text
gcd(det(K), 26) = 1
```

If that condition fails, `K` has no inverse modulo 26.

The main example across these pages uses:

```text
K = [3 3]
    [2 5]
```

and follows the complete path:

```text
HELP → HIAT → HELP
```

I also included another key, an invalid-key question, a modular-inverse table, negative-modulo examples, and the order I use when solving Hill questions in an exam.