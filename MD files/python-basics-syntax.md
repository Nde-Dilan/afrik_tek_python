# 🐍 Python Basics: Your First Steps into Programming

## Welcome to Python Programming! 
This notebook will introduce you to the fundamental building blocks of Python. Let's make learning Python fun and practical! 

### What We'll Learn 🎯
- Python syntax and basic rules
- Variables and how to use them
- Different data types
- Operators and their magic
- Real-world applications

---

## 1. Python Syntax: The Grammar of Code 📝

Python is known for its clean and readable syntax. Let's see some basic rules:

```python
# This is a comment - Python ignores everything after #
print("Hello, Python Learner!")  # Comments can also be at the end of lines

# Python uses indentation for code blocks
if True:
    print("This line is indented")  # Notice the 4 spaces/1 tab
print("This line is not indented")

# Multiple statements in one line (not recommended but possible)
print("First"); print("Second")

# Long line split into multiple lines using \
long_text = "This is a very long line of code that \
            continues on the next line"
```

### 🎯 Practice: Fix the Syntax
```python
# Try to fix these syntax errors!
# Uncomment and run each line separately

#print "Hello"  # What's missing?
#if True
#    print("Indented")
#print("Multiple" print("prints"))
```

---

## 2. Variables: Storing Data 📦

Variables are like containers that store data. Python makes it easy!

```python
# Basic variable assignment
name = "Python Learner"
age = 25
height = 1.75
is_student = True

# Multiple assignment
x, y, z = 1, 2, 3

# Print variables
print(f"Name: {name}")
print(f"Age: {age}")
print(f"Height: {height}")
print(f"Student Status: {is_student}")

# Variable naming rules demonstration
valid_name = "Good"
_also_valid = "Good"
# 1invalid = "Bad"  # Can't start with number
camelCase = "Valid but not Python convention"
snake_case = "Python's preferred naming style"
```

### 🎯 Practice: Create Your Profile
```python
# Create variables for your profile
your_name = input("Enter your name: ")
your_age = int(input("Enter your age: "))
your_favorite_number = float(input("Enter your favorite number: "))

# Calculate some fun facts
days_lived = your_age * 365
seconds_lived = days_lived * 24 * 60 * 60

print(f"\n🎉 {your_name}'s Profile 🎉")
print(f"Age in days: {days_lived:,}")
print(f"Age in seconds: {seconds_lived:,}")
print(f"Your favorite number doubled: {your_favorite_number * 2}")
```

---

## 3. Data Types: Different Flavors of Data 🍨

Python has several basic data types. Let's explore them!

```python
# Numbers
integer_number = 42
float_number = 3.14
complex_number = 1 + 2j

# Strings
single_quotes = 'Hello'
double_quotes = "Hello"
multi_line = """This is a
multi-line
string"""

# Boolean
is_true = True
is_false = False

# None type
empty_value = None

# Check types
print(f"Type of 42: {type(integer_number)}")
print(f"Type of 3.14: {type(float_number)}")
print(f"Type of 'Hello': {type(single_quotes)}")
print(f"Type of True: {type(is_true)}")
```

### 🎯 Practice: Type Explorer
```python
# Let's explore type conversion
number_string = "123"
string_to_int = int(number_string)
string_to_float = float(number_string)

print(f"Original: {number_string} ({type(number_string)})")
print(f"As integer: {string_to_int} ({type(string_to_int)})")
print(f"As float: {string_to_float} ({type(string_to_float)})")

# Try some conversions
age = input("Enter your age: ")
next_year_age = int(age) + 1
print(f"Next year you'll be {next_year_age}!")
```

---

## 4. Operators: The Tools of Mathematics 🧮

Python provides various operators for different operations.

```python
# Arithmetic Operators
print("🔢 Arithmetic Operators")
print(f"Addition: 5 + 3 = {5 + 3}")
print(f"Subtraction: 5 - 3 = {5 - 3}")
print(f"Multiplication: 5 * 3 = {5 * 3}")
print(f"Division: 5 / 3 = {5 / 3}")
print(f"Floor Division: 5 // 3 = {5 // 3}")
print(f"Modulus: 5 % 3 = {5 % 3}")
print(f"Exponentiation: 5 ** 3 = {5 ** 3}")

# Comparison Operators
print("\n🔍 Comparison Operators")
x, y = 5, 3
print(f"x = {x}, y = {y}")
print(f"x > y: {x > y}")
print(f"x < y: {x < y}")
print(f"x == y: {x == y}")
print(f"x != y: {x != y}")
print(f"x >= y: {x >= y}")
print(f"x <= y: {x <= y}")

# Logical Operators
print("\n🧠 Logical Operators")
a, b = True, False
print(f"a and b: {a and b}")
print(f"a or b: {a or b}")
print(f"not a: {not a}")
```

### 🎯 Final Challenge: Build a Simple Calculator
```python
def calculator():
    print("🧮 Simple Calculator 🧮")
    num1 = float(input("Enter first number: "))
    operator = input("Enter operator (+, -, *, /): ")
    num2 = float(input("Enter second number: "))
    
    if operator == "+":
        result = num1 + num2
    elif operator == "-":
        result = num1 - num2
    elif operator == "*":
        result = num1 * num2
    elif operator == "/":
        result = num1 / num2 if num2 != 0 else "Cannot divide by zero!"
    else:
        result = "Invalid operator!"
    
    print(f"\nResult: {result}")

# Run the calculator
calculator()
```

---

## 🎉 Congratulations! 

You've learned the basic building blocks of Python programming:
- Syntax rules and structure
- Variables and their usage
- Different data types
- Operators and calculations

### 📚 Practice Tips
- Experiment with different variable types
- Try combining different operators
- Write small programs using what you've learned
- Don't be afraid to make mistakes - they're part of learning!

### 🎯 Mini Homework
1. Create variables of each data type
2. Write a program that converts temperature between Celsius and Fahrenheit
3. Create a more advanced calculator with additional operations

Remember: Programming is like learning a new language - practice makes perfect! 🚀
