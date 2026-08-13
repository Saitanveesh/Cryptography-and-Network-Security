# Hill Cipher — Reverse Calculation

Once I have `K^-1`, I use it on each ciphertext block.

For the earlier example:

```text
K^-1 = [15 17]
       [20  9]
```

and:

```text
C = HIAT
```

I split it into:

```text
HI  AT
```

## Block 1: HI

```text
H = 7
I = 8

C = [7]
    [8]
```

Multiply by `K^-1`:

```text
[15 17] [7]   [241]
[20  9] [8] = [212]
```

Reduce modulo 26:

```text
241 mod 26 = 7 = H
212 mod 26 = 4 = E
```

So:

```text
HI → HE
```

## Block 2: AT

```text
A = 0
T = 19
```

```text
[15 17] [ 0]   [323]
[20  9] [19] = [171]
```

Reduce modulo 26:

```text
323 mod 26 = 11 = L
171 mod 26 = 15 = P
```

So:

```text
AT → LP
```

Putting the blocks together:

```text
HIAT → HELP
```

The reverse formula I keep is:

```text
P = K^-1 C mod 26
```

This only works because the key matrix has a valid inverse modulo 26.