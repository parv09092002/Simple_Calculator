import argparse


def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y == 0:
        return "Error: Division by zero"
    return x / y


def calculator(operation, num1, num2):
    if operation == '1':
        print(f"{num1} + {num2} = {add(num1, num2)}")
    elif operation == '2':
        print(f"{num1} - {num2} = {subtract(num1, num2)}")
    elif operation == '3':
        print(f"{num1} * {num2} = {multiply(num1, num2)}")
    elif operation == '4':
        print(f"{num1} / {num2} = {divide(num1, num2)}")
    else:
        print("Invalid input")


if name == "__main__":
    parser = argparse.ArgumentParser(description="Simple Calculator")

    
    parser.add_argument("operation", nargs='?', help="Operation: 1 (Add), 2 (Subtract), 3 (Multiply), 4 (Divide)")
    parser.add_argument("num1", nargs='?', type=float, help="First number for the calculation")
    parser.add_argument("num2", nargs='?', type=float, help="Second number for the calculation")

    
    args = parser.parse_args()

    
    if not args.operation or not args.num1 or not args.num2:
        # If arguments are missing, prompt the user for input interactively
        print("Simple Calculator~")
        print("Select operation:")
        print("1. Add")
        print("2. Subtract")
        print("3. Multiply")
        print("4. Divide")
        
        operation = input("Enter choice (1/2/3/4): ")
        num1 = float(input("Enter first number: "))
        num2 = float(input("Enter second number: "))
    else:
        # If arguments are provided, use them
        operation = args.operation
        num1 = args.num1
        num2 = args.num2

    
    calculator(operation, num1, num2)
