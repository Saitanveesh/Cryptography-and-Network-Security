# Playfair Cipher — Encryption Rules

Once I have a valid digraph, I locate both letters in the same 5×5 matrix.

Using the `MONARCHY` matrix:

```text
M O N A R
C H Y B D
E F G I K
L P Q S T
U V W X Z
```

Every pair falls into one of three cases.

## 1. Same row

For encryption I move both letters **one place to the right**.

```text
same row → RIGHT
```

I wrap around at the right edge.

Example:

```text
MO → ON
RM → MO
```

## 2. Same column

For encryption I move both letters **one place down**.

```text
same column → DOWN
```

I wrap around at the bottom.

Example:

```text
ME → CL
UM → MC
```

## 3. Rectangle

If the letters are in different rows and different columns, I keep each letter's row and take the other letter's column.

I remember it as:

```text
keep ROWS
swap COLUMNS
```

Example:

```text
H = row 2, column 2
I = row 3, column 4
```

After swapping columns:

```text
row 2, column 4 = B
row 3, column 2 = F
```

So:

```text
HI → BF
```

## The short version I remember

```text
ROW       → RIGHT
COLUMN    → DOWN
RECTANGLE → SWAP COLUMNS
```

At the edges, I wrap around instead of stopping.