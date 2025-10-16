import tkinter as tk
from tkinter import messagebox

def addition():
    try:
        nums = list(map(float, entry.get().split()))
        result.set(f"Result: {sum(nums)}")
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers separated by spaces.")

def subtraction():
    try:
        nums = list(map(float, entry.get().split()))
        if len(nums) != 2:
            raise ValueError
        result.set(f"Result: {nums[0] - nums[1]}")
    except ValueError:
        messagebox.showerror("Input Error", "Please enter exactly two numbers separated by space.")

def multiplication():
    try:
        nums = list(map(float, entry.get().split()))
        res = 1
        for num in nums:
            res *= num
        result.set(f"Result: {res}")
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers separated by spaces.")

def division():
    try:
        nums = list(map(float, entry.get().split()))
        if len(nums) != 2:
            raise ValueError
        if nums[1] == 0:
            raise ZeroDivisionError
        result.set(f"Result: {nums[0] / nums[1]}")
    except ZeroDivisionError:
        messagebox.showerror("Math Error", "Cannot divide by zero.")
    except ValueError:
        messagebox.showerror("Input Error", "Please enter exactly two numbers separated by space.")

def average():
    try:
        nums = list(map(float, entry.get().split()))
        result.set(f"Result: {sum(nums)/len(nums)}")
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers separated by spaces.")

# GUI Setup
root = tk.Tk()
root.title("Simple Calculator")
root.geometry("400x300")
root.resizable(False, False)

tk.Label(root, text="Enter numbers separated by space:", font=("Arial", 12)).pack(pady=10)

entry = tk.Entry(root, width=40, font=("Arial", 12))
entry.pack(pady=5)

tk.Button(root, text="Addition", width=15, command=addition).pack(pady=2)
tk.Button(root, text="Subtraction", width=15, command=subtraction).pack(pady=2)
tk.Button(root, text="Multiplication", width=15, command=multiplication).pack(pady=2)
tk.Button(root, text="Division", width=15, command=division).pack(pady=2)
tk.Button(root, text="Average", width=15, command=average).pack(pady=2)

result = tk.StringVar()
tk.Label(root, textvariable=result, font=("Arial", 14), fg="blue").pack(pady=10)

tk.Button(root, text="Exit", width=10, command=root.quit).pack(pady=5)

root.mainloop()


