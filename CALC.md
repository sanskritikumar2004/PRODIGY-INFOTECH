# PRODIGY-INFOTECH
import tkinter as tk

# Function to evaluate expressions
def press(key):
    entry.insert(tk.END, key)

def clear():
    entry.delete(0, tk.END)

def calculate():
    try:
        result = eval(entry.get())  # Evaluate math expression
        entry.delete(0, tk.END)
        entry.insert(tk.END, str(result))
    except:
        entry.delete(0, tk.END)
        entry.insert(tk.END, "Error")

# Create main window
root = tk.Tk()
root.title("Calculator")
root.geometry("300x400")
root.resizable(False, False)

# Entry box
entry = tk.Entry(root, width=20, font=('Arial', 18), bd=8, relief='ridge', justify='right')
entry.grid(row=0, column=0, columnspan=4, padx=10, pady=10)

# Button layout
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('=', 4, 2), ('+', 4, 3),
]

# Create buttons dynamically
for (text, row, col) in buttons:
    if text == "=":
        action = calculate
    else:
        action = lambda x=text: press(x)
    tk.Button(root, text=text, width=6, height=2, font=('Arial', 14),
              command=action).grid(row=row, column=col, padx=5, pady=5)

# Clear button
tk.Button(root, text="C", width=26, height=2, font=('Arial', 14), command=clear).grid(
    row=5, column=0, columnspan=4, padx=5, pady=5
)

# Run the application
root.mainloop()
