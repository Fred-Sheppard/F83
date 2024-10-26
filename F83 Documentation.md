## Terminology
### Token
- A single number or operator. To the best of our knowledge, each token takes up exactly 1 byte of space. A script may use 200 bytes/tokens before the input buffer runs out of memory.
### Expression
- A token or series of tokens that can be evaluated by the calculator
### Script
- An expression or series of expressions chained by `:` that can be run by pressing `=` one or more times to produce a result.
### Chaining
- Using the `:` operator to run multiple expressions in succession. Can be very powerful, but comes at a cost - scripts using chaining will save each expression in history separately - once you evaluate another expression, that script will be gone, and will have to be retyped.
## Settings
-  To use `Rnd`, number format must be set to `Fix -> 0`.
- By convention, degrees are used as the angle unit to enable larger values to be used with `Pol`.
## Table of Operations
### Variables
| Operation           | Expression                                                                 |
| ------------------- | -------------------------------------------------------------------------- |
| $x, y$ <- $a, b$    | $\text{Rec}\left(\sqrt{a^2+b^2}, \tan^{-1}\left(\frac{b}{a}\right)\right)$ |
|                     |                                                                            |
| $x$ <- $A, A \ge 0$ | $\text{Rec}\left(A, 0\right)$                                              |
| $x$ <- $A, A \le 0$ | $\text{Rec}\left(A, 180\right)$                                            |
| $y$ <- $A, A \ge 0$ | $\text{Rec}\left(A, 90\right)$                                             |
| $y$ <- $A, A \le 0$ | $\text{Rec}\left({-A}, 270\right)$                                         |
| $x++$               | $\text{Rec}\left(x+1, 0\right)$                                            |
| $y++$               | $\text{Rec}\left(y+1, 90\right)$                                           |
### Comparisons
| Operation | Expression                                     |
| --------- | ---------------------------------------------- |
| $x == A$  | $\text{Rnd}\left(10^{-9\|A - x\|}- .49\right)$ |
### Boolean Logic
| Operation    | Expression  |
| ------------ | ----------- |
| !A           | $\|A - 1\|$ |
| $A$ && $B$   | $AB$        |
| $A$ \|\| $B$ | ??          |
| $A$ ^ $B$    | ??          |
### Operators
| Operation        | Expression                                     |
| ---------------- | ---------------------------------------------- |
| $x \mod y$       | $x - y\text{Rnd}\left(\frac{x}{y} - .5\right)$ |
| $⌊x⌋$, $x \ge 0$ | $Rnd\left(x - .5\right)$                       |
| $⌈x⌉$, $x \ge 0$ | $Rnd\left(x + .49\right)$                      |
*Comment - The $.49$ above is to prevent whole numbers from being rounded up. e.g. 1 would get rounded up to 2*
## Display
1. Set `Input/Output` to `(3) LineI/LineO`.
2. Set `Multiline Font` to `(2) Small Font`.
3. `7` is used as `Off`, `8` as `On`.
4. **Cnv**: `A` will store the empty line: `7777777777`.

| Operation       | Expression      |
| --------------- | --------------- |
| `line[x] <- On` | $A + 10^{10-x}$ |
|                 |                 |
## For-loop
### Summation
$$
\sum_{x=0}^{A} f(x) = 
\frac{A}{x-B-1} + 0\text{Rec}\left(x+1, 0\right) + f(x) M+
$$
- **Setup**: $x$ <- $A$
- **Answer**: The summation will be stored in $M$.



