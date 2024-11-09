# 🎤 Kanye Quote Generator
This Python application displays random Kanye West quotes using the Kanye Rest API. Each time you press the button, a new quote appears in the application window.

## 📂 Project Structure
- **get_quote**: Fetches a random quote from the Kanye Rest API and displays it on the canvas.
- **User Interface**: A simple Tkinter interface featuring a button with Kanye's image and a canvas for displaying quotes.
---
## 🔧 Code Explanation
### 1. Import Libraries and Define get_quote
```python
from tkinter import *
import requests

def get_quote():
    response = requests.get("https://api.kanye.rest")
    response.raise_for_status()
    data = response.json()
    quote = data["quote"]
    canvas.itemconfig(quote_text, text=quote)
```
- get_quote: Sends a request to the Kanye Rest API and retrieves a random quote. The quote is then updated on the canvas using itemconfig.
### 2. Set Up the Tkinter Window and Canvas
```python
window = Tk()
window.title("Kanye Says...")
window.config(padx=50, pady=50)

canvas = Canvas(width=300, height=414)
background_img = PhotoImage(file="background.png")
canvas.create_image(150, 207, image=background_img)
quote_text = canvas.create_text(150, 207, text="Kanye Quote Goes HERE", width=250, font=("Arial", 30, "bold"), fill="white")
canvas.grid(row=0, column=0)
```
- window: Initializes the main Tkinter window, adding padding for a clean layout.
- canvas: Creates a canvas for displaying the background image and the quote text.
- background_img: Adds an image (background.png) to the canvas as a background for the quote.
### 3. Add Button to Fetch New Quote
```python
kanye_img = PhotoImage(file="kanye.png")
kanye_button = Button(image=kanye_img, highlightthickness=0, command=get_quote)
kanye_button.grid(row=1, column=0)
```
- kanye_button: Displays an image (kanye.png) and, when clicked, triggers get_quote to fetch and display a new quote.
### 4. Run the Application
```python
window.mainloop()
```
- mainloop: Runs the Tkinter event loop, allowing the window to stay open and respond to user interactions.
---
## 📝 Setup Instructions
1. Install Required Libraries: Ensure you have the requests library installed:
```bash
pip install requests
```
2. Download Images: Place background.png and kanye.png in the same directory as the script.
3. Run the Application:
```bash
python script_name.py
```
4. Usage: Click the button to fetch and display a new Kanye quote.
---
