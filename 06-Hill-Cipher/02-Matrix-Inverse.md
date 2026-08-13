# Hill Cipher — Matrix Inverse mod 26

This is the part I wanted written slowly because the inverse used in Hill cipher is **not** just the ordinary decimal matrix inverse.

For a 2×2 key:

```text
K = [a b]
    [c d]
```

I use four steps.

## Step 1 — determinant

```text
det(K) = ad - bc
```

For:

```text
K = [3 3]
    [2 5]
```

I get:

```text
det(K) = (3×5) - (3×2)
       = 15 - 6
       = 9
```

## Step 2 — check whether the inverse can exist

I need:

```text
gcd(det(K), 26) = 1
```

Here:

```text
gcd(9,26) = 1
```

so this key is valid.

A quick check I can use with modulo 26: if the determinant is even or divisible by 13, it cannot have an inverse modulo 26.

## Step 3 — modular inverse of the determinant

I need a number `x` such that:

```text
9x ≡ 1 (mod 26)
```

Trying small values:

```text
9 × 3 = 27
27 mod 26 = 1
```

So:

```text
9^-1 mod 26 = 3
```

## Step 4 — adjugate and modulo 26

For a 2×2 matrix:

```text
[a b]       [ d -b]
[c d]  →    [-c  a]
```

So:

```text
[3 3]       [ 5 -3]
[2 5]  →    [-2  3]
```

Now multiply by the determinant inverse `3`:

```text
3 × [ 5 -3]   [ 15  -9]
    [-2  3] = [ -6   9]
```

Reduce negative values modulo 26:

```text
-9 mod 26 = 17
-6 mod 26 = 20
```

Therefore:

```text
K^-1 = [15 17]
       [20  9]     mod 26
```

## Quick modular-inverse table

These are the values from 0 to 25 that actually have inverses modulo 26:

| `a` | `a^-1 mod 26` |
|---:|---:|
| 1 | 1 |
| 3 | 9 |
| 5 | 21 |
| 7 | 15 |
| 9 | 3 |
| 11 | 19 |
| 15 | 7 |
| 17 | 23 |
| 19 | 11 |
| 21 | 5 |
| 23 | 17 |
| 25 | 25 |

If the determinant reduces to a value outside this set, I know immediately that the matrix is not invertible modulo 26.