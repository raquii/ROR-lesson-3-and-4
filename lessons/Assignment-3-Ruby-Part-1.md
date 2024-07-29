# Introduction to Ruby Syntax: Assignment

This assignment goes over the basics of Ruby syntax covered in Lesson 3.

1. Create a new branch, `lesson3`
2. Complete each program below

---

## Contact Form

In `contact_form.rb`, build a program that collects contact information into a hash.

This program should do the following:

- Create a hash, `contact`
- Prompt the user for the following information:
  - First Name, stored using the key `:first_name`
  - Last Name (`:last_name`)
  - Age (`:age`)
  - Street (`:street`)
  - City (`:city`)
  - State (`:state`)
- Output `contact` to the console (`puts`)
- Output the keys for `contact` to the console
  > Hint: `Hash` has a method to retrieve keys. Note that this method returns an `Array` of keys.
- Output the values for the hash to the console
- Update `:first_name`, `:last_name`, and `:city` to be capitalized
  > Hint: `String` has a method for this. Make sure you are assigning this value to the key!
- Change the `:state` as stored in the person hash to uppercase.
- Output the hash to the console again.

### Method Naming Conventions in Ruby

When looking up methods in the documentation for this assignment, you may encounter methods that end in a bang (`!`), question mark(`?`), or equal sign (`=`), which is a Ruby naming convention that tells us something special about these methods.

- `!` indicates that a method is "dangerous": it transforms the object it was called on instead of returning a transformed copy. Bang methods have non-bang equivalents that return a copy instead of modifying "in place".
- `?` indicates a method returns a boolean
- `=` indicates a method is a special type of method called a **setter**. We will talk more about these later.

---

## Guess the Number Game

In `guess_the_number.rb`, build a game that generates a random number and allows a player to guess the number until correct.

To create the random number, use Ruby's `#rand` method. If you pass a [`Range`](https://ruby-doc.org/3.2.2/Range.html) as an argument, `rand` will return an integer within that range.

For example, the following returns a value from 1 to 100, inclusive:

```ruby
secret_number = rand(1..100)
```

The program should do the following:

- Generate random number between 1-100.
- In a `loop`, prompt the user for a guess.
   > Careful! Remember that the return value of `#gets` is a `String` and Ruby does not do implicit type conversion.
   >
   > Instead, you'll need to use the `String` method for converting to an integer: `#to_i`.
- If the guess is incorrect, output to the user whether their guess was too high or too low.
- If the guess is correct, congratulate the player & ask if they want to play again:
   - If so, generate a new random number.
   - If not, `exit` the loop and the program.
- Handle if the guess is invalid (not a number, outside of the range)
   > HINT: Check in irb what `#to_i` returns if called on a string that is not a number and use this to handle your conditional

---

## Guess My Number Game

In `guess_my_number.rb`, build a program that guesses what number a user is thinking of, between 1 and 100.

The program should:

- Ask the user to think of a number between 1-100 and enter `"ready"` when ready
- Output a guess
- Prompt the user to indicate if the guess was `"too high"`, `"too low"`, or `"correct"`
  - Prompt again if the user response is not one of the three options
- Perform additional guesses until correct
- Keep track of the remaining lowest and highest possible values and guess between them
- If the program has exhausted all valid options and is still not given `"correct"`, accuse the player of cheating and end the game
- Prompt player to play again if `"correct"` or cheating

---

## Submitting Your Work

- add, commit, and push your work
- create a pull request
As usual, you should add, commit, and push your work.
Then create a pull request for the `lesson3` branch on GitHub, and include a link to the pull request in your homework submission.
