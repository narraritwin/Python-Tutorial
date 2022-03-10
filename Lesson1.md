# **Python!** Lesson 1

# Hello World

Your first program in any language is traditionally the "Hello World" program:

```py
print('Hello World!')
```

If you're using [replit](https://replit.com/), then just copy-paste this code
and hit the run button.

If you're running the program on your own computer, copy-paste the code into a
file (let's say it's `hello_world.py`, but you can name it whatever you want).
Then, type `python3 hello_world.py` into your terminal and hit enter.

There are a few things to deconstruct here:

1. `print(...)` is a function which outputs something to the console.
2. `'Hello World!'` is a string (notice the single quotes). To denote a
   string, you can use either single or double quotes, but it's good style
   to be consistent with whichever you choose.

# Data Types

There are several common data types you will use in Python:

1. `int` - This stands for integer, so it can store... integers! Python
   integers, unlike most other languages, can support almost any size number
   you want. Even 10^100, a googol! This is likely the most commonly-used
   data type, so remember it!
2. `str` - This stands for string, so it can store... strings! Specifically,
   strings of characters, like `'Hello World!'` or `"Mr. Big Words Man"`. If
   not the integer, this is the most commonly-used data type. Note the quotes
   around the strings; you can use either single or double quotes, but make
   sure to be consistent with whichever you choose!
3. `float` - This stands for floating-point number, so it stores... floating
   balloons! ~~Oh wait this is a Python tutorial.~~ "Floating-point number"
   is really just a fancy name for a decimal. If you really want to get into
   the specifics, see [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754).
4. `bool` - This stands for boolean, which really just means `True` or `False`
   (be careful about the capitals!)

# Variables

## Variable Names

Variable names can be almost anything you can think of. But of course, there
must be a few rules so that Python can understand you:

1. You can only use the characters a-z, A-Z, 0-9, and _ (an underscore). Note
   that you cannot use a space in a variable name
2. The variable name cannot start with a digit. Otherwise, when Python is
   parsing your code it will see the number and try to parse your variable
   name like `23_and_me` as a number, which it obviously is not!

## Style Guide

When you're writing code, you want to make sure that it looks neat. Of course,
looking at neat code is nice to you, but even if you're able to come back to your
code 3 months later and understand what it does, what about in the future, when
you have coworkers? They need to understand your code too, and they would get
annoyed if your code was badly formatted (just like you probably would to others).

The official Python style guide is detailed in
[PEP8](https://www.python.org/dev/peps/pep-0008/)

The important part for variable names is that they use `snake_case`. So you
should separate your words with underscores, and keep all the letters lowercase.

## Examples

```py
number = 3435                 # Integer
my_name = 'Mr. Big Words Man' # String
pi = 3.1415926535897932       # Float
am_i_smart = True             # Boolean
```

# The Print Function

When you call `print(x)` for some object `x` (usually it'll be one of the
data types we've described above), Python will output `x` to the console.
For example, the following code:

```py
print(3435)
print('Mr. Big Words Man')
print(3.1415926535897932)
print(True)
```
will output the following to the console:
```
3435
Mr. Big Words Man
3.1415926535897932
True
```

Now, what about this code?
```py
print(78498, 'hi', 2.718281828, False)
```

When you give `print` multiple values, it prints out the values separated
by spaces, and ends with a newline. So the output looks like this:
```
78498 hi 2.718281828 False
```

Note that if you want to print multiple things without a space between them,
you can convert the variables to strings and then use a `+` to concatenate them:

```py
name = 'Arthur T. Benjamin'
age = 60
print(name + ' is ' + str(age) + '!')
```

Note that we didn't cast `name` to a string, because it's already a string!
The astute among you might have realized the last line can be replaced with
```py
print(name, 'is', str(age) + '!')
```

And that's all you need to know! There are a few more advanced things you can
do with `print`, but you won't need them yet.

# The Input Function

So now we can print out stuff. But what if we wanted to get input from the
user, for example their name? Well, here's the magic of Python:

```py
my_name = input('Enter your name: ')
print('Hi ' + my_name + '!')
```

Try running this! You can create interactive programs like this, which end up
being quite a lot of fun to play with.

Now, there's only one thing we need to address before you'll master input and output. Try running the following program:

```py
favorite_number = input('Enter your favorite number: ')
print('Your favorite number is', favorite_number)
```

If you run this program, it works. However what if you outputted double their favorite number?

```py
favorite_number = input('Enter your favorite number: ')
print('Your favorite number is', favorite_number * 2)
```

You might get the following:

```
Enter your favorite number: 42
Your favorite number is 4242
```

So what happened here? Well, we can debug with the function `type`. It returns the... type of the variable (or constant) you pass into it.

```py
favorite_number = input('Enter your favorite number: ')
print(type(favorite_number))
```

It outputs

```
<class 'str'>
```

Which means that `favorite_number` is a string, not an integer. Hmm... how do we fix this?

Remember when we explained a line like

```py
print(name + ' is ' + str(age) + '!')
```
where we had to cast `age`, which was an int, to `str` to concatenate properly? Well now, we need to cast `favorite_number` to an int. Here is the fixed version of the code:

```py
favorite_number = int(input('Enter your favorite number: '))
print('Your favorite number is', favorite_number * 2)
```

The important part here is the `int()` around the input function. Before, we used
`str()` to cast to a string. Now, we're using `int()` to cast to an integer. If needed,
you could also use `float()`. Technically, you can also use `bool()` in the same way,
but I can't really think of a time you'd need that (instead of a `yes`/`no`).

And that's all there is to `input`!

# Homework

1. Create a program that outputs a poem (It can be any poem you choose,
   but make sure you output it on several lines).
2. Create a calculator for the area of a circle. So you would input a radius r,
   and the program would output the area of a circle with radius r.

# Extra

## f-strings

Remember how we did stuff like this?

```py
print(name + ' is ' + str(age) + '!')
```

This could get cumbersome if we have a lot more things to print, e.g.

```py
print(name + ' is ' + str(age) + ' and has a ' + str(car) + ' while living in ' + str(country) + '!')
print(name, 'is', age, 'and has a', car, 'while living in', str(country) + '!')
```

Now, the second line shows a nicer way of doing it, as it's more readable. However in Python 3.6, f-strings were introduced, which make this formatting a lot nicer:

```py
print(f'{name} is {age} and has a {car} while living in {country}!')
```

## Escape Characters

Let's say we wanted to print this sentence. We might try:

```py
print('Let's say we wanted to print this sentence.')
```

But you can see what went wrong from the colors. Python looked at what we wanted as the string, saw the apostrophe, and stopped the string there. And now it's all confused for why you had a random `s` after.
What we can do instead is use an escape character: replace the `'` inside the string with `\'`:

```py
print('Let\'s say we wanted to print this sentence.')
```

This just tells Python "Yes, I know there's an apostrophe here, but I don't mean to end the string"

There are a few other common escape characters:

- `\'` - A single quote
- `\"` - A double quote
- `\n` - A newline (inside a string, you can do something like `'Hello\nNext line'`)
- `\t` - A tab or indent character
