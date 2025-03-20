# Python-Calculator-Project
Developed a command-line calculator in Python that performs basic arithmetic operations, including addition, subtraction, multiplication, division, exponentiation, modulus, and floor division. Implemented a user-friendly interface with a loop for continuous calculations and an option to restart or exit.

import os
        
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    return x / y

def exponential(x, y):
    return x ** y

def Floor_division(x, y):
    return x // y

def Modulus(x, y):
    return x % y

operator_dict = {
    '+': add,
    '-': subtract,
    '*': multiply,
    '/': divide,
    '**': exponential,
    '//': Floor_division,
    '%': Modulus
}


def calculator():
    num1 = float(input("Enter first number: "))
    for symbol in operator_dict:
        print(symbol)
        
    continue_operation = True
    
    while continue_operation:
        operator_symbol = input("Pick an operation: ")
        
        num2 = float(input("Enter next number: "))
        calculator_function = operator_dict[operator_symbol]
        output = calculator_function(num1, num2)
        print(f"{num1} {operator_symbol} {num2} = {output}")
        
        should_continue = input(f"Type 'y' to continue calculating with {output}, or type 'n' to start a new calculation: , or type 'x' to exit the calculator: ")
        if should_continue == 'y':
            num1 = output
        elif should_continue == 'n':
            continue_operation = False
            os.system('cls')
            calculator()
        else:
            continue_operation = False
            print("Thank you for using the Calculator using Python!")

calculator()
