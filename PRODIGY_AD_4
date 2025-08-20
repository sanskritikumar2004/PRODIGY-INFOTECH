import tkinter as tk
from tkinter import messagebox, simpledialog

# Functions
def add_task():
    task = entry.get()
    if task.strip() != "":
        listbox.insert(tk.END, task)
        entry.delete(0, tk.END)
    else:
        messagebox.showwarning("Input Error", "Task cannot be empty!")

def delete_task():
    selected_task = listbox.curselection()
    if selected_task:
        listbox.delete(selected_task)
    else:
        messagebox.showwarning("Selection Error", "Please select a task to delete.")

def edit_task():
    selected_task = listbox.curselection()
    if selected_task:
        current_task = listbox.get(selected_task)
        new_task = simpledialog.askstring("Edit Task", "Modify task:", initialvalue=current_task)
        if new_task and new_task.strip() != "":
            listbox.delete(selected_task)
            listbox.insert(selected_task, new_task)
    else:
        messagebox.showwarning("Selection Error", "Please select a task to edit.")

# Main GUI window
root = tk.Tk()
root.title("To-Do List")
root.geometry("400x400")

# Input field
entry = tk.Entry(root, width=30, font=('Arial', 14))
entry.pack(pady=10)

# Buttons
button_frame = tk.Frame(root)
button_frame.pack(pady=5)

add_button = tk.Button(button_frame, text="Add Task", width=10, command=add_task)
add_button.grid(row=0, column=0, padx=5)

edit_button = tk.Button(button_frame, text="Edit Task", width=10, command=edit_task)
edit_button.grid(row=0, column=1, padx=5)

delete_button = tk.Button(button_frame, text="Delete Task", width=10, command=delete_task)
delete_button.grid(row=0, column=2, padx=5)

# Task List
listbox = tk.Listbox(root, width=40, height=15, font=('Arial', 12), selectmode=tk.SINGLE)
listbox.pack(pady=10)

# Run the app
root.mainloop()
