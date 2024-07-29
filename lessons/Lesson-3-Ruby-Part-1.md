# Introduction to Ruby Syntax

Since we already have a foundational understanding of programming language basics because of our knowledge of JavaScript, these next few lessons are designed to use that knowledge to get us up to speed on Ruby syntax.

## Getting Started

1. Fork and clone [this repository](https://github.com/Code-the-Dream-School/ROR-lesson-3-and-4.git)
2. `cd` into your local repository directory

### Confirm Your Ruby Version

> ❗**IMPORTANT:** For Ruby development, Windows users should always use the *Windows Subsystem for Linux*.

While you should already have installed `ruby >=3.2` as part of your machine setup, let's confirm we are on `3.2` or greater:

```sh
ruby -v
```

⚠️ If you are on an older version of Ruby, **STOP** and go through the machine setup again.

## Ruby vs. JavaScript

**Ruby** and **JavaScript** are both popular, [high-level programming languages](https://en.wikipedia.org/wiki/High-level_programming_language) with plenty similarities and differences between them.

You may notice many of the syntactical variations of each language as we go along, but there are two important differences in the structures of these languages to note:

1. **Object-Oriented Inheritance**

   - Ruby is a **true object-oriented language** because it uses **class-based inheritance**.

   - JavaScript uses **prototypal inheritance** and is thus not considered a *true* object-oriented language.

2. **Threading**

   - Ruby is multithreaded.

   - JavaScript is single-threaded.

   While we won't manage threading explicitly in our Ruby code, Ruby on Rails makes heavy use of multithreading to optimize processes.

### ***Go Deeper: Single & Multi-Threading*** (optional)

**Threading** refers to a programs ability to split itself to complete multiple tasks at the same time.

A single-threaded program can only complete a single command at a time, while a multi-threaded program can divide itself into multiple threads that can complete multiple commands concurrently.

Single-threaded languages like JavaScript make heavy use of asynchronous programming, such as `Promise`, `async`/`await` and callbacks, to work around the limitations of their single thread.

## Ruby Basics

### Resources

#### Supplemental Material

In addition to the lesson provided here, you may also wish to supplement your learning with these additional resources:

- [Learning Ruby from a JavaScript background](https://github.com/gauthamchandra/learning-ruby-from-js/blob/master/README.md)

  > Provides a great, introductory overview to Ruby for those coming from a JavaScript background.

  To supplement this lesson, complete *"Pure Basics and Primitive Types"*

- [Odin Project: Ruby on Rails](https://www.theodinproject.com/paths/full-stack-ruby-on-rails/courses/ruby)

  > A comprehensive Rails course with detailed explanations and exercises.

  To supplement this lesson, complete *"Basic Ruby"*

#### References

Here is a list of important Ruby reference pages for you to bookmark:

- [Official Ruby Documentation](https://docs.ruby-lang.org/en/)
- [Ruby Core Reference](https://ruby-doc.org/) - Another Ruby Documentation site
  > FYI: You may encounter this site more frequently than the official Ruby docs when googling methods. It is pulled directly from the source code and is a trust-worthy source, but is mostly a duplicate of the official docs.
- [rubydoc.info](https://rubydoc.info/stdlib/core/index) - Another Ruby documentation site that also contains documentation for Ruby gems
- [Ruby Cheatsheet](https://github.com/ThibaultJanBeyer/cheatsheets/blob/master/Ruby-Cheatsheet.md) - A quick reference to Ruby syntax

---

### Variables in Ruby

We can declare and assign a variable in Ruby like so:

```ruby
first_variable = 7
```

That's it. There is no `const`, `let`, or `var`.

Note the naming convention for Ruby variables use ***snake case***, where words are separated with an underscore (`_`).

#### Type Safety in Ruby

Similar to JavaScript, Ruby is a **dynamically-typed language**, meaning variables can change their data type at runtime and these types do not need to be explicitly defined.

However, unlike JavaScript, Ruby data types will not be implicitly coerced into other data types, and will raise errors when attempting to perform operations on inappropriate data types. You may hear this referred to as Ruby being **"strongly typed"**.

Compare the following identical operation in each language:

**JavaScript**

```js
// dynamic reassignment of a variable to a different data type
let num = 1
num = "one"
// loose typing allows an integer to be coerced to a string
console.log(num + 1)
// => "one1"
```

**Ruby**

```ruby
# dynamic reassignment of a variable to a different data type
num = 1
num = "one"
# raises an error because you can't add a string to an integer
puts num + 1
#=>:2:in `+': no implicit conversion of Integer into String (TypeError)
```

### Outputting to the Console

In ruby, there is no `console.log`. Instead, the `puts` and `print` methods output values to the console.

The difference between them being that the `puts` method adds a new line to the end:

```ruby
2.times { puts "Hello World!" }
# > Hello World!
# > Hello World!
2.times { print "Hello World!" }
# > Hello World!Hello World!
```

### String Interpolation

In JavaScript, we do string interpolation using backticks and dollar sign:

```js
let name = "Maria"
console.log(`Hello, ${name}.`)
// => Hello, Maria.
```

In Ruby, string interpolation uses double quotes and a hash symbol:

```ruby
name = "Maria"
puts "Hello, #{name}."
# => Hello, Maria.
```

### Method Invocation

In JavaScript, we are required to include parenthesis when invoking a function or method

```js
function sayHello() {
  console.log('Hello!')
}

sayHello()
// => Hello!
```

In Ruby, parenthesis to invoke methods are optional, provided that the argument is the last thing on the line. In fact, when a method has no arguments, using parenthesis goes against Ruby convention!

```ruby
def say_hello
  puts "Hello!"
end

say_hello
# => Hello!
```

So, while this is technically valid:

```ruby
say_hello()
```

It is best avoided in Ruby.

On the other hand, when a method takes parameters, omitting the parenthesis is unconventional, as it often makes the code more difficult to read.

```ruby
def say_hello_to(name)
  puts "Hello, #{name}!"
end

say_hello_to("Maria")
# => Hello, Maria!
```

There are occasional exceptions to this standard, one of which you have seen many times in this lesson already: `puts`!

`puts` is a method that is often invoked without wrapping its argument(s) in parenthesis, and you may encounter other examples of this approach in your journey into Ruby, so while we recommend you stick to conventional style, it's good to understand that the option exists.

### Follow-Along: Variables, Strings, and Out`puts`

Time for your first ruby program!

Before we get started, let's quickly go over a few other things we are going to use:

- Comments start with a `#` in Ruby.
- `#gets` method gets a line of input from the console and returns the input as a string
- `#chomp` method removes the record separator from the end of a string, if present, including new lines

#### Instructions

1. Copy the following code into `lesson_3.rb`

   ```ruby
   puts "Enter your name." # Outputs a prompt to the console
   name = gets.chomp       # Gets an input from the console
   puts "Well hello, #{name}!"  # Responds with a greeting
   name = some_value
   ```

2. Run it in your terminal, and follow the prompt:

   ```sh
   ruby lesson_3.rb
   ```

*Hmm...You got an error.*

```ruby
lesson_3.rb:4:in `<main>': undefined local variable or method `some_value' for main:Object (NameError)
```

Luckily, the Ruby error tells you exactly where the error is: `lesson_3.rb:4` indicates the error is on line `4` of the file `lesson_3.rb`!

This is because the final line of the program references a variable we never declared.

Remove it and run the program again, this time without an error!

### Symbols

**Symbols** are a unique Ruby data type similar to strings, that are declared with a colon (`:`)

```ruby
:my_first_symbol
```

The most special part of symbols are that they are [**immutable**](https://en.wikipedia.org/wiki/Immutable_object): once a symbol is created, referencing it will always point to the same memory allocation.

We can see this in action by asking for our symbol's `object_id`, which is its memory address:

```ruby
:my_first_symbol.object_id
# => 2286108
:my_first_symbol.object_id == :my_first_symbol.object_id
# => true
```

Much like your home address, the `object_id` tells the program where in memory it can retrieve an object.

This is different from strings, which are **mutable**. Each time we write a string, even if it is exactly the same as a previously created string, it will receive a new `object_id`:

```ruby
"my first string".object_id
# => 13520
"my first string".object_id == "my first string".object_id
# => false
```

As you might imagine, there are performance benefits to an object having the same `object_id` every time it is referenced, which is why Ruby prefers Symbols as the key for Hashes!

### Hashes

The Ruby data type for storing key-value pairs is called a **Hash**. The keys for hashes can be any data type, but are often symbols. The values of those keys can also be of any type.

There are two frequently encountered syntax for declaring hashes. The first is the original, Ruby-specific *hash-rocket* (`=>`) syntax:

```ruby
dog = {
  :name => "Sombra",
  :breed => "Dachshund"
  :age => 12
}
```

This syntax is perfectly valid, and is using symbols as keys. When Ruby outputs a hash, it will use the *hash-rocket* syntax.

However, it is now more common when declaring a hash to use the following syntax:

```ruby
dog = {
  name: "Sombra",
  breed: "Dachshund"
  age: 12
}
```

In this notation, the keys are also symbols, but the colon is after the symbol name. You may notice that this looks remarkably like declaring a JavaScript `Object`, and that is because JavaScript calls its version of a hash an `Object`!

> In Ruby, a `Hash` is a *subclass* of `Object`, which is the default root of all Ruby objects.

You can add to an existing hash with bracket syntax:

```ruby
dog[:favorite_toy] = "squeaky duck"
```

Or create an empty hash like so:

```ruby
new_hash = {}
```

### Follow Along

Let's explore strings, symbols and hashes a bit more in the Interactive Ruby interpreter, [IRB](https://github.com/ruby/irb)!

1. Open IRB in your terminal:

    ```sh
    irb
    ```

   **You can exit irb at any time by entering `exit` into the prompt!**

2. Create an instance of each data type:

    ```ruby
    my_string = "this is a string. "
    my_symbol = :im_a_symbol
    my_hash = {}
    ```

3. The `#class` method returns the Class of an object:

    ```ruby
    my_string.class
    # => String
    my_symbol.class
    # => Symbol
    my_hash.class
    # => Hash
    ```

4. Each class provides methods to objects derived from it. While all three of these data types share access to some methods, like the `class` method, they also have methods that are unique to their class.

    ```ruby
    my_string.chomp
    # => "this is a string."
    my_symbol.chomp
    # => (irb):7:in `<main>': undefined method `chomp' for :im_a_symbol:Symbol
    ```

    Calling a method that belongs to the `String` class on a `Symbol` will raise an undefined method error.

5. We can list all of the methods available to an object with the `methods` method:

    ```ruby
    my_string.methods
    ```

    Wow. That is a long list! Feel free to try it with `my_symbol` and `my_hash`, too.

### Ruby Documentation

Ruby developers don't memorize all the methods of a given class. Instead, we look them up in the [Official Ruby Documentation](https://docs.ruby-lang.org/en/).

Let's take a look:

1. Open the Ruby docs in your browser and select your Ruby version.

    **It is important to use the docs that match your Ruby version!**

2. Search for the `String` class.

    This will bring you to a page with information about `String` and all of the methods it defines.

    The side-bar indicates a few important things:

    - The Parent Class: `Object`
    - Included Modules: `Comparable`
    - Methods

3. Look for the `#class` method in the "**Methods**" side-bar. (**HINT**: You won't find it.)

    *So, why is `#class` not listed as a method for `String` when we were able to call it on an instance of string without an error?*

    We will get more into inheritance later, but for now, the reason you won't find the `#class` method listed under the `String` Methods has to do with what it *inherits* from its parent!

### Control Flow

Let's talk about conditionals in Ruby.

Here is some JavaScript:

```javascript
const x = 17
if (x > 18) {
    console.log("x is more than 18")
} else if (x > 11) {
    console.log("x is more than 11")
} else {
    console.log("x is less than or equal to 11")
}
```

and here is Ruby:

```ruby
x = 17
if x > 18
  puts "x is more than 18"
elsif x > 11
  puts "x is more than 11"
else
  puts "x is less than or equal to 11"
end
```

As you can see, there are some syntactic differences: The `else if` keyword in JavaScript becomes `elsif` in Ruby, Ruby has no parenthesis around conditional statements or curly brackets around the blocks, and Ruby closes blocks with the keyword `end`.

Ruby has an additional conditional keyword, `unless`, which is effectively `if not`. It can be paired with `else` just like `if`:

```ruby
x = 0

unless x.positive?
  warn "x is not a positive number"
end
```

`if`/`unless` can also come at the end of a line following an expression. For example:

```ruby
x = 0
warn "x is not a positive number" unless x.positive?
```

Ruby also supports ternary statements:

```ruby
x = 0

x.positive? ? puts "x is positive" : puts "x is not a positive number"
```

As well as `case` (AKA switch) statements:

```ruby
x = 0
case x
when x.positive?
  puts "x is positive"
when x.zero?
  puts "x is zero"
else
  puts "x is "
end
```

### Loops

There are various ways to do loops in Ruby. Go ahead and open IRB to follow along.

A quick way to loop an action a set number of times is to call `#times` on an integer:
```ruby
5.times do
  puts "Hi There"
end
```

`#times` accepts a **block argument** which allows us to track what loop iteration we are in. (You'll learn more about Ruby's "blocks" in the next lesson.)

```ruby
5.times do |x|
  puts x # The value is "0-indexed", so this will print numbers 0 to 4 instead of 1 to 5
end
```

The `Array#each` method will loop through the array it is called on, passing each element to the block:

```ruby
[1,2,3].each do |x|
  puts x
end
```

`for` loops exist in Ruby, but are used much less frequently than in other languages

```ruby
for i in 1..5
  puts i
end
```

Ruby also offers `while` loops:

```ruby
x = 0
while x < 5
  x += 1
  puts x
end
```

Note that Ruby uses `+=` and `-=` to increment and decrement, respectively.

And `until` loops, which are effectively `while not`:

```ruby
x = 5
until x < 1
  puts x
  x -= 1
end
```

`while`/`until` can also be placed after an expression:

```ruby
x = 0
puts x while (x += 1) <= 5
```

Finally, the `loop` keyword, which will run until exited with the `break` keyword:

```ruby
x = 5
loop do
  puts x
  x -= 1
  break if x < 1
end
```

In all loop types in Ruby, you can skip an iteration with the `next` keyword:

```ruby
[1, 2, 3, 0].each do |x|
  next unless x.positive?

  puts x
end
```

### Percent Notation

Ruby offers a unique notation for creating arrays and quoted strings called **Percent Notation** which you may encounter in various Ruby projects. While Ruby also accepts creating these objects using a standard notation, percent notation saves typing.

For example, to create a quoted string using a string literal, we would need to do the following:

```ruby
puts "\"What's that again?\""
# => "\"What's that again?\""
```

To do the same using percent notation, we can avoid the `\` escape character altogether:

```ruby
puts %q["What's that again?"]
# => "\"What's that again?\""
```

For arrays, percent notation allows us to skip things like commas, quotes around strings, and the colon for symbols:

```ruby
# an array of strings
%w[foo bar baz] # => ["foo", "bar", "baz"]

# an array of symbols
%i[foo bar baz] # => [:foo, :bar, :baz]
```

A full list of percent literals can be found [here.](https://docs.ruby-lang.org/en/3.2/syntax/literals_rdoc.html#label-Percent+Literals)
