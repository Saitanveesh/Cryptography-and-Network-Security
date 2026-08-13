# 05 — Playfair Cipher: Part I

After Caesar, the next cipher introduced in class was the **Playfair cipher**.

The first difference I noticed was that Caesar works on one letter at a time, while Playfair works on **pairs of letters**.

Those two-letter groups are called **digraphs**.

For now I am stopping before the actual encryption rules. I first wanted to get the setup right: where Playfair came from, how the keyword becomes a 5×5 matrix, and how plaintext `P` has to be prepared before encryption can even begin.

---

## 1. A little background

The Playfair cipher was devised by **Charles Wheatstone** in the 19th century and was later promoted by **Lord Playfair**, whose name became attached to the cipher.

Unlike Caesar, it does not encrypt each letter independently.

Instead of:

```text
A
T
T
A
C
K
```

Playfair starts by preparing pairs such as:

```text
AT  TA  CK
```

That immediately gave me a question:

> If the cipher works on pairs, how do I decide which two letters belong together?

Before answering that, I first needed the Playfair matrix.

---

# 2. The keyword

Playfair starts with a **keyword**.

I will use this example throughout the page:

```text
KEYWORD = MONARCHY
```

The keyword is not copied blindly into the matrix. I first:

```text
1. convert it to uppercase;
2. remove spaces and non-letters;
3. merge J with I for the 5×5 convention used here;
4. remove repeated letters while keeping the first occurrence.
```

For:

```text
MONARCHY
```

there are no repeated letters, so the cleaned keyword stays:

```text
MONARCHY
```

If the keyword were:

```text
BALLOON
```

I would remove later repetitions and keep:

```text
BALON
```

The order matters. I keep the first occurrence of each letter.

---

# 3. Why is the matrix 5×5?

This was my next question because English has 26 letters:

```text
26 letters
```

but a 5×5 matrix has only:

```text
5 × 5 = 25 cells
```

So one pair of letters has to share a cell or be treated as one symbol.

The common convention I am using here is:

```text
I and J share one position
```

In practice, before building the matrix or preparing plaintext, I convert:

```text
J → I
```

That leaves 25 symbols for 25 cells.

```text
A B C D E
F G H I K
L M N O P
Q R S T U
V W X Y Z
```

Notice that `J` is not listed separately.

Different Playfair descriptions may use another convention, but I am keeping **I/J combined** consistently in this repo.

---

# 4. Building the 5×5 matrix from the keyword

I build the matrix in two stages.

## Step 1 — place the keyword letters

With:

```text
KEYWORD = MONARCHY
```

I place the unique letters from left to right, row by row:

```text
M O N A R
C H Y _ _
_ _ _ _ _
_ _ _ _ _
_ _ _ _ _
```

## Step 2 — fill the remaining alphabet

Now I continue with the alphabet and skip:

```text
letters already used in the keyword
J, because I/J share a position
```

The final matrix becomes:

```text
M O N A R
C H Y B D
E F G I K
L P Q S T
U V W X Z
```

I can check it by making sure:

```text
25 cells are filled
no letter appears twice
J is not separate
all remaining letters appear once
```

---

## 5. What rules am I applying to the matrix?

At this stage I am only setting up the matrix, not encrypting with it yet.

The matrix rules I am keeping are:

```text
1. Use a 5×5 grid.
2. Treat I and J as one symbol.
3. Put the cleaned keyword first.
4. Keep only the first occurrence of repeated keyword letters.
5. Fill unused letters in alphabetical order.
6. Never place the same letter twice.
```

One detail that helped me was to think of the matrix as being completely determined once I choose the keyword and the I/J convention.

The actual Playfair encryption movement inside the matrix comes later. I am not adding those rules until they are covered in class.

---

# 6. Preparing plaintext `P`

Once the matrix was clear, I moved to the plaintext.

Before splitting `P` into pairs, I first normalize it.

For this repo I use:

```text
1. convert to uppercase;
2. remove spaces and punctuation;
3. convert J → I.
```

Example:

```text
P = HIDE THE GOLD
```

becomes:

```text
HIDETHEGOLD
```

If the plaintext contains `J`:

```text
P = JUMP
```

I prepare it as:

```text
IUMP
```

because the matrix does not contain a separate `J`.

---

# 7. Splitting plaintext into digraphs

