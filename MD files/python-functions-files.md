# 🔧 Python Functions, Modules, and File Operations

## Welcome to Advanced Python Concepts! 
Learn how to write reusable code and handle files like a pro! 

### What We'll Learn 🎯
- Creating and using functions
- Working with modules
- Reading and writing files
- Real-world applications

---

## 1. Functions: Your Code Building Blocks 🏗️

Functions are reusable pieces of code that perform specific tasks.

```python
# Basic function definition
def greet(name):
    """This is a docstring - it explains what the function does"""
    return f"Hello, {name}!"

# Using the function
print(greet("Python Learner"))

# Function with multiple parameters
def calculate_total(price, tax_rate=0.1):
    """Calculate total price including tax"""
    tax = price * tax_rate
    return price + tax

# Using default parameters
print(f"Total with default tax: ${calculate_total(100):.2f}")
print(f"Total with custom tax: ${calculate_total(100, 0.15):.2f}")

# Function with multiple returns
def check_number(num):
    if num > 0:
        return "Positive"
    elif num < 0:
        return "Negative"
    return "Zero"

print(check_number(-5))
```

### 🎯 Practice: Create Your Own Functions
```python
# Temperature converter function
def convert_temperature(temp, from_unit='C'):
    """Convert between Celsius and Fahrenheit"""
    if from_unit.upper() == 'C':
        result = (temp * 9/5) + 32
        return f"{temp}°C = {result:.1f}°F"
    else:
        result = (temp - 32) * 5/9
        return f"{temp}°F = {result:.1f}°C"

# Test the function
print(convert_temperature(100))  # Celsius to Fahrenheit
print(convert_temperature(212, 'F'))  # Fahrenheit to Celsius
```

---

## 2. Advanced Function Concepts 🚀

```python
# Function with *args (variable number of arguments)
def calculate_average(*numbers):
    """Calculate average of any number of values"""
    return sum(numbers) / len(numbers)

print(f"Average of 2, 4, 6: {calculate_average(2, 4, 6)}")
print(f"Average of 1, 2, 3, 4, 5: {calculate_average(1, 2, 3, 4, 5)}")

# Function with **kwargs (keyword arguments)
def create_profile(**details):
    """Create a user profile from keyword arguments"""
    profile = []
    for key, value in details.items():
        profile.append(f"{key}: {value}")
    return "\n".join(profile)

# Using **kwargs
profile = create_profile(name="John", age=25, city="New York", hobby="Coding")
print(f"\nProfile:\n{profile}")

# Lambda functions (anonymous functions)
square = lambda x: x**2
print(f"\nSquare of 5: {square(5)}")
```

---

## 3. Modules: Using Python's Power 📚

```python
# Importing built-in modules
import random
import math
from datetime import datetime

# Using random module
print("\n🎲 Random Module Examples:")
print(f"Random number (1-100): {random.randint(1, 100)}")
print(f"Random choice from list: {random.choice(['apple', 'banana', 'orange'])}")

# Using math module
print("\n📐 Math Module Examples:")
print(f"Square root of 16: {math.sqrt(16)}")
print(f"Pi: {math.pi:.4f}")

# Using datetime
print("\n📅 DateTime Examples:")
print(f"Current date and time: {datetime.now()}")
```

### 🎯 Practice: Create Your Own Module
```python
# Save this in a file named 'utils.py'
def is_palindrome(text):
    """Check if text is palindrome"""
    clean_text = ''.join(char.lower() for char in text if char.isalnum())
    return clean_text == clean_text[::-1]

def count_vowels(text):
    """Count vowels in text"""
    return sum(1 for char in text.lower() if char in 'aeiou')

# In another file:
# from utils import is_palindrome, count_vowels
```

---

## 4. File Handling: Working with Files 📂

```python
# Writing to a file
def write_to_file():
    with open('example.txt', 'w') as file:
        file.write("Hello, this is line 1\n")
        file.write("This is line 2\n")
        file.write("And this is line 3")

# Reading from a file
def read_file():
    try:
        with open('example.txt', 'r') as file:
            content = file.read()
            print("📄 File contents:")
            print(content)
    except FileNotFoundError:
        print("File not found!")

# Append to a file
def append_to_file(text):
    with open('example.txt', 'a') as file:
        file.write(f"\n{text}")

# Write and read demonstration
write_to_file()
read_file()
append_to_file("This line was appended!")
read_file()
```

### 🎯 Practice: File Operations
```python
# Create a simple note-taking program
def note_taking_app():
    while True:
        print("\n📝 Note Taking App")
        print("1. Add note")
        print("2. View notes")
        print("3. Exit")
        
        choice = input("Choose an option (1-3): ")
        
        if choice == '1':
            note = input("Enter your note: ")
            with open('notes.txt', 'a') as file:
                file.write(f"{datetime.now()}: {note}\n")
            print("✅ Note saved!")
            
        elif choice == '2':
            try:
                with open('notes.txt', 'r') as file:
                    print("\n📖 Your Notes:")
                    print(file.read())
            except FileNotFoundError:
                print("No notes found!")
                
        elif choice == '3':
            print("👋 Goodbye!")
            break

# Run the note-taking app
note_taking_app()
```

## 5. Working with CSV Files 📊

```python
import csv

# Writing to CSV
def write_csv_example():
    data = [
        ['Name', 'Age', 'City'],
        ['John', 25, 'New York'],
        ['Emma', 28, 'London'],
        ['Carlos', 22, 'Madrid']
    ]
    
    with open('people.csv', 'w', newline='') as file:
        writer = csv.writer(file)
        writer.writerows(data)

# Reading from CSV
def read_csv_example():
    with open('people.csv', 'r') as file:
        reader = csv.reader(file)
        print("\n📊 CSV Contents:")
        for row in reader:
            print(f"{', '.join(row)}")

# Demo CSV operations
write_csv_example()
read_csv_example()
```

---

## 🎉 Congratulations!

You've learned:
- Creating and using functions
- Working with modules
- File operations (read/write)
- CSV file handling

### 📚 Practice Ideas
1. Create a module with utility functions
2. Build a file-based task manager
3. Create a CSV data analyzer
4. Build a simple logging system

### 🎯 Challenge Project: Personal Journal
Create a program that:
- Allows writing daily journal entries
- Saves entries with timestamps
- Supports reading past entries
- Includes search functionality

Remember: The best way to learn is by doing! Try combining functions, modules, and file operations in your projects! 🚀
