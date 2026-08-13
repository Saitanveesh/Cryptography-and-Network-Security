# Hill Cipher — Forward Calculation

For the examples here I use column vectors and:

```text
A = 0, B = 1, ..., Z = 25
```

With a 2×2 key matrix:

```text
K = [3 3]
    [2 5]
```

I take plaintext two letters at a time.

## Example: HELP

Split it as:

```text
HE  LP
```

For `HE`:

```text
H = 7
E = 4

P = [7]
    [4]
```

Multiply by `K`:

```text
[3 3] [7]   [33]
[2 5] [4] = [34]
```

Now reduce each value modulo 26:

```text
33 mod 26 = 7  = H
34 mod 26 = 8  = I
```

So:

```text
HE → HI
```

For `LP`:

```text
L = 11
P = 15

[3 3] [11]   [78]
[2 5] [15] = [97]
```

Reduce modulo 26:

```text
78 mod 26 = 0  = A
97 mod 26 = 19 = T
```

So:

```text
LP → AT
```

Putting both blocks together:

```text
HELP → HIAT
```

The formula I keep for the forward step is:

```text
C = K P mod 26
```

The order matters. I am using **column vectors**, so I do not switch midway to `P K`.