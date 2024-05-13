# Operators

An **operator** is a symbol for performing an operation or conditional evaluation on one or more values. Operators are used in Lua to manipulate data, perform arithmetic calculations, compare values, and control program flow. Understanding operators is essential for writing efficient and expressive Lua scripts in Highrise.

## Logical Operators

Logical operators are used to perform logical operations on boolean values. Lua supports the following logical operators:

- `and`: Returns `true` if both operands are `true`.
- `or`: Returns `true` if at least one operand is `true`.
- `not`: Returns the opposite boolean value of the operand.

### Logical AND Operator (`and`)

The logical AND operator (`and`) returns `true` if both operands are `true`. Otherwise, it returns `false`. Here's an example of using the logical AND operator in Lua:

```lua
local a = true
local b = false

print(a and b) --> false
print(a and true) --> true
```

In this example, the expression `a and b` evaluates to `false` because `b` is `false`. The expression `a and true` evaluates to `true` because both `a` and `true` are `true`.

### Logical OR Operator (`or`)

The logical OR operator (`or`) returns `true` if at least one operand is `true`. Otherwise, it returns `false`. Here's an example of using the logical OR operator in Lua:

```lua
local a = true
local b = false

print(a or b) --> true
print(false or b) --> false
```

In this example, the expression `a or b` evaluates to `true` because `a` is `true`. The expression `false or b` evaluates to `false` because both operands are `false`.

### Logical NOT Operator (`not`)

The logical NOT operator (`not`) returns the opposite boolean value of the operand. If the operand is `true`, it returns `false`. If the operand is `false`, it returns `true`. Here's an example of using the logical NOT operator in Lua:

```lua
local a = true
local b = false

print(not a) --> false
print(not b) --> true
```

In this example, `not a` evaluates to `false` because `a` is `true`. `not b` evaluates to `true` because `b` is `false`.

## Comparison Operators

In this table, `a` and `b` represent variables or values that are being compared.

| Operator | Description          | Example     | Result |
|----------|----------------------|-------------|--------|
| `==`     | Equal to             | `a == b`    | `true` if `a` is equal to `b`, `false` otherwise |
| `~=`     | Not equal to         | `a ~= b`    | `true` if `a` is not equal to `b`, `false` otherwise |
| `<`      | Less than            | `a < b`     | `true` if `a` is less than `b`, `false` otherwise |
| `>`      | Greater than         | `a > b`     | `true` if `a` is greater than `b`, `false` otherwise |
| `<=`     | Less than or equal to | `a <= b`  | `true` if `a` is less than or equal to `b`, `false` otherwise |
| `>=`     | Greater than or equal to | `a >= b` | `true` if `a` is greater than or equal to `b`, `false` otherwise |

### Comparison Examples

In this table, `a` and `b` represent variables or values that are being compared.

| Expression | Description | Result |
|------------|-------------|--------|
| `5 == 5`   | `5` is equal to `5` | `true` |
| `5 ~= 5`   | `5` is not equal to `5` | `false` |
| `10 < 20`  | `10` is less than `20` | `true` |
| `20 > 30`  | `20` is greater than `30` | `false` |
| `15 <= 15` | `15` is less than or equal to `15` | `true` |
| `25 >= 30` | `25` is greater than or equal to `30` | `false` |

## Arithmetic Operators

Arithmetic operators are used to perform mathematical calculations on numeric values. In this table, `a` and `b` represent variables or values that are being operated on.

| Operator | Description | Example | Result |
|----------|-------------|---------|--------|
| `+`      | Addition    | `a + b` | Sum of `a` and `b` |
| `-`      | Subtraction | `a - b` | Difference between `a` and `b` |
| `*`      | Multiplication | `a * b` | Product of `a` and `b` |
| `/`      | Division    | `a / b` | Quotient of `a` divided by `b` |
| `%`      | Modulus     | `a % b` | Remainder of `a` divided by `b` |
| `^`      | Exponentiation | `a ^ b` | `a` raised to the power of `b` |
| `-`      | Negation    | `-a`    | Negative value of `a` |
| `//`     | Floor Division | `a // b` | Quotient of `a` divided by `b`, rounded down to the nearest integer |

## Compound Assignment Operators

You can use compound assignment operators to combine an arithmetic operation with an assignment. These operators provide a shorthand way to update the value of a variable based on its current value. In this table, `a` and `b` represent variables or values that are being operated on.

| Operator | Description | Example | Equivalent |
|----------|-------------|---------|------------|
| `+=`     | Add and assign | `a += b` | `a = a + b` |
| `-=`     | Subtract and assign | `a -= b` | `a = a - b` |
| `*=`     | Multiply and assign | `a *= b` | `a = a * b` |
| `/=`     | Divide and assign | `a /= b` | `a = a / b` |
| `%=`     | Modulus and assign | `a %= b` | `a = a % b` |
| `^=`     | Exponentiate and assign | `a ^= b` | `a = a ^ b` |
| `//=`    | Floor divide and assign | `a //= b` | `a = a // b` |

## Miscellaneous Operators

Lua also provides other operators for specific operations and manipulations:

- `..`: Concatenation operator used to combine strings.
- `#`: Length operator used to get the length of a string or table.

### Concatenation Operator (`..`)
The concatenation operator (`..`) is used to combine strings in Lua. You can use this operator to concatenate two or more strings into a single string. Here's an example of using the concatenation operator in Lua:

```lua
local firstName = "Alice"
local lastName = "Smith"
local fullName = firstName .. " " .. lastName
print(fullName) --> "Alice Smith"
```

In this example, the strings `firstName` and `lastName` are concatenated to form the full name `Alice Smith`.

### Length Operator (`#`)

The length operator (`#`) is used to get the length of a string or table in Lua. For strings, the length operator returns the number of characters in the string. For tables, the length operator returns the number of elements in the table. Here's an example of using the length operator in Lua:

```lua
local text = "Hello, Lua!"
local length = #text
print(length) --> 11
```

In this example, the length operator `#text` returns the number of characters in the string `text`, which is `11`.

## Operator Precedence

Operator precedence determines the order in which operators are evaluated in an expression. Operators with higher precedence are evaluated first. If operators have the same precedence, they are evaluated from left to right. You can use parentheses `()` to override the default precedence and explicitly specify the order of evaluation.

Here's the general order of precedence for Lua operators, from highest to lowest:

1. `^`
2. `-` (unary), `not`, `#`
3. `*`, `/`, `%`
4. `+`, `-`
5. `..`
6. `<`, `<=`, `>`, `>=`
7. `==`, `~=`
8. `and`
9. `or`

By understanding operator precedence, you can write expressions that are clear, concise, and correctly evaluated in Lua.