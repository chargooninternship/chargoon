### - use strict

1. **'use strict'. When it is located at the top of a script, the whole script works the “modern” way.**
2. Please make sure that "use strict" is at the top of your scripts, otherwise strict mode may not be enabled.

### - var

1. `let` – is a modern variable declaration.
2. `var` – is an old-school variable declaration. Normally we don’t use it at all, but we’ll cover subtle differences from `let` in the chapter [The old "var"], just in case you need them.
3. `const` – is like `let`, but the value of the variable can’t be changed.

### - type OF

- `number` for numbers of any kind: integer or floating-point, integers are limited by `±(2531)`.
- `bigint` is for integer numbers of arbitrary length.
- `string` for strings. A string may have zero or more characters, there’s no separate single-character type.
- `boolean` for `true`/`false`.
- `null` for unknown values – a standalone type that has a single value `null`.
- `undefined` for unassigned values – a standalone type that has a single value `undefined`.
- `object` for more complex data structures.
- `symbol` for unique identifiers.

### - Interaction: alert, prompt, confirm

**`alert`**

shows a message.

**`prompt`**

shows a message asking the user to input text. It returns the text or, if Cancel button or Esc is clicked, `null`.

**`confirm`**

shows a message and waits for the user to press “OK” or “Cancel”. It returns `true` for OK and `false` for Cancel/Esc.

### - operators

The operators `++` and `--` can be placed either before or after a variable.

- When the operator goes after the variable, it is in “postfix form”: `counter++`.
- The “prefix form” is when the operator goes before the variable: `++counter`.

### - comparison

- Comparison operators return a boolean value.
- Strings are compared letter-by-letter in the “dictionary” order.
- When values of different types are compared, they get converted to numbers (with the exclusion of a strict equality check).
- The values `null` and `undefined` equal `==` each other and do not equal any other value.
- Be careful when using comparisons like `>` or `<` with variables that can occasionally be `null/undefined`. Checking for `null/undefined` separately is a good idea.

### - IF

- The if(...) statement evaluates a condition in parentheses and, if the result is true, executes a block of code.
- The operator is represented by a question mark `?`. Sometimes it’s called “ternary”, because the operator has three operands. It is actually the one and only operator in JavaScript which has that many.

The syntax is:

`let result = condition ? value1 : value2;`

### - operators

JavaScript supports the following operators:

**Arithmetical**Regular: `* + - /`, also `%` for the remainder and `**` for power of a number.
The binary plus `+` concatenates strings. And if any of the operands is a string, the other one is converted to string too:

`alert( '1' + 2 ); // '12', string alert( 1 + '2' ); // '12', string`**Assignments**There is a simple assignment: `a = b` and combined ones like `a *= 2`.**Bitwise**Bitwise operators work with 32-bit integers at the lowest, bit-level: see the when they are needed.**Conditional**The only operator with three parameters: `cond ? resultA : resultB`. If `cond` is truthy, returns `resultA`, otherwise `resultB`.**Logical operators**Logical AND `&&` and OR `||` perform short-circuit evaluation and then return the value where it stopped (not necessary `true`/`false`). Logical NOT `!` converts the operand to boolean type and returns the inverse value.**Nullish coalescing operator**The `??` operator provides a way to choose a defined value from a list of variables. The result of `a ?? b` is `a` unless it’s `null/undefined`, then `b`.**Comparisons**Equality check `==` for values of different types converts them to a number (except `null` and `undefined` that equal each other and nothing else), so these are equal:

`alert( 0 == false ); // true alert( 0 == '' ); // true`
Other comparisons convert to a number as well.
The strict equality operator `===` doesn’t do the conversion: different types always mean different values for it.
Values `null` and `undefined` are special: they equal `==` each other and don’t equal anything else.
Greater/less comparisons compare strings character-by-character, other types are converted to a number.**Other operators**There are few others, like a comma operator.

# [Loops]

- We covered 3 types of loops:

  `// 1
  while (condition) {
  ...
  }

  // 2
  do {
  ...
  } while (condition);

  // 3
  for(let i = 0; i < 10; i++) {
  ...
  }`

- The variable declared in `for(let...)` loop is visible only inside the loop. But we can also omit `let` and reuse an existing variable.
- Directives `break/continue` allow to exit the whole loop/current iteration. Use labels to break nested loops.

Details in: [Loops: while and for].

Later we’ll study more types of loops to deal with objects.

# [The “switch” construct]

The “switch” construct can replace multiple `if` checks. It uses `===` (strict equality) for comparisons.

For instance:

`let age = prompt('Your age?', 18);

switch (age) {
case 18:
alert("Won't work"); // the result of prompt is a string, not a number
break;

case "18":
alert("This works!");
break;

default:
alert("Any value not equal to one above");
}`

Details in: [The "switch" statement].

# [Functions]

We covered three ways to create a function in JavaScript:

1. Function Declaration: the function in the main code flow

   `function sum(a, b) {
   let result = a + b;

   return result;
   }`

2. Function Expression: the function in the context of an expression

   `let sum = function(a, b) {
   let result = a + b;

   return result;
   };`

3. Arrow functions:

   `// expression at the right side
   let sum = (a, b) => a + b;

   // or multi-line syntax with { ... }, need return here:
   let sum = (a, b) => {
   // ...
   return a + b;
   }

   // without arguments
   let sayHi = () => alert("Hello");

   // with a single argument
   let double = n => n \* 2;`

- Functions may have local variables: those declared inside its body or its parameter list. Such variables are only visible inside the function.
- Parameters can have default values: `function sum(a = 1, b = 2) {...}`.
- Functions always return something. If there’s no `return` statement, then the result is `undefined`.
