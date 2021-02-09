## object

1. An object can be created with figure brackets {…} with an optional list of properties. A property is a “key: value” pair, where key is a string (also called a “property name”), and value can be anything.

We can imagine an object as a cabinet with signed files. Every piece of data is stored in its file by the key. It’s easy to find a file by its name or add/remove a file.

2. We can add, remove and read files from it any time.
   Property values are accessible using the dot notation.

3. We can also use multiword property names, but then they must be quoted

**' "likes birds": true '**

### dot notation and Square brackets

1. The dot requires the key to be a valid variable identifier. That implies: contains no spaces, doesn’t start with a digit and doesn’t include special characters ($ and \_ are allowed).

2. Here, the variable key may be calculated at run-time or depend on the user input. And then we use it to access the property. That gives us a great deal of flexibility.

For instance:
`
let user = {
name: "John",
age: 30
};

let key = prompt("What do you want to know about the user?", "name");

// access by variable
alert( user[key] ); // John (if enter "name")
`

### Computed properties

1. We can use square brackets in an object literal, when creating an object. That’s called computed properties.

2. Square brackets are much more powerful than the dot notation. They allow any property names and variables. But they are also more cumbersome to write.

So most of the time, when property names are known and simple, the dot is used. And if we need something more complex, then we switch to square brackets.

### Property names limitations

As we already know, a variable cannot have a name equal to one of language-reserved words like “for”, “let”, “return” etc.

### Property existence test, “in” operator

most of the time the comparison with undefined works fine. But there’s a special case when it fails, but "in" works correctly.

## Object references and copying

- A variable assigned to an object stores not the object itself, but its “address in memory” – in other words “a reference” to it.
- When an object variable is copied, the reference is copied, but the object itself is not duplicated.

## Cloning and merging, Object.assign

- That’s also doable, but a little bit more difficult, because there’s no built-in method for that in JavaScript. But there is rarely a need – copying by reference is good most of the time.

- But if we really want that, then we need to create a new object and replicate the structure of the existing one by iterating over its properties and copying them on the primitive level.
- Instead of cloning, we use object.assign()

## Object methods, "this"

` To access the object, a method can use the this keyword.`
`The value of this is the object “before dot”, the one used to call the method.`

## “this” is not bound

- In JavaScript, keyword this behaves unlike most other programming languages. It can be used in any function, even if it’s not a method of an object.

- The value of `this` is evaluated during the run-time, depending on the context.

For instance, here the same function is assigned to two different objects and has different “this” in the calls:

`let user = { name: "John" };
let admin = { name: "Admin" };

function sayHi() {
alert( this.name );
}

_// use the same function in two objects
user.f = sayHi;
admin.f = sayHi;_// these calls have different this
// "this" inside the function is the object "before the dot"
user.f(); // John (this == user)
admin.f(); // Admin (this == admin)

admin['f'](); // Admin (dot or square brackets access the method – doesn't matter)`

The rule is simple: if `obj.f()` is called, then `this` is `obj` during the call of `f`. So it’s either `user` or `admin` in the example above.

- Calling without an object: this == undefined

## Arrow functions have no “this”

- Arrow functions are special: they don’t have their “own” this. If we reference this from such a function, it’s taken from the outer “normal” function.

## Constructor, operator "new"

///?????????????
