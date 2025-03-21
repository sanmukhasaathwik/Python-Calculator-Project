# Python-Calculator-Project
Developed a command-line calculator in Python that performs basic arithmetic operations, including addition, subtraction, multiplication, division, exponentiation, modulus, and floor division. Implemented a user-friendly interface with a loop for continuous calculations and an option to restart or exit.

import os

class Calculator:
    def __init__(self):
        self.num1 = None
        self.num2 = None
        self.operator_dict = {
            '1': ('Addition (+)', self.add),
            '2': ('Subtraction (-)', self.subtract),
            '3': ('Multiplication (*)', self.multiply),
            '4': ('Division (/)', self.divide),
            '5': ('Exponentiation (**)', self.exponentiate),
            '6': ('Floor Division (//)', self.floor_divide),
            '7': ('Modulus (%)', self.modulus),
            '8': ('Exit', None)
        }

    def get_number(self, prompt):
        while True:
            try:
                return float(input(prompt))
            except ValueError:
                print("Invalid input! Please enter a valid number.")

    def add(self, x, y):
        return x + y

    def subtract(self, x, y):
        return x - y

    def multiply(self, x, y):
        return x * y

    def divide(self, x, y):
        try:
            return x / y
        except ZeroDivisionError:
            return "Error! Division by zero is not allowed."

    def exponentiate(self, x, y):
        return x ** y

    def floor_divide(self, x, y):
        try:
            return x // y
        except ZeroDivisionError:
            return "Error! Division by zero is not allowed."

    def modulus(self, x, y):
        try:
            return x % y
        except ZeroDivisionError:
            return "Error! Division by zero is not allowed."

    def display_menu(self):
        print("\n📌 Available Operations:")
        for key, (name, _) in self.operator_dict.items():
            print(f"{key}. {name}")

    def calculate(self):
        while True:
            os.system('cls' if os.name == 'nt' else 'clear')  # It will clears the screen.
            self.display_menu()

            choice = input("\nEnter the number of the operation you want to perform: ")

            if choice == '8':
                print("Thank you for using the Python Calculator!")
                break

            if choice not in self.operator_dict:
                print("Invalid choice! Please select a valid operation.")
                input("Press Enter to continue...")
                continue

            self.num1 = self.get_number("Enter first number: ")
            self.num2 = self.get_number("Enter second number: ")

            operation_name, operation_function = self.operator_dict[choice]
            result = operation_function(self.num1, self.num2)

            print(f"{operation_name}: {self.num1} {' '.join(operation_name.split()[-1])} {self.num2} = {result}")
            input("\nPress Enter to continue...")

if __name__ == "__main__":
    calc = Calculator()
    calc.calculate()
