# 🎮 Object-Oriented Programming in Python

## Welcome to the World of OOP! 
Learn how to structure your code using objects and classes - the building blocks of modern software.

### What We'll Learn 🎯
- Classes and Objects
- Attributes and Methods
- Inheritance and Polymorphism
- Encapsulation and Abstraction
- Real-world OOP examples

---

## 1. Classes and Objects: The Building Blocks 🏗️

```python
# Basic Class Definition
class Dog:
    # Class attribute
    species = "Canis familiaris"
    
    # Constructor (initializer) method
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute
    
    # Instance method
    def bark(self):
        return f"{self.name} says Woof!"
    
    def info(self):
        return f"{self.name} is {self.age} years old"

# Creating objects (instances) of the class
buddy = Dog("Buddy", 5)
luna = Dog("Luna", 3)

# Using our objects
print(buddy.bark())
print(luna.info())
print(f"Both {buddy.name} and {luna.name} are {Dog.species}")
```

### 🎯 Practice: Create Your First Class
```python
# Create a Student class
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
        self.courses = []
    
    def add_course(self, course):
        self.courses.append(course)
        return f"{self.name} enrolled in {course}"
    
    def get_info(self):
        courses_info = ", ".join(self.courses) if self.courses else "No courses"
        return f"Student: {self.name}\nGrade: {self.grade}\nCourses: {courses_info}"

# Test the Student class
student1 = Student("Alice", 10)
print(student1.add_course("Python Programming"))
print(student1.add_course("Web Development"))
print("\n" + student1.get_info())
```

---

## 2. Inheritance: Building on Existing Classes 👨‍👦

```python
# Parent class
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species
    
    def make_sound(self):
        return "Some generic sound"

# Child classes
class Cat(Animal):
    def __init__(self, name, breed):
        super().__init__(name, species="Felis catus")
        self.breed = breed
    
    def make_sound(self):
        return f"{self.name} says Meow!"

class Bird(Animal):
    def __init__(self, name, can_fly=True):
        super().__init__(name, species="Aves")
        self.can_fly = can_fly
    
    def make_sound(self):
        return f"{self.name} says Tweet!"

# Creating instances
kitty = Cat("Whiskers", "Persian")
birdy = Bird("Tweety")

print(kitty.make_sound())
print(birdy.make_sound())
print(f"Is {birdy.name} a {birdy.species}? Yes!")
```

### 🎯 Practice: Vehicle Hierarchy
```python
class Vehicle:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year
    
    def start_engine(self):
        return "Engine started!"

class Car(Vehicle):
    def __init__(self, brand, model, year, fuel_type="Gasoline"):
        super().__init__(brand, model, year)
        self.fuel_type = fuel_type
        self.wheels = 4
    
    def honk(self):
        return "Beep beep!"

class ElectricCar(Car):
    def __init__(self, brand, model, year, battery_capacity):
        super().__init__(brand, model, year, fuel_type="Electric")
        self.battery_capacity = battery_capacity
    
    def start_engine(self):
        return "Silent start... Ready to go!"

# Test the vehicles
tesla = ElectricCar("Tesla", "Model 3", 2023, "75kWh")
toyota = Car("Toyota", "Camry", 2022)

print(f"{tesla.brand} {tesla.model}: {tesla.start_engine()}")
print(f"{toyota.brand} {toyota.model}: {toyota.start_engine()}")
```

---

## 3. Encapsulation: Protecting Data and Methods 🔒

```python
class BankAccount:
    def __init__(self, owner, initial_balance=0):
        self._owner = owner  # Protected attribute
        self.__balance = initial_balance  # Private attribute
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return f"Deposited ${amount}. New balance: ${self.__balance}"
        return "Invalid deposit amount"
    
    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return f"Withdrew ${amount}. New balance: ${self.__balance}"
        return "Insufficient funds or invalid amount"
    
    def get_balance(self):
        return f"Current balance: ${self.__balance}"

# Using the BankAccount class
account = BankAccount("John Doe", 1000)
print(account.deposit(500))
print(account.withdraw(200))
print(account.get_balance())
# print(account.__balance)  # This would raise an error
```

---

## 4. Polymorphism: Many Forms, One Interface 🔄

```python
class Shape:
    def area(self):
        pass
    
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
        self.pi = 3.14159
    
    def area(self):
        return self.pi * self.radius ** 2
    
    def perimeter(self):
        return 2 * self.pi * self.radius

# Using polymorphism
def print_shape_info(shape):
    print(f"Area: {shape.area():.2f}")
    print(f"Perimeter: {shape.perimeter():.2f}")

# Test different shapes
rect = Rectangle(5, 3)
circ = Circle(4)

print("Rectangle:")
print_shape_info(rect)
print("\nCircle:")
print_shape_info(circ)
```

---

## 5. Final Project: Game Character System 🎮

```python
class Character:
    def __init__(self, name, level=1):
        self.name = name
        self.level = level
        self.health = level * 100
        self.is_alive = True

    def take_damage(self, damage):
        self.health -= damage
        if self.health <= 0:
            self.health = 0
            self.is_alive = False
        return f"{self.name} took {damage} damage. Health: {self.health}"

    def heal(self, amount):
        if self.is_alive:
            self.health += amount
            return f"{self.name} healed for {amount}. Health: {self.health}"
        return f"{self.name} is defeated and cannot heal"

class Warrior(Character):
    def __init__(self, name, level=1):
        super().__init__(name, level)
        self.armor = level * 10
        
    def take_damage(self, damage):
        reduced_damage = max(0, damage - self.armor)
        return super().take_damage(reduced_damage)
    
    def battle_cry(self):
        return f"{self.name}: For glory!"

class Mage(Character):
    def __init__(self, name, level=1):
        super().__init__(name, level)
        self.mana = level * 50
        
    def cast_spell(self, cost):
        if self.mana >= cost:
            self.mana -= cost
            return f"{self.name} cast a spell! Mana left: {self.mana}"
        return f"{self.name} is out of mana!"

# Test the game system
warrior = Warrior("Conan", 5)
mage = Mage("Gandalf", 4)

print(warrior.battle_cry())
print(warrior.take_damage(70))
print(mage.cast_spell(100))
print(mage.take_damage(50))
print(warrior.heal(30))
```

---

## 🎉 Congratulations!

You've learned:
- Creating classes and objects
- Inheritance and its benefits
- Data protection with encapsulation
- Polymorphic behavior
- Real-world OOP applications

### 📚 Practice Ideas
1. Create a library management system
2. Build a simple RPG character system
3. Design a school management system
4. Implement a banking system

### 🎯 Challenge Project: E-Commerce System
Create a system with:
- Product classes
- Shopping cart functionality
- User accounts
- Order processing

Remember: OOP is about organizing code in a way that mirrors real-world relationships! 🚀