Now I start making two-letter groups.

If the letters are different, I simply keep the pair.

Example:

```text
P = ATTACK
```

Start from the left:

```text
AT  TA  CK
```

Each group has two letters, so the preparation is complete.

But two special cases appear:

```text
1. both letters in a pair are the same;
2. one letter is left at the end.
```

That is where the dummy letter is used.

---

# 8. Dummy letter `X`

The normal dummy/filler letter I use is:

```text
X
```

## Case 1 — repeated letters would form one pair

Suppose:

```text
P = BALLOON
```

If I simply split every two letters, I would get:

```text
BA  LL  OO  N
```

But `LL` contains the same letter twice, so I do **not** keep `LL` as one digraph.

Instead I insert `X` between the repeated letters.

Working from left to right:

```text
BA
```

Next I see:

```text
LL
```

so I make:

```text
LX
```

The second `L` is not discarded. I use it again when I continue reading the plaintext.

That gives:

```text
BA  LX  LO  ON
```

So the prepared form is:

```text
BALLOON → BA LX LO ON
```

This point matters: inserting `X` changes the pairing from that position onward.

---

## Case 2 — one letter is left at the end

Suppose:

```text
P = HELLO
```

Working through it:

```text
HE
LL → repeated, so use LX
LO
```

This becomes:

```text
HE  LX  LO
```

No letter is left at the end in this case.

For a clearer odd-length example:

```text
P = CAT
```

I get:

```text
CA  T
```

The last `T` needs a partner, so I append the filler:

```text
CA  TX
```

---

# 9. What if the plaintext itself contains `X`?

This is where blindly saying “always insert X” creates a problem.

Suppose the next pair would be:

```text
XX
```

If I tried to separate those repeated `X` letters by inserting another `X`, I would still have:

```text
XX
```

which has not solved anything.

So for this repository I use a fallback filler:

```text
Normal filler   = X
Fallback filler = Q when X would create an XX pair
```

### Example

Take:

```text
P = TAXXI
```

Start from the left:

```text
TA
```

The next two letters are:

```text
XX
```

Instead of inserting `X`, I use `Q`:

```text
XQ
```

Then I continue from the second original `X`:

```text
XI
```

So I prepare it as:

```text
TAXXI → TA XQ XI
```

The fallback `Q` is a convention I am choosing explicitly so the preprocessing rule stays deterministic.

---

## 10. What if the final unpaired letter is `X`?

The same problem can happen at the end.

Suppose the prepared plaintext leaves one final:

```text
X
```

Appending the normal filler `X` would create:

```text
XX
```

So I use the same fallback rule:

```text
X → XQ
```

Example:

```text
P = HELIX
```

The pairs become:

```text
HE  LI  X
```

The last `X` is unpaired, so:

```text
HE  LI  XQ
```

---

# 11. The plaintext-preparation procedure I am using

I can now write the whole preprocessing step without touching encryption yet.

```text
Input: Plaintext P

1. Convert P to uppercase.
2. Remove spaces and punctuation.
3. Convert J → I.
4. Start reading from the left.
5. Take two letters.
6. If the two letters are different, keep them as a digraph.
7. If they are the same:
      insert X after the first letter;
      but if that repeated letter is X, insert Q instead.
8. Continue from the second original repeated letter.
9. If one letter remains at the end:
      append X;
      but if the remaining letter is X, append Q.
10. Stop when every letter belongs to a two-letter digraph.
```

A few examples together:

| Original `P` | Prepared digraphs |
|---|---|
| `ATTACK` | `AT TA CK` |
| `BALLOON` | `BA LX LO ON` |
| `CAT` | `CA TX` |
| `TAXXI` | `TA XQ XI` |
| `HELIX` | `HE LI XQ` |
| `JUMP` | `IU MP` |

---

# 12. Where I am stopping

At this point I can:

```text
choose a keyword
        ↓
clean the keyword
        ↓
build the 5×5 matrix
        ↓
normalize P
        ↓
split P into valid digraphs
```

The next question is obviously:

> Once I have a digraph and both letters are somewhere inside the 5×5 matrix, how do I produce the ciphertext pair?

That is the actual Playfair encryption step. I am leaving it for the next update after it is taught in class.

For now, the interactive lab only builds the matrix and prepares digraphs. It does **not** pretend to teach encryption early.