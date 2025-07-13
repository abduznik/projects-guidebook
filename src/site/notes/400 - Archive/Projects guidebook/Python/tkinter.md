---
{"dg-publish":true,"dg-path":"Python/tkinter.md","permalink":"/python/tkinter/"}
---


# Tkinter: Build Stunning Desktop Apps with Python!

Tkinter is Python's standard library for creating graphical user interfaces (GUIs). It's perfect for building simple tools, utilities, and even complex applications right on your desktop.

## Why Tkinter?

*   **Included with Python:** No extra installation needed for basic use.
*   **Easy to Learn:** Relatively straightforward for beginners.
*   **Cross-Platform:** Your apps will run on Windows, macOS, and Linux.

## Your First Tkinter App: "Hello, GUI!"

Let's create a simple window that displays a greeting.

```python
import tkinter as tk

# 1. Create the main window
window = tk.Tk()
window.title("My First GUI App")
window.geometry("300x200") # Set window size

# 2. Create a widget (a Label to display text)
label = tk.Label(window, text="Hello, Tkinter World!", font=("Arial", 16))

# 3. Place the widget in the window
label.pack(pady=50) # Add some padding from the top

# 4. Start the event loop (keeps the window open and responsive)
window.mainloop()
```

### Explanation

*   `tk.Tk()`: Creates the main application window.
*   `window.title()`: Sets the title bar text.
*   `window.geometry()`: Defines the window's width and height.
*   `tk.Label()`: Creates a text display widget.
*   `label.pack()`: A simple layout manager that packs widgets into the window.
*   `window.mainloop()`: Starts the GUI event loop, listening for user interactions.

## Interactive Buttons: Making Things Happen!

Let's add a button that changes the label's text when clicked.

```python
import tkinter as tk

def change_greeting():
    label.config(text="Button was clicked!")

window = tk.Tk()
window.title("Interactive App")
window.geometry("300x200")

label = tk.Label(window, text="Click the button below", font=("Arial", 14))
label.pack(pady=20)

# Create a Button widget
button = tk.Button(window, text="Click Me!", command=change_greeting) # Link button to function
button.pack()

window.mainloop()
```

### Key Takeaway

The `command` attribute of a `Button` widget is used to specify a function that should be called when the button is pressed. Notice we pass the function name `change_greeting` without parentheses `()`.

## Getting User Input: The Entry Widget

Use the `Entry` widget to get single-line text input from the user.

```python
import tkinter as tk

def show_input():
    user_text = entry_field.get() # Get text from the Entry widget
    result_label.config(text=f"You typed: {user_text}")

window = tk.Tk()
window.title("Input Example")
window.geometry("400x150")

entry_field = tk.Entry(window, width=40, font=("Arial", 12))
entry_field.pack(pady=10)

submit_button = tk.Button(window, text="Show Text", command=show_input)
submit_button.pack()

result_label = tk.Label(window, text="", font=("Arial", 12, "bold"))
result_label.pack(pady=10)

window.mainloop()
```

## Exercise: Simple Temperature Converter

Create a Tkinter application with two `Entry` widgets (one for Celsius, one for Fahrenheit) and two buttons. When a button is clicked, convert the temperature from one unit to the other and display the result.

## Recommended Resources

*   **Real Python - Python GUI Programming With Tkinter:** [https://realpython.com/python-gui-tkinter/](https://realpython.com/python-gui-tkinter/)
*   **Tkinter Tutorial (Python Tutorial):** [https://www.pythontutorial.net/tkinter/](https://www.pythontutorial.net/tkinter/)

## Video Tutorial
<iframe src="https://www.youtube.com/embed/TbPIBC2-R40?si=WMFZTQRR1I3hLVgR" title="" style="width:100%; aspect-ratio:16/9" loading="lazy" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
