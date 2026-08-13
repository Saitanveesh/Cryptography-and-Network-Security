# Playfair Cipher — Worked Example

Using the `MONARCHY` matrix:

```text
M O N A R
C H Y B D
E F G I K
L P Q S T
U V W X Z
```

Take:

```text
P = INSTRUMENTS
```

Prepared digraphs:

```text
IN ST RU ME NT SX
```

Working pair by pair:

```text
IN → GA   rectangle
ST → TL   same row
RU → MZ   rectangle
ME → CL   same column
NT → RQ   rectangle
SX → XA   same column
```

So I get:

```text
C = GATLMZCLRQXA
```

This example is useful because it contains all three Playfair cases in one message.