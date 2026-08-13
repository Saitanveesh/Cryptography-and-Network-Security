# Hill Cipher — Solved Questions and Shortcuts

I collected the small checks here because most Hill-cipher mistakes happen before the final multiplication.

---

## Question 1 — Can this key be used?

Take:

```text
K = [2 4]
    [2 6]
```

Determinant:

```text
det(K) = (2×6) - (4×2)
       = 12 - 8
       = 4
```

Now:

```text
gcd(4,26) = 2
```

This is not 1, so the matrix has no inverse modulo 26.

I stop here. There is no point trying to calculate `K^-1`.

---

## Question 2 — Another forward example

Use:

```text
K = [7  8]
    [11 11]
```

and:

```text
P = MATH
```

Split:

```text
MA  TH
```

For `MA`:

```text
M = 12
A = 0

[7  8] [12]   [84]
[11 11] [ 0] = [132]
```

Modulo 26:

```text
84 mod 26  = 6 = G
132 mod 26 = 2 = C
```

So:

```text
MA → GC
```

For `TH`:

```text
T = 19
H = 7

[7  8] [19]   [189]
[11 11] [ 7] = [286]
```

Modulo 26:

```text
189 mod 26 = 7 = H
286 mod 26 = 0 = A
```

Therefore:

```text
MATH → GCHA
```

---

## Question 3 — Find the inverse of the second key

For:

```text
K = [7  8]
    [11 11]
```

Determinant:

```text
77 - 88 = -11
```

Reduce it modulo 26:

```text
-11 mod 26 = 15
```

Now find the inverse of 15:

```text
15 × 7 = 105
105 mod 26 = 1
```

So:

```text
15^-1 mod 26 = 7
```

Adjugate:

```text
[ 11  -8]
[-11   7]
```

Multiply by 7 and reduce modulo 26:

```text
K^-1 = [25 22]
       [ 1 23]
```

That is the matrix I would use to reverse the earlier `GCHA` result.

---

# Shortcuts I keep beside the formulas

## 1. Check the determinant before doing anything long

For modulo 26:

```text
valid only if gcd(det(K),26) = 1
```

Since:

```text
26 = 2 × 13
```

an even determinant or a determinant divisible by 13 is immediately invalid.

## 2. Negative modulo is not negative in the final answer

Examples:

```text
-3 mod 26  = 23
-9 mod 26  = 17
-11 mod 26 = 15
```

I can keep adding 26 until the value is between 0 and 25.

## 3. Reduce early

After each row multiplication I reduce modulo 26. This keeps the numbers small and makes arithmetic easier to check.

## 4. Do not use the normal decimal inverse

Hill cipher needs the inverse **modulo 26**.

The important part is:

```text
determinant inverse mod 26
×
adjugate
×
mod 26
```

## 5. Matrix order matters

This repo uses column vectors:

```text
C = K P mod 26
```

If I copy a worked example from a source using row vectors, the result may differ even when both calculations are internally correct. I first check the convention instead of assuming one answer is wrong.

## 6. Block size follows matrix size

```text
2×2 K → 2 letters per block
3×3 K → 3 letters per block
```

If the final block is short, a filler has to be added according to the convention being used.

---

## My exam-order checklist

When I see a Hill-cipher question, I do it in this order:

```text
1. Write A=0 ... Z=25.
2. Check whether vectors are rows or columns.
3. Write K clearly.
4. For reverse work, calculate det(K) first.
5. Check gcd(det(K),26)=1.
6. Find det(K)^-1 mod 26.
7. Form the adjugate.
8. Reduce K^-1 mod 26.
9. Multiply one block at a time.
10. Apply mod 26 after every block.
11. Convert numbers back to letters.
```

That order saves me from doing a page of work with a key matrix that was invalid from the beginning.