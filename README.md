# Lua 5.3 - Quick Guide

Helpful resources: [Lua Crash Course - A quick overview with a guide](https://www.youtube.com/watch?v=Q10xtMnDHaI) / [Lua Reference Manual](https://www.lua.org/manual/5.3/) / [Lua Users Wiki](http://lua-users.org/wiki/)

## Table of Contents
- [Lua - Quick Guide](#lua-53---quick-guide)
  - [ToC](#table-of-contents)
  - [Print Statements](#print-statements)
  - [Comments](#comments)
  - [Variables](#variables)
    - [Numbers](#numbers)
    - [Strings](#strings)
    - [Boolean](#boolean)
  - [Conditional Statements](#conditional-statements)
    - [Comparison Operators](#comparison-operators)
    - [Combining Statements](#combining-statements)
    - [Nested Statements](#nested-statements)
    - [Invert Values](#invert-values)
  - [Functions](#functions)
  - [Scope](#scope)
    - [Global Variables](#global-variables)
  - [Loops](#loops)
    - [Infinite Loops](#infinite-loops)
    - [Nested Loops](#nested-loops)
  - [Tables](#tables)
    - [Table Manipulation](#table-manipulation)
    - [Two Dimensional Tables](#two-dimensional-tables)
    - [Key Tables](#key-tables)
    - [Returning a Table from a Function](#returning-a-table-from-a-function)
  - [Math](#math)
  - [Modules](#modules)

## Print Statements

Print statements are used to output text or values to the console. They are essential for debugging and displaying information to the developer.

```lua
print("Hello, developer")
```

## Comments

Comments are used to add explanations or notes within the code. They are ignored by the Lua interpreter and are solely for the benefit of developers reading the code.

```lua
-- This is an example of a comment in Lua
print("Hello, developer") -- An inline comment
-- The following line of code will not be executed due to it being commented out
--print("Hello, World")
```

## Variables

Variables are containers for storing data values. In Lua, variables can hold different types of data.

```lua
-- Types
local pizzas_to_order = 10 -- Number: Stores numeric values
local first_name = "Ed" -- String: Stores text
local is_alive = false -- Boolean: Stores true or false
local empty_variable = nil -- Nil: Represents no value or invalid value
```

### Numbers

Numbers in Lua can be integers or floating-point values. Lua supports various arithmetic operations.

- Addition: \+ 
- Subtraction: \-
- Multiplication: \* 
- Division: /
- Power: ^
- Modulus: %

```lua
local a = 1
local b = 2
local c = a + b
print(c)
-- Output: 3

local d = b - a
print(d)
-- Output: 1

local e = 1 * 3 * 4
print(e)
-- Output: 12

local f = (1+3) * 2
print(f)
-- Output: 8
```

```lua
print(10//2)
-- Output: 5 (integer division)

print(10/2)
-- Output: 5.0 (float division)

print(2^2) 
-- Output: 4 (exponentiation)

print(5%2) 
-- Output: 1 (modulus)

print(-b) 
-- Output: -2 (negation)
```

```lua
-- Incrementing
local level = 1
level = level + 1
print(level)
-- Output: 2
```

### Strings

Strings are sequences of characters used to represent text. Lua provides operations for manipulating strings.

```lua
-- Concatenate strings using the .. operator
local phrase = "My name is "
local name = "Eddy"
print(phrase .. name)
-- Output: "My name is Eddy"

-- Combining strings with numbers
local amount_of_creatures = 21
local creature = "toads"
print("There are " .. amount_of_creatures .. " " .. creature .. " in the swamp")
-- Output: "There are 21 toads in the swamp"
````

### Boolean

Boolean values represent true or false conditions. They are used in logical operations and control structures.

```lua
local is_conscious = true
print(is_conscious)
-- Output: true

is_conscious = false
print(is_conscious)
-- Output: false
```

## Conditional Statements

Conditional statements allow the program to make decisions based on certain conditions.

```lua
-- Variable assignment
local age = 16

-- if statement for comparison
if age < 18 then
  print("The age is under 18")
end

-- elseif and else for comparisons
if age > 18 then
  print("The age is over 18")
elseif age == 18 then
  print("The age is exactly 18")
else
  print("The age is under 18")
end
```

### Comparison Operators

Comparison operators are used to compare values.

- Equal to: == 
- Less than: < 
- Greater than: \> 
- Less than or equal to: <= 
- Greater than or equal to: \>= 
- Not equal to: ~=

```lua
-- Boolean comparison
local is_alive = true

if is_alive then
    print("The dog lives!")
end
```

```lua
-- String comparisons
local name = "Edd"

if name == "Edd" then -- This condition is false
  print("Edd")
elseif name ~= "Edd" then -- This condition is true
  print("I'd swear, but standards won't let me")
end
```

### Combining Statements

Logical operators can be used to combine multiple conditions.

```lua
local x = 10

if x == 10 and x < 0 then -- Both conditions must be true (which they aren't)
  print("Dog")
elseif x == 100 or x > 0 then -- At least one condition must be true
  print("Cat")
end
-- Output: Cat
```

### Nested statements

Conditional statements can be nested within each other.

```lua
local animal = "Dog"
local isAlive = true

if animal == "Dog" then
  if isAlive == true then
    print("The dog is alive! :)")
  else
    print("The dog is dead! :(")
  end
end
-- Output: "The dog is alive! :)"
```

### Invert Values

The **not** keyword can be used to invert a boolean value:

```lua
local x = 10

if not (x == 10) then -- This is equivalent to "x ~= 10"
  print("here")
end

if x ~= 10 then -- This is equivalent to "not (x = 10)"
  print("here")
end
```

## Functions

Functions are reusable blocks of code that perform specific tasks.

```lua
-- Function to calculate and print tax
function printTax(price)
  local tax = price * 0.21
  print("The tax is $" .. tax)
end

printTax(200) 
-- Output: The tax is $42
```

```lua
-- Function that returns a value
function calculateTax(price)
  return price * 0.21
end

local result = calculateTax(100)
print(result) 
-- Output: 21

-- Reusing the function with variables
local bread = 130
local milk = 110

local breadTax = calculateTax(bread)
-- Output: 27.3
local milkTax = calculateTax(milk) 
-- Output: 23.1

print("Bread Tax = " .. breadTax)
print("Milk Tax = " .. milkTax)
```

```lua
-- Function with multiple parameters
function displayInfo(name, age, origin)
  print(name .. " is " .. age .. " years old and is from " .. origin)
end

displayInfo("Ed", 12, "Peachcreek")
-- Output: Ed is 12 years old and is from Peachcreek
```

## Scope

Scope refers to the visibility and lifetime of variables within a program.

```lua
-- Local scope example
function foo()
  local a = 10
end

print(a) -- Output: nil (a is not accessible outside the function)
```

```lua
-- Block scope example
local isAlive = true
if isAlive then
  local a = 10
end

print(a) -- Output: nil (a is not accessible outside the if block)
```

### Global Variables

Be careful using global variables as they can cause errors which are hard to trace.

```lua
myValue = 69 -- No local declaration will create a global
```

## Loops

Loops are used to repeat a block of code multiple times.

```lua
-- While loop
local index = 0

while index <= 10 do
  index = index + 1
end

print("The current index is " .. index)
-- Output: The current index is 11
```

```lua
-- For loop
local count = 0

for index = 1, 5 do
  count = count + 1
end

print("The total count is " .. count)
-- Output: The total count is 5
```

### Infinite Loops

An infinite loop continues indefinitely unless explicitly broken (use with caution).

```lua
local index = 0

-- This loop will run forever, printing increasing numbers
while index >= 0 do
 index = index + 1
 print(index)
 -- Output: 1
 -- Output: 2
 -- Output: 3
 -- Output: ...
end
```

### Nested Loops

Loops can be nested within each other.

```lua
local count = 0

for index_one = 1, 10 do
  for index_two = 1, 10 do
    count = count + 1
  end
end

print(count)
-- Output: 100
```


## Tables

Tables are the primary data structure in Lua, these can be used to create more complex data structures.

```lua
-- Basic table (array-like)
local colors = { "red", "green", "blue" }

-- Tables start with index one, not with index zero as in C
print(colors[1]) -- Output: red
print(colors[2]) -- Output: green
print(colors[3]) -- Output: blue

-- Using a loop to iterate through your table
-- "#" returns the length of the table
for index = 1, #colors do
  print(colors[index])
end
```

### Table Manipulation
```lua
-- Insert at the end of the table
local colors = { "red", "green", "blue" }

table.insert(colors, "yellow")

local index = #colors -- 4 (this is the last index in the table)

print(colors[index])
-- Output: yellow
```

```lua
-- Insert at a specific index
local colors = { "red", "green", "blue" }

table.insert(colors, 2, "grey")

for index = 1, #colors do
  print(colors[index])
  -- Output: red, grey, green, blue
end
```

```lua
-- Remove from a specific index
local colors = { "red", "green", "blue" }

table.remove(colors, 1)

for index = 1, #colors do
  print(colors[index])
  -- Output: green, blue
end
```

### Two Dimensional Tables

Tables can contain other tables, creating multi-dimensional structures.

```lua
-- Tables within tables
local data = {
  {"Lee", 15},
  {"Marie" 13},
  {"May", 12}
}

for index = 1, #data do
  print(data[index][1] .. " is " .. data[index][2] .. " years old") 
  -- Output: Lee is 15 years old,
  -- Output: Marie is 13 years old,
  -- Output: May is 12 years old
end
```


### Key Tables

Tables can use keys instead of numeric indices, creating dictionary-like structures.

```lua
local teams = {
    ["team_a"] = 12,
    ["team_b"] = 15
}

print(teams["team_a"])
-- Output: 12

for key, value in pairs(teams) do
  print(key .. ":" .. value)
end

-- Insert into key table
teams["team_c"] = 1

-- Remove key from table
teams["team_a"] = nil
```


### Returning a Table from a Function

Functions can return tables, allowing for multiple return values.

```lua
function get_team_scores()
  local scores = {
    ["teamA"] = 12,
    ["teamB"] = 15
  }

  return scores
end

local scores = get_team_scores()
local total = 0

for key, value in pairs(scores) do
  total = total + value
end

print("Total score of all teams:" .. total)
-- Output: 27
```


## Math

Lua provides a math library with various mathematical functions.

[Users Wiki](http://lua-users.org/wiki/MathLibraryTutorial) / [Lua Documentation](https://www.lua.org/manual/5.3/manual.html#6.7)

```lua
-- Absolute value
local x = -10
print(math.abs(x))
-- Output: 10

-- Ceiling (round up)
local x = 1.2
print(math.ceil(x))
-- Output: 2

-- Convert radians to degrees
print(math.deg(math.pi))
-- Output: 180

-- Floor (round down)
local x = 1.2
print(math.floor(x))
-- Output: 1

-- Pi constant
print(math.pi)
-- Output: 3.14159...

-- Convert degrees to radians
print(math.rad(180))
-- Output: 3.14159...

-- Random number generation
print(math.random()) -- Random value between 0 and 1
print(math.random(100)) -- Random integer from 1 to 100
print(math.random(20, 100)) -- Random integer from 20 to 100

-- Square root
print(math.sqrt(100))
-- Output: 10
```

## Modules

Modules allow you to organize and reuse code across multiple files.

```lua
-- To include code from another file
require("another_file")
```