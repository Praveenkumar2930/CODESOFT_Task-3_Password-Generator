# Password Generator

## Overview

This Python script generates secure and random passwords based on user-defined criteria. It allows the user to specify the desired length of the password and whether to include uppercase letters, lowercase letters, numbers, and special characters.

## Features

- Generate passwords of a specified length
- Option to include:
  - Uppercase letters (A-Z)
  - Lowercase letters (a-z)
  - Numbers (0-9)
  - Special characters (!@#$%^&*()-_=+[]{}|;:',.<>?/)

## Requirements

- Python 3.x

## Usage


   
   


1. **Run the script**:

   ```bash
   python password_generator.py
   ```

2. **Follow the prompts** to generate a password based on your preferences.

## Example

```python
# Sample execution
$ python password_generator.py
Enter the desired length of the password: 12
Include uppercase letters? (yes/no): yes
Include lowercase letters? (yes/no): yes
Include numbers? (yes/no): yes
Include special characters? (yes/no): yes

Generated password: g7#A1t!Wq5m@
```

## Script Details

Here is the main script (`password_generator.py`):

```python
import tkinter as tk
from tkinter import ttk
import random

class PasswordGeneratorApp:
    def __init__(self, master):
        self.master = master
        self.master.title("Password Generator")

        self.create_widgets()

    def create_widgets(self):
        # Password Length Label and Entry
        length_label = ttk.Label(self.master, text="Password Length:")
        length_label.grid(row=0, column=0, padx=10, pady=10, sticky=tk.W)

        self.length_entry = ttk.Entry(self.master, width=10)
        self.length_entry.grid(row=0, column=1, padx=10, pady=10, sticky=tk.W)

        # Password Complexity Label and Combobox
        complexity_label = ttk.Label(self.master, text="Password Complexity:")
        complexity_label.grid(row=1, column=0, padx=10, pady=10, sticky=tk.W)

        self.complexity_combobox = ttk.Combobox(self.master, values=["Weak", "Strong", "Very Strong"])
        self.complexity_combobox.set("Strong")  # Default to "Strong"
        self.complexity_combobox.grid(row=1, column=1, padx=10, pady=10, sticky=tk.W)

        # Generate Password Button
        generate_button = ttk.Button(self.master, text="Generate Password", command=self.generate_password)
        generate_button.grid(row=2, column=0, columnspan=2, pady=10)

        # Display Generated Password Label
        self.password_label = ttk.Label(self.master, text="")
        self.password_label.grid(row=3, column=0, columnspan=2, padx=10, pady=10)

    def generate_password(self):
        try:
            # Get password length from the entry
            length = int(self.length_entry.get())

            # Validate the length
            if length <= 0:
                self.password_label.config(text="Invalid length. Please enter a positive integer.")
                return

            # Get complexity choice from the combobox
            complexity = self.complexity_combobox.get()

            # Generate the password based on complexity
            password = self._generate_password(length, complexity)

            # Display the generated password
            self.password_label.config(text=f"Generated Password: {password}")

        except ValueError:
            self.password_label.config(text="Invalid input. Please enter a valid integer for the password length.")
        except Exception as e:
            self.password_label.config(text=f"An error occurred: {e}")

    def _generate_password(self, length, complexity):
        # Define character sets for password generation
        lowercase_letters = "abcdefghijklmnopqrstuvwxyz"
        uppercase_letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        digits = "0123456789"
        special_characters = "!@#$%^&*_/"

        # Combine character sets based on complexity
        if complexity == "Weak":
            characters = lowercase_letters + uppercase_letters
        elif complexity == "Strong":
            characters = lowercase_letters + digits + uppercase_letters
        elif complexity == "Very Strong":
            characters = lowercase_letters + uppercase_letters + digits + special_characters
        else:
            raise ValueError("Invalid complexity choice")

        # Generate the password
        password = ''.join(random.choice(characters) for _ in range(length))
        return password

# Main application
root = tk.Tk()
app = PasswordGeneratorApp(root)
root.mainloop()
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## Contact

For any questions or suggestions, please open an issue or contact [@praveenkumaru101@gmail.com](mailto:your-praveenkumaru101@gmail.com).
