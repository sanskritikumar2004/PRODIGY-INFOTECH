import tkinter as tk

# Global variables
running = False
counter = 0  # time in milliseconds


def update_time():
    global counter
    if running:
        counter += 1
        # Convert counter (ms) to minutes, seconds, ms
        minutes, seconds = divmod(counter // 100, 60)
        milliseconds = counter % 100
        time_display = f"{minutes:02d}:{seconds:02d}:{milliseconds:02d}"
        label.config(text=time_display)
        # Call update_time again after 10 ms
        root.after(10, update_time)


def start():
    global running
    if not running:
        running = True
        update_time()


def pause():
    global running
    running = False


def reset():
    global running, counter
    running = False
    counter = 0
    label.config(text="00:00:00")


# GUI Setup
root = tk.Tk()
root.title("Stopwatch")
root.geometry("300x200")

# Display label
label = tk.Label(root, text="00:00:00", font=("Arial", 40), fg="black")
label.pack(pady=20)

# Buttons frame
button_frame = tk.Frame(root)
button_frame.pack(pady=10)

start_btn = tk.Button(button_frame, text="Start", width=8, command=start)
start_btn.grid(row=0, column=0, padx=5)

pause_btn = tk.Button(button_frame, text="Pause", width=8, command=pause)
pause_btn.grid(row=0, column=1, padx=5)

reset_btn = tk.Button(button_frame, text="Reset", width=8, command=reset)
reset_btn.grid(row=0, column=2, padx=5)

# Run
root.mainloop()
